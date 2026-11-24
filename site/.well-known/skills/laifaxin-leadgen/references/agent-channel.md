---
doc_id: laifaxin-agent-channel
title: 官方 Agent 通道（接口映射与调用纪律）
description: 来发信官方 Agent Skill 作为本 skill 首选执行通道的接入、接口映射（带证据等级）、调用纪律与降级规则；绑箱动作维持网页通道。
status: active
updated: 2026-11-20
owner: 贸知事
---

# 官方 Agent 通道（接口映射与调用纪律）

## 这是什么

来发信官方提供的 Agent 接入（接入页 https://agent.laifa.xin ）：一个装在用户本机的官方 Skill，通过网页授权拿到一枚可单独撤销的应用凭据，之后调用来发信平台的 Web 接口完成查询与操作。本 skill 把它定为**首选执行通道**：规则、台账、额度闸与发送确认闸仍全部在本 skill，官方通道只负责「把操作送达平台」，它只换执行路径——接口直达，不再逐页模拟点击；稳不稳以各接口的证据等级为准（见下表），不预设。

## 接入与授权（细则在 SKILL.md §1.1 第 1 步、§1.2）

1. 安装：按接入页现行说明装官方 Skill（一行安装或压缩包手工安装，装到宿主的技能目录）。
2. 配置与授权：由 AI 发起网页授权，把授权链接与用户码**原样**发给用户；用户本人在网页登录、核对用户码一致、选对工作空间、点「允许授权」；官方工具随即在用户本机完成凭据的交换与保存（AI 不接触凭据本身），AI 只查连接状态，账号与工作空间读回正确才算连上。用户明确选择委托代办时，按 SKILL §1.1 的保险库路径走：AI 弹出所在助手自带的安全凭据录入卡，用户在卡里填账号密码存入保险库（AI 看不到明文、不发链接或自制表单；无此卡时才引导用户自己打开凭据保管，无保险库则回默认路径），AI 只打开官方工具给出的授权链接、用保险库凭据登录（凭据由保险库填充、AI 不读明文），逐字核对用户码与工作空间无误才代点允许，核对不上即停手转用户；委托只管这一次授权，遇滑块、短信等真人验证立即停手、转用户本人，验证码也不经聊天代填；用户没明确委托，走本人点允许的默认路径。
3. 查连接状态只读官方工具的输出（凭据字段由其自动遮盖）；万一见到未遮盖的凭据值，立即停手、不复制、不记录、不写进任何文件。凭据由官方工具保存在用户本机（权限受限的配置文件），**本 skill 不读取、不保存、不经手**；有效期 30 天、无自动续期，到期重走第 2 步（用户再点一次允许）。撤销路径（实站核正）：授权确认页底部有「管理已授权应用」入口，点开即达已授权应用管理页（api.laifaxin.com/account/authorized-apps），用户可随时在那里撤销。
4. 授权失败或过期：把平台返回的提示如实告诉用户并重走授权；**不改用密码登录、不读取浏览器 Cookie 或会话**（官方连接口径，与 R23 一致）。
5. 宿主跑不了本机脚本时本通道不可用，按 SKILL.md §1.4 降级卡全面回网页操作。

## 接口映射（证据等级按 R26 标注）

证据等级说明：**读实测**＝2026-11-16 以个人 SVIP 账号（z7pvxh）经网页授权凭据逐一真实调用成功，实测接口共四个：/expenses/give-status、/sequences/sequence-list、/contacts/companies/show、/mails/mails-list；表中标「读：实测」的行即指这四个，其余读接口仍属契约级；**契约级**＝官方接口目录在册、参数契约经官方前端源码核对吻合，写操作未在真实账号试执行——首次经接口执行时按 §4 章首要求先小步验证、回读确认再放量。

| 本 skill 操作 | 官方接口（路径） | 证据等级 |
| --- | --- | --- |
| 搜客·AI 数据库（找新客） | /refine/company-list（关键词/客群 query_en；**结果不带 domain 字段，取种子域名须另调 /domain/base-info**）、/refine/company-list-by-name、/domain/resolve-domain-name | 实测（2026-11-18） |
| 搜客·已保存公司检索 | /contacts/company-search（**只搜账号已保存公司**，客户管理内按名检索用；不用于搜新客）、/contacts/people-search（**只搜账号已保存联系人**，与 company-search 同口径；不用于搜新客） | company-search 实测（2026-11-18）；people-search 契约级 |
| 公司详情 | /domain/base-info（公司 id 或域名均可） | 实测（2026-11-18） |
| 搜相似【禁用】 | /domain/similar-list | **禁用，不许调用**（Tony 2026-11-21 令）：接口保留登记仅作识别；找相似公司一律改走 /refine/company-list 关键词搜索（§4.1、§5.2(e)）。历史实测记录：2026-11-18 接口调用实测通过，跨语种相关性为单种子抽样观察（德语种子前 5 家 5/5 相关，非全量验证） |
| AI 推演客群 | /profile/inference-product-add、inference-segment-generate、inference-segment-list、inference-product-save | 实测（2026-11-18；建产品与生成客群各扣 2 点） |
| 批量搜索任务 | /refine/task-create、task-list、task-info、task-status、task-delete | 链路实测可用（2026-11-18 阶段 0：create 建完即 finished、delete 后 list 回读确认已删、info 可读回）；**计费口径未证实**（源码口径「有效 −2/未知 −1/无效 0」在本轮实测中未发生——任务计数全 0、creditCount 前后不变，不得作为计费依据，待后续核实） |
| 搜客·领英/地图/谷歌 | /search/linkedin-company-v2-*、/search/map-data-*、/clouds/google-search/* | 契约级 |
| AI 评分全流程 | /clues/rating-task-*（启/停/改名/删/查——**该族没有「建任务」端点**）、/clues/rating-result-*（结果/存联系人/存禁发）；**建评分任务按来源走**：AI 数据库 /refine/company-rating、领英 /search/linkedin-company-rating、结果页重评 /clues/rating-result-rating-again | 契约级（含存联系人/存禁发等写动作，未实测） |
| 保存与管理联系人/公司 | 公司本体新建 /contacts/company/add、保存 /contacts/company/save；批量改字段 /contacts/companies/save（**不是保存口**：选择集＋changeField/changeType/changeValue 批量改字段，配方见下「公司字段回写配方」）；/contacts/* 管理族 | 读：实测｜写：部分实测（companies/save 批量改 short_description、phone_number 已实测可写；contact/add 带 c_id 写入与回查已实测；contact/delete 已实测；company/add、company/save 契约级，其余管理族契约级） |
| 补关联/补字段（查重命中后） | /contacts/contact/save（saveContactField 语义：{cid, 字段名: 值} 逐字段保存）；撞重取 cid 走 /contacts/contacts/show 的 email 精确匹配回查（/contacts/email-info 契约级） | 实测（2026-11-19：{cid, c_id, c_name} 改挂公司落地、{cid, remark} 可写、补后回读已核；**name 字段传值返回 success 但回读不生效，补姓名走网页端联系人编辑**） |
| 公司字段注册表 | /fields/company-fields（belongTo:"company", saveType:"read"，17 个系统字段） | 实测（2026-11-18） |
| 发件身份（系统通道昵称） | /mailbox/sender-list、sender-save、sender-add、sender-check | list 读实测；save 写读往返实测（2026-11-18 阶段 0）；add/check 源码级 |
| 平台产品档案（卖家档案） | /profile/product-list、product-add、product-save、product-delete、product-default | list 实测；add/save/delete 写往返实测（2026-11-18 阶段 0，五字段逐字一致）；default 未实测 |
| 邮箱验证（只用于一对一精发，见 SKILL §4.1 验证闸） | /contacts/contacts/verify（批量选区形状：{selectAll:false, selectKeys:[cid…], selectSort:{}, selectTotal:n}，一次提交只回一个 backendId） | 实测（2026-11-18：单个联系人提交后接口约 2.5 秒返回任务号，回读联系人 verify_status=valid、verify_time 已刷新；2026-11-19：2 人批量选区提交约 3 秒落回；落回时延不稳定——另有样本 150 秒未落回、300 秒不变，响应体不带结果、须按 SKILL §4.1 回读协议回读；大批量耗时未测） |
| 格式检查（非验证） | /tools/email-address-check | 定性实测（2026-11-19：只验邮箱格式，对不存在的域名同样返回 success，不返回有效性结论；源码口径为群发回信地址格式校验——**禁止当邮箱验证用**，验证一律走 /contacts/contacts/verify） |
| 智能跟进计划 | /sequences/*（建/步/激活/报表）；**加人分流写死**：往计划加**指定联系人**用 /contacts/contacts/sequence-add，按视图/标签**整批**加入才用 /sequences/contact-add，两口不许混用；**建步配方**（官方配方口径）：step-create 的 senders 传发件身份 _id（取 /mailbox/sender-list 的 _id），传单发用的完整发件标识会回「发送者错误」 | 读：实测｜写：契约级（未实测） |
| 群发任务 | 建/删/启/停：/tasks/mass/add、/tasks/mass/delete、/tasks/mass/drop、/tasks/mass/multi-delete、/tasks/mass/multi-drop、/tasks/mass/start、/tasks/mass/stop；计数：/tasks/mass-count；任务输入回读：/tasks/mass-info；配置：/tasks/get-mass-config、/tasks/save-mass-config；撤销：/tasks/mass-revoke | 读接口实测；写接口仅实测到校验失败路径（2026-11-19：mass-count 与 get-mass-config 真调成功；mass/add 按官方前端源码的向导草稿体提交——模板为空回「邮件模板为空」、收件人为空回「任务对象为空」，零收件人建不了任务）；**成功建任务未实测**——首次正式建群发时，先以 sendAtOnce=false＋未来时间提交**已经用户确认的真实任务**（收件人与内容都已确认），回读 mass-info 核对（任务状态为未发送/待启动、收件数与选区一致）无误、经用户点头才 start，不许拿未确认的名单试发。**口径写死**：mass/add 是提交动作（带 sendAtOnce/timeStart，官方随附说明原文口径），接口全量目录（417 个端点）与官方前端源码里都没有「只存草稿不提交」的端点（此全量断言待专项核验，登记 BK-148-观2）——用户只说「先准备、不要发」时只存本机方案与模板、不调这个接口，只做选区核对（mass-count）并回报；limitNum:0 表示不限量、不是零封；**重发已有任务时读 /tasks/mass-info 的任务输入**（不要拿统计口 /marketing/task-details 当任务输入读）；请求体字段与网页向导草稿同构（name/mode/match/exclude/contentsIds/attIds/filters/logic/keyword/selectOption/selectSort/selectKeys/selectTotal/skipNum/limitNum/channel/senders/track/timeSleep/fromName/replyTo/proxy/attNormal/sendAtOnce/timeStart/aiGuard），contentsIds 须给真实模板 id、收件人选区须非空（先用 /tasks/mass-count 按同口径数字段数确认 >0 再提交） |
| 精发/收信/回复/追踪 | /mails/*（列表/打开/存稿/发送/状态/追踪） | 读：实测｜写：单发已实测（官方包配方，见「单发配方要点」）、其余契约级 |
| 每月权益领取（§1.6） | /expenses/give-status（查）、/expenses/give-get（领） | 读：实测｜领：契约级（未实测） |
| 点数/费用读数与算账口径 | /account/*、/expenses/*。**余额三口定位**：本月赠送桶看 /expenses/give-status 的 creditCount、总持有看 /tasks/mass-count 响应的 creditCount、流水查 /expenses/billing/show（须带 filter{source:'total'} 并按时间倒序，空 filter 回空列表）；**扣点口径**：建群发任务不扣点、不预留，实际发送时按封扣（流水 source=send、−1/封；**不存在域名/未验证地址被计入任务后、真发时扣不扣点未验，不许按已扣口径向用户报账**）；AI 推演建产品与生成客群各 −2 点（流水 source='ai'） | 读实测（扣点口径为 2026-11-19 全量对账三余额口互证＋逐笔流水样本） |
| 禁发名单登记与查询（⑪） | /contacts/black/*（域名）、companies-black、contacts-black、/mails/mails-address-black | 契约级 |
| 绑箱状态查询/校验 | /mails/accounts-list、/mails/accounts-check；**只查状态/配置探测三口**：/mails/accounts-config（配置回填）、/mails/accounts-poste-config（邮箱配置探测）、/mails/accounts-show（单个已绑账号详情） | 契约级（三口为 2026-11-19 全量对账补显名；accounts-add、accounts-save 涉填授权码，按 R23 有意不显名、不走接口；同族 accounts-delete 属删账号的账号级动作、回网页，/mailbox/account-items 与 accounts-list 同为账号列表口，本表不单列） |
| 邮件模板/签名/片段 | 模板：/mailbox/templates-list（**参数口径写死**：{filter:{}, current, pageSize, sort:{_id:1}, owner:"everyone"}，缺 sort/owner 曾实测回参数校验错误）、template-info、template-add、template-save、template-delete、templates-delete、templates-folder-list、template-folder-add、template-folder-save、template-folder-delete、templates-update（移动/共享）、template-score；签名：/mailbox/sign-list、sign-add、sign-save、sign-delete、sign-default-set；片段：/mailbox/snippets-list、snippets-text-list、snippets-content-add、snippets-content-save、snippets-content-delete、snippets-folder-list、snippets-folder-add、snippets-folder-save、snippets-folder-delete、snippets-delete、snippets-move | 实测（2026-11-19 全量对账：自建对象生命周期实测通过、测后删净回查；templates-list 参数口径同轮钉死） |
| 群发统计与任务日志（marketing） | /marketing/tasks/show（任务数据）、/marketing/tasks/show-count（计数）、/marketing/task-details（单任务明细）、/marketing/task-logs（收件人日志；**status 须传枚举值如 total/delivered，传 all 回空；gtid 放 filter 内、平铺顶层回参数错误**）、/marketing/task-rename | 实测（2026-11-19 全量对账通过）；/marketing/task-html、task-preview 与 tracks 追踪族未覆盖（缺样本/涉真实发送日志），不在口径内、要用先小步验证 |
| 跟进记录与跟进任务（record） | 记录：/record/log-list、log-add、log-save、log-delete；任务：/record/task-list、task-info、task-add、task-save、task-delete、tasks-delete（task-list 属缺参 500 家族，配方见下节） | 实测（2026-11-19 全量对账：自建对象生命周期实测通过、测后删净/恢复基线） |
| 视图（views） | /views/views-list、view-config、view-fields、view-add、view-save、view-rename、view-delete、views-pin、views-pin-save（多带 type 区分视图对象、置顶保存口用 viewType） | 实测（2026-11-19 全量对账通过） |
| WhatsApp 会话（§4.4） | 已停用（2026-11-24），无接口、不走浏览器通道 | 不适用 |

两条边界写死：

- **绑箱动作不走接口**：绑定要填的授权码是凭据，不许经 AI 构造的请求体传递（R23）；绑定仍在来发信网页由用户本人填入（见《邮箱绑定指南》），接口只做两件事——查已绑账号列表、对已绑账号做连通性校验；凡要新填、重填授权码的动作一律回网页。
- **禁发名单**：登记与查询走上表黑名单接口（即平台禁发名单管理接口）；一切禁发类写操作（含 AI 评分结果里的「存禁发」）同为契约级、未实测；名单对发送的拦截效力以平台实际行为为准，本 skill 不另作保证，发送前四查（R13）照旧。
- **列表接口参数（实测范围）**：已实测的列表类接口（task-list、sender-list、companies/show）必须带 `filter:{}` 与 `sort:{}`，缺参返回 500；**还须带 `current`（页码）**，sender-list 等接口缺 current 不返回数据（实测）；其余列表接口未逐一验证，调用时默认同样带上，遇 500 或空返回先补此三参再排查。company-people 的 pageSize 须 ≥10（传小报 422，实测）。
- **批量选择信封（实测样本）**：带选择集的写口（邮箱验证、批量改字段、群发选区）请求体带同一套信封字段——`selectAll`、`selectKeys`、`selectSort`、`selectTotal`；其中批量改字段口缺 `selectTotal` 回 422（实测 2026-11-18，见下「公司字段回写配方」）；`match`/`exclude` 类字段传数组、不传标量（全量对账一手确认）。

## 缺参 500 兜底：预检、配方与报错翻译（2026-11-19 实测沉淀）

本节是 R29（官方 Agent 通道纪律）在参数层面的执行细则：接口返回 500 或异常时，先按本节预检表自查参数、按报错翻译表处置，**不许把参数没给全误判成平台故障、更不许原样重试硬闯**；预检通过仍失败的，才按调用纪律对账或回网页。上文「列表接口参数（实测范围）」是本节的摘要口径，逐口细则以本节为准。

### 一、客户端预检表（调用前必查）

下列 6 个列表接口同属缺参 500 家族：**缺必填参数时回 HTTP 500 且不提示缺什么**。其中序列三口已经 12 次对照实测坐实（缺参 6/6 全 500、补齐 6/6 全 success，与数据有无、序列是否激活无关）；其余三口只确认了缺参会 500、必填集未逐一实证，表中逐口标「待核」，首次调用先小步验证，不要把三口的待核配方当实证契约用。调用前先按本表逐项自查，缺项在本地补齐或拦下说明，不许把缺参请求发出去撞 500。

| 接口 | 调用前必查 | 缺了会怎样 | 补法 |
| --- | --- | --- | --- |
| `/sequences/contact-list` | `seqId`、`current`、`pageSize`、`filter`、`sort` 五项齐全；`sort` 用 `{"create_time": -1}` | 缺 `filter`/`sort` → HTTP 500，无字段提示 | 按下方配方 4 的契约体发；`filter` 无条件时传 `{}`，不许省略 |
| `/sequences/activity-list` | 同上五项；`sort` 用 `{"createAt": -1}`（注意是 createAt，与另外两口的 create_time 不同，实测如此、勿写错） | 同上 | 按下方配方 5 发 |
| `/sequences/email-list` | 同上五项；`sort` 用 `{"create_time": -1}` | 同上 | 按下方配方 6 发 |
| `/refine/task-list` | `filter`、`sort`、`current` 三项必带 | 缺参 → HTTP 500 | `filter` 传 `{}`、`current` 从 1 起；**待核**：`sort` 的契约字段名与方向未逐一实证，暂按 `{}` 占位时留意可能仍回 500、先小步验证 |
| `/expenses/orders/show` | **待核**：该口在缺参 500 家族六例内，但必填字段集合未逐一实证 | 缺参 → HTTP 500 | 暂按列表口通用形状带齐 `filter:{}`、`sort:{}`、`current`、`pageSize` 再发；仍 500 时回网页查订单，不许反复重试 |
| `/record/task-list` | **待核**：同上，必填字段集合未逐一实证 | 缺参 → HTTP 500 | 同上，按下方配方 3 的已知部分发 |

预检通用规则（对全部列表类接口，不止这 6 个）：

1. 列表口一律默认带齐 `filter`、`sort`、`current`、`pageSize` 四件套再发，无筛选条件时 `filter` 传 `{}`，不许整项省略。
2. 预检不通过（本地发现缺项）→ 不发请求，直接按缺项补齐；补不出（如不知道某口的 sort 契约）→ 先小步验证或回网页，不许拿 500 当探针反复撞。
3. 已按配方发仍回 500 的，先走下方报错翻译表处置，不许原样重发。

### 二、六例请求配方

以下均为 POST，经官方 Agent 通道调用。序列三例为 2026-11-19 复测实证的契约体（两个序列、含 7,725 联系人与空序列各验一遍，全 success）；其余三例给已知部分，缺口标「待核」。

**配方 1：批量搜索任务列表 `/refine/task-list`**（已知部分）

```json
{ "current": 1, "pageSize": 10, "filter": {}, "sort": {} }
```

**待核**：`sort` 的契约字段名与方向未实证；调用该口先小步验证，`sort:{}` 仍回 500 时按第三节处置，不许猜字段名硬试。

**配方 2：订单详情 `/expenses/orders/show`**（已知部分）

```json
{ "current": 1, "pageSize": 10, "filter": {}, "sort": {} }
```

**待核**：上式为列表口通用形状，**不是该口的实证契约**；该口可能另有专属必填字段（如订单标识类字段）。调用失败按第三节处置并回网页查订单，不许反复换参数撞。

**配方 3：跟进任务列表 `/record/task-list`**（已知部分，同配方 2，通用形状非实证契约，专属必填字段待补实测）

```json
{ "current": 1, "pageSize": 10, "filter": {}, "sort": {} }
```

**配方 4：序列联系人列表 `/sequences/contact-list`（实证）**

```json
{ "seqId": "<序列id>", "current": 1, "pageSize": 10,
  "filter": {}, "sort": { "create_time": -1 } }
```

实测：未激活序列照常返回数据（样本序列 total = 7725）；空序列回 `total: 0`。

**配方 5：序列动态列表 `/sequences/activity-list`（实证）**

```json
{ "seqId": "<序列id>", "current": 1, "pageSize": 10,
  "filter": {}, "sort": { "createAt": -1 } }
```

注意 `sort` 字段是 `createAt`，与配方 4、6 的 `create_time` 不同——照抄错口的字段名等于没补。

**配方 6：序列邮件列表 `/sequences/email-list`（实证）**

```json
{ "seqId": "<序列id>", "current": 1, "pageSize": 10,
  "filter": {}, "sort": { "create_time": -1 } }
```

实测：从未发过信的序列回 `total: 0`，不是报错。

### 三、报错翻译表（平台返回 → 人话原因 → 处置）

原则先行：**500 不等于平台坏了**。先按本表对号入座、按处置走；处置里写「不要重试」的，一次都不许多发（与 R29、调用纪律同口径）。

| 平台返回 | 人话原因 | AI 应做的处置 |
| --- | --- | --- |
| HTTP 500，`message: "Internal Server Error"`，不写明缺什么 | 多半是请求参数没给全（缺参 500 家族的典型长相）；也可能是该口自身的服务端问题（如个人工作区调企业档案） | ① 先回预检表逐项核对、按配方补齐再发一次；② 参数已齐仍 500 → 停手，不要原样重试硬闯，按调用纪律对账，能回网页完成的回网页，并把请求体与返回原文记进台账待报平台 |
| HTTP 422，报错里写明字段名（如 `"belongTo" 是必须的`、缺 `selectTotal`、pageSize 过小） | 平台把缺什么说清楚了，这是正常参数校验 | 照报错把字段补上再发；422 是好报错，不许当故障上报 |
| HTTP 403，`access_denied`「此操作不在应用授权范围内，请在网页中操作」 | 这个接口没开放给 Agent 通道（实测：查验证进度的 `/operation/backend-progress` 就是这种） | 不要换参数重试；该操作回网页完成，并向用户说明「这个功能接口没开放，我改走网页操作」 |
| HTTP 401/403 或 HTTP 203 且 `success: false`（未授权类） | 授权过期或作用域不够 | 停该操作，重走网页授权（用户点一次允许）；不换凭据、不换工作区硬闯（R29） |
| `success: false` 且 message 是明确业务话（如买 `vip_month` 时提示已是 SVIP） | 不是故障，是平台在拒绝这笔业务，理由已写明 | 把理由用人话转告用户，按用户意思换方案（如改买其他档），不要重试同一单 |
| 买点数包下单 `POST /expenses/pay/order-create`（`goodsType: "creditCount"`）回 HTTP 500 | 平台该商品的接口下单目前是坏的（本方实测那次已回查确认：订单没建上、没扣费，不是用户的问题）；但 500 也可能发生在订单已建成、只是响应失败时 | **不要反复下单**；先回读订单与点数余额确认到底建成没有、扣费没有：确认未建成 → 告诉用户「点数包现在接口买不了，请到网页端买，扫码就能付」，并把本次失败记台账待报平台，用户在网页买完后回读余额确认到账；确认不了 → 先停手、把情况如实告诉用户再定，不许在没确认前就引导去网页重复购买 |
| `success: true` 但回读查无此事（如附件登记对 store 类文件 id 回成功、附件库里却没有这一行） | 假成功：接口收了不该收的输入、又不报错 | 凡写操作一律回读验证才算完成（调用纪律既有口径）；回读对不上 → 按未完成处置：附件登记改走 att 类上传拿到的 file id，或回网页处理，并记台账 |
| 建字段 `POST /fields/field/create` 回 HTTP 500（错误码 11000） | 出现过一次，同参数复测未再复现（3 次均成功），按间歇问题处理、不认定是稳定故障；11000 一般是重复键类错误 | 先回读字段列表确认到底建成没有：已建成 → 当成功收尾；没建成 → 换个字段名重试一次；仍失败停手报用户，不要连环重试 |
| 单发回「该邮箱无法发送，请联系客服解锁发送」 | 按顺序查三个原因：① 收件人是 QQ/163/126/新浪等中国地区邮箱——平台配合反诈一律禁发、与发件方无关（2026-11-19 同账号同通道对照实测坐实：发非国内邮箱成功、发 QQ 邮箱立刻回此错）② 发件标识 `sender` 只填了裸 name ③ 以上都不是才轮到账号侧问题；这条报错不构成账号被锁的证据 | ① 先看收件人域名：国内邮箱 → 换非国内邮箱重发（测试用 Gmail 或 email@zhijixinxi.com）；确有正当需要向国内邮箱发送的（如内贸），告知用户可联系官方客服（bd@zhijixinxi.com）完成认证、申请加入白名单，白名单生效前不要反复重试；② 收件人没问题，再核对 `sender` 是否完整标识（形如 `1804106008.z7pvxh`），从已发送记录读回；③ 两项都无误仍被拒，才按账号侧问题查账号状态，不要一上来就让用户找客服 |
| 网页端写信窗发送回「该邮箱无法发送，请联系客服解锁发送」 | 同上先查收件人：收件人是国内邮箱就是平台禁发（2026-11-19 真实用户事故：测试信发到自己 QQ 邮箱被拦、被误判成通道被锁）；收件人非国内邮箱时，才可能是所选发件身份被停用或平台异常——网页端发件标识由平台下拉给定、不存在填错 | ① 收件人是国内邮箱 → 换非国内邮箱重发（测试默认 email@zhijixinxi.com 或用户自己的 Gmail）；确需向国内邮箱发送的，告知用户联系官方客服（bd@zhijixinxi.com）认证申请白名单；② 收件人没问题：回读 `/mailbox/sender-list` 看所选身份的 `status`、换一个身份试发一封：换身份能发＝单个身份问题，用能发的身份继续并记台账；③ 所有身份、对多个非国内收件人都发不出，才按平台异常处置：如实告诉用户、台账标黄灯记日期、走问题反馈报平台核查，等待期间冷开发可用已绑自有邮箱低量顶上（企业邮箱优先，守 R27 与新箱爬坡、不做批量冷发）；不许反复点发送硬撞 |
| 单发回「发送对象地址格式错误」／「需要明确 sendAtOnce」 | 收件人格式不对（只写了裸邮箱）、或漏传 `sendAtOnce` | 收件人改 `<邮箱>` 或 `显示名 <邮箱>` 格式；补 `sendAtOnce` 后再发（配方见单发配方要点） |
| 提交邮箱验证后，只回一个 `backendId`、迟迟查不到结果 | 验证是异步作业：提交响应只给编号、不给结果；拿编号查状态的接口只回显参数、没有进度字段；结果最终只落在联系人记录的 `verify_status`/`verify_time` 上，且单次实测观察到从未验证过的联系人 30 分钟以上未回落（样本有限，此时间仅作观察口径） | 不要盯着任务状态接口空转，也不要重复提交；按 SKILL §4.1 回读协议回读联系人字段判读，超时未回落就如实告诉用户「验证结果还没回来」，发送前验证闸按 §4.1 既有口径处置，不许假装已验证 |

## 单发配方要点（官方包实测，2026-11-17/18）

证据等级：**已实测（官方包配方）**——来源为官方 Agent 包 `references/workflows.md`「单发直发配方」，2026-11-17/18 在个人工作区（z7pvxh、仅系统账号、无绑定邮箱）经网页端与 API 双路实测发通并多轮修订；本 skill 侧首次使用仍按 SKILL.md §4 章首口径先小步验证。绑定邮箱通道的 `maid/sender` 取法见下（以 `/mails/accounts-list` 行与已发送记录为准），自有通道经 API 发送未逐项实测。

- **接口**：`POST /mails/sendmail-add`，与普通写信共用，无需先建模板或任务。最小请求体六个字段缺一不可：`maid`、`sender`、`to`、`subject`、`html`、`sendAtOnce`。可选字段：`senderName`（逐封发件昵称）、`replyTo`（逐封回信邮箱），见下「发件昵称」「回信邮箱」两条。
- **已发送记录（`POST /mails/mails-list`）请求体契约（2026-11-23 实测补齐）**：完整请求体＝`{"current":1,"pageSize":10,"sort":{},"owners":[],"filter":{"maid":"<账号标识>","parent":"/","boxName":"INBOX","keyword":""}}`；`sort` 与 `owners` 必填，缺 `sort` 返回 422「"sort" is required」；`filter.boxName` 取 INBOX／OUTBOX／Drafts／Deleted／Spam，传空字符串返回 422；系统账号的 `maid` 取 `"system"`，绑定邮箱取 accounts-list 对应行。**读接口重试**：读接口返回 HTTP 200 但响应不完整或解析失败（平台侧传输中断，2026-11-23 实测高频：同一请求多次调用约半数被中途截断、截断点随机成簇，重试可成功），首次失败后最多再重试 3 次（合计最多 4 次请求）、间隔递增（约 2 秒、5 秒、10 秒），重试成功按正常结果处理、不必上报；重试用尽仍败才按 D1 如实报「没查成」。本重试只适用于读接口；写操作结果不明仍按 R29 先对账、不自动重试。
- **发件标识 `sender`**：必须用**完整标识**（形如 `1804106008.z7pvxh`）；只填发件人列表里的裸 `name` 会被拒，报「该邮箱无法发送，请联系客服解锁发送」——处置顺序写死：先核对发件标识、再查账号状态；这条报错不构成账号被锁的证据（实测对照：标识错误必报此错、换完整标识即发送成功）。完整标识从已发送记录（`POST /mails/mails-list`）读回、缓存复用；记录里有多个 `sender` 时按目标发件人的 `name` 后缀匹配、同后缀取最新；工作区还没有已发送记录时，从网页端写信窗的发件人下拉取。
- **收件人格式**：每个地址写 `<邮箱>` 或 `显示名 <邮箱>`，多人用英文逗号拼接；只写裸邮箱报「发送对象地址格式错误」。漏传 `sendAtOnce` 报「需要明确 sendAtOnce」。
- **`single`**：`true`＝分别发送（每个收件人单独一封、互不可见，发送状态总数＝收件人数）；省略或 `false`＝一封同达（收件端能看到全部收件人）。精发与多人发送必须显式传 `true`，单收件人直发同样用 `true`。
- **正文与附件**：`html` 字段传 HTML（段落 `<p>`、换行 `<br>`、加粗 `<strong>`）；只传纯文本会连成一段。附件先 `upload` 取得 `url/name/size` 再填 `attachments`（与附件库引用 `attIds` 别混）；**上传后须等 `/file/save-log` 成功才算服务端落点完成**，只拿到 upload 返回不算落稳。
- **追踪**：`track: true` 在正文末尾埋追踪像素；打开数据查 `/mails/track-info`，参数 `sid` 取已发送记录的 `ssid` 字段（不是发送返回的 sendId）。真实打开事件回录未端到端验通，查到空数组不等于没人打开。
- **定时**：`sendAtOnce: false`＋`timeStart`（未来 90 天内的毫秒时间戳，缺失或超限后端明确报错）；提交返回邮件 `id`（不是 sendId），到点自动发出。改期 `/mails/change-timer`（参数 `{id, timeStart}`）、取消 `/mails/cancel-timer`（参数 `{id}`）；取消是幂等的，取消后必须回查列表确认该记录落 Drafts 且 `timeStart` 为 null 才算生效。改期契约（1.5.5 立）：经 change-timer 只传 `{id, timeStart}` 改期，原信的 `senderName` 与 `replyTo` **原样保留**；经 sendmail-add 带 id 重新提交改期时，未重传的 `senderName`/`replyTo` 会被**清空**——走这条路必须按已确认值重传两参数，提交后能读回的读回核验、读不回的在执行记录里回报实际入参，不许默默清空。
- **发件昵称**：发送请求可用 `senderName` 参数逐封设昵称（2026-11-24 平台上线、实测生效：收件头 From 名即所传昵称）；`fromName` 字段仍被忽略，别用错字段名。昵称同时是发件人身份属性，在发件人设置里维护（`/mailbox/sender-save`），网页端发送显示身份昵称；API 单发要显示昵称就传 `senderName`（可逐封自定义；昵称代改场景默认传与发件身份昵称一致的值）。【2026-11-24 更正：下面这段是旧口径的历史实测记录，现行结论以本条开头为准】分通道口径（2026-11-19 定案）：**网页端发送时发件人名称真实生效**——网页端把主发件身份昵称改为测试名后网页真发 1 封，收件原始头 header_from_name 即为新昵称（改后已恢复原值）；**经 Agent API 单发时不带昵称**——把非主用发件身份的 fromName 改成测试值后经 API 发信，收件侧显示名仍是账号 userid；以 fromName 长期为「Tony」的发件身份发对照信、主身份历史已发送邮件，显示名同为 userid，合计 5 样本一致，对照组已排除「延迟生效」解释。即旧口径下问题只在 API 单发路径：sender 的 fromName 改动未反映在 API 单发的收件侧显示名上（该段为 2026-11-19 历史实测记录）；现行解法是 API 单发时传 `senderName` 参数（见本条开头）。昵称设置本身（sender-save）写读往返已实测可用。
- **回信邮箱（`replyTo`，2026-11-24 平台上线、实测生效）**：单发请求传 `replyTo` 可逐封指定回信邮箱，客户点回复时回到该邮箱。平台定版（Tony 2026-11-24 确认）：收到信的 Reply-To 头里含**两个地址**——所指定的邮箱＋发件地址本身，是平台**有意设计**，回复同时投往两处，不作缺陷处理。另分清两层：`replyTo` 入参只收单个地址是请求层限制，与发送侧双地址是两回事，不许混为一谈。群发任务的回信邮箱走任务配置字段（见群发任务行），与本参数分开。
- **系统通道注意**：`maid: "system"` 从平台大量轮换域名发出、扣通用点数，与群发共用同一平台系统通道，是正式发送通道之一。**运营实测（Tony 2026-11-18）**：收件人以企业邮箱为主时投递表现好、比免费邮箱更容易进收件箱，日量可达数千至数万封；实际量以平台账号额度与点数预算为界。**收件侧区分**：官方实测样本（数量有限）中直发 Gmail 均进垃圾箱——此为免费邮箱（Gmail 等）侧的小样本结论；名单混有免费邮箱收件人时单独分组、先小样实测，通道仍按 SKILL.md 优先级口径选（默认系统通道），只有满足例外 (b) 或用户明确指定时才改用绑定邮箱通道，企业邮箱与免费邮箱的结论不互相外推。平台账号侧有自身风控（发送被拒先核对发件标识、再查账号状态），禁发名单四查与熔断对系统通道同等适用（见 SKILL.md §4.2 路线丙与 §4.3）。`readReceipt`（已读回执）与 `priority`（优先级）在系统通道下不生效。

## 公司字段回写配方（modifyCompanies，实测 2026-11-18）

- **接口**：`POST /contacts/companies/save`（批量改字段口）。正解参数：`{selectAll:false, selectKeys:[公司_id], selectSort:{}, selectTotal:1, changeField:"<字段名>", changeType:"renew", changeValue:<新值>}`。踩坑记录：只传 {_id, 字段} 报 422（缺 selectTotal）；传 {ids:[...]} 返回 success 但 matchedCount=0（假成功），一律不用。
- **已实测可写字段**：short_description（公司简介，改＋恢复全程读回无残留）、phone_number（公司电话）。判读注意：同值写入 matchedCount=1、**modifiedCount=0**——是后端 no-op 语义，不等于字段不可写；改值写入 modifiedCount=1 且回读在位才算验通。
- **字段存在性以注册表为准**：`POST /fields/company-fields` {belongTo:"company", saveType:"read"} 返回 17 个系统字段（orgName、domain、website、countryCode、status、tags、employees、industry、phone_number、linkedin_url、facebook_url、twitter_url、founded、short_description、company_address、create_time、scoreLevels）。**公司没有 remark 字段**（记录转储/编辑表单/类型定义/字段注册表四源核实）；公司级备注走自定义字段补建（SKILL §4.1 B4，补建路径已实测——2026-11-19 网页端建并回验、失败降级）。联系人有 remark 与 source。

## 接口引导信息处置（ai_hint）

平台接口的部分返回会带两个额外字段：`code`（情形代码，机器可读）与 `ai_hint`（给 AI 的一句话指引，写清原因与建议动作）。这不是报错字段，平台是在提醒有更合适的走法；收到后先确认本次操作结果：返回里有状态字段的按状态字段对账，状态缺失或结果不明的先查状态对账（与 R29 同口径）；确认结果后，再按结果处理当前操作、按指引调整后续安排。处置口径写死：

- **默认按指引改道**：指引管的是后续安排——已经成功执行的当次操作不重做、不撤销（结果按状态对账确认即可）；此后同类操作按指引调整走法（例如同量级的发送改走单发、不再重复建小群发任务）。不许看一眼就丢开、按原路继续。
- **按代码处置**：情形代码是处置的锚（下列代码值是我方建议值、平台尚未确认；实际处置以平台返回代码的语义为准，语义对上就按本节处置）。`SMALL_BATCH_USE_SINGLE`（小批量群发改单发）→ 后续同类批次改走系统通道单发逐封发（配方见本文件「单发配方要点」）；当次仅在状态对账确认原操作未执行、且未生成可继续发送的任务或预约后，才可改单发；已成功创建的任务或已成功发送的邮件不因本提示另行单发，结果未明时不另行提交。`SINGLE_VIA_BOUND_MAILBOX`（单发走了绑定邮箱）→ 后续冷发改走系统通道，绑定邮箱留给客户回复后的跟进；当次适用上述结果对账与不重复执行口径。指引里没写清的目标接口与参数不许猜，按本文件既有配方与 SKILL.md 既有口径走。
- **例外**：用户明确要求按原路执行的，照用户要求办，但在日报里显名（收到的代码、未改道的理由）。
- **日报显名**：当日每一次收到引导都记进日报第⑥段——代码、原计划路线、实际改走的路线；未改道的写明理由。
- 平台没返回这两个字段时按原口径执行，本节不构成额外动作。

## 调用纪律（与 R29 同口径）

1. 接口命令默认先预览、确认无误才真执行；请求体走文件或标准输入，不拼进命令行。
2. **写操作结果不明（超时、断连、状态待确认）不自动重试**：先查状态对账再决定，防重复发送、重复建计划；台账先记「待确认」态、不记成功；该操作没有状态查询接口时（如群发启停），回网页核对实际状态再决定，仍核不清就报用户人工确认，不许凭猜测重发或宣布完成。
3. 读到「仍在处理」类状态不许报成已完成（如发信状态 pending ≠ 已发送）。
4. 每次接口操作的留痕按 §2.3 编号溯源记台账，与网页操作同等要求。

## 降级规则

| 情形 | 处置 |
| --- | --- |
| 接口返回未授权/作用域拒绝（401/403/203 等） | 停该操作 → 回网页完成 → 向用户说明原因；不换凭据、不换工作区 ID 硬闯 |
| 凭据到期/失效 | 重走网页授权（用户点一次允许）；走不通则全面回网页操作 |
| 通道整体不可用（宿主限制、装不上） | 全面回网页操作，设置页标 degraded 并向用户明示 |
| 接口行为与文档不符、文档未覆盖或写不清 | 先按 SKILL.md D1 动态抓取（只读优先、写验证只用自建测试对象）定性，再按实测继续执行；确认属文档不符、平台错误或文档未覆盖（平台有此功能、只是文档缺失）的，按 D1 自动经系统通道反馈作者 |
| 账号级操作（改密码、绑身份、管理授权、建/入企业） | 官方凭据按设计不可用，一律回网页由用户本人完成 |
| 网络超时/限流/服务端错误（读操作） | 交官方客户端自带重试处理（等待递增、遵守服务端 Retry-After），AI 不叠加自己的重试；写操作不走客户端重试，按调用纪律第 2 条（先对账、无查询接口回网页核对） |

## R23 附注：代办边界与通知绑定代办链（C3 读码形态）

R23 红线不变：Muse 不存邮箱凭据、不模拟网页登录邮箱、不抓取任何会话令牌。在此之内的代办边界写死：

- **允许**：① 官方 Agent 通道授权的委托代办（§1.1 保险库路径：凭据经安全录入卡直达保险库、AI 只打开官方授权链接、核对用户码与工作空间后代点当次授权页的「允许」——仅限该次授权、一次性，用户码只用于当场核对、不写入任何记录）；② 通知绑定代办链中，用户本人扫码登录后，AI 代填来发信个人设置表单（填账号通知邮箱、点获取验证码）；验证码由 AI 在用户已登录的通知邮箱里只读验证码邮件取得后代填（读码形态，Tony 2026-11-19 裁定批准；只读验证码邮件、只用于本次绑定、读后不留存），读不到或用户不愿意时仍可由用户口述或粘贴。
- **禁止**：AI 输入任何账号密码、代扫码、读取或保存验证码以外的邮箱内容、保留用户邮箱的登录会话、把验证码写入任何记录。
- **C3 当前执行读码形态（Tony 2026-11-19 裁定）**：通知绑定时 AI 可读用户通知邮箱的验证码邮件完成绑定，护栏＝只读验证码邮件、只用于本次绑定、读后不留存；口述/粘贴代填仍可作为读不到码或用户不愿意时的回落。绑定对象是账号通知邮箱（`/account/renew-email` 变更的账号邮箱），与发件身份（mailbox/sender-*）是两套东西，不许混淆。
