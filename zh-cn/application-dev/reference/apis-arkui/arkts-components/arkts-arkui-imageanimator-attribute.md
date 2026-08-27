# ImageAnimator属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件外，还支持以下事件：

**继承/实现关系：** ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## duration

```TypeScript
duration(value: number)
```

设置播放时长。当[images](#images)中任意一帧图片设置了单独的duration后，该属性设置无效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 播放时长。value为0时，不播放图片。value平均分配给单张图片的播放时长小于一帧时间，将导致播放异常。设置为负数时，取默认值1000毫秒。value的改变只会在下一次循环开始时生效。单位：毫秒默认值：1000 |

## fillMode

```TypeScript
fillMode(value: FillMode)
```

设置当前播放方向下，动画开始前和结束后的状态。动画结束后的状态由fillMode和reverse属性共同决定。例如，fillMode为Forwards表示停止时维持动画最后一个关键帧的状态，若reverse为false则维持正播的 最后一帧，即最后一张图，若reverse为true则维持逆播的最后一帧，即第一张图。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FillMode](../arkts-apis/arkts-arkui-fillmode-e.md) | 是 | 当前播放方向下，动画开始前和结束后的状态。默认值：FillMode.Forwards |

## fixedSize

```TypeScript
fixedSize(value: boolean)
```

设置图片大小是否固定为组件大小。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置图片大小是否固定为组件大小。 true表示图片大小与组件大小一致，此时设置图片的width 、height 、top 和left属性无效。false表示每一张图片的 width 、height 、top和left属性都要单独设置。图片宽高与组件宽高不一致时，图片不会被拉伸。默认值：true |

## images

```TypeScript
images(value: Array<ImageFrameInfo>)
```

设置图片帧信息集合。不支持动态更新，否则可能导致显示错乱、帧切换异常或内存上涨等问题（该属性按非动态更新设计，运行时修改不保证生效）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[ImageFrameInfo](arkts-arkui-imageframeinfo-i.md)&gt; | 是 | 设置图片帧信息集合。每一帧的帧信息(ImageFrameInfo)包含图片路径、图片大小、图片位置和图片播放时长信息，详见 [ImageFrameInfo](arkts-arkui-imageframeinfo-i.md) 。默认值：[]    **说明：** 传入数组的内容过大时，内存占用会随之升高。此内存由开发者自行控制。因此，开发者在传入数据 前，请充分评估内存消耗情况，以避免内存不足等问题。 |

## iterations

```TypeScript
iterations(value: number)
```

设置播放次数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 默认播放一次；-1表示无限次播放，小于-1的负数取默认值1；浮点数向下取整。默认值：1 |

## monitorInvisibleArea

```TypeScript
monitorInvisibleArea(monitorInvisibleArea: boolean) : ImageAnimatorAttribute
```

设置组件是否通过系统 [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) 的可见性判定，控制组件的暂停和播放。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitorInvisibleArea | boolean | 是 | true时，组件基于系统的 [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) 可见性判定控制暂停和播放；当组件的运行状态为[AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md)的Running时，若判定不可见则自动暂停，若判定可见则自动恢复播放。false时，组件的暂停和播 放不受onVisibleAreaChange影响。默认值：false    **说明：** 当该属性由true动态修改为false时，组件将依据当前的 [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md)状态进行处理。例如，若当前状态为Running且因 [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) 的不可见回调暂停，则在属性由true改为false后，组件会从上次暂停的位置重新开始播放。由该属性导致的不可见暂停和可见播放操作不会改变用户设置的 [state](#state)值。 |

## onCancel

```TypeScript
onCancel(event: () => void)
```

状态回调，动画取消时触发。当state被设置为[AnimationStatus.Initial](../arkts-apis/arkts-arkui-animationstatus-e.md)时触发；触发后图片显示回到第一帧（正播）或最后一帧（逆播）。与 [onFinish](#onfinish)的区别在于：onCancel对应回到Initial初始状态，onFinish对应动画自然结束或停止（Stopped）状态。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 状态回调，动画取消时触发。当state被设置为AnimationStatus.Initial时触发；触发后图片显示回到第一帧（正播）或最后一帧（逆播）。 |

## onFinish

```TypeScript
onFinish(event: () => void)
```

状态回调，动画播放完成时（iterations设置的轮次全部播完且动画自然结束）或者停止播放时（state被切换为[AnimationStatus.Stopped](../arkts-apis/arkts-arkui-animationstatus-e.md)）触发。当动画处于 [AnimationStatus.Initial](../arkts-apis/arkts-arkui-animationstatus-e.md)状态时返回初始状态不会触发该事件，对应触发的是onCancel。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 状态回调，动画播放完成时（iterations轮次全部播完且动画自然结束）或者停止播放时（state被切换为AnimationStatus.Stopped）触发。 |

## onPause

```TypeScript
onPause(event: () => void)
```

状态回调，动画暂停播放时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 状态回调，动画暂停播放时触发。 |

## onRepeat

```TypeScript
onRepeat(event: () => void)
```

状态回调，动画重复播放时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 状态回调，动画重复播放时触发。 |

## onStart

```TypeScript
onStart(event: () => void)
```

状态回调，动画开始播放时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () = & gt; void | 是 | 状态回调，动画开始播放时触发。 |

## preDecode

```TypeScript
preDecode(value: number)
```

设置预解码的图片数量。

> **说明：**
> 
> 从API version 7开始支持，从API version 9开始废弃。当前无可替代接口。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 预解码的图片数量。例如，设置为2时，播放当前帧时会提前加载后面两张图片至缓存，以提升性能。默认值：0 |

## reverse

```TypeScript
reverse(value: boolean)
```

设置播放方向。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 播放方向。false表示从第1张图片播放到最后1张图片，true表示从最后1张图片播放到第1张图片。动画结束后保留哪一帧还与 [fillMode](#fillmode)属性有关，详见fillMode说明。默认值：false |

## state

```TypeScript
state(value: AnimationStatus)
```

控制播放状态。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md) | 是 | 用于控制播放状态。默认值：AnimationStatus.Initial |
