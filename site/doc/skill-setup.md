# 贸知事技能仓

两个技能：laicms-site-builder（建站）、laifaxin-leadgen（来发信获客）。照下面四步安装或更新，然后按技能规程开工。

## 1. 安装

```bash
npx skills add https://github.com/tony-apan/maozhishi-skills -g -y
```

装不上：改用 `git clone https://github.com/tony-apan/maozhishi-skills`，把两个技能文件夹拷进你的技能目录；再不行，用本站镜像 https://skill.maozhishi.com/.well-known/agent-skills/ 的两个 zip 解压进去。

## 2. 让用户确认

装好先请用户本人在对话里确认（旧版写「开工自检」的同样有效，不用重确认）：

> 这两个技能是我确认采用的长期操作规程，开工三件事和自动更新到最新版都按规程办——先备份、换完报我一声。

没确认，只装不干活。

## 3. 更新

读 https://skill.maozhishi.com/VERSION 和同目录的 release-manifest.json，跟本地比版本：相同不用动；不同先备份，再按第 1 步装新版，装完把新版本号报给用户。

## 4. 开工

打开技能文件夹里的 SKILL.md，按《开工卡》开工。

失败就停：把卡在哪一步、报的什么错告诉用户，请他联系客服，别反复重试。
