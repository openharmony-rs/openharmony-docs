# PanRecognizer

手势识别器对象。

**继承/实现关系：** PanRecognizer extends [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getDirection

```TypeScript
getDirection(): PanDirection
```

返回当前滑动手势识别器的识别方向。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PanDirection | 当前滑动手势识别器的识别方向。 |

## getDistance

```TypeScript
getDistance(): number
```

返回当前滑动手势识别器触发的最小滑动距离。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前滑动手势识别器触发的最小滑动距离。单位：vp |

## getDistanceMap

```TypeScript
getDistanceMap(): Map<SourceTool, number>
```

返回滑动手势识别器在不同输入源的情况下触发的最小滑动距离。

> **说明：**
>
> 仅支持对通过Pan手势初始化配置修改的设备类型进行阈值查询。对于默认滑动阈值，可通过查询[SourceTool](arkts-arkui-sourcetool-e.md).Unknown类型获取。其他未主动设置的类型则无法获取。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Map&lt;SourceTool, number&gt; | 不同输入源的滑动手势识别器触发的最小滑动距离。滑动距离的单位：vp |

## getPanGestureOptions

```TypeScript
getPanGestureOptions(): PanGestureOptions
```

返回当前滑动手势识别器的属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PanGestureOptions | 当前滑动手势识别器的属性。 |

