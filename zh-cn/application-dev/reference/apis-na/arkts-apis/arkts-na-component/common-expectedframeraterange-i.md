# ExpectedFrameRateRange

设置动画期望的帧率。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ExpectedFrameRateRange--><!--Device-unnamed-export declare interface ExpectedFrameRateRange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expected

```TypeScript
expected: int
```

期望的最优帧率，单位为帧/秒（fps）。 取值范围为[min, max]。设置为0时，将跟随应用的帧率。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExpectedFrameRateRange-expected: int--><!--Device-ExpectedFrameRateRange-expected: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max: int
```

期望的最大帧率，单位为帧/秒（fps）。 取值范围为[min, 设备最大帧率]。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExpectedFrameRateRange-max: int--><!--Device-ExpectedFrameRateRange-max: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min: int
```

期望的最小帧率，单位为帧/秒（fps）。 取值范围为[0, 设备最大帧率]。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExpectedFrameRateRange-min: int--><!--Device-ExpectedFrameRateRange-min: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

