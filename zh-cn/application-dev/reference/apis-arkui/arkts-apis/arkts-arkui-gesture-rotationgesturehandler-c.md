# RotationGestureHandler

旋转手势处理器对象类型。

**继承/实现关系：** RotationGestureHandler extends [GestureHandler](arkts-arkui-gesture-gesturehandler-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class RotationGestureHandler--><!--Device-unnamed-export declare class RotationGestureHandler-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: RotationGestureHandlerOptions)
```

旋转手势处理器的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGestureHandler-constructor(options?: RotationGestureHandlerOptions)--><!--Device-RotationGestureHandler-constructor(options?: RotationGestureHandlerOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RotationGestureHandlerOptions](arkts-arkui-gesture-rotationgesturehandleroptions-i.md) | 否 | 旋转手势处理器配置参数。 |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): this
```

设置旋转手势处理器取消回调。旋转手势处理器识别成功后，接收到触摸取消事件时触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGestureHandler-onActionCancel(event: Callback<GestureEvent>): this--><!--Device-RotationGestureHandler-onActionCancel(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 旋转手势处理器取消回调。返回手势事件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前旋转手势处理器对象。 |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): this
```

设置旋转手势处理器结束回调。旋转手势处理器识别成功后，手指抬起时触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGestureHandler-onActionEnd(event: Callback<GestureEvent>): this--><!--Device-RotationGestureHandler-onActionEnd(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 旋转手势处理器结束回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前旋转手势处理器对象。 |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): this
```

设置旋转手势处理器识别成功回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGestureHandler-onActionStart(event: Callback<GestureEvent>): this--><!--Device-RotationGestureHandler-onActionStart(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 旋转手势处理器识别成功回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前旋转手势处理器对象。 |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): this
```

设置旋转手势处理器更新回调。旋转手势处理器移动过程中触发回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGestureHandler-onActionUpdate(event: Callback<GestureEvent>): this--><!--Device-RotationGestureHandler-onActionUpdate(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 旋转手势处理器更新回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前旋转手势处理器对象。 |

