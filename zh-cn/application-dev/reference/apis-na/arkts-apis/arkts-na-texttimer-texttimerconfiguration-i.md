# TextTimerConfiguration

ContentModifier接口使用的TextTimer配置。 开发者需要自定义class实现ContentModifier接口。

**继承/实现关系：** TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface TextTimerConfiguration--><!--Device-unnamed-export declare interface TextTimerConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: long
```

计时器时间（isCountDown为true时生效），单位为毫秒。最长不超过86400000毫秒（24小时）。 0&lt;count&lt;86400000时，count值为倒计时初始值。否则，使用默认值为倒计时初始值。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerConfiguration-count: long--><!--Device-TextTimerConfiguration-count: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## elapsedTime

```TypeScript
elapsedTime: long
```

计时器经过的时间，单位为设置格式的最小单位。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerConfiguration-elapsedTime: long--><!--Device-TextTimerConfiguration-elapsedTime: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCountDown

```TypeScript
isCountDown: boolean
```

是否倒计时。 true：计时器开启倒计时，例如从30秒 ~ 0秒；false：计时器开始计时，例如从0秒 ~ 30秒。 默认值：false。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerConfiguration-isCountDown: boolean--><!--Device-TextTimerConfiguration-isCountDown: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startTime

```TypeScript
startTime?: int
```

计时器经过的时间，单位为设置格式的最小单位。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerConfiguration-startTime?: int--><!--Device-TextTimerConfiguration-startTime?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## started

```TypeScript
started: boolean
```

是否已经开始了计时。 true：开始计时；false：未开始计时。 默认值：false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerConfiguration-started: boolean--><!--Device-TextTimerConfiguration-started: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

