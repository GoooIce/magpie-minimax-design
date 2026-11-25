# magpie-minimax-design

把本机 **MiniMax Design** 订阅接入 **magpie**（兼容 OpenCode provider 插件规范）的社区插件项目。

## 定位与现有包的区别

对照社区仓库 [magpie-community/plugins](https://github.com/magpie-community/plugins)：

- `packages/minimax-design`（`@magpie-community/agent-minimax-design`）：**Agent 插件**，方向相反——是把 magpie 网关接到 MiniMax Design 里当作自定义模型，且仅支持 Windows。
- `packages/minimax`（`@magpie-community/opencode-minimax-auth`）：**MiniMax Code (`mcode`)** 的 provider 插件，走 `mcode` 设备码 OAuth 流程。
- **本项目**：**Provider 插件**，目标是把本机已登录的 **MiniMax Design**（基于 OpenCode / Pi，Electron app id `@hilo`）订阅接入 magpie，让 magpie 下的其他 agent 可以调用该订阅模型与额度。

## 本机环境线索（macOS）

- MiniMax Design 应用：`/Applications/MiniMax Design.app`（Bundle ID：`com.minimax.hub`）
- MiniMax Design 本地数据目录：`~/Library/Application Support/@hilo/desktop`
- magpie 应用与 CLI：`/Applications/magpie.app/Contents/MacOS/magpie`
- magpie 配置目录：`~/.config/magpie`

## 参考资料

- magpie 插件文档：<https://usemagpie.ai/docs/plugins>（Quick start：<https://usemagpie.ai/docs/plugins#quick>）
- 社区插件仓库：<https://github.com/magpie-community/plugins>
  - 订阅 provider 模板参考：`packages/zen-free`、`packages/minimax`
  - 读取本机桌面客户端登录态参考：`packages/astudio`、`packages/catpaw`、`packages/agnes-code`

## 本地开发与验证（规划）

```sh
# 单元测试
bun test

# 本地加载到 magpie（建议先在沙箱 HOME 中验证，避免影响日常配置）
/Applications/magpie.app/Contents/MacOS/magpie plugin add .
/Applications/magpie.app/Contents/MacOS/magpie plugin
```
