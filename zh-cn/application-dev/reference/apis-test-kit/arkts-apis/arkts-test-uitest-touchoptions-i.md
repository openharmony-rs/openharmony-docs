# TouchOptions

触摸操作的通用选项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-declare interface TouchOptions--><!--Device-unnamed-declare interface TouchOptions-End-->

**系统能力：** SystemCapability.Test.UiTest

## duration

```TypeScript
duration?: int
```

操作持续时间（毫秒），最小值和默认值均为 1500。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TouchOptions-duration?: int--><!--Device-TouchOptions-duration?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

## pressure

```TypeScript
pressure?: double
```

触摸的压力值，取值范围为 0 到 1， 默认值为 1。

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

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

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TouchOptions-speed?: int--><!--Device-TouchOptions-speed?: int-End-->

**系统能力：** SystemCapability.Test.UiTest

