# 光影巨幕 - 远程更新说明

## 文件用途

| 文件 | 用途 |
|---|---|
| `update.json` | 最新版本信息、APK 下载地址、更新日志、是否强制更新 |
| `update-channel.json` | 多镜像源配置（GitHub + Gitee），用于提升下载速度和稳定性 |

## 更新流程

1. 发布新版本时，把 APK 上传到 GitHub Release / Gitee Release。
2. 计算 APK 的 `apk_size`（字节）和 `apk_md5`，填入 `update.json`。
3. 提升 `versionCode` 和 `versionName`。
4. 提交并推送这两个 JSON 文件到仓库。
5. APP 启动/设置页会读取 `update-channel.json` 中的镜像，按优先级检测 `update.json`。
6. 若服务器 `versionCode` 大于本地，弹出更新提示；用户确认后开始下载并显示进度。

## 下载稳定性策略

- **多镜像**：优先 GitHub，失败/慢于 50KB/s 自动切 Gitee。
- **断点续传**：下载服务支持 RANGE 请求，断网恢复后从上次位置继续。
- **重试**：每个镜像失败自动重试 3 次。
- **校验**：下载完成后校验 MD5，不一致则提示重新下载。

## 重要提示

- `update.json` 与 APK 下载链接必须能被未登录的客户端直接访问。
- 若仓库为私有，客户端无法读取 GitHub raw 链接；请使用 Gitee 公开仓库或 CDN 作为更新通道。
- 源码仓库仍可保持私有，只需把更新文件和 APK 放在公开位置即可。
