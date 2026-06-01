# 状态码

// 任务状态常量
const (
	TaskStatusWaiting    = "WAITING"    // 等待中
	TaskStatusProcessing = "PROCESSING" // 处理中
	TaskStatusFinish     = "FINISH"     // 已完成
	TaskStatusAborted    = "ABORTED"    // 已终止
)

子任务：AigcImageTask、AigcVideoTask状态
Status：任务状态，取值：
        PROCESSING：处理中；
        FINISH：已完成。

        示例值：FINISH
ErrCode：错误码。源异常时返回非0错误码，返回0时请使用各个具体任务的 ErrCode。
