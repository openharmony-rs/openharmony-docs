# ProgressListener

```TypeScript
type ProgressListener = (progress: ProgressInfo) => void
```

定义进度数据变化的订阅函数，当选择不使用系统默认进度显示时，可设置该项获取粘贴过程的进度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-pasteboard-type ProgressListener = (progress: ProgressInfo) => void--><!--Device-pasteboard-type ProgressListener = (progress: ProgressInfo) => void-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | ProgressInfo | 是 | 定义进度上报的数据结构，且仅当进度指示选项[ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md#ProgressIndicator)设置为 NONE时才会上报此信息。 |

