# 接入教程

# 支持的模型

> 如果你在官网发觉有更多好玩的模型，请联系管理员把模型加入进来

| 模型 | 说明 |
|------|------|
| fal-ai/flux-1/dev | 画图 |
| fal-ai/flux-1/dev/image-to-image |画图|
| fal-ai/flux-1/dev/redux | 画图 |
| fal-ai/flux-1/schnell | 画图 |
| fal-ai/flux-1/schnell/redux | 画图|
| fal-ai/flux-pro/kontext |画图|
| fal-ai/flux-pro/kontext/max |画图 |
| fal-ai/flux-pro/kontext/max/multi | 画图 |
| fal-ai/flux-pro/kontext/max/text-to-image |画图 |
| fal-ai/flux-pro/kontext/multi |画图 |
| fal-ai/flux-pro/kontext/text-to-image |画图 |

---

# Fal-ai API 接口文档

> **约定**  
header 带上 `Authorization: Bearer your-key`  
官网是用 `Authorization: key your-key`  
将官网的 `https://queue.fal.run` 更换为 你的请求域名
输入、输出、请求方式跟官网一致

## 1. 生成任务

### 接口

```
POST {{BASE_URL}}/fal-ai/{{model}}
```

### 示例

```shell
curl --request POST \
  --url {{BASE_URL}}/fal-ai/flux-1/dev \
  --header 'Authorization: Bearer your-key' \
  --header 'Content-Type: application/json' \
  --data '{
     "prompt": "Extreme close-up of a single cat eye, direct frontal view. Detailed iris and pupil. Sharp focus on eye texture and color. Natural lighting to capture authentic eye shine and depth. The word \"openai-hk\" is painted over it in big, white brush strokes with visible texture."
}'
```
具体的请求方式请详看各个模型的文档。请注意，**请求参数可能在中转中不能正确生效**，你可以从prompt开始测试，如果你发现了文档中的某个参数无法正常生效，你可以联系客服进行维护。

### 返回体

```json
{
  "status": "IN_QUEUE",
  "request_id": "551a32da-52b2-4be8-bf2f-bfb7cce2b324",
  "response_url": "https://queue.fal.run/fal-ai/flux-1/requests/551a32da-52b2-4be8-bf2f-bfb7cce2b324",
  "status_url": "https://queue.fal.run/fal-ai/flux-1/requests/551a32da-52b2-4be8-bf2f-bfb7cce2b324/status",
  "cancel_url": "https://queue.fal.run/fal-ai/flux-1/requests/551a32da-52b2-4be8-bf2f-bfb7cce2b324/cancel",
  "queue_position": 0
}
```

> **说明**  
返回体中的 `response_url` 为下一步请求链接，需要将 `https://queue.fal.run` 替换为 你的中转地址。

---

## 2. 获取任务结果

> 获取结果有时效，请务必保存

### 接口

```
GET {BASE_URL}/fal-ai/{modelname}/requests/{request_id}
```

### 示例

```shell
curl --request GET \
  --url {{BASE_URL}}/fal-ai/flux-1/requests/551a32da-52b2-4be8-bf2f-bfb7cce2b324 \
  --header 'Authorization: Bearer hk-your-key' \
  --header 'Content-Type: application/json'
```

---

### 返回体.图片

结果在 `images`

```json
{
  "images": [
    {
      "url": "https://v3.fal.media/files/rabbit/aQEmU4lEKKIIr9cDOChUB.png",
      "width": 1024,
      "height": 768,
      "content_type": "image/png"
    }
  ],
  "timings": {
    "inference": 1.2249955059960485
  },
  "seed": 920212137,
  "has_nsfw_concepts": [false],
  "prompt": "Extreme close-up of a single cat eye, direct frontal view. Detailed iris and pupil. Sharp focus on eye texture and color. Natural lighting to capture authentic eye shine and depth. The word \"openai-hk\" is painted over it in big, white brush strokes with visible texture."
}
```

### 返回体.视频

结果在 `video`

```json
{
  "video": {
    "url": "https://v3.fal.media/files/lion/eSsTNfWQRXfWGim1B8ZL5_output.mp4",
    "content_type": "video/mp4",
    "file_name": "output.mp4",
    "file_size": 946834
  }
}
```

---

> 获取结果有时效，请务必保存

---
