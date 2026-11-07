# DeepSeek Chat（GitHub Pages）

纯 HTML/CSS/JavaScript 的 DeepSeek API 聊天网页，无需服务器或构建步骤。

## 部署
1. 将本仓库的 GitHub Pages 设置为 GitHub Actions。
2. 工作流会自动发布仓库根目录中的网页。
3. 部署完成后，在 Settings → Pages 查看访问地址。

## 使用
打开网页，点击「设置」，填写 DeepSeek API Key，选择模型并设置 System Prompt 后保存即可。

API 地址：`https://api.deepseek.com/chat/completions`

## 安全说明
- API Key 只保存在当前页面内存中，刷新后需要重新输入。
- 不要把 API Key 写入源码、仓库或公开截图。
- 这是纯前端静态网页，浏览器必须直接持有 API Key；GitHub Pages 无法隐藏密钥。
- 聊天记录只保存在当前页面内存中，刷新后清空。
