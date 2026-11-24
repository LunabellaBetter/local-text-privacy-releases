# Local Text Privacy — Official Releases

**Local Text Privacy** 是一款本地优先、离线运行的桌面端文本隐私脱敏与实体还原工具，用于在将敏感文本发送给外部大语言模型（AI）前进行本地占位符替换，并在收到 AI 回复后于本地精确还原真实实体。

> 本仓库仅用于托管正式发布文档与 [GitHub Releases](https://github.com/LunabellaBetter/local-text-privacy-releases/releases) 桌面端安装包及 SHA-256 校验文件，不包含产品源码。

---

## 核心原则

- **本地优先、离线处理**：识别候选、人工复核、脱敏替换与实体还原均在本机离线完成，不向云端发送原文或恢复映射。
- **人工复核优先**：所有敏感实体候选均支持人工确认、调整与冲突仲裁。
- **单会话隔离**：同一时刻仅保留一个活动映射，需明确结束并清理会话后才开启新任务；支持对同一份脱敏映射连续还原多版 AI 回复。
- **可选加密归档（UPV）**：默认仅在内存中处理；如需持久保存映射或词库，可使用口令保护的加密 `.upv` 容器（Argon2id + AES-256-GCM）。

---

## 支持平台与下载入口

请前往 [Releases 页面](https://github.com/LunabellaBetter/local-text-privacy-releases/releases) 下载对应平台安装包及 `.sha256` 校验文件：

| 平台 | 安装包文件 | 校验文件 |
|---|---|---|
| **macOS (Apple Silicon / arm64)** | `LocalTextPrivacy-V1.2.3-macOS-AppleSilicon.zip` | `LocalTextPrivacy-V1.2.3-macOS-AppleSilicon.zip.sha256` |
| **Windows (x64 / AMD64)** | `LocalTextPrivacy-V1.2.3-Windows-x64.zip` | `LocalTextPrivacy-V1.2.3-Windows-x64.zip.sha256` |

---

## 安装方法

### macOS (Apple Silicon)

1. 下载 `LocalTextPrivacy-V1.2.3-macOS-AppleSilicon.zip` 与对应的 `.sha256` 文件。
2. 校验 SHA-256 一致后，双击解压得到 `Local Text Privacy.app`。
3. 将 `Local Text Privacy.app` 拖入「应用程序（Applications）」目录或保留在您指定的本地目录中。
4. 首次打开请参考下方 **macOS Gatekeeper 注意事项**。

### Windows (x64)

1. 下载 `LocalTextPrivacy-V1.2.3-Windows-x64.zip` 与对应的 `.sha256` 文件。
2. 校验 SHA-256 一致后，将压缩包解压至本地目录（建议路径不含特殊受限系统目录）。
3. 进入解压后的 `Local Text Privacy` 文件夹，双击运行 `Local Text Privacy.exe`。
4. 如 Windows Defender SmartScreen 提示未知发布者，请在核验 SHA-256 无误后，点击「更多信息 → 仍要运行」。

---

## SHA-256 校验方法

下载安装包与 `.sha256` 文件到同一目录后，在终端执行校验：

### macOS（Terminal）

```bash
shasum -a 256 -c LocalTextPrivacy-V1.2.3-macOS-AppleSilicon.zip.sha256
```

输出 `LocalTextPrivacy-V1.2.3-macOS-AppleSilicon.zip: OK` 即表示文件完整且未被篡改。

### Windows（PowerShell）

```powershell
Get-FileHash .\LocalTextPrivacy-V1.2.3-Windows-x64.zip -Algorithm SHA256
Get-Content .\LocalTextPrivacy-V1.2.3-Windows-x64.zip.sha256
```

比对两行十六进制哈希值（忽略大小写）完全一致即可。

---

## 签名与 macOS Gatekeeper 注意事项

- **macOS**：当前版本仅包含本地 **Ad-hoc 签名**，**不包含 Apple Developer ID 签名与 Apple 公证（Notarization）**。首次启动时，macOS Gatekeeper 可能提示“无法验证开发者”。
  - **正确打开方式**：先核对 ZIP 的 SHA-256；确认一致后，在 Finder 中**右键点击 `Local Text Privacy.app` → 选择「打开」**，或在「系统设置 → 隐私与安全性」中点击「仍要打开」。
  - **请勿关闭全局 Gatekeeper**；若系统提示应用已损坏或发现恶意软件，请立即停止并重新核验下载来源与 SHA-256。
- **Windows**：当前版本为未进行商业代码签名的便携版（One-folder ZIP），首次运行可能触发 SmartScreen 提醒，请务必先核对 SHA-256。

---

## 当前版本更新说明（V1.2.3）

- **支持同一活动映射连续多次实体还原**：在 `RESTORED` 状态下，只要当前活动 Mapping 仍然有效，可继续粘贴 AI 重新生成的第二版、第三版回复并再次点击“执行实体还原”，无需重新脱敏。
- **结果与审计报告隔离刷新**：每次还原均完整覆盖当前还原结果并刷新审计统计，不残留前一次还原数据。
- **安全边界保持不变**：明确结束会话并清理内存后，还原按钮自动禁用，旧 Token 无法继续恢复；保留原有安全提示“这不代表 AI 回复语义未经改变”。
- **版本号统一**：应用元数据、使用指南与双平台构建包版本号统一更新为 `1.2.3`。

完整变更历史见 [CHANGELOG.md](./CHANGELOG.md)。
