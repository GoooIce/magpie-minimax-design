# AGENTS.md

## 目标

开发一个符合 [magpie-community/plugins](https://github.com/magpie-community/plugins) 规范的 OpenCode / magpie **provider 插件**，将本机 **MiniMax Design** 的订阅（模型、流式对话、工具调用、配额/额度查询等）接入 magpie。

## 架构与协议约定

1. **插件形态**：OpenCode / magpie provider 插件（ESM，`"type": "module"`），参考 `magpie-community/plugins` 中的 `packages/minimax`、`packages/zen-free`、`packages/astudio`、`packages/catpaw`。
2. **本机排查入口**：
   - 应用：`/Applications/MiniMax Design.app`（`com.minimax.hub`）
   - 本地配置/状态目录：`~/Library/Application Support/@hilo/desktop`
   - 本机 magpie CLI：`/Applications/magpie.app/Contents/MacOS/magpie`
3. **社区合入要求（若后续提交 PR 到 `magpie-community/plugins`）**：
   - 在 README、PR 说明和 `registry.json` 的中英文 `summary` 中清晰写明与现有 `@magpie-community/opencode-minimax-auth`（MiniMax Code）和 `@magpie-community/agent-minimax-design`（Agent 方向）的区别。
   - 通过社区仓库的 `bun scripts/check.mjs <name>` 和 `scripts/try.sh` 沙箱验证。

## 安全与边界

- 禁止将本机真实 token、cookie、refresh token、账号 ID 或个人会话内容写入代码、测试夹具、文档或 Git 提交历史。
- 调试时优先使用独立沙箱 `HOME` 运行 magpie，不要破坏 `~/.config/magpie` 与 `~/Library/Application Support/@hilo/desktop` 中的现有登录态。
- 注意 MiniMax Design 运行中可能会回写内存配置到磁盘；任何只读探测不要修改其本地状态文件。
