# TextTimerConfiguration

ContentModifier接口使用的TextTimer配置。

开发者需要自定义class实现ContentModifier接口。

**继承/实现关系：** TextTimerConfiguration extends [CommonConfiguration<TextTimerConfiguration>](CommonConfiguration<TextTimerConfiguration>)

**起始版本：** 12

<!--Device-unnamed-declare interface TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>--><!--Device-unnamed-declare interface TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: number
```

计时器时间（isCountDown为true时生效），单位为毫秒。最长不超过86400000毫秒（24小时）。 0<count<86400000时，count值为倒计时初始值。否则，使用默认值为倒计时初始值。

默认值：60000。

**类型：** number

**默认值：** 60000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextTimerConfiguration-count: number--><!--Device-TextTimerConfiguration-count: number-End-->

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

<!--Device-TextTimerConfiguration-elapsedTime: number--><!--Device-TextTimerConfiguration-elapsedTime: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCountDown

```TypeScript
isCountDown: boolean
```

是否倒计时。

true：计时器开启倒计时，例如从30秒 ~ 0秒；false：计时器开始计时，例如从0秒 ~ 30秒。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextTimerConfiguration-isCountDown: boolean--><!--Device-TextTimerConfiguration-isCountDown: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startTime

```TypeScript
startTime?: number
```

计时器正向计时模式下的初始时间，仅当isCountDown为false时该参数设置生效。

默认值：0

单位：毫秒

当值为负数时，计时器将从负值开始计时，经过0后继续向正数计时。

**类型：** number

**默认值：** 0

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextTimerConfiguration-startTime?: number--><!--Device-TextTimerConfiguration-startTime?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## started

```TypeScript
started: boolean
```

是否已经开始了计时。

true：开始计时；false：未开始计时。

默认值：false

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextTimerConfiguration-started: boolean--><!--Device-TextTimerConfiguration-started: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

