# PanGesture

滑动手势事件，当滑动的最小距离达到设定的最小值时触发滑动手势事件。

**继承/实现关系：** PanGesture extends [Gesture](arkts-arkui-gesture-gesture-c.md#Gesture)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class PanGesture--><!--Device-unnamed-export declare class PanGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate(factory: () => PanGesture, value?: PanGestureHandlerOptions | PanGestureOptions): PanGesture
```

创建滑动手势对象。继承自[Gesture](arkts-arkui-gesture-gesture-c.md#Gesture)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGesture-static $_instantiate(factory: () => PanGesture, value?: PanGestureHandlerOptions | PanGestureOptions): PanGesture--><!--Device-PanGesture-static $_instantiate(factory: () => PanGesture, value?: PanGestureHandlerOptions | PanGestureOptions): PanGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | () =&gt; PanGesture | 是 |  |
| value | [PanGestureHandlerOptions](arkts-arkui-gesture-pangesturehandleroptions-i.md) \| [PanGestureOptions](arkts-arkui-gesture-pangestureoptions-c.md) | 否 | 滑动手势处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PanGesture](arkts-arkui-gesture-pangesture-c.md) |  |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): this
```

设置滑动手势取消回调。滑动手势识别成功后，接收到触摸取消事件时触发回调。返回手势事件信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGesture-onActionCancel(event: Callback<GestureEvent>): this--><!--Device-PanGesture-onActionCancel(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 滑动手势取消回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): this
```

设置滑动手势结束回调。滑动手势识别成功后，手指抬起时触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGesture-onActionEnd(event: Callback<GestureEvent>): this--><!--Device-PanGesture-onActionEnd(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 滑动手势结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): this
```

设置滑动手势识别成功回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGesture-onActionStart(event: Callback<GestureEvent>): this--><!--Device-PanGesture-onActionStart(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 滑动手势识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): this
```

设置滑动手势更新回调。fingerList为多根手指时，该回调监听每次只会更新一根手指的位置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGesture-onActionUpdate(event: Callback<GestureEvent>): this--><!--Device-PanGesture-onActionUpdate(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 滑动手势更新回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

