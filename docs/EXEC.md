# cocosmcp_exec

经 `cocos-meta-mcp` 扩展 → `POST http://127.0.0.1:3921/exec`。

| mode | 说明 |
|------|------|
| `message` / `eval` | 主进程 |
| `scene-script` / `scene-eval` | 场景进程（`scene-eval` → `cocos-meta-mcp` / `eval`） |
| `open-url` | 打开预览 URL |

## 本地桥安全

HTTP 桥仅监听 `127.0.0.1`，并校验：

1. **Host** 必须为 loopback（防 DNS rebinding）
2. 带 **Origin** 的请求须为扩展 / loopback，或列在 `COCOSMCP_ALLOWED_ORIGINS`（逗号分隔）
3. 无 Origin 的本地客户端（MCP / curl）可正常调用
