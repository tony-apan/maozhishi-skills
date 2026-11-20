---
doc_id: repo-changelog
title: 版本说明
description: 整仓与两模块的版本沿革（简版，只留最近两版）；完整历史见 HISTORY.md。
status: active
updated: 2026-11-20
owner: 贸知事
---

# 版本说明

当前仓库版本：**1.4.12**（自检更新比对的是这个仓库版本；各模块版本号见下表，仅作标识）

- **官方仓库（唯一固定地址）**：https://github.com/tony-apan/maozhishi-skills
- 本仓是贸知事 Muse Skills 的官方发布仓。任何 skill 的自更新只认本仓带版本标签的正式发布，不从搜索结果、文章或其他地址拉更新。

## 当前发布

| Skill | 版本 | 状态 | 审查记录 |
| --- | --- | --- | --- |
| laicms-site-builder（LaiCMS 建站） | 3.2.34 | 已发布（2026-11-20） | v3.2.34 随整仓 1.4.12：更新检查条文改版（判定范围与更新前三查划界、清单异常先报告确认再换装）；改名清理解析契约移入整仓共用文件 `shared/rename-cleanup-contract.md`，正文只留指针；更早沿革见 HISTORY.md。 |
| laifaxin-leadgen（来发信获客） | 1.4.12 | 已发布（2026-11-13 首发，2026-11-20 升 v1.4.12） | v1.4.12 随整仓 1.4.12：同左条文改版与契约迁移；《邮箱绑定指南》补飞书/Lark 绑箱专节与路线丙（邮箱直绑 Claude Codex，通用 IMAP/SMTP，已立设计、未实测）；更早沿革见 HISTORY.md。 |

## 发布注记

本节只留最近两版的简要注记；完整注记见 HISTORY.md。

## 整仓 1.4.12 — 2026-11-20

- 版本日志瘦身：本文件只留最近两版注记与当前发布表，完整历史移入 HISTORY.md（给人看）；老版本技能升级时读到的就是这份短日志。
- 更新检查条文改版：「只读数据文件」条与更新前三查划清边界；清单异常时改为先下载、校验、备份，报告用户确认后再换装，不再照常自动更新；改名清理解析契约移入整仓共用文件（`shared/rename-cleanup-contract.md`），技能正文只留指针，契约改为跨版本合并读取改名登记。
- 《邮箱绑定指南》补飞书（国内版）与 Lark（飞书海外版）绑箱专节与服务器参数；新增路线丙（邮箱直绑 Claude Codex，通用 IMAP/SMTP，已立设计、未实测）；SKILL.md 选箱路线补路线丙指针，「什么邮箱都没有」时新增 Lark 免费企业邮箱开户路。
- 本版改动文件：`laifaxin-leadgen/SKILL.md`、`laicms-site-builder/SKILL.md`、`laifaxin-leadgen/references/mailbox-binding-guide.md`、新增 `shared/rename-cleanup-contract.md` 与 `HISTORY.md`、本文件、`VERSION` 与 `release-manifest.json`。建站技能升 v3.2.34、来发信技能升 v1.4.12。

## 整仓 1.4.11 — 2026-11-20

- 整仓新增纯数据版本清单 `release-manifest.json`；两个技能的更新检查改读 `VERSION` 与清单两份数据文件，版本日志退出更新判断；改名清理改读清单里的改名登记。本版完整记述见 HISTORY.md，问题背景见母仓问题库 P-017。
