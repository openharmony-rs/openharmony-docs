# ProgressInfo

定义进度上报的数据结构，且仅当进度指示选项[ProgressIndicator](arkts-basicservices-pasteboard-progressindicator-e.md#ProgressIndicator)设置为NONE时才会上报此信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-pasteboard-interface ProgressInfo--><!--Device-pasteboard-interface ProgressInfo-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

## progress

```TypeScript
progress: int
```

不使用系统提供的进度条时，系统上报拷贝粘贴任务进度百分比，单位：%。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ProgressInfo-progress: int--><!--Device-ProgressInfo-progress: int-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

