# SystemRecordControllerConfig

定义系统录像控制器面板配置。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## sourceType

```TypeScript
sourceType: SourceType
```

系统使用它来确定应用程序的录制场景，根据
应用程序期望用于流式传输的源类型，并为用户提供
选择匹配降噪模式的能力。支持的源类型包括
{@link SourceType#Source_TYPE_MIC},{@link SourceType#Source_TYPE_CAMCORDER}，以及
{@link SourceType#Source_TYPE_LIVE}。

**类型：** SourceType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

