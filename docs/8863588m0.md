# Callback协议

# 其他参数 请看 官方文档 https://app.klingai.com/cn/dev/document-api/apiReference/updateNotice
参数是一致的,对接时，仅需将请求域名、API key 改成我们

# 异步任务回调协议

对于异步任务（图像生成/视频生成），如果在创建任务时设置了 `callback_url`，当任务状态发生变更时，服务端会主动发送通知。

## 回调数据格式

```json
{
  "task_id": "string",           // 任务ID，系统生成
  "task_status": "string",       // 任务状态
  "task_status_msg": "string",   // 任务状态信息
  "created_at": 1722769557708,   // 任务创建时间（Unix时间戳，单位ms）
  "updated_at": 1722769557708,   // 任务更新时间（Unix时间戳，单位ms）
  "task_result": {
    "images": [                  // 图片类任务的结果
      {
        "index": 0,             // 图片编号，0-9
        "url": "string"         // 生成图片的URL
      }
    ],
    "videos": [                 // 视频类任务的结果
      {
        "id": "string",         // 视频ID，全局唯一
        "url": "string",        // 视频的URL
        "duration": "string"    // 视频总时长，单位s
      }
    ]
  }
}
```

## 任务状态说明

`task_status` 可能的枚举值：
- `submitted`：已提交
- `processing`：处理中
- `succeed`：成功
- `failed`：失败

## 注意事项

- 当任务失败时，`task_status_msg` 会展示失败原因（如触发平台的内容风控等）
- 图片URL示例：`https://h1.inkwai.com/bs2/upload-ylab-stunt/1fa0ac67d8ce6cd55b50d68b967b3a59.png`

