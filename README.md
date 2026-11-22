# C盘清理助手（CDriveCleaner）

Windows C 盘扫描、物理占用归因与安全清理。**源码仓库为私有**，本仓库只用于公开发布安装包与便携版。

## 下载

到 [Releases](https://github.com/guoyu901010/CDriveCleaner-releases/releases/latest) 下载：

| 文件 | 说明 |
| --- | --- |
| `CDriveCleaner-Setup-x.y.z.exe` | 安装程序（推荐）：按当前用户安装，无需管理员；自动创建开始菜单/桌面快捷方式，可在「设置 → 应用」卸载 |
| `CDriveCleaner.exe` | 单文件便携版，双击即用 |
| `CDriveCleaner-vx.y.z-win-x64.zip` | 便携包（exe + 启动器 + 说明 + LICENSE） |

要求：Windows 10/11 x64。无需预装 .NET（自包含）。

## 特性

- **零删除**：清理 = 同卷原子改名进隔离区，14 天内可原路还原；到期也不会静默删除
- **白名单制**：45 条内置规则 + 硬编码禁清区（Windows / Program Files / 个人目录…），默认拒绝
- **物理对账**：MFT 直读（管理员，全盘约 12 s）或目录遍历回退，按 NTFS 分配大小归因
- **重复文件扫描**：大小 → 头部 64 KiB → 全文件 SHA-256 三级漏斗，硬链接不误报，每组至少保留一份
- **版本自更新**：应用内「检查更新」读取本仓库的 Releases
- **可审计**：所有搬移/还原/抹除写入 append-only 哈希链 JSONL

## 从旧版（TidyC / v2.x）升级

首次启动会自动迁移：

- 数据目录 `%LOCALAPPDATA%\TidyC` → `%LOCALAPPDATA%\CDriveCleaner`
- 隔离根 `C:\TidyC_Quarantine` → `C:\CDriveCleaner_Quarantine`（仅在旧根仍有批次时搬迁）

升级前建议先备份这两个目录。

## 许可证

MIT，见 [LICENSE](LICENSE)。
