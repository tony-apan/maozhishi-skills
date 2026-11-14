# 贸知事 AI 工作技能仓（maozhishi-skills）

这是公众号「贸知事」出品的 AI 工作技能集。说白了，就是一套写给 AI 的干活说明书：把外贸日常工作一步步写清楚，你把资料交给 AI，它照着说明书就能帮你把活干完。在 Muse 里可以直接当技能用；用其他 AI 助手，把说明书全文交给它，照样能参照着干。

> 先解释一个词：下面说的「技能」，就是写给 AI 的一份干活说明书。一个模块，就是一件事的一份说明书。

## 它能帮你做什么

- **建一个外贸独立站**：从零搭站、上架产品、写文章，做好之后还能日常更新。
- **找客户、发开发信**：找国外客户、先做背调、再写开发信发出去，后续跟进也有章法。
- **整理公司和产品资料**：把公司介绍、产品规格、图片素材归好类放一处，以后建站、写信、发文章都从这里取，不用每次从头交代。

## 你需要准备什么

- 一个能干活的 AI 助手（比如 Muse，或其他能读长文档的 AI 工具）。
- 相关平台的账号，比如建站平台、邮箱。登录和授权的时候，需要你本人操作一下。
- 公司和产品资料：公司介绍、产品名称和规格、产品图片，有多少先给多少，缺的后面再补。
- 一个放资料的文件夹。本仓自带现成的模板（见下面的「工作区模板」），照着放就行。

## 怎么开始用

**用 Muse**

1. 把本仓下载到你的电脑上。
2. 把你要用的模块文件夹放进 Muse 的自定义技能目录；`workspace-template/` 复制一份到你的工作文件夹，当资料库用。
3. 新开一个会话，告诉 AI 你要干什么，再按说明书开头的开工清单，把资料给它、该授权的授权。

**用其他 AI 助手**

1. 打开你要用的模块里的 `SKILL.md`，把全文复制给你的 AI 助手，告诉它：照这份说明书执行。
2. 按说明书开头的开工清单，把资料给它、该授权的授权。
3. 先拿一件小事试跑，确认效果没问题，再放大来做。

提醒一句：其他 AI 工具的环境我们还没有逐一实测过，用的时候更要先小样试跑。

## 里面有什么

| 模块 | 能干什么 | 版本 | 从哪开始 |
| --- | --- | --- | --- |
| LaiCMS 外贸独立站建站（`laicms-site-builder/`） | 从零建站、上架产品、写文章、日常更新 | v3.2.14 | [laicms-site-builder/SKILL.md](laicms-site-builder/SKILL.md) |
| 来发信 AI 获客（`laifaxin-leadgen/`） | 找客户、做背调、写开发信、跟进 | v1.0.0 | [laifaxin-leadgen/SKILL.md](laifaxin-leadgen/SKILL.md) |
| 工作区模板（`workspace-template/`） | 放公司和产品资料的现成文件夹架子，几个模块共用 | 随仓更新 | [workspace-template/README.md](workspace-template/README.md) |
| 模块地图（`docs/module-map.md`） | 说明几个模块之间怎么配合、共用哪些东西 | 随仓更新 | [docs/module-map.md](docs/module-map.md) |

## 文件一览

- `README.md` —— 本文件，先看这份
- `版本说明.md` —— 每次更新改了什么，都记在这里
- `docs/module-map.md` —— 模块地图：几个模块的关系和共用部分
- `docs/repo-structure-proposal.md` —— 建仓之前写的结构设想（老文档，实际结构以模块地图为准）
- `laicms-site-builder/SKILL.md` —— 建站说明书（主文件）
- `laicms-site-builder/skill.yaml` —— 建站模块的登记信息（名称、标题、简介）
- `laicms-site-builder/references/beauty-review.md` —— 页面好不好看的打分细则，跟着建站说明书一起用，不用另外装东西
- `laifaxin-leadgen/SKILL.md` —— 获客说明书（主文件）
- `laifaxin-leadgen/skill.yaml` —— 获客模块的登记信息（名称、标题、简介）
- `workspace-template/README.md` —— 资料文件夹模板的用法说明
- `workspace-template/00-inbox/INDEX.md` —— 00 收件：新资料先放这里
- `workspace-template/10-sources/INDEX.md` —— 10 来源：记清每份资料从哪来、什么时候的
- `workspace-template/20-knowledge/INDEX.md` —— 20 资料库：整理好的公司和产品资料，是核心一层
- `workspace-template/20-knowledge/公司档案.md` —— 公司档案模板
- `workspace-template/20-knowledge/产品事实底稿-模板.md` —— 产品资料模板，一个产品一份
- `workspace-template/20-knowledge/素材索引.md` —— 图片、文案等素材的清单模板
- `workspace-template/30-tasks/INDEX.md` —— 30 任务：正在做的事和排期
- `workspace-template/40-output/INDEX.md` —— 40 成品：写好的文章、开发信存这里
- `workspace-template/50-data/INDEX.md` —— 50 数据：各类台账和数据放这里
- `workspace-template/90-handover/INDEX.md` —— 90 交接：进度到哪了、卡在哪、下一步做什么

## 先看这里

- **第一次先拿小事试跑**：先做一个产品、一篇文章，看过效果再批量做，别一上来全量铺开。
- **有些事必须你本人来**：登录账号、点授权、绑定邮箱，只能你自己操作，AI 会一步步告诉你点哪里。
- **账号密码别发在聊天里**：按提示用安全的方式录入，AI 不会让你把密码打在对话里。
- **对外发送前先看一遍**：开发信要发出去、文章要发布之前，自己先过一眼内容，确认了再让 AI 发。
- **资料以你确认的为准**：公司和产品的信息，AI 只用你确认过的，不会自己编规格和数字；给错了，记得及时让它改。

## 版本与更新

- 每次更新的记录见 [版本说明.md](版本说明.md)。
- 本仓只发布正式版本；要看最新内容，认准本仓地址即可。
