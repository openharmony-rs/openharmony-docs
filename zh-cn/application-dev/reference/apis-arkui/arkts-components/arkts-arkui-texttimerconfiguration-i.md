# TextTimerConfiguration

ContentModifier接口使用的TextTimer配置。开发者需要自定义class实现ContentModifier接口。

**继承/实现关系：** TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## count

```TypeScript
count: number
```

计时器初始时间，单位为毫秒，isCountDown为true时生效。默认值：60000取值范围为(0, 86400000)，即不超过24小时。超出取值范围时置为默认值。

**类型：** number

**默认值：** 60000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## elapsedTime

```TypeScript
elapsedTime: number
```

计时器经过的时间，单位为设置格式的最小单位。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCountDown

```TypeScript
isCountDown: boolean
```

是否倒计时。true：计时器开启倒计时，例如从30秒 ~ 0秒；false：计时器开始计时，例如从0秒 ~ 30秒。默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## started

```TypeScript
started: boolean
```

是否已经开始了计时。true：开始计时；false：未开始计时。默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startTime

```TypeScript
startTime?: number
```

计时器正向计时模式下的初始时间，仅当isCountDown为false时该参数设置生效。取值范围：无上限，支持负数。默认值：0单位：毫秒当值为负数时，计时器将从负值开始计时，经过0后继续向正数计时。

**类型：** number

**默认值：** 0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
