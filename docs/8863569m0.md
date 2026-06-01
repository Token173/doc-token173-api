# 说明

# Suno API 接口文档

## 基础信息

### API 地址
- 默认地址:
  ```
  https://{BASE_URL}/suno/submit/music
  https://{BASE_URL}/suno/fetch
  ```

## 模型支持

### 支持模型
- chirp-v3-0  (对应版本 v3.0)
- chirp-v3-5  (对应版本 v3.5	)
- chirp-v4   (对应版本 v4.0	)
- chirp-auk  (对应版本 v4.5	)
- chirp-v5   (对应版本 v5.0	)


## 回调通知
- 支持 `notify_hook` 回调地址
- 要求:
  - 请求方式: POST
  - 接收数据: task数据结构

## 使用步骤

### 1. 创建Suno任务

### 2. 查询任务进度

## 数据结构

### Task对象
| 字段 | 类型 | 示例 | 描述 |
|------|------|------|------|
| task_id | string | f4a94d75-087b-4bb1-bd45-53ba293faf96 | 任务ID |
| action | string | MUSIC | 任务类型: MUSIC(生成歌)、LYRICS(生成歌词) |
| status | string | SUCCESS | 任务状态: NOT_START(未启动)、SUBMITTED(已提交处理)、QUEUED(排队)、IN_PROGRESS(执行中)、FAILURE(失败)、SUCCESS(成功) |
| submitTime | number | 1689231405854 | 提交时间 |
| startTime | number | 1689231442755 | 开始执行时间 |
| finishTime | number | 1689231544312 | 结束时间 |
| failReason | string | [Invalid parameter] Invalid value | 失败原因(失败时有值) |
| data | object | - | 具体数据：音乐(数组)、歌词(单个) |

### 音乐续写
- 需要传入 `task_id` 参数指定任务

