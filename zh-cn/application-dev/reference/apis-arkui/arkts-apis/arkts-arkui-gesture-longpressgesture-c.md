# LongPressGesture

用于触发长按手势事件，触发长按手势的最少手指数为1，默认最短长按时间为500毫秒。可配置duration参数控制最短长按时长。 > **说明：** > > 部分设备会优先响应系统的双指长按手势，导致应用的双指长按手势不生效。

**继承/实现关系：** LongPressGesture extends [Gesture](arkts-arkui-gesture-gesture-c.md#Gesture)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class LongPressGesture--><!--Device-unnamed-export declare class LongPressGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate(factory: () => LongPressGesture, value?: LongPressGestureHandlerOptions): LongPressGesture
```

创建长按手势对象。 当组件默认支持可拖拽时，如Text、TextInput、TextArea、HyperLink、Image和RichEditor等组件。长按手势与拖拽会出现冲突，事件优先级如下： 当长按触发时间小于500毫秒时，系统优先响应长按事件而非拖拽事件。 当长按触发时间达到或超过500毫秒时，系统优先响应拖拽事件而非长按事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGesture-static $_instantiate(factory: () => LongPressGesture, value?: LongPressGestureHandlerOptions): LongPressGesture--><!--Device-LongPressGesture-static $_instantiate(factory: () => LongPressGesture, value?: LongPressGestureHandlerOptions): LongPressGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | () =&gt; LongPressGesture | 是 |  |
| value | [LongPressGestureHandlerOptions](arkts-arkui-gesture-longpressgesturehandleroptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LongPressGesture](arkts-arkui-gesture-longpressgesture-c.md) |  |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): this
```

设置长按手势识别成功回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGesture-onAction(event: Callback<GestureEvent>): this--><!--Device-LongPressGesture-onAction(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 长按手势识别成功回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): this
```

设置长按手势取消回调。长按手势识别成功后，接收到触摸取消事件时触发回调。不返回手势事件信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGesture-onActionCancel(event: Callback<GestureEvent>): this--><!--Device-LongPressGesture-onActionCancel(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 长按手势取消回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): this
```

设置长按手势结束回调。长按手势识别成功后，最后一根手指抬起时触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LongPressGesture-onActionEnd(event: Callback<GestureEvent>): this--><!--Device-LongPressGesture-onActionEnd(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 长按手势结束回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

