# SystemRecordControllerChangeInfo（系统接口）

定义系统录像控制器状态改变时携带的信息。
它包括启用状态、应用程序UID和预期的音频源类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## enabled

```TypeScript
enabled: boolean
```

是否启用系统录像控制器面板。
true表示启用面板，false表示禁用面板。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## sourceType

```TypeScript
sourceType?: SourceType
```

启用录制控制器时由应用程序配置的预期音频源类型。
用于匹配对应的录制场景和降噪模式。

**类型：** SourceType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid?: number
```

触发系统记录控制器状态更改的应用程序的UID。
取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

