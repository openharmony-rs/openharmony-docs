# PinchGestureInterface

用于触发捏合手势，最少需要2指，最多5指，最小识别距离为5vp。在支持鼠标和键盘输入的设备上，通过“Ctrl+鼠标滚轮”也可以触发捏合手势。

> **说明：**  
>  
> 捏合手势触发成功后，抬起手指直至不再满足触发条件。再次满足条件时，可重新触发捏合手势。

**继承/实现关系：** PinchGestureInterface extends [GestureInterface<PinchGestureInterface>](GestureInterface<PinchGestureInterface>)

**起始版本：** 7

<!--Device-unnamed-interface PinchGestureInterface extends GestureInterface<PinchGestureInterface>--><!--Device-unnamed-interface PinchGestureInterface extends GestureInterface<PinchGestureInterface>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
(value?: { fingers?: number; distance?: number }): PinchGestureInterface
```

继承自[GestureInterface<T>](arkts-arkui-gesture-gestureinterface-i.md)，设置捏合手势事件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureInterface-(value?: { fingers?: number; distance?: number }): PinchGestureInterface--><!--Device-PinchGestureInterface-(value?: { fingers?: number; distance?: number }): PinchGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { fingers?: number; distance?: number } | 否 | 设置捏合手势事件参数。<br> - fingers：触发捏合的最少手指数，最小为2指，最大为5指。<br/>默认值：2 <br/>取值范围：[2, 5]。当设置的值不在该范围内时，会被转化为默认值。<br/>触发手势的手指数量可以多于fingers数目，但只有最先落下的与fingers相同数目的手指参与手势计算。<br> - distance：最小识别距离，单位为vp。该距离是指当前多根手指位置与手指中心位置的平均距离，与手指落下时的平均距离之间的差值。当这一差值大于或等于最小识别距离时，捏合手势被视为成功。<br/>默认值：5 <br/>**说明：** <br/>取值范围：[0, +∞)。当识别距离的值小于等于0时，会被转化为默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-gesture-pinchgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## constructor

```TypeScript
(options?: PinchGestureHandlerOptions): PinchGestureInterface
```

设置捏合手势事件。与[PinchGesture](PinchGestureInterface(value?: { fingers?: number; distance?: number))}相比，options参数新增isFingerCountLimited，表示是否检查触摸屏幕的手指数量。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureInterface-(options?: PinchGestureHandlerOptions): PinchGestureInterface--><!--Device-PinchGestureInterface-(options?: PinchGestureHandlerOptions): PinchGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PinchGestureHandlerOptions](arkts-arkui-gesture-pinchgesturehandleroptions-i.md) | 否 | 捏合手势处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-gesture-pinchgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onActionCancel

```TypeScript
onActionCancel(event: () => void): PinchGestureInterface
```

Pinch手势识别成功，接收到触摸取消事件触发的回调，不返回手势事件信息。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureInterface-onActionCancel(event: () => void): PinchGestureInterface--><!--Device-PinchGestureInterface-onActionCancel(event: () => void): PinchGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () => void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-gesture-pinchgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PinchGestureInterface
```

Pinch手势识别成功并接收到触摸取消事件的回调。与[onActionCancel](arkts-arkui-gesture-pinchgestureinterface-i.md#onactioncancel-1)相比，该回调返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureInterface-onActionCancel(event: Callback<GestureEvent>): PinchGestureInterface--><!--Device-PinchGestureInterface-onActionCancel(event: Callback<GestureEvent>): PinchGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<GestureEvent> | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-gesture-pinchgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): PinchGestureInterface
```

Pinch手势识别成功，当抬起最后一根满足手势触发条件的手指后，触发回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureInterface-onActionEnd(event: (event: GestureEvent) => void): PinchGestureInterface--><!--Device-PinchGestureInterface-onActionEnd(event: (event: GestureEvent) => void): PinchGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) => void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-gesture-pinchgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionStart

```TypeScript
onActionStart(event: (event: GestureEvent) => void): PinchGestureInterface
```

Pinch手势识别成功后触发回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureInterface-onActionStart(event: (event: GestureEvent) => void): PinchGestureInterface--><!--Device-PinchGestureInterface-onActionStart(event: (event: GestureEvent) => void): PinchGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) => void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-gesture-pinchgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionUpdate

```TypeScript
onActionUpdate(event: (event: GestureEvent) => void): PinchGestureInterface
```

Pinch手势移动过程中回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PinchGestureInterface-onActionUpdate(event: (event: GestureEvent) => void): PinchGestureInterface--><!--Device-PinchGestureInterface-onActionUpdate(event: (event: GestureEvent) => void): PinchGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) => void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PinchGestureInterface](arkts-arkui-gesture-pinchgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

