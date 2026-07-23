# TextClockConfiguration

开发者需要自定义class实现ContentModifier接口。

**继承/实现关系：** TextClockConfiguration extends [CommonConfiguration<TextClockConfiguration>]

**起始版本：** 12

<!--Device-unnamed-declare interface TextClockConfiguration extends CommonConfiguration<TextClockConfiguration>--><!--Device-unnamed-declare interface TextClockConfiguration extends CommonConfiguration<TextClockConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## started

```TypeScript
started: boolean
```

指示文本时钟是否启动。

true：表示启动文本时钟。

false：表示关闭文本时钟。

默认值：true

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextClockConfiguration-started: boolean--><!--Device-TextClockConfiguration-started: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeValue

```TypeScript
timeValue: number
```

当前文本时钟时区的UTC秒数。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextClockConfiguration-timeValue: number--><!--Device-TextClockConfiguration-timeValue: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeZoneOffset

```TypeScript
timeZoneOffset: number
```

当前文本时钟时区偏移量。

取值范围为[-14, 12]，表示东十二区到西十二区，其中负值表示东时区，正值表示西时区，比如东八区为-8。设置值为该取值范围内的浮点数时会进行取整，舍弃小数部分。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextClockConfiguration-timeZoneOffset: number--><!--Device-TextClockConfiguration-timeZoneOffset: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

