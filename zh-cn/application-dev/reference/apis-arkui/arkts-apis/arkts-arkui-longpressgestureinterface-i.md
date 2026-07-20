# LongPressGestureInterface

用于触发长按手势事件，触发长按手势的最少手指数为1，默认最短长按时间为500毫秒。可配置duration参数控制最短长按时长。

> **说明：**  
>  
> 从API version 18开始，部分设备会优先响应系统的双指长按手势，导致应用的双指长按手势不生效。

**继承/实现关系：** LongPressGestureInterface extends [GestureInterface<LongPressGestureInterface>](GestureInterface<LongPressGestureInterface>)

**起始版本：** 7

<!--Device-unnamed-interface LongPressGestureInterface extends GestureInterface<LongPressGestureInterface>--><!--Device-unnamed-interface LongPressGestureInterface extends GestureInterface<LongPressGestureInterface>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
(value?: { fingers?: number; repeat?: boolean; duration?: number }): LongPressGestureInterface
```

创建长按手势对象。继承自[GestureInterface<T>](arkts-arkui-gestureinterface-i.md)。

当组件默认支持可拖拽时，如Text、TextInput、TextArea、HyperLink、Image和RichEditor等组件。长按手势与拖拽会出现冲突，事件优先级如下：

当长按触发时间小于500毫秒时，系统优先响应长按事件而非拖拽事件。

当长按触发时间达到或超过500毫秒时，系统优先响应拖拽事件而非长按事件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressGestureInterface-(value?: { fingers?: number; repeat?: boolean; duration?: number }): LongPressGestureInterface--><!--Device-LongPressGestureInterface-(value?: { fingers?: number; repeat?: boolean; duration?: number }): LongPressGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | { fingers?: number; repeat?: boolean; duration?: number } | 否 | 设置长按手势参数。<br> - fingers：触发长按的最少手指数，最小值为1，&nbsp;最大值为10。<br/>默认值：1<br> - repeat：是否连续触发事件回调。true表示连续触发事件回调，false表示不连续触发事件回调。<br/>默认值：false<br> - duration：触发长按的最短时间，单位为毫秒（ms）。<br/>默认值：500 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

<a id="constructor-1"></a>
## constructor

```TypeScript
(options?: LongPressGestureHandlerOptions): LongPressGestureInterface
```

创建长按手势对象。与[LongPressGesture](arkts-arkui-longpressgestureinterface-i.md))}相比，options参数新增了对isFingerCountLimited参数，表示是否检查触摸屏幕的手指数量。

当组件默认支持可拖拽时，如Text、TextInput、TextArea、HyperLink、Image和RichEditor等组件。长按手势与拖拽会出现冲突，事件优先级如下：

当长按触发时间小于500毫秒时，系统优先响应长按事件而非拖拽事件。

当长按触发时间达到或超过500毫秒时，系统优先响应拖拽事件而非长按事件。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressGestureInterface-(options?: LongPressGestureHandlerOptions): LongPressGestureInterface--><!--Device-LongPressGestureInterface-(options?: LongPressGestureHandlerOptions): LongPressGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [LongPressGestureHandlerOptions](arkts-arkui-longpressgesturehandleroptions-i.md) | 否 | 长按手势处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="onaction"></a>
## onAction

```TypeScript
onAction(event: (event: GestureEvent) => void): LongPressGestureInterface
```

设置长按手势识别成功回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressGestureInterface-onAction(event: (event: GestureEvent) => void): LongPressGestureInterface--><!--Device-LongPressGestureInterface-onAction(event: (event: GestureEvent) => void): LongPressGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 长按手势识别成功回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

<a id="onactioncancel"></a>
## onActionCancel

```TypeScript
onActionCancel(event: () => void): LongPressGestureInterface
```

设置长按手势取消回调。长按手势识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressGestureInterface-onActionCancel(event: () => void): LongPressGestureInterface--><!--Device-LongPressGestureInterface-onActionCancel(event: () => void): LongPressGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 长按手势取消回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

<a id="onactioncancel-1"></a>
## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): LongPressGestureInterface
```

设置长按手势取消回调。长按手势识别成功后，接收到触摸取消事件时触发回调。返回手势事件信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressGestureInterface-onActionCancel(event: Callback<GestureEvent>): LongPressGestureInterface--><!--Device-LongPressGestureInterface-onActionCancel(event: Callback<GestureEvent>): LongPressGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GestureEvent&gt; | 是 | 长按手势取消回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

<a id="onactionend"></a>
## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): LongPressGestureInterface
```

设置长按手势结束回调。长按手势识别成功后，最后一根手指抬起时触发回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LongPressGestureInterface-onActionEnd(event: (event: GestureEvent) => void): LongPressGestureInterface--><!--Device-LongPressGestureInterface-onActionEnd(event: (event: GestureEvent) => void): LongPressGestureInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | 是 | 长按手势结束回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-longpressgestureinterface-i.md) | @syscap SystemCapability.ArkUI.ArkUI.Full@crossplatform |

