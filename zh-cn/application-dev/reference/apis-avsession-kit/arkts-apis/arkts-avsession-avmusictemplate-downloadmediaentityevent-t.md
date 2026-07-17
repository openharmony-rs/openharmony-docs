# DownloadMediaEntityEvent

```TypeScript
type DownloadMediaEntityEvent = (controlType: DownloadControlType, mediaEntity: MediaEntity) => Promise<OperResult>
```

媒体实体下载事件。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type DownloadMediaEntityEvent = (controlType: DownloadControlType, mediaEntity: MediaEntity) => Promise<OperResult>--><!--Device-avMusicTemplate-type DownloadMediaEntityEvent = (controlType: DownloadControlType, mediaEntity: MediaEntity) => Promise<OperResult>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controlType | DownloadControlType | 是 | controlType的可选项包括：开始下载、删除下载、恢复下载、暂停下载。 |
| mediaEntity | MediaEntity | 是 | 媒体实体。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;OperResult&gt; | Promise对象，返回下载媒体实体的操作结果对象。 |

