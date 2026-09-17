# AVDownloadTaskState

```TypeScript
type AVDownloadTaskState = 'init' | 'queued' | 'running' | 'completed' | 'paused' | 'removing' | 'error'
```

离线下载任务状态枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

| 类型 | 说明 |
| --- | --- |
| 'init' | 下载任务初始化。 |
| 'queued' | 下载任务排队等待。 |
| 'running' | 下载任务正在运行。 |
| 'completed' | 下载任务已完成。 |
| 'paused' | 下载任务已暂停。 |
| 'removing' | 下载任务正在移除。 |
| 'error' | 下载任务出错。 |
