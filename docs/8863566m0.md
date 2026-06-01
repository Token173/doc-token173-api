# 状态码

// VEO任务状态常量
const (
	VeoStatusPending                  = "pending"
	VeoStatusImageDownloading         = "image_downloading"
	VeoStatusVideoGenerating          = "video_generating"
	VeoStatusVideoGenerationCompleted = "video_generation_completed"
	VeoStatusVideoGenerationFailed    = "video_generation_failed"
	VeoStatusVideoUpsampling          = "video_upsampling"
	VeoStatusVideoUpsamplingCompleted = "video_upsampling_completed"
	VeoStatusVideoUpsamplingFailed    = "video_upsampling_failed"
	VeoStatusCompleted                = "completed"
	VeoStatusFailed                   = "failed"
	VeoStatusError                    = "error" // 错误（用于错误响应）
)
