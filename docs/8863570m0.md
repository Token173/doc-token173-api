# 参数



## 音乐生成参数说明

### 1. 自定义创作模式 - 普通生成

| 参数名 | 类型 | 描述 | 备注 |
|--------|------|------|------|
| title | String | 音乐标题 | - |
| tags | String | 音乐风格 | 使用半角逗号隔开 |
| generation_type | String | 生成类型 | 默认为 TEXT |
| prompt | String | 音乐创作提示词 | 包括但不限于歌词 |
| negative_tags | String | 不希望出现的风格 | 可以为空字符串 |
| mv | String | 模型 | 默认为 chirp-v4<br>可选: chirp-v3-5, chirp-v3-0<br>扩展上传音频时使用 chirp-v3-5-upload |
| metadata | Object | 自定义参数 | 包含create_mode: custom, vocal_gender: "m"/"f" m为男生 f为女生|

### 2. 自定义创作模式 - 续写

| 参数名 | 类型 | 描述 | 备注 |
|--------|------|------|------|
| title | String | 音乐标题 | - |
| tags | String | 音乐风格 | 使用半角逗号隔开 |
| generation_type | String | 生成类型 | 默认为 TEXT |
| prompt | String | 音乐创作提示词 | 包括但不限于歌词 |
| negative_tags | String | 不希望出现的风格 | 可以为空字符串 |
| mv | String | 模型 | 默认为 chirp-v4<br>可选: chirp-v3-5, chirp-v3-0 |
| continue_at | Float | 续写起始时间 | 从第几秒开始继续创作<br>例如: 120.00 或 61.59 |
| continue_clip_id | String | 续写歌曲ID | 需要继续创作的歌曲id |
| task | String | 任务类型 | 默认为 extend |

### 3. 自定义创作模式 - 上传生成

| 参数名 | 类型 | 描述 | 备注 |
|--------|------|------|------|
| prompt | String | 音乐创作提示词 | 可以为空字符串 |
| generation_type | String | 生成类型 | 默认为 TEXT |
| tags | String | 音乐风格 | 使用半角逗号隔开 |
| negative_tags | String | 不希望出现的风格 | 可以为空字符串 |
| mv | String | 模型 | 请使用 chirp-v3-5-tau |
| title | String | 音乐标题 | - |
| continue_clip_id | String | 续写歌曲ID | 非必传参数，可以为 null |
| continue_at | Float | 续写起始时间 | 非必传参数，可以为 null |
| continued_aligned_prompt | String | 继续创作的对齐提示词 | 非必传参数，可以为 null |
| infill_start_s | Float | 填充开始时间（秒） | 非必传参数，可以为 null |
| infill_end_s | Float | 填充结束时间（秒） | 非必传参数，可以为 null |
| task | String | 任务类型 | 使用 Cover 功能，固定为 cover |
| cover_clip_id | String | 翻唱ID | 要翻唱的原曲id或上传的音频 clip id |

