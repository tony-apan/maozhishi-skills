# 贸知事 AI 工作技能仓（maozhishi-skills）

这是公众号「贸知事」出品的 AI 工作技能集，把外贸日常工作流写成结构化文档：在 Muse 里可直接作为技能运行，其他 AI 助手与工具也可把各模块的 `SKILL.md` 当作指令文档参照执行。用户提供资料与账号授权，AI 按技能流程把活干完。本仓为公开发布仓，只放定版内容。

## 模块索引

| 模块 | 版本 | 用途 | 入口 |
| --- | --- | --- | --- |
| LaiCMS 外贸独立站建站（`laicms-site-builder/`） | v3.2.14 | 从零建站、传产品、写文章、日常更新 | [laicms-site-builder/SKILL.md](laicms-site-builder/SKILL.md) |
| 来发信 AI 获客（`laifaxin-leadgen/`） | v1.0.0 | 找客户、背调、精发开发信与跟进 | [laifaxin-leadgen/SKILL.md](laifaxin-leadgen/SKILL.md) |
| 工作区模板（`workspace-template/`） | 随仓 | 各模块共用的资料库骨架：公司档案、产品事实底稿、素材索引、台账 | [workspace-template/README.md](workspace-template/README.md) |
| 模块地图（`docs/module-map.md`） | 随仓 | 模块关系与共用底座说明 | [docs/module-map.md](docs/module-map.md) |

## 仓库索引

- `README.md` —— 本文件：仓库索引与上手说明
- `版本说明.md` —— 各模块版本历史与变更记录
- `docs/module-map.md` —— 模块地图：模块清单、关系与共用底座
- `docs/repo-structure-proposal.md` —— 建仓前结构建议稿（历史文档，实际结构以模块地图为准）
- `laicms-site-builder/SKILL.md` —— 建站技能主文件：全流程、内容规范与实测补记
- `laicms-site-builder/skill.yaml` —— 建站技能元信息（名称、标题、简介）
- `laicms-site-builder/references/beauty-review.md` —— 美观评审细则：六维评审法，随仓零安装
- `laifaxin-leadgen/SKILL.md` —— 来发信获客技能主文件：找客、背调、精发/群发与跟进全流程
- `laifaxin-leadgen/skill.yaml` —— 来发信技能元信息（名称、标题、简介）
- `workspace-template/README.md` —— 工作区模板说明：七层骨架与用法
- `workspace-template/00-inbox/INDEX.md` —— 00 收件：用户原始资料入口
- `workspace-template/10-sources/INDEX.md` —— 10 来源登记：资料来源、日期与可信度
- `workspace-template/20-knowledge/INDEX.md` —— 20 知识底稿：资料库核心层索引
- `workspace-template/20-knowledge/公司档案.md` —— 公司档案模板
- `workspace-template/20-knowledge/产品事实底稿-模板.md` —— 产品事实底稿模板（一产品一档）
- `workspace-template/20-knowledge/素材索引.md` —— 素材索引模板
- `workspace-template/30-tasks/INDEX.md` —— 30 任务清单：在跑任务、排期与待确认清单
- `workspace-template/40-output/INDEX.md` —— 40 产出：文章、开发信与帖文的主本存档
- `workspace-template/50-data/INDEX.md` —— 50 数据：台账与数据真源
- `workspace-template/90-handover/INDEX.md` —— 90 交接：进度、卡点与下一步

## 快速上手

1. 下载或克隆本仓到本地。
2. 把需要的模块文件夹（如 `laicms-site-builder/`、`laifaxin-leadgen/`）放入你的 Muse 自定义技能目录；`workspace-template/` 复制到你的工作区作为资料库骨架。
3. 新开一个 Muse 会话，按模块 `SKILL.md` 的开工流程提供资料与账号授权，Muse 会按流程执行。

**用其他 AI 助手**：把对应模块的 `SKILL.md` 全文交给你的 AI 助手作为执行指令，并按其中的开工检查提供资料与账号授权即可。其他 AI 工具的环境未经逐一实测，第一次使用请先跑小样验证，再放大规模。

各模块的环境依赖（平台账号、邮箱授权等）以各自 `SKILL.md` 的开工检查为准；第一次使用建议先跑小样验证，再放大规模。

## 版本与更新

- 版本历史见 [版本说明.md](版本说明.md)。
- 本仓只接收定版快照更新，不在此仓做开发讨论。
