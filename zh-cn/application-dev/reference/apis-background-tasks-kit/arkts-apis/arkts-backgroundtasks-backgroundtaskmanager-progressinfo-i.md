# ProgressInfo

通知进度信息。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

<!--Device-backgroundTaskManager-export interface ProgressInfo--><!--Device-backgroundTaskManager-export interface ProgressInfo-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## fileName

```TypeScript
fileName: string
```

通知内容。

**类型：** string

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressInfo-fileName: string--><!--Device-ProgressInfo-fileName: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## isMute

```TypeScript
isMute?: boolean
```

下载进度达到100%时是否静音。

**类型：** boolean

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressInfo-isMute?: boolean--><!--Device-ProgressInfo-isMute?: boolean-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## progressValue

```TypeScript
progressValue?: int
```

通知进度。如果该字段不存在，则不显示通知进度环，显示为普通通知。 取值限定为整数。

**类型：** int

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressInfo-progressValue?: int--><!--Device-ProgressInfo-progressValue?: int-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

## title

```TypeScript
title: string
```

通知标题。

**类型：** string

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressInfo-title: string--><!--Device-ProgressInfo-title: string-End-->

**系统能力：** SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

