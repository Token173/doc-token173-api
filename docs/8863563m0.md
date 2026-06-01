# 状态码

// Luma任务状态常量
const (
	LumaTaskStateQueued     = "queued"     // 排队中
	LumaTaskStatePending    = "pending"    // 等待中
	LumaTaskStateProcessing = "processing" // 处理中
	LumaTaskStateCompleted  = "completed"  // 已完成
	LumaTaskStateFailed     = "failed"     // 失败
	LumaTaskStateError      = "error"      // 错误（用于错误响应）
)
