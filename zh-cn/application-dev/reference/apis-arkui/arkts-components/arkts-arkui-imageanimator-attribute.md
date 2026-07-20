# ImageAnimator属性/事件

除支持[通用属性](./common)外，还支持以下属性：

除支持[通用事件](./common)外，还支持以下事件：

**继承/实现关系：** ImageAnimatorAttribute extends [CommonMethod<ImageAnimatorAttribute>](CommonMethod<ImageAnimatorAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>--><!--Device-unnamed-declare class ImageAnimatorAttribute extends CommonMethod<ImageAnimatorAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="duration"></a>
## duration

```TypeScript
duration(value: number)
```

设置播放时长。当Images中任意一帧图片设置了单独的duration后，该属性设置无效。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-duration(value: number): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-duration(value: number): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 播放时长。<br/>value为0时，不播放图片。<br/>value平均分配给单张图片的播放时长小于一帧时间，将导致播放异常。<br/>设置为负数时，取默认值。<br/>value的改变只会在下一次循环开始时生效。<br/>单位：毫秒<br/>默认值：1000ms |

<a id="fillmode"></a>
## fillMode

```TypeScript
fillMode(value: FillMode)
```

设置当前播放方向下，动画开始前和结束后的状态。动画结束后的状态由fillMode和reverse属性共同决定。例如，fillMode为Forwards表示停止时维持动画最后一个关键帧的状态，若reverse为false则维持正播的最后一帧，即最后一张图，若reverse为true则维持逆播的最后一帧，即第一张图。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-fillMode(value: FillMode): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-fillMode(value: FillMode): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FillMode](../arkts-apis/arkts-arkui-fillmode-e.md) | 是 | 当前播放方向下，动画开始前和结束后的状态。<br/>默认值：FillMode.Forwards |

<a id="fixedsize"></a>
## fixedSize

```TypeScript
fixedSize(value: boolean)
```

设置图片大小是否固定为组件大小。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-fixedSize(value: boolean): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-fixedSize(value: boolean): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置图片大小是否固定为组件大小。 true表示图片大小与组件大小一致，此时设置图片的width 、height 、top 和left属性无效。false表示每一张图片的width 、height 、top和left属性都要单独设置。图片宽高与组件宽高不一致时，图片不会被拉伸。<br/>默认值：true |

<a id="images"></a>
## images

```TypeScript
images(value: Array<ImageFrameInfo>)
```

设置图片帧信息集合。不支持动态更新，动态更新可能会导致不可预期的行为。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-images(value: Array<ImageFrameInfo>): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-images(value: Array<ImageFrameInfo>): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;ImageFrameInfo&gt; | 是 | 设置图片帧信息集合。每一帧的帧信息(ImageFrameInfo)包含图片路径、图片大小、图片位置和图片播放时长信息，详见[ImageFrameInfo](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-imageanimator.md#imageframeinfo对象说明)对象说明。<br/>默认值：[] <br/> **说明：** 传入数组的内容过大时，内存占用会随之升高。此内存由开发者自行控制。因此，开发者在传入数据前，请充分评估内存消耗情况，以避免内存不足等问题。 |

<a id="iterations"></a>
## iterations

```TypeScript
iterations(value: number)
```

设置播放次数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAnimatorAttribute-iterations(value: number): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-iterations(value: number): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 默认播放一次，设置为-1时表示无限次播放，设置为小于-1的负数时取默认值。设置为浮点数时，数值向下取整。<br/>默认值：1 |

<a id="monitorinvisiblearea"></a>
## monitorInvisibleArea

```TypeScript
monitorInvisibleArea(monitorInvisibleArea: boolean) : ImageAnimatorAttribute
```

设置组件是否通过系统[onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange-1)的可见性判定，控制组件的暂停和播放。

**起始版本：** 17

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本17开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAnimatorAttribute-monitorInvisibleArea(monitorInvisibleArea: boolean) : ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-monitorInvisibleArea(monitorInvisibleArea: boolean) : ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| monitorInvisibleArea | boolean | 是 | 当设置为true时，组件将基于系统的[onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange-1)可见性判定，控制组件的暂停和播放。<br/> 当组件的运行状态为[AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md)的Running时，若判定组件不可见，则自动执行暂停操作；若判定为可见，则自动恢复播放。<br/>当设置为false时，组件的暂停和播放不受到onVisibleAreaChange影响。<br/>默认值：false<br/> **说明：** <br/>当该属性由true动态修改为false时，组件将依据当前的[AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md)状态进行处理。<br/> 例如，若当前状态为Running且因[onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange-1)的不可见回调暂停，则在属性由true改为false后，组件会从上次暂停的位置重新开始播放。<br/>由该属性导致的不可见暂停和可见暂停操作不会改变用户设置的[state](ImageAnimatorAttribute#state)值。 |

<a id="oncancel"></a>
## onCancel

```TypeScript
onCancel(event: () => void)
```

状态回调，动画返回最初状态时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-onCancel(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onCancel(event: () => void): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 状态回调，动画返回最初状态时触发。 |

<a id="onfinish"></a>
## onFinish

```TypeScript
onFinish(event: () => void)
```

状态回调，动画播放完成时或者停止播放时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-onFinish(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onFinish(event: () => void): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 状态回调，动画播放完成时或者停止播放时触发。 |

<a id="onpause"></a>
## onPause

```TypeScript
onPause(event: () => void)
```

状态回调，动画暂停播放时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-onPause(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onPause(event: () => void): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 状态回调，动画暂停播放时触发。 |

<a id="onrepeat"></a>
## onRepeat

```TypeScript
onRepeat(event: () => void)
```

状态回调，动画重复播放时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ImageAnimatorAttribute-onRepeat(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onRepeat(event: () => void): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 状态回调，动画重复播放时触发。 |

<a id="onstart"></a>
## onStart

```TypeScript
onStart(event: () => void)
```

状态回调，动画开始播放时触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-onStart(event: () => void): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-onStart(event: () => void): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 状态回调，动画开始播放时触发。 |

<a id="predecode"></a>
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

<!--Device-ImageAnimatorAttribute-preDecode(value: number): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-preDecode(value: number): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 预解码的图片数量。例如，设置为2时，播放当前页时会提前加载后面两张图片至缓存，以提升性能。<br/>默认值：0 |

<a id="reverse"></a>
## reverse

```TypeScript
reverse(value: boolean)
```

设置播放方向。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-reverse(value: boolean): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-reverse(value: boolean): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 播放方向。<br/>false表示从第1张图片播放到最后1张图片，true表示从最后1张图片播放到第1张图片。<br/>默认值：false |

<a id="state"></a>
## state

```TypeScript
state(value: AnimationStatus)
```

控制播放状态。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-ImageAnimatorAttribute-state(value: AnimationStatus): ImageAnimatorAttribute--><!--Device-ImageAnimatorAttribute-state(value: AnimationStatus): ImageAnimatorAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [AnimationStatus](../arkts-apis/arkts-arkui-animationstatus-e.md) | 是 | 默认为初始状态，用于控制播放状态。<br/>默认值：AnimationStatus.Initial |

