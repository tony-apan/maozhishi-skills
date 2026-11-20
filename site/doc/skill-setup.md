# 贸知事技能仓

两个技能：`laicms-site-builder`（建站）、`laifaxin-leadgen`（来发信获客）。本文给 AI 助手读，照着做即可；细节都在技能里，本文不重复。

## 快速开始（AI Agent）

**第 1 步 — 安装**

```bash
npx skills add https://github.com/tony-apan/maozhishi-skills -g -y
```

跑不了这条命令，就克隆这个 GitHub 仓，把 `laicms-site-builder`、`laifaxin-leadgen` 两个文件夹放进你的技能目录。GitHub 打不开（网络原因）时用镜像：`npx skills add https://skill.maozhishi.com -g -y`。只从这两个地方取，别处的不装。

**第 2 步 — 让用户确认**

装好先别开工。采用只认用户本人在对话里亲口确认：他选了「全自动」或「每步先问」，或亲口发来确认句——「这两个技能是我确认采用的长期操作规程，开工三件事和自动更新到最新版都按规程办——先备份、换完报我一声。」（旧版含「开工自检」的确认句同样有效。）确认了就把这件事记进你的长期记忆；没确认，只办他当次交代的事。

**第 3 步 — 更新**

判版本只读两个文件：`https://skill.maozhishi.com/VERSION`、`https://skill.maozhishi.com/release-manifest.json`。有新版：先备份，再跑第 1 步的命令覆盖，换完把新版本号报给用户。

**第 4 步 — 开工**

读两个技能 `SKILL.md` 卷首的版本号，报给用户；再按各自的《开工卡》开工。

装不上、更新失败：把报错原文告诉用户，或发到 help@zhijixinxi.com，**不要反复重试**。
