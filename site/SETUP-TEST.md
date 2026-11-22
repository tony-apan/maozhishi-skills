# 贸知事技能 · 安装步骤（给 AI）

请按下面步骤，为用户把贸知事的两个技能装上。

## 第 1 步：拉取安装

在终端执行：

```
npx skills add https://skill.maozhishi.com -g -y
```

这条命令会把两个技能装进你的技能目录：来发信 laifaxin-leadgen、建站 laicms-site-builder。

## 第 2 步：命令跑不通时改走这条

先取官网索引：https://skill.maozhishi.com/.well-known/agent-skills/index.json ——索引里有每个包的文件名和 sha256；下载地址是 https://skill.maozhishi.com/.well-known/agent-skills/ 后面接文件名。下载后先核对 sha256 与索引一致，再解压到你的技能目录，一个技能一个同名文件夹。

## 第 3 步：核验

读回两个技能的 SKILL.md 版本字段，应为：来发信 v1.4.22、建站 v3.2.43。对不上就停下来告诉用户。

## 第 4 步：装好后

每个技能包里有一份《开工卡》，读它，按它跟用户当面确认后再开工。
