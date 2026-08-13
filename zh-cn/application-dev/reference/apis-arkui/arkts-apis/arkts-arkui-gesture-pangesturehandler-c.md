# PanGestureHandler

滑动手势处理器对象类型。

**继承/实现关系：** PanGestureHandler extends [GestureHandler](arkts-arkui-gesture-gesturehandler-c.md#GestureHandler)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class PanGestureHandler--><!--Device-unnamed-export declare class PanGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: PanGestureHandlerOptions)
```

滑动手势处理器的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandler-constructor(options?: PanGestureHandlerOptions)--><!--Device-PanGestureHandler-constructor(options?: PanGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PanGestureHandlerOptions](arkts-arkui-gesture-pangesturehandleroptions-i.md) | 否 | 滑动手势处理器配置参数。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): this
```

设置滑动手势处理器取消回调。滑动手势处理器识别成功后，接收到触摸取消事件时触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandler-onActionCancel(event: Callback<GestureEvent>): this--><!--Device-PanGestureHandler-onActionCancel(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 滑动手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前滑动手势处理器对象。 |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): this
```

设置滑动手势处理器结束回调。滑动手势处理器识别成功后，手指抬起时触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandler-onActionEnd(event: Callback<GestureEvent>): this--><!--Device-PanGestureHandler-onActionEnd(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 滑动手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前滑动手势处理器对象。 |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): this
```

设置滑动手势处理器识别成功回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandler-onActionStart(event: Callback<GestureEvent>): this--><!--Device-PanGestureHandler-onActionStart(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 滑动手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前滑动手势处理器对象。 |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): this
```

设置滑动手势处理器更新回调。滑动手势处理器移动过程中触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PanGestureHandler-onActionUpdate(event: Callback<GestureEvent>): this--><!--Device-PanGestureHandler-onActionUpdate(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 滑动手势处理器更新回调。&lt;br/&gt;fingerList为多根手指时，该回调监听每次只会更新一根手指的位置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前滑动手势处理器对象。 |

