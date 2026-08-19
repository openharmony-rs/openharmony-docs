# EventLocationInfo

用于点击手势获取点击位置坐标。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface EventLocationInfo--><!--Device-unnamed-export declare interface EventLocationInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getCurrentLocalPosition

```TypeScript
getCurrentLocalPosition(): Coordinate2D
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-EventLocationInfo-getCurrentLocalPosition(): Coordinate2D--><!--Device-EventLocationInfo-getCurrentLocalPosition(): Coordinate2D-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Coordinate2D](arkts-arkui-coordinate2d-i.md) |  |

## default

```TypeScript
default
```

获取点击位置相对于当前组件实时位置的左上角坐标。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-default--><!--Device-EventLocationInfo-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayX

```TypeScript
displayX: double
```

相对于屏幕的左上角X坐标。 取值范围：[0, +∞) 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-displayX: double--><!--Device-EventLocationInfo-displayX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayY

```TypeScript
displayY: double
```

相对于屏幕的左上角Y坐标。 取值范围：[0, +∞) 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-displayY: double--><!--Device-EventLocationInfo-displayY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayX

```TypeScript
globalDisplayX?: double
```

在[全局坐标系](../../../windowmanager/window-terminology.md#全局坐标系)中的X坐标。 取值范围：[0, +∞) 单位：vp

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-globalDisplayX?: double--><!--Device-EventLocationInfo-globalDisplayX?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## globalDisplayY

```TypeScript
globalDisplayY?: double
```

在[全局坐标系](../../../windowmanager/window-terminology.md#全局坐标系)中的Y坐标。 取值范围：[0, +∞) 单位：vp

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-globalDisplayY?: double--><!--Device-EventLocationInfo-globalDisplayY?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowX

```TypeScript
windowX: double
```

相对于窗口的左上角X坐标。 取值范围：[0, +∞) 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-windowX: double--><!--Device-EventLocationInfo-windowX: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowY

```TypeScript
windowY: double
```

相对于窗口的左上角Y坐标。 取值范围：[0, +∞) 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-windowY: double--><!--Device-EventLocationInfo-windowY: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x: double
```

相对于组件左上角的X坐标。 取值范围：[0, +∞) 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-x: double--><!--Device-EventLocationInfo-x: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y: double
```

相对于组件左上角的Y坐标。 取值范围：[0, +∞) 单位：vp

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EventLocationInfo-y: double--><!--Device-EventLocationInfo-y: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

