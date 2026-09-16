# 回收点数计算器 · 桌面版

这里放**安装包**，供用户下载，以及程序自动检查更新用（**仓库请保持公开**）。

## 安装

进右侧 **Releases** → 点最新版本 → 下载 `RecyclePointsCalculator-Setup-…….exe`，双击安装即可，装完自动打开，桌面会生成图标。

不需要管理员权限，也不需要选安装目录。

## 自动更新

装好以后，用户**打开软件就自动检查**：有新版会自动下载，关闭软件时自动装好，下次打开就是新版。界面上也会提示"点这里重启完成更新"。

网络打不开 GitHub 时更新会失败，但不影响使用，下次打开会再试。

## 发新版的方法（作者用）

1. 版本号 +1：改 `desktop\package.json` 里的 `version`
2. 重新打包：在 `desktop` 目录执行 `npm run dist`
3. 在 Releases 里新建一个版本，Tag 填 `v新版本号`，标题随意
4. 上传**三个**文件（第三个最容易漏，别漏）：

- `desktop\release\RecyclePointsCalculator-Setup-新版本号.exe`
- `desktop\release\latest.yml`
- `desktop\release\RecyclePointsCalculator-Setup-新版本号.exe.blockmap`

上传后确认这个版本是「Latest / 最新版本」。

> 为什么要有第三个文件：带上 `.blockmap`，用户更新时**只下载变动的部分**（通常只有几百 KB），而不是整个 117MB。实测 1.0.0 → 1.0.1 只需 377KB。万一漏传，程序会自动退回整包下载，不会出错。

> 文件名必须是英文：GitHub 会把附件名里的中文自动去掉，导致程序找不到更新包。