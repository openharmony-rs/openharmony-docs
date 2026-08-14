# RotationGesture

用于触发旋转手势，最少需要2指，最多5指，最小改变度数为1度。该手势不支持通过触控板双指旋转操作触发。 > **说明：** > > - 从API version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

**继承/实现关系：** RotationGesture extends [Gesture](arkts-arkui-gesture-gesture-c.md#Gesture)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class RotationGesture--><!--Device-unnamed-export declare class RotationGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate(factory: () => RotationGesture, value?: RotationGestureHandlerOptions): RotationGesture
```

设置旋转手势事件。继承自[Gesture](arkts-arkui-gesture-gesture-c.md#Gesture)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGesture-static $_instantiate(factory: () => RotationGesture, value?: RotationGestureHandlerOptions): RotationGesture--><!--Device-RotationGesture-static $_instantiate(factory: () => RotationGesture, value?: RotationGestureHandlerOptions): RotationGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | () =&gt; RotationGesture | 是 |  |
| value | [RotationGestureHandlerOptions](arkts-arkui-gesture-rotationgesturehandleroptions-i.md) | 否 | 旋转手势处理器配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RotationGesture](arkts-arkui-gesture-rotationgesture-c.md) |  |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): this
```

Rotation手势识别成功，接收到触摸取消事件触发的回调。与[onActionCancel](#onActionCancel)相比，该回调返回手势事件信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGesture-onActionCancel(event: Callback<GestureEvent>): this--><!--Device-RotationGesture-onActionCancel(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): this
```

Rotation手势识别成功，当抬起最后一根满足手势触发条件的手指后触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGesture-onActionEnd(event: Callback<GestureEvent>): this--><!--Device-RotationGesture-onActionEnd(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): this
```

Rotation手势识别成功后触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGesture-onActionStart(event: Callback<GestureEvent>): this--><!--Device-RotationGesture-onActionStart(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): this
```

Rotation手势移动过程中触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGesture-onActionUpdate(event: Callback<GestureEvent>): this--><!--Device-RotationGesture-onActionUpdate(event: Callback<GestureEvent>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gesture-gestureevent-i.md)&gt; | 是 | 手势事件回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

