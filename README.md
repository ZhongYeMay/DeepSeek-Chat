# DeepSeek Chat（支持 Gemini）

一个无需构建步骤的纯 HTML / CSS / JavaScript 聊天网页，可在 **DeepSeek** 与 **Google Gemini** 之间切换，适用于 GitHub Pages。

## 使用方法

1. 打开网页，点击「设置」。
2. 在「AI 服务商」中选择 **DeepSeek** 或 **Google Gemini**。
3. 分别填入对应服务商的 API Key。Gemini Key 可以在 [Google AI Studio](https://aistudio.google.com/apikey) 创建。
4. 选择模型并保存。选择 Gemini 时可点击「刷新 Gemini 模型」，使用当前 Key 查询其可用模型。
5. 返回聊天页面发送消息。切换服务商时将新建会话，历史聊天仍可在「历史记录」中打开。

**模型列表提醒：** 可列出的模型不保证当前 Key 一定拥有推理额度或权限；模型调用失败时，以 API 返回的错误消息为准。

## 接口

- DeepSeek 聊天：`https://api.deepseek.com/chat/completions`
- DeepSeek 余额：`https://api.deepseek.com/user/balance`（仅 DeepSeek）
- Gemini 聊天（OpenAI 兼容）：`https://generativelanguage.googleapis.com/v1beta/openai/chat/completions`
- Gemini 模型列表：`https://generativelanguage.googleapis.com/v1beta/models`

聊天接口使用 `Authorization: Bearer <API_KEY>`；Gemini 模型列表接口使用 `x-goog-api-key` 请求头。模型列表拉取失败时仍可手动尝试预设模型。

## 部署

1. 在仓库 Settings → Pages 中选择 **GitHub Actions** 作为发布源。
2. GitHub Actions 将发布仓库根目录的静态网页。
3. 在 Settings → Pages 查看站点访问地址。

## 安全说明

- **纯静态前端会在浏览器中持有并直接发送密钥**，无法像服务端应用一样隐藏密钥。不要共享存有密钥的设备、浏览器配置文件或浏览器数据。
- DeepSeek 和 Gemini 的 API Key 分别保存在当前浏览器的 `localStorage` 中；这不是加密存储。关闭页面或刷新页面不会自动删除它们。
- 密钥不会被写入源码或 GitHub 仓库。不要在 issue、日志、截图、录屏中展示完整密钥。
- 聊天记录也存储于当前浏览器本地存储中。清除网站数据会删除本地会话和密钥。
- 如需对外开放给多人使用，建议改为具有鉴权、速率限制和密钥保管机制的后端代理。
