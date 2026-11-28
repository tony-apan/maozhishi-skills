---
doc_id: laicms-module-standards
title: 模块标准库
description: AllinCMS 37 个模块的标准用法、量化规格与放置基线。
status: active
updated: 2026-11-16
owner: 贸知事
---

# LaiCMS 模块标准库（正式版，2026-11-14）

> 状态：**正式版，已入母仓**。来源：2026-11-14 后台全量盘点＋独立执行验收（缺口分诊已落点）。用途：后续 AI 照此施工的量化依据，也是施工取值与平台巡检的比对基线。
> 原料：① 后台实测盘点 `laicms-module-inventory-2026-11-14.md`（测试站 Muse试跑测试站/Tailpeak Supply，37 模块 / 65 实例 / 设置面 / 主题层，只读实测）；② 官方教程盘点 `allincms-docs-inventory-2026-11-14.md`（allincms.com/docs 40 页逐页采集）；③ 母仓现行 SKILL v3.2.17 与 references/beauty-review.md。
> 来源标注：每条标准尾注来源类别——**【实测】**＝后台盘点直接读到；**【教程】**＝官方文档口径（注明页名）；**【实践】**＝SKILL 现行口径与演示站 7.7 分实践沉淀（引用 SKILL / beauty-review 时注明文件名）。未被本次盘点或文件证据确认的平台行为另标 **【待验】**，不作硬标准。**实测与教程冲突时以实测为准，差异单列第七节，不调和掩盖。**
> 读法：全局层（第一节）先定，再按页面装配（第四节）选模块，逐模块查第三节的字段与量化标准；第六节平台边界先看，省得在改不了的地方耗时间。

---

## 一、全局层（主题与全站口径）

### 1.1 颜色（Inspector ＞ Theme ＞ Colors）

- 共 **32 个颜色字段 / 11 组**：PRIMARY、SECONDARY、ACCENT、BASE、CARD、POPOVER、MUTED、DESTRUCTIVE、BORDER & INPUT、CHART、SIDEBAR。逐组加总为：前八组各 2（16）＋BORDER & INPUT 3＋CHART 5＋SIDEBAR 8＝**32**。【实测】（注：逐组拆分系按总数 32 与 CHART 5 色、SIDEBAR 8 项两处明细推算，未逐组点验。）
- **品牌色只动 PRIMARY**：PRIMARY 影响按钮、链接、徽章，全站生效；演示站现值 `oklch(0.42 0.09 160)`（松绿，深色系，与品类气质一致）。【实测】【实践】（SKILL.md）
- **不要指望 ACCENT 做品牌色**：ACCENT 在 Default 模板的可见组件里基本不被引用，改了前台看不出变化（现值 `oklch(0.55 0.12 250)` 为平台默认，未动）。【实测】【实践】（SKILL.md）
- 改 PRIMARY 前把原值记进交接（可回滚）；保存发布后全站扫一遍生效点（主按钮、链接、徽章），逐页确认无漏网旧色。【实践】（SKILL.md）
- **新品牌选色口径（施工口径，补 G1）**：色相按品类气质定（演示站户外品类取深色松绿为一例）；深浅以主按钮、链接在浅底上可读为准，选定后按上一条纪律发布并逐页扫生效点实测可读性；饱和度保持克制、同屏彩色受控（见下条）。品牌方已给色值时以品牌值为准（收取口径见第八节第 1 项），未给且无从判断品类气质时不自创色值、先收输入。【实践】
- 其余组（BASE/CARD/…）多为平台默认灰阶，无品牌理由不动【实测】；同屏彩色受控：1 主色＋1 辅色＋1 强调色＋灰阶，超过 4 个彩色抢通道判丑点。【实践】（beauty-review.md）
- 主题只能改整体背景与整站风格，**不能单改某模块底色**。【实测】

### 1.2 字体与字距（Typography，仅 4 项）

- Sans-Serif Font、Serif Font、Monospace Font 三档，现值均为 System；自定义字体需嵌入可实际加载的 font family 字符串（填族名字符串，无上传入口）。【实测】
- Letter Spacing（字距）：数值＋滑块，现值 0 em；无品牌理由保持 0。【实测】
- **字号无入口**：标题与正文字号都改不了（见第六节边界）。【实测】层级靠模板自带比例与内容排版实现：美观评审要求标题与正文字号对比 ≥2.5 倍、3–4 个清晰层级，靠 H2 分段、加粗引导句补层级。【实践】（beauty-review.md）

### 1.3 间距、圆角、阴影（Other）

- **SPACING 0.25 rem 是全局间距基准，也是模块级无间距项的唯一替代控制点**：全站留白只从这里调，调前记原值、小样验证再全站发布。【实测】【实践】（SKILL.md）
- **RADIUS 0.625 rem**：全站圆角统一值，不逐模块调（也无处可调）。【实测】
- SHADOW：Color hsl(0 0% 0%)、Opacity 0.1、Blur 3px、Spread 0、Offset X 0 / Y 1px（现值，平台默认级克制阴影，无理由不动）。【实测】
- HSL ADJUSTMENTS 有预设（Hue ±60/±120、Invert、Grayscale、Muted、Vibrant、Dimmer、Brighter）＋ H/S/L 滑块【实测】：整站换调子时用，单页不许用。【实践】（SKILL.md）
- 主题仅 **1 套 Default**，Light/Dark 可切，无主题市场、无复制导出。【实测】
- **Light/Dark 施工口径（补 G18）**：默认全程 Light、不切换，Dark 不纳入验收；品牌方明确要求 Dark 时，先逐页核对 Dark 下的表现再决定 PRIMARY 是否需要另值，未核对前不承诺 Dark 效果。【实践】

### 1.4 全站一致性口径（跨模块硬规矩）

- **数字全站一个值**：评分、产品数、年限、客户数在首页、关于、页脚只许一个值，对不上以事实底稿为准改齐（教训：演示站评分口径曾出现不一致；本次盘点两处原料均为 **4.8/5**）。【实测】【实践】
- **命名全站一套词**：同一栏目在导航、页面标题、模块 Section Label、页脚只许一个叫法（演示站文章栏目统一「Stories」）。【实践】（SKILL.md）
- **联系方式全站一种写法**：邮箱、电话、地址逐字一致；电话邮箱设可点击（mailto:/tel:，冒号英文、无空格）。【实践】（SKILL.md）
- 图文对得上：每张图与所在模块文案主题相符、图注属实；同一张图不在多处当主图复用。【实践】（beauty-review.md）
- 网格列数＝条目数：设几列放几条，条目不够改列数或补条目，不留空白卡。【实践】（beauty-review.md）

---

## 二、模块通用规律（全库实测）

- 模块库共 **37 个 / 10 组**；全站已放置 **65 个实例 / 33 种**；**4 个从未被任何页面使用**：Header (Card)、Image Gallery、Video Section、Logo Cloud。【实测】
- 每个模块配置面板顶部都有 **Anchor ID＋Visible** 两项。【实测】
- 例外（2026-11-22 巡检补记）：Global 模块（Header、Footer 类）配置顶部现为 **Anchor ID＋ScopeMode＋Visible** 三项——ScopeMode 是全局模块的作用域字段、仅 Global 模块有，Page 模块无此项；其可选值未逐项核实前只记存在与适用范围、不写标准取值，施工取值照平台现状。【实测】
- **全部 33 种已用模块都没有间距项、高度项、字号项**；仅 **13 种**有 Columns 列数下拉；无其他版式数值项。【实测】
- 文本字段多带 **/300 字符上限**（Description、Supporting Copy、Quote、Answer 等）；站点描述为 /500。【实测】文章摘要的具体字符上限本次盘点未覆盖文章逐条内容，标 **【待验】（U4）**，见第 17 条与 §5.1。
- 链接字段统一用四档目标选择器：**None / Custom / Internal / Action**。【实测】教程《跳转链接》倡能用 Internal 直接选时优先、不要猜路径（列表是 /products 不是 /product）；但具体模块的实测值以盘点为准（如 Category Showcase 为 Custom，见第 9 条）。【教程】
- **Media Display**：本次盘点已用模块实测均为 **Crop to fill**；教程《图片显示不全》则倡先判断裁剪/拉伸/比例、优先改 **Fit inside**。两说并列，当前标 **【待验】（U5）**：施工时按原图比例与前台效果逐图选，不把任一值定死为全站标准。【实测】【教程】【待验】
- Global 模块（页眉、页脚、弹窗、浮钮）改一处全站生效，保存发布时弹「全局更改确认」，逐项核对影响清单再确认；页面级模块隐藏不弹此确认。【实测】【实践】（SKILL.md）
- 设计器纪律：**每页改完立即保存并验证再切换页面**；发布状态以前台读回为准，不信 Draft 状态条。【实践】（SKILL.md）「切换页面会丢未保存草稿」本次未复核，降格为 **【待验】**（U3），不再写成已证实平台行为。

---

## 三、模块层（逐模块标准，37 条）

> **读条口径**：每个模块条目末尾单列「来源」。条目中写成「推荐 XX–XX 字符」的区间，除非同句另有字段硬上限或 SKILL 明文出处，均为由演示站文案反推的**参考带 / 经验值**，须结合内容质量使用，不作交付硬闸。【实践】
> **Detail Page 口径**：Detail Page 是「选页面」的下拉，盘点实测值是页面名 **Product / Post**；/products、/posts 是对应列表路由，详情前台路径为 /products/{product}、/posts/{post}。不得把路径写成 Detail Page 的实测值。【实测】

### Navigation（4）

**1. Header (Dropdown)**［Global］
- 关键字段：Site Title、Logo Image、Logo Display（Crop to fill）、Tagline、Logo Target；菜单项 Label＋Target（可挂 Dropdown Items、Nested Items）；CTA Label＋CTA Target（演示站 Get a Quote → Action `#contact-form-dialog`）。
- 量化标准：Logo **宽 ≤350、透明 PNG、≤100KB**；一级菜单 **4–6 个**、短英文名；产品下拉只保留 **1 个**、挂真实分类。
- 备注：Logo 只在此模块设；站点信息里的站点图标是 Favicon，两处不要混。适用：全站页眉。
- 来源：【实测】字段、演示值与菜单结构；【教程】《图片规范》《子菜单和下拉菜单》的一级菜单 4–6 个、Logo 尺寸与体积；【实践】（SKILL.md）Logo 位置口径。

**2. Header (Card)**［Global］⚠️ **未实测**（库中未被任何页面使用）——使用前先在测试站验证，字段与标准验证后回填。
- 来源：【实测】仅确认模块存在且未被使用；字段与行为均为【待验】。

**3. Footer (Columns)**［Global］
- 关键字段：Brand、Kicker、Description（/300）、Copyright；COLUMNS 列组（Title＋Links）；SOCIAL 链接组。
- 量化标准：演示站 **4 列**（Shop / Company / Content / Contact）；Description 推荐 **60–150 字符**（/300 上限内留一半）；版权年份、品牌名与页眉逐字一致。
- 备注：社交无真实账号**明确留空**，不挂平台默认假链接（演示站现挂 instagram.com/x.com 通用地址属待清理项）；邮箱用 mailto 可点击。适用：全站页脚。联系值属品牌输入，见第八节第 2 项。
- 来源：【实测】字段、4 列结构与演示值；【教程】《网站联系方式设置》的可点击联系方式；【实践】字符区间为参考带 / 经验值，社交留空为施工口径。

**4. Breadcrumb (Inline)**［Page］
- 关键字段：仅 Anchor ID＋Visible，全站最简模块。
- 标准：除首页外每页必放（列表、详情、关于、联系均有）；路径文案由模板自动生成（如 Posts / Product），**无改名入口**——登记平台边界，不当站内待修项。
- 来源：【实测】字段与逐页装配；【实践】（SKILL.md）路径自动生成、无改名入口的边界口径。

### Heroes（3）

**5. Hero (Commerce)**［Page］（首页主推区）
- 关键字段：Eyebrow、Title、Description（/300）、Secondary Note（/300）；Service Items 3 组（Label＋Value）；Campaign Pills 3 组（Label＋Value）；Actions 2 组（Label＋Target＋Variant Solid/Outline）；Media（图＋Display＋Caption＋Kicker＋Meta）；Product Spotlight（Product Name＋Description /300＋Price Label）。
- 量化标准：图按实测存量 **1920×1280**（教程值只登记第七节 C1，不作正文标准值）；Media Display 按第二节的两说并列口径逐图定；Description 推荐 **80–200 字符**（参考带 / 经验值）；Spotlight 只放 **1 个**主推产品，Price Label 位可放规格口径（如「750 ml / 25 oz」），**不编价格**；主 CTA 用 Solid → 产品页、次 CTA 用 Outline → 关于页。Service Items 的数值口径属品牌输入，见第八节第 5 项。
- 适用：首页。
- 来源：【实测】字段、演示值与媒体库 1920×1280；【教程】《图片规范》的体积临界与 alt 口径；【实践】字符区间、CTA 与不编价格口径。

**6. Page Header (Card)**［Page］（列表页页头）
- 关键字段：Eyebrow、Title、Description（/300）、Kicker；STATS 2 项（Label＋Value）。
- 量化标准：Title 与导航叫法逐字一致（Products / Stories）；Description 推荐 **60–160 字符**（参考带 / 经验值）；STATS 写可兑现口径（如 Catalog / Updated weekly），不编数字。
- 适用：产品列表、文章列表等栏目页。
- 来源：【实测】字段与两页演示值；【实践】字符区间为参考带 / 经验值，一致性与不编数字为施工口径。

**7. Contact Header (Summary)**［Page］（联系页页头）
- 关键字段：Eyebrow、Title、Description（/300）；Quick Details 2 项（Label＋Value）。
- 量化标准：Quick Details **必写响应时限**（演示值 Within one business day）——B 端信任要素；第二项写适用场景（Orders, wholesale, product support）。
- 适用：联系页。
- 来源：【实测】字段与演示值；【实践】响应时限与场景写法为 B2B 施工口径。

### Campaigns（1）

**8. Carousel (Campaign)**［Page］（首页首屏轮播）
- 关键字段：SLIDES 每张含 Eyebrow / Title / Description（/300）/ Media（Image 或 Video＋图＋Media Display＋Show Mask 开关）/ Price Label / Product Label / Primary、Secondary（Label＋Target）；SERVICE 2 项（Icon 下拉＋Title＋Description /300）。
- 量化标准：**3 张**；首张放主推产品特写＋全站主张标题，标题短句两行内（如「Trail-tested. Shelf-ready.」）；图按实测存量 **1920×1280**（教程值只登记 C1）、全套图同一光线感、一图一用途；Media Display 按第二节的两说并列口径逐图定；SERVICE 2 项写可兑现的服务（样品、批发支持），**不借模板的包邮退货承诺**。
- 验收注意：轮播是动态内容，**文本抓取验不了，必须实时渲染逐张核查**。适用：首页首屏。
- 来源：【实测】字段、3 张轮播、SERVICE 与媒体库尺寸；【教程】《图片规范》的体积临界与 alt 口径；【实践】（SKILL.md）首张主张、服务口径与实时渲染验收。

### Catalog（4）

**9. Category Showcase (Grid)**［Page］
- 关键字段：Section Label、Headline、Supporting Copy（/300）；ITEMS（Name＋Description /300＋Media＋Target）；LAYOUT Columns。
- 量化标准：分类 **3–4 个**主要类别、勿太细；**Columns＝条目数**（演示 3 列 3 类）；卡图比例全组统一；Media Display 按第二节的两说并列口径逐图定。Target：演示站实测为 **Custom**（指向各分类查询路径）；教程《跳转链接》倡能用 Internal 时优先用 Internal——两说并列，施工时以后台当场可选目标为准，不把演示值写成教程口径。
- 备注：分类名以后台实名为准；删分类后卡片仍在，须改卡或隐藏模块。适用：首页。分类名单与产品归属属品牌输入，见第八节第 6 项。
- 来源：【实测】字段、3 项、Columns=3 与 Target=Custom；【教程】《产品分类》的 3–4 个主要类别、《跳转链接》的 Internal 优先；【实践】（SKILL.md）分类名与删分类后的卡片处置。

**10. Featured Product List (Showcase)**［Page］
- 关键字段：Section Label、Headline、Supporting Copy（/300）、Merchandising Note（/300）、CTA Label、**Featured Product Action Label**、Product Action Label、Product Image Display；BEHAVIOR（List Page / Detail Page / Category / Sort）。
- 量化标准：**Detail Page 必选 Product（页面名；对应详情路由 /products/{product}）**，选错会造成点击落点错误；每分类只推 **1–2 个**重点品、调高排序值；演示值 List Page=Products、Detail Page=Product、Category=All、Sort=Newest first；Product Image Display 按第二节 Media Display 两说并列口径逐图定。
- 适用：首页精选产品区。
- 来源：【实测】全部字段（含两个 Action Label）与演示值；【教程】《产品模块》《首页推荐产品》的 Detail Page 选择、每分类 1–2 个与排序口径；【实践】（SKILL.md）重点品口径。

**11. Full Product List (Filtered)**［Page］
- 关键字段：Product Action Label、Product Image Display、Detail Page、Page Size、Show Toolbar、Sort、Columns。
- 量化标准：演示值 **Page Size=12、Columns=3、Toolbar 开**；Detail Page 实测为 **Product（页面名）**。产品数量较少、网格明显显空时，可把关 Toolbar 或降列数作为**参考带 / 经验处置**，不设统一数值阈值；Action Label 用买家语言（View product）；Product Image Display 按第二节 Media Display 两说并列口径逐图定。
- 适用：产品列表页。
- 来源：【实测】字段与演示值；【实践】（SKILL.md）数量不足时删模块、改列数或关筛选栏的定性口径（无 <6 阈值）。

**12. Recommended Products (Grid)**［Page］
- 关键字段：Section Label、Headline、Page Size、Columns。
- 量化标准：演示值 **Page Size=3、Columns=3**；Headline 与所在页语境挂钩；内容不足以形成有意义的推荐时，按内容充分性判断隐藏整块，不设「不足 2 件」的数值阈值。空推荐的前台表现未在本次盘点验证，列 **【待验】**（U2），不写成平台定论；Product Image Display 按第二节 Media Display 两说并列口径逐图定。
- 适用：文章列表/详情等页的跨类推荐。
- 来源：【实测】字段与演示值；【实践】内容充分性与隐藏整块为施工判断；【待验】空推荐前台表现（U2）。

### Products（2）

**13. Product Detail (Gallery)**［Page］（产品详情模板）
- 关键字段：Preview Product 下拉（仅编辑预览用）、Specifications Heading、Product Image Display。
- 量化标准：主图 **800 或 1000 正方形**；数值带单位且公制英制双标、三处（规格表/正文/图说）一致；产品正文 **≥450 英文词 / 中文 800 字**（深度地板，硬闸）；Product Image Display 按第二节 Media Display 两说并列口径逐图定。
- 图册口径（补 G19）：主图 1 张必备（尺寸见上）；其余图册张数、顺序与场景/细节配比本库未定，按内容充分性备图、不留空图位；alt 用一句英文写清主体与用途。【教程】《图片规范》；【实践】
- 边界：模板**无价格与购买区块**——购买引导靠正文行动段＋页眉报价弹窗承接，不许假装有价格区。
- 来源：【实测】模板字段与无价格区块的装配事实；【教程】《图片规范》的产品主图尺寸；【实践】（SKILL.md）正文深度地板、单位双标与三处一致。
- 输入依赖：规格表逐行值属品牌输入，见第八节第 4 项。

**14. Product Related (Grid)**［Page］
- 关键字段：Section Label、Headline、Supporting Copy（/300）、Product Action Label、Product Image Display、Detail Page、Page Size、Sort、Columns（演示值 Page Size=3 / Columns=3）。
- 当前状态与标准：演示站有 **5 件产品**，Product Related 仍为隐藏——盘点定性是**施工时已全局关闭**，不是产品数量触发某个数值阈值。后续是否开启按关联内容是否充分、页面是否显空作施工判断，不设「总数 ≤2 关闭 / ≥3 开启」的门槛。
- 适用：产品详情模板。
- 来源：【实测】字段、演示值、5 件产品与隐藏状态及其施工关闭定性；【实践】（SKILL.md）内容不足时删相关模块的定性口径。

### Articles（5）

**15. Featured News List (Editorial)**［Page］
- 关键字段：Section Label、Headline、Supporting Copy（/300）、Digest Label、Feature Label、CTA Label、Post Image Display；BEHAVIOR（List Page / Detail Page）。
- 量化标准：**Detail Page 必选 Post（页面名；对应详情路由 /posts/{post}）**；封面图 **1200×700**；栏目名全站统一一个叫法；Post Image Display 按第二节 Media Display 两说并列口径逐图定。
- 适用：首页精选文章区。
- 来源：【实测】字段、List Page=Posts 与 Detail Page=Post；【教程】《图片规范》的文章主图尺寸、《产品模块》的详情页选择口径；【实践】栏目名全站一致。

**16. Full News List (Filtered)**［Page］
- 关键字段：Post Action Label、Page Size、Show Toolbar、Columns。
- 量化标准：演示值 **Page Size=10、Columns=2、Toolbar 开**——文章列表 2 列与产品列表 3 列的区分是实测现行口径，照用；Detail Page 实测为 **Post（页面名）**；Post Image Display 按第二节 Media Display 两说并列口径逐图定。
- 适用：文章列表页。
- 来源：【实测】字段与全部演示值；【实践】列表列数区分与 Media Display 施工口径。

**17. Post Detail (Article)**［Page］（文章详情模板）
- 关键字段：Preview Post 下拉（编辑预览）、Post Image Display。
- 量化标准：正文 **≥1,200 英文词 / 中文 2,000 字**（深度地板，硬闸；形态篇幅带在此之上：指南 1200–2000、对比 1000–1800、清单 900–1600、诊断 800–1400、案例 800–1200 词，下限取 max(带下限, 地板)）；排版 H2 分段、单段 ≤约 120 中文字 / 60 英文词、结尾必有 CTA 段；搜索快查口径为标题 ≤60 字符、描述 150–160 字符（英文字符口径）。**文章摘要的具体字符上限标【待验】（U4）**：本次盘点未覆盖文章逐条内容，不能把任何具体数值写成已实测标准，施工时须进文章编辑器现场复核。
- 备注：文章编辑器当前只有标题与摘要两个字段，无独立搜索标题/描述字段、无文章分类字段，不要找不存在的字段；Post Image Display 按第二节 Media Display 两说并列口径逐图定。内链与元信息口径（补 G23）：正文内链以结尾 CTA 段为主要落点，正文中间内链的数量本库未定、不作硬标准；作者、发布日期等元信息以模板实际显示为准，编辑器无相应字段，不另设、不假装可填。【实测】【实践】
- 来源：【实测】模板字段与 Detail 装配；【实践】（SKILL.md）正文深度地板、形态篇幅带、单段长度、SEO 标题/描述与编辑器字段口径；【待验】文章摘要具体字符上限。

**18. Post Related (Grid)**［Page］
- 关键字段：Section Label、Headline、Page Size、Columns（演示值 3 / 3）。
- 量化标准：内容不足以形成有意义的关联阅读时，按内容充分性判断隐藏或补内容再留，不设「不足 2 篇」的数值阈值；Post Image Display 按第二节 Media Display 两说并列口径逐图定。
- 适用：文章详情模板。
- 来源：【实测】字段与演示值；【实践】（SKILL.md）内容不足时删相关模块、改列数或补内容的定性口径。

**19. Recommended Articles (Grid)**［Page］
- 关键字段：Section Label、Headline、Page Size、Columns（演示值 3 / 3）。
- 量化标准：Headline 写与宿主页面的关系（如产品页放「Stories for choosing well」）；内容不足以形成有意义的推荐时，按内容充分性判断隐藏，不设「不足 2 篇」的数值阈值；Post Image Display 按第二节 Media Display 两说并列口径逐图定。
- 适用：产品列表等页的跨类推荐。
- 来源：【实测】字段、演示值与 Headline；【实践】内容充分性与隐藏整块为施工判断。

### Media（2）

**20. Image Gallery**［Page］⚠️ **未实测**（库中未被任何页面使用）——使用前先在测试站验证。
- 教程口径先行：先放 **6–12 张**、比例一致；无素材勿放空模块。字段与自有标准验证后回填。
- 来源：【实测】仅确认模块存在且未被使用；【教程】《视频模块和图片画廊》的数量与比例口径；其余字段和行为【待验】。

**21. Video Section**［Page］⚠️ **未实测**（库中未被任何页面使用）——使用前先在测试站验证。
- 教程口径先行：**只支持 YouTube 链接，勿上传本地视频**；选 Split 分栏。字段与自有标准验证后回填。
- 来源：【实测】仅确认模块存在且未被使用；【教程】《视频模块和图片画廊》的 YouTube 与 Split 口径；其余字段和行为【待验】。

### Story（5）

**22. About Intro (Media)**［Page］（关于页首块）
- 关键字段：Eyebrow、Title、Description（/300）、Body（/300）；Media（图＋Caption）。
- 量化标准：两个 /300 是硬上限——关于页长文案拆到 Company Story 等模块分担，不许在一块里硬塞；Caption 写实内容（如「Carry goods for the long trail.」）；Media Display 按第二节的两说并列口径逐图定。
- 适用：关于页。
- 来源：【实测】字段、/300 上限与演示 Caption；【实践】长文案分担与 Caption 写实口径。

**23. Company Story (Media)**［Page］
- 关键字段：Section Label、Headline、Lead（/300）、Body（/300）；NOTE（Note Label＋Note /300）；Media。
- 量化标准：Headline 写一条可兑现的主张式句子（演示值「One rule before anything ships.」）；品牌故事 2–3 句真姿态，不编历史与数字；Media Display 按第二节的两说并列口径逐图定。
- 适用：关于页。
- 来源：【实测】字段与演示值；【实践】（SKILL.md）品牌故事真姿态与不编造口径。

**24. Company Team (Grid)**［Page］（演示站隐藏）
- 关键字段：MEMBERS（Photo＋Name＋Role＋Bio /300）；Columns（演示值 3）。
- 量化标准：Bio 推荐 **60–160 字符**（参考带 / 经验值）；**无真实成员照片与信息就隐藏整块**，不放占位假人（演示站即因 Photo 未选而隐藏）；Photo Display 按第二节 Media Display 两说并列口径逐图定。
- 适用：关于页。
- 来源：【实测】字段、Photo 未选与隐藏状态；【实践】字符区间为参考带 / 经验值，无真实材料隐藏整块。
- 输入依赖：成员照片与信息属品牌输入，见第八节第 3 项。

**25. Company Values (Grid)**［Page］
- 关键字段：VALUES（Title＋Description /300）；Columns。
- 量化标准：演示值 **4 项 / Columns=2**；条目数与列数要整除（4 项→2 或 4 列），不留半行空白卡；Description 推荐 **60–180 字符**（参考带 / 经验值）。
- 适用：关于页。
- 来源：【实测】字段、4 项与 Columns=2；【实践】字符区间为参考带 / 经验值，条目与列数整除为版式口径。

**26. Material Story (Split)**［Page］（首页材质故事）
- 关键字段：Section Label、Headline、Supporting Copy（/300）；Media（图＋Display）；NOTES 3 项（Title＋Description /300）；Action（Label＋Target）。
- 量化标准：NOTES **3 项**写材质/护理硬知识，每项 Description 推荐 **60–160 字符**（参考带 / 经验值）；图与文案主题对得上（演示教训：封面图与文章主题错位被评审点名返工）；Media Display 按第二节的两说并列口径逐图定。
- 变体：无实物材质的服务商把本块换成服务流程或案例块，其余顺序不变。适用：首页（Feature Grid 之后、Featured Product List 之前）。
- 来源：【实测】字段、3 项 NOTES 与首页装配顺序；【实践】字符区间为参考带 / 经验值，图文对应与服务商变体为施工口径。

### Proof（5）

**27. Company Stats (Grid)**［Page］（演示站隐藏）
- 关键字段：STATS（Value＋Label＋Description）；Columns（演示值 4 项 / 4 列）。
- 量化标准：**数字只用资料里已确认的，一个值全站一致**；对不上就隐藏整块、不许凑数——演示站「Core products 38」与在售 5 件对不上，即按此隐藏。
- 适用：关于页。
- 来源：【实测】4 项 STATS、Columns=4、评分 4.8/5 与隐藏状态；【实践】数字核实与全站一致口径。
- 输入依赖：统计数字已确认值属品牌输入，见第八节第 3 项。

**28. FAQ (Accordion)**［Page］
- 关键字段：Section Label、Headline、Supporting Copy（/300）、Support Note（/300）；Items（Question＋Answer /300）。
- 量化标准：**必备五题**——起订量、样品政策、交期、定制（logo/包装）、付款与物流口径，缺题就是缺信任；Answer /300 是硬上限，长答案拆题或链到详情页；教程首次量口径 3–5 个 FAQ，与五题口径的合并见第七节 C8。
- 适用：首页、关于页。
- 来源：【实测】字段与 5 项 Items；【教程】《建站前准备》的首次 3–5 个 FAQ；【实践】五题主题清单与长答案处置。
- 输入依赖：五题答案数值属品牌输入，见第八节第 5 项。

**29. Feature Grid (Proof)**［Page］（首页特性证明）
- 关键字段：Eyebrow、Heading、Description（/300）；Proof Rows（Label＋Title＋Description /300＋Meta＋Action Label＋Target）；Columns（演示值 3 行 / 3 列）。
- 量化标准：每行一个**可验证**的凭据点（流程、检测、条款），不写空话形容词；行数与列数对齐。
- 适用：首页（Hero (Commerce) 之后、Material Story (Split) 之前）。
- 来源：【实测】字段、3 行、Columns=3 与首页装配顺序；【实践】可验证凭据点与行列对齐口径。

**30. Logo Cloud**［Page］⚠️ **未实测**（库中未被任何页面使用）——使用前先在测试站验证。
- 红线先行：只放**真实授权**的客户/合作方 Logo，无授权不许放（编造背书是内容红线）；字段与标准验证后回填。
- 来源：【实测】仅确认模块存在且未被使用；【实践】真实授权红线；其余字段和行为【待验】。

**31. Social Proof (Quotes)**［Page］（演示站隐藏）
- 关键字段：Section Label、Headline、Rating Label；REVIEWS（Quote /300＋Name＋Detail）；Columns（演示值 3）。
- 量化标准：**只放真实评价，用户拿不出就删掉/隐藏整块，不摆假评价撑门面**；Rating Label 的分数全站一个值（演示 4.8/5）；Quote 推荐 **60–200 字符**（参考带 / 经验值）。
- 适用：首页（Featured Product List 之后、Featured News List 之前）。
- 来源：【实测】字段、3 项 REVIEWS、Columns=3、Rating Label 4.8/5 与隐藏状态；【实践】字符区间为参考带 / 经验值，真实评价红线。
- 输入依赖：真实评价原文与评分属品牌输入，见第八节第 3 项。

### Forms（6）

**32. Contact Dialog Form (Modal)**［Global］（询盘弹窗）
- 关键字段：Anchor ID（演示实值 `contact-form-dialog`，页眉 CTA 以 Action 引用它）、Title、Description（/300）、Eyebrow、Close Label；Form 下拉。
- 量化标准：**Anchor ID 不许改**（改了页眉 CTA 触发失效）；必须绑站内真实表单，绑完在前台试填一次确认能提交、能收信；一页先放 **1 个**弹窗。
- 适用：全站（页眉 CTA 落点）。
- 来源：【实测】Anchor ID 实值、字段与 Form 绑定；【教程】《弹窗表单》的一页 1 个与提交测试；【实践】Anchor ID 不改的前台联动口径。
- 输入依赖：绑定表单名与弹窗文案属品牌输入，见第八节第 8 项。

**33. Contact Form (Split)**［Page］（首页/关于/联系三处复用）
- 关键字段：Eyebrow、Title、Description（/300）；Email / Phone / Address / Hours Value；Response Title/Description＋四 Label；Form Card（Eyebrow/Title/Description）＋Form 下拉。
- 量化标准：四项联系值全站一种写法、逐字一致；绑真实表单＋前台试填；演示站邮箱用站域名邮箱，不用私人真实联系方式；表单字段第一版只留 Name / Email / Topic / Message 四字段全必填；成功提示现值为 "Thanks. Your message has been sent."，**可否修改未验证，见 C11**，未实测前不写成固定文案、也不承诺可改。
- 适用：首页联系区、关于页收尾、联系页。
- 来源：【实测】模块字段、三处装配、表单字段与成功提示现值；【教程】《表单修改教程》的四字段与前台提交测试；【实践】联系值全站一致与站域名邮箱口径；【待验】成功提示可否修改（C11）。
- 输入依赖：联系值属品牌输入，见第八节第 2 项；绑定表单名见第八节第 8 项。

**34. Contact Info (Grid)**［Page］
- 关键字段：Contact Items（Type 下拉 Email/Phone/Address/Hours＋Label＋Value＋Detail /300）；Social Links；Columns（演示值 4 项 / 2 列）。
- 量化标准：四项齐（邮箱、电话、地址、工时）；电话邮箱可点击；社交无真实账号留空，不挂默认假链接。
- 适用：联系页。
- 来源：【实测】字段、4 项 Contact Items、2 项 Social Links 与 Columns=2；【教程】《网站联系方式设置》的可点击口径；【实践】四项齐与社交留空口径。

**35. Location Map (Interactive)**［Page］（演示站隐藏）
- 关键字段：Address、Google Maps URL、Latitude、Longitude、Zoom、Map Type；DETAILS 2 项。
- 量化标准：演示值 Zoom=14、Map Type=Map；Maps URL 从 Google 地图**分享**复制准确位置链接，勿只复制搜索结果；**URL 为空时隐藏整块**（演示站处置）；前台地图显示灰块多半是外部地图问题，不要当自己页面毛病反复改。
- 适用：联系页（页头、信息卡之后，表单之前）。
- 来源：【实测】字段、经纬度、Zoom、Map Type、URL 空与隐藏状态；【教程】《添加位置地图》的分享链接口径；【实践】URL 空隐藏与灰块排查口径。
- 输入依赖：准确地址属品牌输入，见第八节第 2 项。

**36. Newsletter (Inline)**［Page］
- 关键字段：Section Label、Headline、Supporting Copy（/300）；FORM（Email Placeholder、Submit Label、Fine Print /300）。
- 量化标准：Submit Label 用动作词（演示值 Subscribe）；Fine Print 写清发送频率与退订口径，不夸大不承诺效果。
- 适用：首页（FAQ 之后、联系区之前）、单页收尾。
- 来源：【实测】字段与演示值；【实践】动作词、Fine Print 与不承诺效果口径。
- 输入依赖：发送频率与退订机制属品牌输入，见第八节第 7 项。

**37. Social Floating Button**［Global］（演示站隐藏）
- 关键字段：Brand 下拉（如 WhatsApp）、URL、Label、Show Label 开关、Position（演示值 Bottom Right）。
- 量化标准：URL 格式 `https://wa.me/区号+手机号`，无空格无符号；**每页只一个**，发布前点测；有真实号码才挂，没有就整个删掉/隐藏（施工口径）。「留空会被平台顶回演示假号」本次盘点未验证，降格为 **【待验】**（U1），不作平台行为断言。
- 适用：全站悬浮。
- 来源：【实测】字段、演示 URL、Show Label 关、Position 与隐藏状态；【教程】《WhatsApp 悬浮按钮》的 URL 格式、每页一个与发布前点测；【实践】无真实号码时删掉/隐藏；【待验】留空回填说法（U1）。
- 输入依赖：WhatsApp 真实号码属品牌输入，见第八节第 8 项。

---

## 四、页面装配标准（7 条路由）

全站 7 条路由均为模块拼装、无整页富文本。每页另有 3 个 Global（Header (Dropdown)、Footer (Columns)、Contact Dialog Form (Modal)，及按需的 Social Floating Button）不在下表重复计。

### 4.1 首页（演示站实测 15 个实例）

按买家动线排 **11 个页面模块**，顺序定版不调换（精选文章在前、FAQ 在后）：

| # | 模块 | 备注 |
|---|---|---|
| 1 | Carousel (Campaign) | 首屏，主推特写＋主张标题。【实测】 |
| 2 | Category Showcase (Grid) | 分类卡，Columns＝分类数。【实测】 |
| 3 | Hero (Commerce) | 主推区，Spotlight 1 个主推品。【实测】 |
| 4 | Feature Grid (Proof) | 特性证明 3 行 3 列。【实测】 |
| 5 | Material Story (Split) | 服务商换服务流程/案例块。【实测】【实践】 |
| 6 | Featured Product List (Showcase) | Detail Page 选 Product（页面名）。【实测】 |
| 7 | Social Proof (Quotes) | 无真实评价则删，不占位。【实测】【实践】 |
| 8 | Featured News List (Editorial) | 栏目名全站统一。【实测】【实践】 |
| 9 | FAQ (Accordion) | 必备五题。【实测】【实践】 |
| 10 | Newsletter (Inline) | 【实测】 |
| 11 | Contact Form (Split) | 收尾询盘区。【实测】 |

动线逻辑：先看懂卖什么 → 凭什么信 → 看产品 → 读内容 → 留询盘。首页至少 **3 处行动点**（轮播按钮、主推产品卡、页尾联系区）。
新站先按教程最小集跑通（Header → Carousel → Category Showcase → Featured Product → Featured News → Footer）再按上表补齐，两口径关系见第七节 C7。

### 4.2 产品列表页（实测 8 个实例）

Breadcrumb → Page Header (Card) → Full Product List (Filtered) → Recommended Articles (Grid)。【实测】

### 4.3 文章列表页（实测 8 个实例）

Breadcrumb → Page Header (Card) → Full News List (Filtered) → Recommended Products (Grid)。【实测】

### 4.4 产品详情模板（实测 7 个实例）

Breadcrumb → Product Detail (Gallery) → Product Related (Grid；演示站当前隐藏，原因是施工时全局关闭，见第 14 条)。购买承接靠正文行动段＋页眉弹窗。【实测】【实践】（SKILL.md）

### 4.5 文章详情模板（实测 7 个实例）

Breadcrumb → Post Detail (Article) → Post Related (Grid)。【实测】

### 4.6 关于页（实测 11 个实例）

Breadcrumb → About Intro (Media) → Company Story (Media) → Company Stats (Grid，数字核实才放) → Company Values (Grid) → Contact Form (Split) → Company Team (Grid，有真人才放)。【实测】单页收尾必须有行动入口，没有在美观评审功能性扣分。【实践】（beauty-review.md）

### 4.7 联系页（实测 9 个实例）

Breadcrumb → Contact Header (Summary) → Contact Info (Grid) → Location Map (Interactive，有准确地址才放) → Contact Form (Split)。【实测】

---

## 五、内容量与图片标准（跨模块汇总）

### 5.1 文案量

| 对象 | 标准 | 来源 |
|---|---|---|
| 模块短文案（Description 等） | 硬上限多为 **/300**；推荐区间见各模块条目（多为 60–200，均为参考带 / 经验值） | 【实测】（/300）；【实践】（推荐区间） |
| 产品正文 | **≥450 英文词 / 中文 800 字**（深度地板，硬闸） | 【实践】（SKILL.md） |
| 文章正文 | **≥1,200 英文词 / 中文 2,000 字**（地板）；形态带：指南 1200–2000 / 对比 1000–1800 / 清单 900–1600 / 诊断 800–1400 / 案例 800–1200 词，实际下限＝max(带下限, 地板) | 【实践】（SKILL.md） |
| 文章摘要 | 具体字符上限未定：本次盘点未覆盖文章逐条内容，不把任何数值写成已实测标准，施工时现场复核 | 【待验】（U4） |
| SEO 标题 / 描述 | 标题 ≤60 字符；描述 150–160 字符（英文字符口径） | 【实践】（SKILL.md） |
| 正文段长 | 单段 ≤约 120 中文字 / 60 英文词；H2 分段不跳级 | 【实践】（SKILL.md） |
| 站点描述 | /500 上限 | 【实测】 |
| 表单字段 | Name 0/120、Message 0/1200（Contact Inquiry 值） | 【实测】 |

英文词数与中文字数是两套并行口径、**不互相换算**（勿用 1.8 倍之类系数互推）。

### 5.2 图片

| 用途 | 尺寸 | 体积 | 来源 |
|---|---|---|---|
| Banner（轮播/Hero） | **1920×1280**（正文标准值；教程值只登记 C1） | 多数图 ≤300KB；**超 500kB 必慢** | 【实测】（尺寸）；【教程】《图片规范》（体积） |
| 产品主图 | **800 或 1000 正方形** | 多数图 ≤300KB；**超 500kB 必慢** | 【教程】《图片规范》 |
| 文章主图/封面 | **1200×700** | 多数图 ≤300KB；**超 500kB 必慢** | 【教程】《图片规范》 |
| Logo | 宽 ≤350、透明 PNG | ≤100KB；**超 500kB 必慢** | 【教程】《图片规范》 |
| Favicon | 512 正方形简洁品牌图 | ≤100KB；**超 500kB 必慢** | 【教程】《图片规范》 |
| 全站通用 | 先转 **WebP**；alt 写清内容；传进媒体库不用外链 | **超 500kB 必慢** | 【教程】《图片规范》 |

备图顺序：先按模块定尺寸再备图。演示站媒体库现状：9 张全为 **1920×1280**，与教程分类尺寸不一致，见 C1/C2。

### 5.3 内容量门槛（站级）

- 首次量：**3–4 个主分类、每类 ≥2 个产品、3 篇文章、3–5 个 FAQ**（FAQ 与必备五题的合并见 C8）。按 3 个分类计，教程首次量对应产品合计 ≥6 个；与本节旧稿曾写的较低门槛冲突，见 C12。【教程】《建站前准备》《首页必备模块》
- 演示站现状为 **5 个产品**，这只是现状记录，不是合格门槛，也不构成 Product Related 的开关阈值。【实测】
- 内容量不够时：删相关模块、改列数或关筛选栏，不硬凑假内容撑场面。【实践】（SKILL.md）

---

## 六、平台边界（显名，改不了的别耗时间）

1. **全模块无间距项、高度项、字号项**（33 种已用模块全核）；留白只能动全局 SPACING 0.25rem。【实测】
2. 仅 **13 / 33** 种模块有 Columns 列数项，其余版式由模板定死。【实测】
3. **字号无入口**（标题、正文均无）；字体只有族名字符串＋字距。【实测】
4. 不能单改某模块底色，只能改整体背景/主题 token。【实测】
5. **ACCENT token 在 Default 可见组件基本不被引用**，品牌色走 PRIMARY。【实测】【实践】（SKILL.md）
6. 仅 1 套 Default 主题，无主题市场、无自定义 CSS/JS 入口。【实测】
7. **产品详情模板无价格/购买区块**，购买引导靠正文行动段＋弹窗表单承接。【实测】
8. 页眉半透明无开关：缓解靠内容层（Hero 图避开高对比区与文字压顶）。【实践】（SKILL.md）
9. Breadcrumb 路径文案模板自动生成，无改名入口。【实测】
10. 联系表单成功提示可否修改**未验证**：现值见第 33 条，教程与旧口径冲突，见 C11；未实测前不列作「固定文案」边界。
11. 页脚社交可挂通用平台地址（演示站现状）——是可填字段而非强制，但无真实账号应留空（口径见第 3 条）。【实测】【实践】（SKILL.md）
12. 404 等运行时页面样式平台定死，不在美化范围。【实践】（SKILL.md）
13. **4 个模块未实测**：Header (Card)、Image Gallery、Video Section、Logo Cloud——使用前先在测试站验证。【实测】
14. 全局块保存发布有确认弹窗【实践】（SKILL.md）；「设计器切换页面会丢未保存草稿」本次未复核，已移入待验项 U3，不作平台边界断言。
15. 站点设置面仅 4 项（站点信息 / 站点语言 / Google 追踪 / 域名）；本次盘点**未见「AI 配置」入口**（与教程说法冲突，见 C4）。【实测】
16. **GEO / AI 搜索无口径（补 G24）**：本库只覆盖传统 SEO（标题/描述字符口径与编辑器字段），未覆盖 GEO/AI 搜索可见性的字段、结构与验收口径；不作任何 GEO 承诺，有需求须另立标准后再施工。【实践】

### 待验项（不作硬标准或平台边界）

- **U1【待验】Social Floating Button 留空回填**：「留空会被平台顶回演示假号」本次盘点未验证，不作平台行为断言；无真实号码时删掉/隐藏只是施工口径。**裁定前施工口径（G15）**：有真实号码才挂，按第 37 条格式填写并发布前点测；无号码整个不挂，不试留空。
- **U2【待验】Recommended Products 空推荐表现**：「空推荐会显示无内容提示」本次盘点未验证，不作平台行为断言；内容不足时隐藏只是施工判断。**裁定前施工口径（G13）**：内容是否充分由施工方逐页人工判断，不足就隐藏整块，不依赖平台空状态提示；Recommended Articles 同此处置。
- **U3【待验】设计器切换页面与未保存草稿**：「切换页面会丢未保存草稿」本次盘点未复核，不作平台行为断言；每页改完立即保存只是操作纪律。**裁定前施工口径（G14）**：按最严口径执行——每页改完立即保存并验证再切换页面。
- **U4【待验】文章摘要具体字符上限**：本次盘点未覆盖文章逐条内容，不把任何具体数值写成已实测标准；施工时进文章编辑器现场复核。**裁定前施工口径（G8）**：摘要长度以编辑器现场复核结果为准；SEO 标题暂用文章标题承接、SEO 描述暂用摘要近似承接，未核前不承诺任何数值。
- **U5【待验】Media Display 取值**：实测已用模块均为 Crop to fill，教程倡优先 Fit inside；两说并列，逐图按原图比例与前台效果验证，不定死为全站标准。**裁定前施工口径（G7）**：不全站定死，每张图按原图比例与前台效果逐图选定并逐图核对一次。

---

## 七、冲突与存疑（以实测为准，差异不调和）

**C1. Banner/轮播图尺寸：教程 1800×1000 vs 实测存量 1920×1280。**
教程《图片规范》给 Banner 1800×1000（16:9）；实测演示站媒体库 9 张图全部 1920×1280（3:2），Carousel 与 Hero (Commerce) 均正常显示并通过 7.7 分评审【实践】（演示站评审沉淀）。本库正文标准值统一采用 **1920×1280**；1800×1000 **只在本节登记**，不进入模块条目或汇总表。尚待同图两尺寸前台对照验证何者呈现更优（见文末问题 1），但不影响正文当前口径。**裁定前施工口径（G12）**：全部按 1920×1280 备图（即正文现行口径），对照实测完成前不改尺寸标准。

**C2. 产品图尺寸口径的新旧差：SKILL 旧句「像素尺寸查无出处、不写死」已被教程数值取代。**
SKILL 施工通则写于教程盘点之前，称产品图/横幅像素尺寸「原工具包查无出处，不写死，第一次后台实测确认后记交接」；本次教程盘点给出了产品主图 800/1000 正方形、文章主图 1200×700 等明确数值。本库以教程数值为准先行；SKILL 该句待下一版修订对齐。

**C3. 中文站篇幅地板的适用条件：SKILL 有中文 2,000 字口径 vs 实测站点语言现状。**
按盘点原话：站点语言**默认语言为英语、已启用 1 种语言**；默认语言的自动翻译开关与已启用开关均为禁用，盘点未使用「锁定」定性。教程《开启网站多语言》称绑定 AI API 后可添加语言。两口径不矛盾但适用条件不同：未开多语言时中文内容填在英语环境；中文地板（产品 800 字 / 文章 2,000 字）适用于已开中文语言或中文站场景，引用时须注明条件。

**C4. 「AI 配置」入口：教程说有 vs 实测设置面未见。**
教程《绑定 AI API》称「后台设置→AI 配置」可选服务商、粘 Key；实测设置面仅 4 项（站点信息 / 站点语言 / Google 追踪 / 域名），未见 AI 配置，设计器底部仅有 AI 助手输入条。以实测为准：当前测试站未见该入口（可能与账号或版本有关），涉及多语言/翻译功能时先复核入口再承诺。

**C5. 弹窗模块名：教程「Contact Form (Split) Popup Form」vs 实测模块库无此名。**
教程《弹窗表单》称设计器加「Contact Form (Split) Popup Form 模块、Props 选表单」；实测模块库中是两个独立模块：Contact Dialog Form (Modal)［Global］与 Contact Form (Split)［Page］。以实测为准：弹窗走 Contact Dialog Form (Modal)，靠 Anchor ID 被页眉 CTA 的 Action 触发。

**C6. 分类页是否存在：教程「建好类别即有分类页」vs 既有实测「无独立分类页」。**
教程《产品分类》称建好类别即有分类页、勿在 Routes 重建；既有实测口径（SKILL 既往盘点）为分类 slug 自动去连字符且无独立分类页。本次盘点范围是后台设计器，**未复核分类页前台形态**，两说并列存疑：下次施工时点分类卡前台实测一次再定论，本库暂不采任何一说为标准。**裁定前施工口径（G9）**：分类卡 Target 按后台当场可选目标填写，不预设分类页存在与否；上线前点分类卡做一次前台实测再定论。

**C7. 首页模块集：教程 7 步最小集 vs SKILL 11 模块全集。**
教程《首页必备模块》的顺序（Header→Dropdown→Carousel→Category Showcase→Featured Product→Featured News→Footer）是跑通用的最小集；SKILL 定版 11 模块是合格站全集。定位不同、并行保留：新站先最小集跑通，再按 4.1 补齐全集，不互相替代。**施工取舍口径（补 G22）**：默认按 11 模块全集交付；仅当用户明确只要先跑通上线时才可停在最小集，且交付说明须标注「最小集交付」并列未补齐项，不许把最小集冒充全集。

**C8. FAQ 数量：教程「首次 3–5 个」vs SKILL「必备五题」。**
教程《建站前准备》的首次量是 3–5 个 FAQ；SKILL 的 B2B 清单要求五题（起订量/样品/交期/定制/付款物流）齐备。合并执行口径：**至少 5 题且五题齐备**为交付标准，3–5 仅作首次上线未补齐前的过渡记录，不作交付口径。

**C9. 地图模块字段：教程只提 URL vs 实测还有经纬度/Zoom/Map Type。**
教程《添加位置地图》只讲粘贴 Google Maps URL；实测模块除 URL 外还有 Latitude、Longitude、Zoom、Map Type 字段且均有值（演示站 URL 空、经纬度有值、模块隐藏）。以实测字段为准填写；URL 与经纬度哪个决定前台定位，未实测，存疑登记。**裁定前施工口径（G11）**：无准确地址先隐藏整块；有地址后 URL 与经纬度/Zoom/Map Type 都按实测字段填齐，并前台看一次定位再交付（地址本身属品牌输入，见第八节第 2 项）。

**C10. 域名占位文案未本地化（小瑕疵登记）。**
实测域名输入框占位文案显示原始键名 `domains.domainPlaceholder`，属平台小瑕疵，仅登记，不影响标准执行。

**C11. 表单成功提示可否修改：教程称可改 vs SKILL 旧口径称固定。**
教程《表单修改教程》称后台「表单」可改名称、按钮、**成功提示**与字段；本次盘点只读确认 Contact Inquiry 有成功提示字段及现值 "Thanks. Your message has been sent."，未实际修改、保存并前台验证。SKILL 旧口径称其为平台固定文案。两边证据都不完整：教程证明编辑入口/字段存在，不等于当前站点保存后一定生效；旧口径也没有本次修改失败的实证。故标存疑，正文不写「可改」或「改不了」，须做一次改值→保存→前台提交→恢复原值的实测再定。**裁定前施工口径（G10）**：不改成功提示、沿用现值；业务必须改文案时，先完成上述四步实测确认生效后再改。

**C12. 产品总量门槛：教程首次量合计 ≥6 vs 本库旧稿「至少 3 个产品」。**
教程《建站前准备》《首页必备模块》要求 3–4 个主分类、每类 ≥2 个产品，按最低 3 类计算，首次量产品合计 **≥6**。本库旧稿 §5.3 曾写「合格演示门槛：至少 3 个产品」，该数值无出处，已删除；演示站现有 5 个产品只记为现状，不作门槛。教程的分类与每类数量口径继续保留，是否另设脱离分类结构的全站总量门槛，未定。

---

## 八、开工输入清单（品牌事实）

> 本节列「写什么」的事实来源：下列事实不在标准库内、只能由品牌方/用户提供。**总纪律：缺哪项停哪项**——对应模块按各条目既有口径隐藏或留空，不许编造、不许拿演示站数值顶替、不许执行方自创后冒充品牌事实。逐项收齐并核对后，才开工对应部分。

1. **品牌视觉**：PRIMARY 色值（品牌方给值，或确认沿用现值；选色方法见 §1.1）；Logo 文件（宽 ≤350、透明 PNG、≤100KB）；Favicon 文件（512 正方形、≤100KB）；PRIMARY 前景色如需改动须一并给值，否则保持平台默认。缺 → 页眉 Logo 位与品牌色停工，不代画、不编造色值。（关联 G2）
2. **品牌基础信息**：域名、站域名邮箱、电话、地址、营业时间/工时（全站一种写法，逐字确认）。缺 → 第 33/34 条与页脚 Contact 列停工或隐藏，不许占位假值上线。（关联 G3、G11）
3. **公司事实**：成立年份；统计数字逐项已确认值（产品数、客户数、年限、评分等）；团队成员照片＋姓名/职位/介绍；真实客户评价原文与评分来源。缺哪项 → 第 27/24/31 条对应模块隐藏，不凑数、不编造。（关联 G4）
4. **产品事实**：每个产品的名称、分类归属、规格表逐行值（容量/尺寸/重量/材料/流明/电池等，带单位、公制英制双标）、产品图片。缺 → 该产品停工不上架；规格表的行集与行数本库未定，按产品实际属性给齐、不凑行，行值不许执行方自拟顶替。（关联 G5、G20）
5. **批发条款**：起订量、样品政策、交期、定制（logo/包装）范围、付款与物流口径——即 FAQ 五题的答案数值与各模块 Service Items 的数值来源。缺 → FAQ 五题不视为可交付（第 28 条），带数值的服务项只写无数值口径。（关联 G5、G16）
6. **分类结构**：3–4 个主分类名单与每类产品归属（每类 ≥2 个产品）。缺 → 第 9 条分类卡停工，不许执行方自行拆分品类凑数后冒充品牌分类。（关联 G6）
7. **运营口径**：Newsletter 发送频率、退订机制、订阅处理方式。缺 → 第 36 条 Fine Print 只写已确认部分，不承诺频率与效果。（关联 G17）
8. **表单与联系渠道**：站内真实表单名（弹窗与联系区绑定用，以后台实名为准）、弹窗 Title/Description 等文案确认稿、WhatsApp 真实号码（浮钮用）。缺 → 表单绑定停工，不许沿用演示站表单名冒充；无真实号码则浮钮不挂（第 37 条）。（关联 G21、G15）
9. **网站风格**：开工不询问、默认外贸 B 端（固定枚举 track: b2b，见 SKILL「定网站风格」与 references/style-profiles.md），记入开工简报；用户主动提出做 C 端并完成切换复核的记 track: c2c。缺 → 按默认轨开工、简报补记，不许两轨混搭施工。

---

## 附：美观评审衔接

- 每页做完/改完、交付前过六维评审（概念 / 一致性 / 层级 / 细节 / 功能 / 创新），**总评 ≥7 且概念 >5** 才过关；概念 ≤5 总评封顶 6。细则见母仓 references/beauty-review.md。
- 平台边界不动时终评 **7.2–7.6 属正常，不承诺 8 分以上**；演示站现行终评 7.7（概念 8.5 / 一致性 8.0 / 层级 7.0 / 细节 7.5 / 功能 7.5 / 创新 7.5）【实践】（演示站评审沉淀）。
- 常见丑点先查：同图多处复用、空模块硬撑、演示品牌残留、同屏彩色 >4、层级平、间距乱、页眉页脚逐页不一致。

---

## 起草者拿不准的问题（待定）

1. **C1 的呈现优选**：正文标准值已统一为实测 1920×1280；教程值只在 C1 登记。仍需同图两尺寸前台对照实测一次，确认何者呈现更优后再决定是否改标准。
2. **C6 分类页**：教程与既有实测正相反，本次盘点未覆盖前台分类页形态；需要一次前台点分类卡的实测才能销账，本稿只登记不裁定。
3. **/300 字段的推荐区间**（如 Description 60–200 字符）：本稿已统一定性为**参考带 / 经验值、非硬标准**；仍未经多站验证，后续若要升级为硬标准，须补多站实测依据。

---

## 九、验收缺口处置记录（2026-11-14 分诊）

> 依据：独立执行验收报告 `standards-execution-test-2026-11-14.md` 文末缺口清单 G1–G24。类别口径：**A＝库内可修**（标准库自己补清取值/口径，已直接改入正文）；**B＝输入契约类**（品牌事实不在标准库内，已入第八节「开工输入清单（品牌事实）」，并在相关条目加指向）；**C＝待平台裁定类**（保留【待验】/冲突标记不假装已定，每项补「裁定前施工口径」，口径提炼自验收报告中执行方实际采用的绕行办法）。分诊计数：**A 6 条、B 9 条、C 9 条**，合计 24 条。落点行号为本节写入时（本节位于文末、不影响前文行号）的行号。

| 编号 | 类别 | 落点 |
|---|---|---|
| G1 | A | §1.1 新增「新品牌选色口径」（L18） |
| G2 | B | 第八节第 1 项（L472，含 PRIMARY 前景色处置）；品牌色值收取与 §1.1 互指 |
| G3 | B | 第八节第 2 项（L473）；第 3 条、第 33 条加指向 |
| G4 | B | 第八节第 3 项（L474）；第 24/27/31 条加指向 |
| G5 | B | 第八节第 4 项（L475）＋第 5 项（L476）；第 5/13/28 条加指向 |
| G6 | B | 第八节第 6 项（L477）；第 9 条加指向 |
| G7 | C | §六 U5 补「裁定前施工口径」（L424），U5 仍标【待验】 |
| G8 | C | §六 U4 补「裁定前施工口径」（L423），U4 仍标【待验】 |
| G9 | C | §七 C6 补「裁定前施工口径」（L446），C6 仍存疑并列 |
| G10 | C | §七 C11 补「裁定前施工口径」（L461），C11 仍存疑并列 |
| G11 | C | §七 C9 补「裁定前施工口径」（L455），C9 仍存疑；地址本身属品牌输入，入第八节第 2 项（L473） |
| G12 | C | §七 C1 补「裁定前施工口径」（L431），C1 呈现优选仍待对照实测 |
| G13 | C | §六 U2 补「裁定前施工口径」（L421），U2 仍标【待验】 |
| G14 | C | §六 U3 补「裁定前施工口径」（L422），U3 仍标【待验】 |
| G15 | C | §六 U1 补「裁定前施工口径」（L420），U1 仍标【待验】；WhatsApp 号码属品牌输入，入第八节第 8 项（L479） |
| G16 | B | 第八节第 5 项（L476）；第 28 条加指向 |
| G17 | B | 第八节第 7 项（L478）；第 36 条加指向 |
| G18 | A | §1.3 新增「Light/Dark 施工口径」（L35） |
| G19 | A | 第 13 条新增「图册口径」（L146） |
| G20 | B | 第八节第 4 项（L475，含规格表行集口径）；第 13 条加指向 |
| G21 | B | 第八节第 8 项（L479）；第 32 条加指向 |
| G22 | A | §七 C7 补「施工取舍口径」（L449）；C7 两集并行保留不变 |
| G23 | A | 第 17 条备注补「内链与元信息口径」（L174） |
| G24 | A | §六新增第 16 项「GEO / AI 搜索无口径」（L416） |

> 分诊纪律自查：本轮修订只依据标准库草案与验收报告两份文件内已有的事实，未新编平台行为；C 类 9 项的【待验】/存疑标记全部保留，无一项被写成已验证。
