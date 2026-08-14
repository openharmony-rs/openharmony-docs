# TouchOptions

触摸操作的通用选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-declare interface TouchOptions--><!--Device-unnamed-declare interface TouchOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## duration

```TypeScript
duration?: int
```

操作持续的时间，取值范围为大于等于1500的整数，默认值为1500，单位：ms。取值小于1500时抛出17000007错误码， 为null或undefined时使用默认值。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TouchOptions-duration?: int--><!--Device-TouchOptions-duration?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## pressure

```TypeScript
pressure?: double
```

触摸的压力值，取值范围为[0, 1]，包含0和1，默认值为0。取值为null或undefined时按照默认值处理，其他超出取值范围情况时抛出17000007错误码。

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TouchOptions-pressure?: double--><!--Device-TouchOptions-pressure?: double-End-->

**系统能力：** SystemCapability.Test.UiTest

## speed

```TypeScript
speed?: int
```

操作速度（每秒像素数），取值范围为 200 到 40000。 如果超出范围或为 null 或未定义，则默认设置为 600。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TouchOptions-speed?: int--><!--Device-TouchOptions-speed?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

