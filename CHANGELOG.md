# Changelog

All notable changes to **Local Text Privacy** releases are documented in this file.

## [1.2.3] - 2026-11-24

### Fixed
- **支持同一活动映射连续多次执行实体还原**：修复首次实体还原成功后“执行实体还原”按钮被永久禁用的问题。只要当前活动 Mapping 尚未结束，用户可以继续粘贴 AI 重新生成的多版回复并重复执行还原，每次执行都会完整刷新还原结果与审计报告。
- **无活动映射门禁保护**：在点击还原入口补充活动 Mapping 检查（fail-closed），会话结束清理后禁用还原按钮并拒绝旧 Token 恢复。

### Changed
- 更新 `RESTORED` 状态工作流引导提示，明确说明可继续粘贴新回复再次还原，同时保留安全提醒：“这不代表 AI 回复语义未经改变”。
- 统一 macOS Apple Silicon、Windows x64 安装包及应用内「使用指南」版本号为 `V1.2.3`。

## [1.2.2] - 2026-11-12

### Highlights
- 统一双平台主窗口标题为 `Local Text Privacy`，使用指南唯一显示版本号。
- 接入 V5 品牌图标资产与紧凑短码默认模式（临时模式短码 + 长期模式标准 PVT 码）。
- 完成 macOS Apple Silicon 与 Windows x64 原生打包构建。
