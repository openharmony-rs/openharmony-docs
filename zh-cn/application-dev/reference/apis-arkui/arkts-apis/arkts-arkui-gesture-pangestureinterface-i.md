# PanGestureInterface

滑动手势事件，当滑动的最小距离达到设定的最小值时触发滑动手势事件。

**继承/实现关系：** PanGestureInterface extends [GestureInterface<PanGestureInterface>]

**起始版本：** 7

<!--Device-unnamed-interface PanGestureInterface extends GestureInterface<PanGestureInterface>--><!--Device-unnamed-interface PanGestureInterface extends GestureInterface<PanGestureInterface>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
(value?: { fingers?: number; direction?: PanDirection; distance?: number } | PanGestureOptions): PanGestureInterface
```

创建滑动手势对象。继承自[GestureInterface<T>](arkts-arkui-gesture-gestureinterface-i.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureInterface-(value?: { fingers?: number; direction?: PanDirection; distance?: number } | PanGestureOptions): PanGestureInterface--><!--Device-PanGestureInterface-(value?: { fingers?: number; direction?: PanDirection; distance?: number } | PanGestureOptions): PanGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { fingers?: number; direction?: PanDirection; distance?: number } \| PanGestureOptions | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-gesture-pangestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## constructor

```TypeScript
(options?: PanGestureHandlerOptions): PanGestureInterface
```

创建滑动手势对象。与[PanGesture](PanGestureInterface(value?: { fingers?: number; direction?: PanDirection; distance?: number) | PanGestureOptions)}相比，options参数新增了对isFingerCountLimited和distanceMap参数，分别表示是否检查触摸屏幕的手指数量以及指定不同输入源触发滑动手势事件的最小滑动距离。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureInterface-(options?: PanGestureHandlerOptions): PanGestureInterface--><!--Device-PanGestureInterface-(options?: PanGestureHandlerOptions): PanGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PanGestureHandlerOptions](arkts-arkui-gesture-pangesturehandleroptions-i.md) | 否 | 滑动手势处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-gesture-pangestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onActionCancel

```TypeScript
onActionCancel(event: () => void): PanGestureInterface
```

设置滑动手势取消回调。滑动手势识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureInterface-onActionCancel(event: () => void): PanGestureInterface--><!--Device-PanGestureInterface-onActionCancel(event: () => void): PanGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () => void | 是 | 滑动手势取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-gesture-pangestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PanGestureInterface
```

设置滑动手势取消回调。滑动手势识别成功后，接收到触摸取消事件时触发回调。返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureInterface-onActionCancel(event: Callback<GestureEvent>): PanGestureInterface--><!--Device-PanGestureInterface-onActionCancel(event: Callback<GestureEvent>): PanGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<GestureEvent> | 是 | 滑动手势取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-gesture-pangestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): PanGestureInterface
```

设置滑动手势结束回调。滑动手势识别成功后，手指抬起时触发回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureInterface-onActionEnd(event: (event: GestureEvent) => void): PanGestureInterface--><!--Device-PanGestureInterface-onActionEnd(event: (event: GestureEvent) => void): PanGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) => void | 是 | 滑动手势结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-gesture-pangestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionStart

```TypeScript
onActionStart(event: (event: GestureEvent) => void): PanGestureInterface
```

设置滑动手势识别成功回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureInterface-onActionStart(event: (event: GestureEvent) => void): PanGestureInterface--><!--Device-PanGestureInterface-onActionStart(event: (event: GestureEvent) => void): PanGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) => void | 是 | 滑动手势识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-gesture-pangestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

## onActionUpdate

```TypeScript
onActionUpdate(event: (event: GestureEvent) => void): PanGestureInterface
```

设置滑动手势更新回调。fingerList为多根手指时，该回调监听每次只会更新一根手指的位置信息。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureInterface-onActionUpdate(event: (event: GestureEvent) => void): PanGestureInterface--><!--Device-PanGestureInterface-onActionUpdate(event: (event: GestureEvent) => void): PanGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) => void | 是 | 滑动手势更新回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGestureInterface](arkts-arkui-gesture-pangestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

