# TextTimerOptions

用于构建TextTimer组件的选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface TextTimerOptions--><!--Device-unnamed-export interface TextTimerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextTimerController
```

TextTimer控制器。

**类型：** TextTimerController

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerOptions-controller?: TextTimerController--><!--Device-TextTimerOptions-controller?: TextTimerController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: long
```

计时器时间（isCountDown为true时生效），单位为毫秒。最长不超过86400000毫秒（24小时）。 0<count<86400000时，count值为计时器初始值。否则，使用默认值为计时器初始值。 默认值：60000ms。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerOptions-count?: long--><!--Device-TextTimerOptions-count?: long-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isCountDown

```TypeScript
isCountDown?: boolean
```

倒计时开关。 true：计时器开启倒计时，例如从30秒~0秒。 false：计时器开始计时，例如从0秒~30秒。 默认值：false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerOptions-isCountDown?: boolean--><!--Device-TextTimerOptions-isCountDown?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startTime

```TypeScript
startTime?: int
```

计时器经过的时间，单位为设置格式的最小单位。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextTimerOptions-startTime?: int--><!--Device-TextTimerOptions-startTime?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

