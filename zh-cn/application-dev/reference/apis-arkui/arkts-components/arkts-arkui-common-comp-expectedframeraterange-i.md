# ExpectedFrameRateRange

```TypeScript
declare interface ExpectedFrameRateRange
```

设置动画期望的帧率。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expected

```TypeScript
expected: number
```

期望的最优帧率，单位为帧/秒（fps）。

取值范围为[min, max]，超出范围时不生效。设置为0时，将跟随应用的帧率。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max: number
```

期望的最大帧率，单位为帧/秒（fps）。

取值范围为[min, 设备最大帧率]。设备最大帧率取决于设备屏幕的刷新率，例如60Hz屏幕的设备最大帧率为60fps，120Hz屏幕的设备最大帧率为120fps。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min: number
```

期望的最小帧率，单位为帧/秒（fps）。

取值范围为[0, 设备最大帧率]。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
