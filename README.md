# AI 中转 API 接入文档全集：Claude / GPT / Gemini / Grok 配置教程与接口说明

docs.token173.net 的 GitHub 镜像。线上文档站：https://docs.token173.net

首页放三样东西：怎么拿到 Key、各家客户端填什么、模型 ID 对照。细节都在 `docs/` 目录里，按接口分文件。

## 三步开始用

1. 注册账号：https://token173.net，新账号送 0.2 美元额度
2. 建令牌：后台左侧「令牌」→ 新建 → 复制 `sk-` 开头的字符串
3. 填配置：按下面两张表选协议，改 Base URL 和 Key

## Base URL 对照表

| 场景 | 填什么 | 注意 |
|---|---|---|
| OpenAI 兼容（GPT / Gemini / Grok / 国产模型） | `https://token173.net/v1` | 必须带 `/v1` |
| Anthropic 协议（Claude / Claude Code） | `https://token173.net` | 不要带 `/v1` |
| Google 原生协议（generateContent） | `https://token173.net/v1beta` | 走 `x-goog-api-key` |
| 图像接口 | `https://token173.net/v1/images/generations` | OpenAI 图像格式 |
| 视频接口 | `https://token173.net/v1/videos/generations` | 异步提交 + 轮询 |

这张表是接入时最容易出错的地方，八成的 404 都是协议和路径没对上。

## 模型 ID 对照

**文本**

| 系列 | 模型 ID |
|---|---|
| Claude | `claude-opus-5-5`、`claude-sonnet-5-5`、`claude-haiku-5-5`、`claude-fable-5-2`、`claude-fable-5-1`、`claude-fable-5`、`claude-opus-4-8` |
| OpenAI | `gpt-6-astra`、`gpt-6.1-sol`、`gpt-6.1-terra`、`gpt-6-sol`、`gpt-5.6-sol`、`gpt-5.6-terra`、`gpt-5.5`、`gpt-5.4` |
| Gemini | `gemini-4-carbon`、`gemini-4-argon`、`gemini-3.8-flash`、`gemini-3-pro-preview`、`gemini-2.5-flash` |
| Grok | `grok-4.7`、`grok-4.5` |
| 国产 | `glm-5.3-flash`、`deepseek-v4-pro`、`deepseek-v4-pro-0813`、`deepseek-v4-flash-0731`、`kimi-k3`、`MiniMax-H3` |

**图像**

| 模型 ID | 说明 |
|---|---|
| `gpt-image-2.6-flare` | 2.6 的快速迭代版，布局优化，低画质最快约 6 秒 |
| `gpt-image-2.6-sunburst` | 2.6 的细节版，编辑精度和一致性更好 |
| `gpt-image-2.5-sunburst` | 写实与细节 |
| `gpt-image-2` | 基础版，单价低 |
| `gemini-nano-banana-2.1` | 谷歌图像系列 |

**视频**

| 模型 ID | 说明 |
|---|---|
| `veo_3_1` | 文本/图生视频，带音频 |
| `doubao-seedance-2-0-fast-260128` | 豆包快速版 |

模型名即 ID，全小写，不要加空格。

## 快速验证

```bash
curl https://token173.net/v1/chat/completions \
  -H "Authorization: Bearer sk-你的令牌" \
  -H "Content-Type: application/json" \
  -d '{"model":"gpt-6.1-sol","messages":[{"role":"user","content":"在吗"}]}'
```

有正常返回说明 Key 和网络都没问题，接着按各客户端文档配置。

## 文档目录

`docs/` 下按接口分文件，每个文件是一份 OpenAPI 描述，可以直接导入 Postman 或 Apifox。想看某个接口的参数和返回结构，找对应的 md 文件即可。

## 常见客户端

| 客户端 | 类型 | 关键配置 |
|---|---|---|
| Cherry Studio | 桌面 | OpenAI 兼容，`https://token173.net/v1` |
| LobeChat | Web | 自定义 OpenAI 端点 |
| ChatBox | 桌面/移动 | OpenAI 兼容 |
| Claude Code | CLI | `ANTHROPIC_BASE_URL`，不带 `/v1` |
| Gemini CLI | CLI | `GOOGLE_GEMINI_BASE_URL` |
| Cursor | IDE | Override OpenAI/Anthropic Base URL |
| Cline | IDE 插件 | Anthropic 或 OpenAI 模式二选一 |
| Dify / n8n | 平台 | OpenAI 兼容渠道 |
| OneAPI / NewAPI | 网关 | 作为上游渠道填入 |

## 计费规则

- 充值比例：2 元 = 1 美元额度
- 注册赠 0.2 美元，不限时
- 按 token 或按张/按条计费，后台日志逐笔可查
- 失败请求不扣费

## 常见问题

**Q：为什么调用返回 404？**
九成是 Base URL 路径不对。Anthropic 协议不带 `/v1`，OpenAI 协议必须带 `/v1`。

**Q：为什么返回 401？**
Key 不完整、过期或被删。后台令牌页确认状态，重新复制一次。

**Q：模型名写对了却报找不到模型？**
检查大小写和分隔符，全部小写、用 `-` 连接；另外确认令牌所在分组是否包含该模型。

**Q：能开票吗？**
后台有充值记录，需要发票联系客服，提供金额和抬头。

**Q：文档里没有我要的接口怎么办？**
去线上文档站搜，或者提 issue，会补。

## 相关仓库

- Claude 专题：[claude-api](https://github.com/Token173/claude-api)
- GPT 专题：[gpt-api](https://github.com/Token173/gpt-api)
- Gemini 专题：[gemini-api](https://github.com/Token173/gemini-api)
- 图像接口：[gpt-image-api](https://github.com/Token173/gpt-image-api)
- 视频接口：[veo-proxy-](https://github.com/Token173/veo-proxy-)
