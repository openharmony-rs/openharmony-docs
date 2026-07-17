# PanRecognizer

手势识别器对象。

**继承/实现关系：** PanRecognizer extends [GestureRecognizer](arkts-arkui-gesture-gesturerecognizer-c.md)

**起始版本：** 12

<!--Device-unnamed-declare class PanRecognizer extends GestureRecognizer--><!--Device-unnamed-declare class PanRecognizer extends GestureRecognizer-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getDirection

```TypeScript
getDirection(): PanDirection
```

返回当前滑动手势识别器的识别方向。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PanRecognizer-getDirection(): PanDirection--><!--Device-PanRecognizer-getDirection(): PanDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanDirection](arkts-arkui-gesture-pandirection-e.md) | 当前滑动手势识别器的识别方向。 |

## getDistance

```TypeScript
getDistance(): number
```

返回当前滑动手势识别器触发的最小滑动距离。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PanRecognizer-getDistance(): number--><!--Device-PanRecognizer-getDistance(): number-End-->

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
> 仅支持对通过Pan手势初始化配置修改的设备类型进行阈值查询。对于默认滑动阈值，可通过查询[SourceTool](../arkts-components/arkts-arkui-common-sourcetool-e.md).Unknown类型获取。其他未主动设置的类型则无法获取。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PanRecognizer-getDistanceMap(): Map<SourceTool, number>--><!--Device-PanRecognizer-getDistanceMap(): Map<SourceTool, number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Map](../../apis-arkts/arkts-apis/arkts-arkts-collections-map-c.md)<SourceTool, number> | 不同输入源的滑动手势识别器触发的最小滑动距离。滑动距离的单位：vp |

## getPanGestureOptions

```TypeScript
getPanGestureOptions(): PanGestureOptions
```

返回当前滑动手势识别器的属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanRecognizer-getPanGestureOptions(): PanGestureOptions--><!--Device-PanRecognizer-getPanGestureOptions(): PanGestureOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureOptions](arkts-arkui-gesture-pangestureoptions-c.md) | 当前滑动手势识别器的属性。 |

