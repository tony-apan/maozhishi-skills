# 贸知事 AI 工作技能仓（maozhishi-skills）

[![技能仓 v1.4.22](https://img.shields.io/badge/%E6%8A%80%E8%83%BD%E4%BB%93-v1.4.22-orange?style=flat-square)](VERSION) [![建站技能 v3.2.43](https://img.shields.io/badge/%E5%BB%BA%E7%AB%99%E6%8A%80%E8%83%BD-v3.2.43-green?style=flat-square)](laicms-site-builder/SKILL.md) [![来发信 v1.4.22](https://img.shields.io/badge/%E6%9D%A5%E5%8F%91%E4%BF%A1-v1.4.22-blue?style=flat-square)](laifaxin-leadgen/SKILL.md)

公众号「贸知事」出品的**外贸获客技能仓**。所谓「技能」，就是**写给 AI 的一份干活说明书**：你把资料交给 AI，它照着说明书把活干完——建站、找客户、写开发信、跟进，都在这里。

## 1️⃣ 先注册

先到这两个官网把账号注册好，再回来往下走：

- [来发信官网](https://laifa.xin)：做 AI 获客用。
- [AllinCMS 官网](https://www.allincms.com)：建外贸独立站用。

<a id="先复制这段话"></a>
## 2️⃣ 跟你的 AI 说一句话

打开你平时用的 AI，把这句话发给它就行——不用下载，不用复制长文：

「请阅读 https://skill.maozhishi.com/doc/cli-setup.md ，为我装上贸知事的来发信和独立站两个 skill。」

它会照着仓库把两个技能装好，装好后当面跟你确认，再带你开工。

### 给来安装的 AI

这句走不通时，看官网的备选办法 https://skill.maozhishi.com/doc/skill-setup.md 。

- 推荐装法：从官网发现索引 https://skill.maozhishi.com/.well-known/agent-skills/index.json 取两个包的文件名与 sha256，下载地址是 https://skill.maozhishi.com/.well-known/agent-skills/ 后面接文件名；下载后先把 sha256 与索引对一遍，对上再装。本仓的 laifaxin-leadgen/ 与 laicms-site-builder/ 两个目录是同一内容的展开形态。
- 装法：每个技能放进你的技能目录、同名文件夹即可。
- 每个技能包里有自己的《开工卡》，装好后的确认按它走。

## 🎁 它能帮你做什么

- **建外贸独立站**：搭站、上架产品、写文章、日常更新。
- **找客户、发开发信**：找国外客户、做背调、写开发信、跟进。
- **整理资料**：公司和产品资料归好类放一处，建站、写信都从这里取。

## 📦 里面有什么

### 1️⃣ [外贸独立站 · 全自动更新 · SEO/GEO](laicms-site-builder/SKILL.md)

**建站、上架产品、写文章、日常更新**；自带 **SEO/GEO**：按客户的搜索意图做内容，**让网站被搜索引擎和 AI 推荐，带来流量、询盘和订单**。附模块标准库，开工先选风格（外贸 B 端／跨境 C 端）

📖 **使用说明**：[新手使用说明](laicms-site-builder/references/beginner-guide.md)——带截图的全流程说明，跟着走一遍就会。

### 2️⃣ [来发信 AI 获客 · 24 小时全自动开发客户](laifaxin-leadgen/SKILL.md)

**找客户、做背调、写开发信、自动跟进**，还能**梳理 WhatsApp 会话、提炼客户痛点**；平台操作走**官方 Agent 通道**（网页授权一次、接口直达，不用一页页点）；每月免费点数**自动帮你领**，不用惦记

📖 **使用说明**：[新手使用说明](laifaxin-leadgen/references/beginner-guide.md)——从注册到发出第一封开发信，跟着走一遍就会。

### 3️⃣ B2B 运营 ![测试中](https://img.shields.io/badge/%E6%B5%8B%E8%AF%95%E4%B8%AD-orange?style=flat-square)

**免费 B2B 平台注册、铺店、产品上架**；公司和产品资料整理一次，多个平台复用

### 4️⃣ 社媒运营 ![测试中](https://img.shields.io/badge/%E6%B5%8B%E8%AF%95%E4%B8%AD-orange?style=flat-square)

**公众号、视频号等平台的内容发布与运营**；网站新文章自动备帖、分发到各平台

### 5️⃣ 广告投放 ![测试中](https://img.shields.io/badge/%E6%B5%8B%E8%AF%95%E4%B8%AD-orange?style=flat-square)

**海外广告投放、盯盘与优化**；Google、Meta 等平台的广告账户搭建、预算分配与效果优化，自动盯花费与询盘成本，钱花偏了先提醒你

### 6️⃣ [工作区模板](workspace-template/README.md) ![随仓更新](https://img.shields.io/badge/%E9%9A%8F%E4%BB%93%E6%9B%B4%E6%96%B0-grey?style=flat-square)

放公司和产品资料的**文件夹架子**，各模块共用

每个文件的详细清单，见 [文件索引](file-index.md)。

**现在是这两套技能，后续会不断新增。** 缺哪一块、想要什么新技能，或者用着出了问题，都可以到仓库的 [Issues](https://github.com/tony-apan/maozhishi-skills/issues) 里提出来，作者会看、会更新。

## 🔄 版本与更新

每次更新改了什么，见仓库里的版本说明（CHANGELOG.md，给人看的版本历史）。新技能、新版本**先在贸知事社群里发**，社群成员优先更新、优先用上；想优先，扫文末二维码进社群。

## 🏗️ 建站先开通 AllinCMS

想先了解平台本身？看 [AllinCMS 平台介绍与文档地图](laicms-site-builder/references/laicms-platform-guide.md)：平台是什么、怎么收费、官方教程在哪，一篇看懂。

建外贸独立站用的是 AllinCMS。还没有账号的，先看 [联系说明](laicms-site-builder/contact-guide.md)，里面写了怎么联系官方开通；也可以先到 [AllinCMS 官网](https://www.allincms.com) 了解一下。账号开通后，回来让你的 AI 照着建站技能开工就行。

## 📧 来发信

想先了解平台本身？看 [来发信平台介绍与文档地图](laifaxin-leadgen/references/laifaxin-platform-guide.md)：平台是什么、点数怎么花、官方文档在哪，一篇看懂。

[来发信官网](https://laifa.xin)：上面「来发信 AI 获客」技能配套的平台。找客户、验证邮箱、发开发信、自动跟进，都在来发信里完成；技能是写给 AI 的说明书，让你的 AI 照着把这些活一步步干完。先在官网注册账号，再回来用技能开工。

## 💬 联系与社群

用着有问题，或者想和同行交流 AI 做外贸的经验，欢迎来找我们：

- 仓库 [Issues](https://github.com/tony-apan/maozhishi-skills/issues)：提问、提需求、报问题，作者会回、会更新
- 邮箱：**help@zhijixinxi.com**
- 微信：扫下面的码加好友，备注「技能仓」，拉你进贸知事社群——**新技能、新版本在群里优先发**

<img src="https://cos.files.maozhishi.com/data/web/web-files/wx/tony-apan.png" width="220" alt="微信二维码">
