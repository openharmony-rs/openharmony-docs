# RotationGestureInterface

用于触发旋转手势，最少需要2指，最多5指，最小改变度数为1度。该手势不支持通过触控板双指旋转操作触发。

**继承/实现关系：** RotationGestureInterface extends [GestureInterface<RotationGestureInterface>](GestureInterface<RotationGestureInterface>)

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
(value?: { fingers?: number; angle?: number }): RotationGestureInterface
```

继承自[GestureInterface<T>](arkts-arkui-gestureinterface-i.md)，设置旋转手势事件。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { fingers?: number; angle?: number } | 否 | 设置旋转手势事件参数。<br> - fingers：触发旋转手势所需的最少手指数，&nbsp;最小为2指，最大为5指。<br/>默认值：2 <br/>取值范围：[2, 5]。当设置的值小于2或大于5时，会被转化为默认值。<br/>触发手势时手指数量可以多于fingers参数值，但仅最先落下的两指参与手势计算。<br> - angle：触发旋转手势所需的最小角度变化，单位为deg。<br/>默认值：1 <br/>**说明：** <br/>当改变度数的值小于等于0或大于360时，会被转化为默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## constructor

```TypeScript
(options?: RotationGestureHandlerOptions): RotationGestureInterface
```

设置旋转手势事件。与[RotationGesture](RotationGestureInterface(value?: { fingers?: number; angle?: number ))}相比，
options参数新增了isFingerCountLimited参数，表示是否检查触摸屏幕的手指数量。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RotationGestureHandlerOptions | 否 | 旋转手势处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onActionCancel

```TypeScript
onActionCancel(event: () => void): RotationGestureInterface
```

Rotation手势识别成功，接收到触摸取消事件触发的回调。该回调不返回手势事件信息。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): RotationGestureInterface
```

Rotation手势识别成功，接收到触摸取消事件触发的回调。与[onActionCancel](arkts-arkui-rotationgestureinterface-i.md#onactioncancel-1)相
比，该回调返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback&lt;GestureEvent&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): RotationGestureInterface
```

Rotation手势识别成功，当抬起最后一根满足手势触发条件的手指后触发的回调。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionStart

```TypeScript
onActionStart(event: (event: GestureEvent) => void): RotationGestureInterface
```

Rotation手势识别成功后触发的回调。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionUpdate

```TypeScript
onActionUpdate(event: (event: GestureEvent) => void): RotationGestureInterface
```

Rotation手势移动过程中触发的回调。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RotationGestureInterface | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

