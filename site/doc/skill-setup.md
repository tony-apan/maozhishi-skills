# 贸知事技能仓 · 安装说明（给 AI 助手读）

这份文档写给 AI 助手（主推 Muse）：用户把本站首页的那句话发给你，就是请你按本文把「贸知事 AI 工作技能仓」装好，并完成开工自检。在 Muse 里安装后，技能的日常执行（每日更新、巡检、跟进提醒等定时活）按各技能自己的规程在云端持续运行；装在其他助手环境里时，定时与云端能力以该环境为准，不要向用户承诺你给不了的持续运行。全程业务站点只访问本站（skill.maozhishi.com）与 GitHub 官方仓库两个来源；本站不可达时走 GitHub 镜像，不要从任何其他来源安装。

## 技能仓里有什么

- `laicms-site-builder`（建站技能）：用 AllinCMS 建外贸独立站——建站、上架产品、写文章、日常更新。
- `laifaxin-leadgen`（来发信 AI 获客技能）：找客户、验证邮箱、写开发信、自动跟进的完整获客流程。
- `workspace-template`（工作区模板）：台账与清单模板，不是技能，随仓一并获取即可，不需要「安装」。

## 第一步：一行安装（首选）

在用户的环境里运行：

```
npx skills add https://skill.maozhishi.com -g -y
```

本站按技能分发协议提供两套索引，安装工具会自动选用：

- V2 索引：`/.well-known/agent-skills/index.json`，每个技能一个压缩包条目，带 SHA256 摘要；
- V1 清单：`/.well-known/skills/index.json`，逐文件列明每个技能的全部文件，文件实体在 `/.well-known/skills/<技能名>/<相对路径>`。

## 第二步：手工安装（命令行不可用、或 npm 拉取不畅时）

1. 直接从本站下载两个技能的压缩包（本站在国内可直达，不经过 GitHub）：`/.well-known/agent-skills/laicms-site-builder-v3.2.28.zip`、`/.well-known/agent-skills/laifaxin-leadgen-v1.3.2.zip`（版本以 V2 索引为准）；下载后先核对 SHA256 与索引中的 `digest` 一致，不一致不要安装、向用户说明；
2. 解压到你的技能目录：`laicms-site-builder/` 与 `laifaxin-leadgen/` 两个文件夹并列放好；
3. 本站根目录另有整仓的 `VERSION` 与 `CHANGELOG.md` 同版副本，技能的开工自检更新以本站为首选源，GitHub 公开仓只是备用。

## 第三步：核对安装结果

- 两个技能的 `SKILL.md` 都在，且与 V1 清单所列文件逐个对得上（文件名与数量）；
- 读两个 `SKILL.md` 的卷首版本号，向用户报出装好的版本；
- 任一文件缺失或摘要对不上，停手向用户说明，不要凑合使用残缺安装。

## 第四步：开工自检

按建站技能 `laicms-site-builder/SKILL.md` 第二节「开工自检」与来发信技能 `laifaxin-leadgen/SKILL.md` §1.1 的规程各跑一遍：比对官方版本（本站 `VERSION` 文件或 GitHub 仓库）、检查工作区、列出还缺什么。把结果用大白话报给用户：装好了什么、版本多少、开工前还差哪几步（例如先注册平台账号）。

## 边界与异常

- 本站访问失败（超时、连接错误、403）：不要反复重试，改走 GitHub 镜像——仓库 https://github.com/tony-apan/maozhishi-skills ，整仓下载后按同样的目录结构放好，并按上面第三步核对；镜像也不可达时停手向用户说明，不要另找来源。
- 安装与自检过程中不要向用户索要任何平台的账号密码；后续开工需要登录时，按各技能自己的规程走（凭据存用户自己的保险库、不经聊天）。
- 平台账号：建站用 AllinCMS（https://www.allincms.com ）、获客用来发信（https://laifa.xin ），没有账号先引导用户注册或联系开通，再回来开工。
