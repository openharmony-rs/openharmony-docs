# OnAVDownloadProgressChangeHandle

```TypeScript
type OnAVDownloadProgressChangeHandle = (taskId: string, progress: number) => void
```

离线下载任务进度变化事件回调方法。当下载进度相比上次变化超过1%，且距上次触发时间超过500ms时，触发该事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | string | 是 | 离线下载任务ID。 |
| progress | number | 是 |  |
