# 光影巨幕（TVBox 系本地化修补工程）

> 本仓库为**私人自用**的安卓 TV / 手机影视客户端本地化修补工程，**不对外公开、不分发、不盈利**。

## 用途
- 本地化修补 `com.ldw.cinema.mobile`（光幕影院 / 光影巨幕）APK。
- 内置合规片源（Internet Archive 公有领域 / CC 合集）与用户自选源的分发配置。
- 多设备源配置同步与换源（见下「换源 / 更新配置」）。

## 目录结构
- `ldw_patch/decoded/`：APK 反编译工程（smali 源码）。
- `ldw_patch/decoded/assets/user_source_candidates.json`：源候选清单（含分类线路）。
- `ldw_patch/decoded/assets/combined.json`：TVBox 站点配置（sites / lives / parses）。
- `ldw_patch/signed/`：已签名交付 APK。
- `ldw_patch/tools/`：构建 / 签名工具。

## 换源 / 更新配置（另一台设备）
1. 拉取本仓库：`git clone <本仓库地址>`。
2. 编辑 `ldw_patch/decoded/assets/user_source_candidates.json`（或 `combined.json`）里的线路。
3. `git commit && git push` 回仓库。
4. 客户端从仓库地址加载最新配置，即完成换源 / 更新。

> ⚠️ 合规边界：仅维护**私有、自用、合规**的源；客户端不内置全网自动爬取 / 自动检索代码，不绕过站点防盗链，不做公开再分发。

## 合规声明
本工程仅用于个人学习 / 自用，片源以公有领域 / CC 与用户已授权内容为准。
