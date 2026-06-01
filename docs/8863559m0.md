# 接入教程 

### Replicate 官方格式调用
| 如果有需要的模型可以联系客服添加

将官网的 https://api.replicate.com 更换为 {{BASE_URL}}/replicate
输入、输出、请求方式跟官网一致

接入流程
1. 创建任务
    提交任务后，获取到任务 ID
2. 获取任务进度
    通过任务ID查询任务进度，获取结果
    
    
PS：返回的资源连接仅有1个小时有效期    

返回体 关键字段说明

项目	类型	说明
input	object	输入
output	string 或者 []string	内容输出 url
status	string	状态 状态 starting processing succeeded failed


1.生成任务.路径方式
以 black-forest-labs/flux-schnell 为例
```
curl --request POST \
  --url {{BASE_URL}}/replicate/v1/models/black-forest-labs/flux-schnell/predictions \
  --header 'Authorization: Bearer hk-you-key' \
  --header 'Content-Type: application/json' \
  --data '{
    "input": {
      "prompt": "Japanese cartoon anime style, (1 person) (Gender: Male, Age: 30, Hair: Short black hair, Outfit: Dark blue hunting attire, includes a fitted jacket and trousers.) (A dimly lit room filled with tension,  is questioning Female, 27 years old, long black hair, pink tulle dress., who stands nervously in her pink dress, the sound of rain pattering against the window.)",
      "go_fast": true,
      "megapixels": "1",
      "num_outputs": 1,
      "aspect_ratio": "1:1",
      "output_format": "jpg",
      "output_quality": 80,
      "num_inference_steps": 4
    }
  }'
```

返回体 id 为下一步查询任务 id
```
{
  "id": "qpt5jq1fssrmc0cmd5hvy31mdg",
  "model": "black-forest-labs/flux-schnell",
  "version": "dp-4d0bcc010b3049749a251855f12800be",
  "input": {
    "aspect_ratio": "1:1",
    "go_fast": true,
    "megapixels": "1",
    "num_inference_steps": 4,
    "num_outputs": 1,
    "output_format": "jpg",
    "output_quality": 80,
    "prompt": "Japanese cartoon anime style, (1 person) (Gender: Male, Age: 30, Hair: Short black hair, Outfit: Dark blue hunting attire, includes a fitted jacket and trousers.) (A dimly lit room filled with tension,  is questioning Female, 27 years old, long black hair, pink tulle dress., who stands nervously in her pink dress, the sound of rain pattering against the window.)"
  },
  "logs": "",
  "output": null,
  "data_removed": false,
  "error": null,
  "status": "starting",
  "created_at": "2025-01-15T09:54:55.566Z",
  "urls": {
    "cancel": "https://api.replicate.com/v1/predictions/qpt5jq1fssrmc0cmd5hvy31mdg/cancel",
    "get": "https://api.replicate.com/v1/predictions/qpt5jq1fssrmc0cmd5hvy31mdg",
    "stream": "https://stream.replicate.com/v1/files/bcwr-gvuc2rokjozhlaxh6dcvk6tvhh2ymt4egnnpxvmtqql57angyfsq"
  }
}
```

2.生成任务.version 方式
以 lucataco/flux-schnell-lora 为例子
参考文档 https://replicate.com/lucataco/flux-schnell-lora?input=http
通过参考文档 得到 version 为 2a6b576af31790b470f0a8442e1e9791213fa13799cbb65a9fc1436e96389574
```
curl --request POST \
  --url {{BASE_URL}}/replicate/v1/predictions \
  --header 'Authorization: Bearer hk-your-key' \
  --header 'Content-Type: application/json' \
  --data '{
    "version": "2a6b576af31790b470f0a8442e1e9791213fa13799cbb65a9fc1436e96389574",
    "input": {
      "prompt": "Japanese cartoon anime style, (1 person) (Gender: Male, Age: 30, Hair: Short black hair, Outfit: Dark blue hunting attire, includes a fitted jacket and trousers.) (A dimly lit room filled with tension,  is questioning Female, 27 years old, long black hair, pink tulle dress., who stands nervously in her pink dress, the sound of rain pattering against the window.)",
      "hf_lora": "alvdansen/frosting_lane_flux",
      "lora_scale": 0.8,
      "num_outputs": 1,
      "aspect_ratio": "1:1",
      "output_format": "webp",
      "output_quality": 80,
      "prompt_strength": 0.8,
      "num_inference_steps": 4
    }
  }'
```

返回体格式上面格式一致
获取任务
通过上面的生产任何获取到 任务 id
结果在关键字段 output 上
注意 返回结果及其链接文件都有时效性
get {{BASE_URL}}/replicate/v1/predictions/{id}

```
curl --request GET \
  --url {{BASE_URL}}/replicate/v1/predictions/ctdwaehfz1rm80cmd5nsjd8114 \
  --header 'Authorization: Bearer hk-you-key' \
  --header 'Content-Type: application/json'
```
返回体

```json
{
  "id": "ctdwaehfz1rm80cmd5nsjd8114",
  "model": "black-forest-labs/flux-schnell",
  "version": "dp-4d0bcc010b3049749a251855f12800be",
  "input": {
    "aspect_ratio": "1:1",
    "go_fast": true,
    "megapixels": "1",
    "num_inference_steps": 4,
    "num_outputs": 1,
    "output_format": "jpg",
    "output_quality": 80,
    "prompt": "Japanese cartoon anime style, (1 person) (Gender: Male, Age: 30, Hair: Short black hair, Outfit: Dark blue hunting attire, includes a fitted jacket and trousers.) (A dimly lit room filled with tension,  is questioning Female, 27 years old, long black hair, pink tulle dress., who stands nervously in her pink dress, the sound of rain pattering against the window.)"
  },
  "logs": "Using seed: 62182\nrunning quantized prediction\nUsing seed: 62182\n  0%|          | 0/4 [00:00<?, ?it/s]\n 75%|███████▌  | 3/4 [00:00<00:00, 15.38it/s]\n100%|██████████| 4/4 [00:00<00:00, 13.43it/s]\nTotal safe images: 1 out of 1\n",
  "output": [
    "https://replicate.delivery/xezq/RoEhEdyl8PoIGFFPg46TU4Svj24i1NDVYmzehJfqLuX9nTFUA/out-0.jpg"
  ],
  "data_removed": false,
  "error": null,
  "status": "succeeded",
  "created_at": "2025-01-15T10:03:39.896Z",
  "started_at": "2025-01-15T10:03:40.584470194Z",
  "completed_at": "2025-01-15T10:03:41.142386377Z",
  "urls": {
    "cancel": "https://api.replicate.com/v1/predictions/ctdwaehfz1rm80cmd5nsjd8114/cancel",
    "get": "https://api.replicate.com/v1/predictions/ctdwaehfz1rm80cmd5nsjd8114",
    "stream": "https://stream.replicate.com/v1/files/bcwr-q57vie7wuzg3wxv2hvpajgmzqzmxe67kqddednevutmrpdcft6xq"
  },
  "metrics": {
    "image_count": 1,
    "predict_time": 0.557916184
  }
}
```






