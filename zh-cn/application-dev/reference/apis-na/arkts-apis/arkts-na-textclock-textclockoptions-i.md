# TextClockOptions

用于构建TextClock组件的选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface TextClockOptions--><!--Device-unnamed-export declare interface TextClockOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextClockController
```

TextClock controller. Anonymous Object Rectification.

**类型：** [TextClockController](arkts-na-textclock-textclockcontroller-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextClockOptions-controller?: TextClockController--><!--Device-TextClockOptions-controller?: TextClockController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeZoneOffset

```TypeScript
timeZoneOffset?: double
```

设置时区偏移量。 取值范围为[-14, 12]，表示东十二区到西十二区，其中负值表示东时区，正值表示西时区，比如东八区为-8。设置值为该取值范围内的浮点数时会进行取整，舍弃小数部分。 对横跨国际日界线的国家或地区，用-13（UTC+13）和-14（UTC+14）来保证整个国家或者区域处在相同的时间，当设置的值不在取值范围内时，将使用当前系统的时区偏移量。 设置值为{ 9.5, 3.5, -3.5, -4.5, -5.5, -5.75, -6.5, -9.5, -10.5, -12.75 }集合中的浮点数时不进行取整。 默认值：当前系统的时区偏移量。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextClockOptions-timeZoneOffset?: double--><!--Device-TextClockOptions-timeZoneOffset?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

