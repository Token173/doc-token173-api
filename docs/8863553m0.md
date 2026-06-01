# 聊天完成对象



| 参数 | 类型 | 描述 |
|-|-|-|
| id | string | 聊天完成的唯一标识符 |
| choices | array | 聊天完成选项列表。如果n大于1,可以有多个选项 |
| created | integer | 创建聊天完成的Unix时间戳(秒) |  
| model | string | 用于聊天完成的模型 |
| system_fingerprint | string | 该指纹表示模型运行的后端配置 |
| object | string | 对象类型,总是 chat.completion |
| usage | object | 完成请求的使用统计信息 |
| completion_tokens | integer | 生成的完成中的标记数 |
| prompt_tokens | integer | 提示中的标记数 |
| total_tokens | integer | 请求中使用的标记总数(提示 + 完成) |

```JSON
{
  "id": "chatcmpl-123",
  "object": "chat.completion",
  "created": 1677652288,
  "model": "gpt-3.5-turbo-0613",
  "system_fingerprint": "fp_44709d6fcb",
  "choices": [{
    "index": 0,
    "message": {
      "role": "assistant",
      "content": "\n\nHello there, how may I assist you today?",
    },
    "finish_reason": "stop"
  }],
  "usage": {
    "prompt_tokens": 9,
    "completion_tokens": 12,
    "total_tokens": 21
  }
}
```


