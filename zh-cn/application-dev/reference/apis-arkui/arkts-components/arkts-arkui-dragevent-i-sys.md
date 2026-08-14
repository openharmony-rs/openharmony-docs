# DragEvent

拖拽事件信息。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare interface DragEvent--><!--Device-unnamed-declare interface DragEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableInternalDropAnimation

```TypeScript
enableInternalDropAnimation(configuration: string): void
```

使用系统的内置动效，且该动效只有系统应用可使用。仅支持在onDrop阶段使用。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-enableInternalDropAnimation(configuration: string): void--><!--Device-DragEvent-enableInternalDropAnimation(configuration: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | string | 是 | 动效配置参数，字符串内容为json格式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [190003](../errorcode-drag-event.md#190003-当前阶段不允许操作) | Operation not allowed for current phase. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## executeFollowHandMorphDropAnimation

```TypeScript
executeFollowHandMorphDropAnimation(onAnimationFinished: Callback<void>, animationOption?: string): void
```

设置一个跟手变形落位动效执行完成后的回调，该回调由系统在拖拽框架动效结束后触发。使用callback异步回调。 > **说明：** > > 1. 该接口仅在[dragAnimationType](#dragAnimationType)设置为DragAnimationType.FOLLOW_HAND_MORPH时生效。 > > 2. 不要在回调中实现与动效无关的逻辑，避免影响执行效率。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-executeFollowHandMorphDropAnimation(onAnimationFinished: Callback<void>, animationOption?: string): void--><!--Device-DragEvent-executeFollowHandMorphDropAnimation(onAnimationFinished: Callback<void>, animationOption?: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onAnimationFinished | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 拖拽框架动效结束后触发的回调。 |
| animationOption | string | 否 | 落位动效参数。&lt;br&gt; 参数为JSON字符串格式，包含以下字段：&lt;br&gt; **CubicCurveEnable**: boolean，表示是否启用三次曲线 动画。设置为true时启用三次曲线动画，设置为false时不启用。&lt;br&gt; **SpringEnable**: boolean，表示是否启用弹簧动画。设置为true时启用弹簧动画效果，设置为false时不启用。 &lt;br&gt; **dropAnimationCurve**: number[]，表示落位动画曲线参数，其含义由SpringEnable和CubicCurveEnable决定（SpringEnable优先级更高）。当 SpringEnable为true时，数组长度为3，格式为[response, dampingRatio, blendDuration]，对应 [curves.springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md#springMotion)的弹簧曲线参数；当SpringEnable为false且CubicCurveEnable为true 时，数组长度为4，格式为[x1, y1, x2, y2]，对应[curves.cubicBezierCurve](../arkts-apis/arkts-arkui-curves-cubicbeziercurve-f.md#cubicBezierCurve)的三次贝塞尔曲线控制点 参数。&lt;br&gt; **说明：** SpringEnable优先级高于CubicCurveEnable，当两者同时为true时，以弹簧动画为准。当SpringEnable和CubicCurveEnable均未正确设置时，使用默 认弹簧动效。&lt;br&gt; **dropPosition**: number[]，落位位置坐标。数组长度为2，格式为[x, y]，单位为px，表示拖拽元素落位时的目标位置坐标，取值范围为(-∞, +∞)。&lt;br&gt; **dropSize**: number[]，落位尺寸。数组长度为2，格式为[width, height]，单位为px，表示拖拽元素落位时的目标尺寸，取值范围为(0, +∞)。 |

## dragAnimationType

```TypeScript
dragAnimationType?: DragAnimationType
```

设置拖拽动画类型。该属性仅支持在[onDragStart](arkts-arkui-commonmethod-c.md#onDragStart)阶段设置，可在[onDragStart](arkts-arkui-commonmethod-c.md#onDragStart)、 [onDragEnter](arkts-arkui-commonmethod-c.md#onDragEnter)、[onDragMove](arkts-arkui-commonmethod-c.md#onDragMove)、 [onDragLeave](arkts-arkui-commonmethod-c.md#onDragLeave)、 onDrop、 [onDragEnd](arkts-arkui-commonmethod-c.md#onDragEnd)回调中获取。 默认值为DEFAULT **系统接口：** 此接口为系统接口。

**类型：** [DragAnimationType](arkts-arkui-draganimationtype-e-sys.md)

**默认值：** DragAnimationType.DEFAULT

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-dragAnimationType?: DragAnimationType--><!--Device-DragEvent-dragAnimationType?: DragAnimationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

