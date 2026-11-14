# AllinCMS 官方教程索引

> 用途：操作前先在这里找到对应官方页，再打开官网最新版核对一遍再动手（口径见 SKILL 第十一章「教程保鲜」）。
> 每条记：标题、官网地址、要点三行、抓取日期。官网与索引不一致时以官网为准，并当场更新本索引与抓取日期。
> 官网选型价格页（https://www.allincms.com/website-solution）不在文档站内，未收录进本索引。
> 官网首页 https://www.allincms.com/ 仅作辅助核对（非教程页、不计条目）：官网公示的开通方式是扫码加客服微信、人工开通，开户指路见同目录《联系说明.md》。

## 索引状态

- 正式版：2026-11-14 实时逐页打开官网文档站全部栏目核实建成，共 40 条 /docs 教程页，按文档站栏目顺序排列，抓取日期均为 2026-11-14。
- 保鲜规则：官网与本索引不一致时以官网为准，并当场更新本索引对应条目与抓取日期。

## 一、建站前准备

### 建站流程

- 官网地址：https://www.allincms.com/docs
- 要点：
  - 理清顺序不展开操作：准备→编辑→检查→运营，全站教程的总入口。
  - 先判断自己处在哪一步，再进对应文档细看。
  - 遇问题先用文档站右上角搜索。
- 抓取日期：2026-11-14

### 建站前准备

- 官网地址：https://www.allincms.com/docs/quickstart/preparation
- 要点：
  - 备齐 5 类再开始：域名（推荐 .com）、公司/产品/文章资料、图片尺寸、联系方式、账号；服务器由平台提供。
  - 首次量：3–4 个主分类、每类 2 个产品、3 篇文章、3–5 条 FAQ。
  - 上线前自己提交一次测试表单，验收收信邮箱。
- 抓取日期：2026-11-14

### 图片规范

- 官网地址：https://www.allincms.com/docs/content/image-guidelines
- 要点：
  - 先按模块定尺寸再备图，统一压缩 WebP，超 500kB 必慢。
  - Banner 1800×1000、产品主图 800/1000 正方形、文章主图 1200×700、Logo 宽 ≤350 透明 PNG、Favicon 512。
  - 多数图 ≤300KB（Logo、Favicon ≤100KB）；alt 写清图片内容。
- 抓取日期：2026-11-14

### 快速上手

- 官网地址：https://www.allincms.com/docs/quickstart/overview
- 要点：
  - 先少量真实内容跑通再丰富，不要先装修首页。
  - 9 步：新建站点→产品类别→添加产品→添加文章→改首页→改页面→进阶模块→上线检查→持续丰富。
  - 内容为空的页面会 404，先有内容再谈排版。
- 抓取日期：2026-11-14

## 二、建站编辑流程

### 新建站点

- 官网地址：https://www.allincms.com/docs/quickstart/create-site
- 要点：
  - 登录 workspace.laicms.com/sign-in 创建站点，获得临时域名后先开前台验证。
  - 404/空白排查：主题为空才建默认主题（预设选「默认」）。
  - 启用主题，Home 发布并设为主页。
- 抓取日期：2026-11-14

### 站点图标和站点通知邮箱（导航名：站点基础设置）

- 官网地址：https://www.allincms.com/docs/quickstart/site-settings
- 要点：
  - 入口：站点后台→设置→站点信息。
  - Favicon 用简洁正方形品牌图。
  - Notification Email 填能收信的邮箱接收表单/询盘通知，保存后提交测试表单验证。
- 抓取日期：2026-11-14

### 产品分类

- 官网地址：https://www.allincms.com/docs/content/product-categories
- 要点：
  - 先做 3–4 个主要类别，不要分太细。
  - 建好类别即有分类页，不要在 Routes 里重建同名页；Slug 用清晰英文。
  - 后台改分类名后，顶部菜单需在设计器手动同步。
- 抓取日期：2026-11-14

### 添加产品

- 官网地址：https://www.allincms.com/docs/content/add-products
- 要点：
  - 每个主要分类先备 2 个代表产品，先改模板产品、删测试内容。
  - 填名称、Slug（英文）、一句话简介、分类、主图与相册压缩图后发布；排序数字越大越靠前。
  - 404 常因产品模块 Detail Page 未选对。
- 抓取日期：2026-11-14

### 添加文章

- 官网地址：https://www.allincms.com/docs/content/add-posts
- 要点：
  - 先备 3 篇（公司介绍、产品知识、案例），先改模板文章。
  - 填标题、英文 Slug、摘要、正文、封面后发布。
  - 检查 /posts 与首页模块显示；404 常因文章模块详情页未选 /posts。
- 抓取日期：2026-11-14

### 首页必备模块

- 官网地址：https://www.allincms.com/docs/pages/homepage-basics
- 要点：
  - 前提：3–4 分类、每类 ≥2 产品、3 篇文章；先改默认模块，不要全删重建。
  - 顺序：Header→Dropdown→Carousel→Category Showcase→Featured Product→Featured News→Footer。
  - 验收 7 项全过再做进阶模块。
- 抓取日期：2026-11-14

### 产品模块

- 官网地址：https://www.allincms.com/docs/content/product-module
- 要点：
  - 检查默认的 Category Showcase + Featured Product List，不要删掉重做。
  - Detail Page 必选 /products（文章选 /posts），否则点击 404。
  - 不要同时保留两个产品模块。
- 抓取日期：2026-11-14

### 首页推荐产品

- 官网地址：https://www.allincms.com/docs/content/homepage-featured-products
- 要点：
  - 调高重点产品的排序值，每分类只选 1–2 个。
  - 先确认产品已发布且模块 Detail Page=/products。
  - 发布后查前台详情页与手机端是否拥挤。
- 抓取日期：2026-11-14

### 新建页面

- 官网地址：https://www.allincms.com/docs/pages/create-page
- 要点：
  - 先有路由再绑定页面；默认页 Home/Products/Posts/About/Contact 直接改。
  - 缺 Cases/OEM/Services 等页面时才新建。
  - 流程：Routes 建路由→Themes 建页面→页面设置选路由并启用→前台验证。
- 抓取日期：2026-11-14

### 跳转链接

- 官网地址：https://www.allincms.com/docs/pages/redirect-link
- 要点：
  - 能用 Internal 直接选的优先用 Internal；分类/产品/文章/页面各有 Internal 路径。
  - 不要猜路径（列表页是 /products，不是 /product）。
  - 选 Product/Post 后还须选对应 slug。
- 抓取日期：2026-11-14

### 导航顺序

- 官网地址：https://www.allincms.com/docs/pages/menu-order
- 要点：
  - 只保留核心入口：Home→Products→News/Blog→About Us→Contact Us。
  - 重点页放 Products 后或 Contact 前；在设计器 Header 里拖拽排序。
  - 一级菜单不要多，名称用短英文。
- 抓取日期：2026-11-14

### 顶部菜单：普通菜单和下拉菜单（导航名：子菜单和下拉菜单）

- 官网地址：https://www.allincms.com/docs/pages/dropdown-menu
- 要点：
  - 新手只保留 1 个产品下拉。
  - 普通菜单与下拉项都用 Internal 选页面或产品分类；一级菜单 4–6 个。
  - 桌面端与手机端都要验收展开与点击。
- 抓取日期：2026-11-14

### 网站联系方式设置

- 官网地址：https://www.allincms.com/docs/pages/contact-links
- 要点：
  - 电话、邮箱设为可点击：选中文字→Target 填 mailto:邮箱 / tel:号码（只留数字+区号）。
  - 冒号用英文冒号、无空格。
  - 发布后用手机实测点击效果。
- 抓取日期：2026-11-14

### 表单修改教程

- 官网地址：https://www.allincms.com/docs/pages/form-editor
- 要点：
  - 后台「表单」改名称/按钮/成功提示/字段；第一版只留 Name/Email/Topic/Message 四字段必填。
  - 下拉的 Label 是客户看到的文字，Value 用英文小写加短横线。
  - 改完在前台提交测试，确认能收信。
- 抓取日期：2026-11-14

### 添加位置地图

- 官网地址：https://www.allincms.com/docs/pages/location-map
- 要点：
  - 联系页/页脚/公司介绍可加地图：AI 指令或手动 Forms→Location Map。
  - 从 Google 地图分享复制准确位置链接，不要只复制搜索结果链接。
  - 粘贴到模块 Google Maps URL 后在前台核对位置。
- 抓取日期：2026-11-14

### WhatsApp 悬浮按钮

- 官网地址：https://www.allincms.com/docs/pages/whatsapp-floating-button
- 要点：
  - Forms→Social Floating Button，Brand 选 WhatsApp。
  - URL=https://wa.me/号码（区号+手机号、无空格符号），Position 选 Bottom Right。
  - 每页只放一个，发布前点测。
- 抓取日期：2026-11-14

### 添加弹窗表单（导航名：弹窗表单）

- 官网地址：https://www.allincms.com/docs/pages/popup-form
- 要点：
  - 先在 Forms 建好表单并确认能收信。
  - 设计器加 Contact Form (Split) Popup Form 模块，Props 选已建表单；按钮 CTA 的 Target 选 Action 对应弹窗。
  - 一页先放 1 个，必须提交测试。
- 抓取日期：2026-11-14

### 视频模块和图片画廊

- 官网地址：https://www.allincms.com/docs/pages/media-sections
- 要点：
  - 视频只支持 YouTube 链接，不要上传本地视频。
  - Media→Video Section 选 Split 分栏；画廊 Media→Image Gallery 先放 6–12 张、比例一致。
  - 没有素材就不要放空模块。
- 抓取日期：2026-11-14

### 进阶页面

- 官网地址：https://www.allincms.com/docs/pages/advanced-pages
- 要点：
  - 基础跑通后再做；推荐顺序：Cases→画廊→视频→弹窗→上线检查→统一调色。
  - Cases 路由 /cases，准备 3–6 个案例。
  - 每加一个模块，发布后在前台点一遍验证。
- 抓取日期：2026-11-14

### 整体背景色和主题色

- 官网地址：https://www.allincms.com/docs/pages/theme-colors
- 要点：
  - 基础内容完成后再调色。
  - 只能改整体背景与整站主题风格，不能单改某个模块底色。
  - 用 AI 对话说清色调或在 Theme 选现成主题，Preview 后再 Publish。
- 抓取日期：2026-11-14

## 三、上线前检查

### 上线检查

- 官网地址：https://www.allincms.com/docs/launch/launch-checklist
- 要点：
  - 像真实客户一样用浏览器加手机点一遍前台。
  - 顺序：模板内容→联系方式→表单收信→404 链接→图片手机端→域名 HTTPS；逐页改页面描述。
  - 表单必自测：提交 Test Inquiry，5 分钟内查收件箱。
- 抓取日期：2026-11-14

### 域名解析

- 官网地址：https://www.allincms.com/docs/domains/bind-domain
- 要点：
  - 后台 Settings→Domains 复制 CNAME 目标，到域名平台加 @ 与 www 两条 CNAME（不要选 A 记录）。
  - 回后台添加根域名与 www 域名；等 DNS/SSL 5–30 分钟，不要反复删了重配。
  - 不要乱删 MX/TXT 记录。
- 抓取日期：2026-11-14

### Cloudflare 解析

- 官网地址：https://www.allincms.com/docs/domains/cloudflare-dns
- 要点：
  - 仅域名在 Cloudflare 购买或 DNS 托管在 Cloudflare 时看本页。
  - 根域名 A 记录开代理、www CNAME 关代理（仅 DNS），根域名 301 跳 www。
  - www 开代理会导致验证失败。
- 抓取日期：2026-11-14

### 迁移旧站

- 官网地址：https://www.allincms.com/docs/domains/migrate-old-site
- 要点：
  - 仅旧后台迁移用户看本页；先在新后台核对产品/文章/图片/页面完整。
  - 旧后台解绑原域名后，回新后台换新 CNAME，等 10–30 分钟。
  - 不要删 MX/TXT 记录。
- 抓取日期：2026-11-14

### 网站不安全

- 官网地址：https://www.allincms.com/docs/domains/ssl-not-secure
- 要点：
  - 多为 SSL 未签发或未走 https 访问。
  - 排查顺序：等 SSL 10–30 分钟→手动输 https 完整地址→无痕/换浏览器排缓存→回后台看 DNS/SSL 状态。
  - DNS 未通过时不要干等 SSL。
- 抓取日期：2026-11-14

### 发布失败

- 官网地址：https://www.allincms.com/docs/troubleshooting/publish-failed
- 要点：
  - 处理 Failed to publish：先复制重要文案→刷新→重进设计器→重做修改→再发布→前台检查。
  - 不要连续点发布。
  - 多次失败时截图联系支持。
- 抓取日期：2026-11-14

### 恢复页面、产品和文章历史版本

- 官网地址：https://www.allincms.com/docs/troubleshooting/page-history-restore
- 要点：
  - 页面在设计器左上角 History，产品/文章在编辑页左上角历史。
  - 先预览核对再 Save+Publish。
  - 整条删除或媒体文件删除不能直接恢复。
- 抓取日期：2026-11-14

### 图片显示不全

- 官网地址：https://www.allincms.com/docs/troubleshooting/image-fit
- 要点：
  - 先判断是裁剪、拉伸还是比例问题，优先改 Fit inside。
  - Crop to fill 铺满会裁边，Stretch 易变形不要用。
  - 仍不好就换原图：产品图正方形、Banner 横图、上传前压缩。
- 抓取日期：2026-11-14

### 常见问题

- 官网地址：https://www.allincms.com/docs/troubleshooting/faq
- 要点：
  - 本页是问题索引而非教程：按域名 HTTPS、页面链接、页面功能、产品图片、发布上线五类查对应文档。
  - 排查顺序：确认现象→找文档→按避坑汇总检查→不行保留截图联系支持。
- 抓取日期：2026-11-14

## 四、上线后运营

### 查询网站收录并提交站点地图

- 官网地址：https://www.allincms.com/docs/launch/google-search-console-sitemap
- 要点：
  - 三件事：site: 查收录→连 GSC→提交 sitemap.xml。
  - 提交不等于马上收录，一般要几天到几周。
  - 先确认 https://域名/sitemap.xml 能打开再提交。
- 抓取日期：2026-11-14

### Google Analytics 4 (GA4) 设置

- 官网地址：https://www.allincms.com/docs/launch/google-analytics-4
- 要点：
  - 只填 G- 开头的衡量 ID 到后台 Google 追踪，不要粘整段脚本、不要用旧 UA-。
  - GA 建 Web 数据流时网址只填域名。
  - 无痕打开前台后，在 GA4 实时概览验活跃用户。
- 抓取日期：2026-11-14

### 文章 SEO 教程

- 官网地址：https://www.allincms.com/docs/content/seo-article-structure
- 要点：
  - 写回答客户真实问题的文章，不要 AI 批量灌水。
  - 先给 AI 真实资料、人工审核事实，每篇只解决一个问题。
  - 顺序：定问题→备资料→开头先给答案→H2/H3 分段→链接产品/分类/联系页。
- 抓取日期：2026-11-14

## 五、AI 工具

### 用 Muse 对话搭建网站

- 官网地址：https://www.allincms.com/docs/launch/muse-ai-website-building
- 要点：
  - 登录 Muse 对话给出目标、资料与想要效果，先确认样本再整站。
  - 资料要有使用权；参数、价格、认证自己核对。
  - 登录信息不要写入正文或公开截图。
- 抓取日期：2026-11-14

### 绑定 AI API

- 官网地址：https://www.allincms.com/docs/launch/ai-api-configuration
- 要点：
  - 供 AI 翻译与智能对话用；以 DeepSeek 为例：开放平台实名加小额充值→创建 Key→后台设置→AI 配置选 DeepSeek、粘贴 Key、获取模型选 Flash 保存。
  - Key 只显示一次，创建后立即保存。
  - 日常翻译不要选 Pro。
- 抓取日期：2026-11-14

### 开启网站多语言

- 官网地址：https://www.allincms.com/docs/launch/site-languages
- 要点：
  - 内容基本完整后再开；先绑定 AI API，否则无法翻译。
  - 后台设置→站点语言添加，只选真实目标市场。
  - 看已翻译/未翻译/失败数，完成后在前台切换检查。
- 抓取日期：2026-11-14

### AI建站自动上传网站内容

- 官网地址：https://www.allincms.com/docs/launch/codex-auto-content-upload
- 要点：
  - 装 AI 工具加模型、新建空白项目、发启动指令装 skill 并自测。
  - 先确认完整清单，先做 1 产品加 1 文章样本验收再批量。
  - 参数不要凭空编、图片须进后台媒体库、上传后必看前台。
- 抓取日期：2026-11-14
