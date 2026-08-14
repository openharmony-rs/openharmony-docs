# ScrollableCommonMethod

CommonScrollableMethod

**继承/实现关系：** ScrollableCommonMethod extends CommonMethod<T>

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare class ScrollableCommonMethod--><!--Device-unnamed-declare class ScrollableCommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoAdjustScrollBarMargin

```TypeScript
autoAdjustScrollBarMargin(enable: boolean | undefined): T
```

设置滚动条是否自动调整边距。默认不会自动调整边距。 打开滚动条自动边距调整后，滚动条滚动方向上会避让组件[padding](arkts-arkui-commonmethod-c.md#padding)、 [safeAreaPadding](arkts-arkui-commonmethod-c.md#safeAreaPadding)、 [contentStartOffset](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#contentstartoffset22) /[contentEndOffset](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#contentendoffset22)区 域。如果设置了 [scrollBarMargin](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#scrollbarmargin20)属性，则自 动调整边距不生效。当[padding](arkts-arkui-commonmethod-c.md#padding)、[safeAreaPadding](arkts-arkui-commonmethod-c.md#safeAreaPadding)、 [contentStartOffset](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#contentstartoffset22) 、[contentEndOffset](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#contentendoffset22)在水 平方向上的总和大于组件的宽度，或在垂直方向上的总和大于组件的高度时，滚动条不显示。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-autoAdjustScrollBarMargin(enable: boolean | undefined): T--><!--Device-ScrollableCommonMethod-autoAdjustScrollBarMargin(enable: boolean | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 | 是否自动调整边距。 &lt;br&gt;true：自动调整边距。 &lt;br&gt;false：不自动调整边距。 &lt;br&gt;undefined：不自动调整边距。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## backToTop

```TypeScript
backToTop(backToTop: boolean): T
```

设置滚动组件是否支持点击状态栏回到顶部。 支持当前页面的滚动组件收到点击状态栏事件后，通过动画回到顶部。点击状态栏后，后台应用的滚动组件不受影响，不做回到顶部的动作。本属性不受 [enableScrollInteraction](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#enablescrollinteraction11) 设置的影响。

**起始版本：** 15

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为15。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-backToTop(backToTop: boolean): T--><!--Device-ScrollableCommonMethod-backToTop(backToTop: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| backToTop | boolean | 是 | 设置滚动组件是否支持点击状态栏回到顶部。设置为true支持点击状态栏通过动画回到顶部，设置为false不支持点击状态栏回到顶部。&lt;br/&gt;默认值：&lt;br/&gt;API version 18之前：false。 &lt;br/&gt;API version 18及以后：滚动方向是水平方向时为false，是垂直方向时为true。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## clipContent

```TypeScript
clipContent(clip: ContentClipMode | RectShape): T
```

设置滚动容器的内容层裁剪区域。 从API版本26.0.0开始，内容层裁剪区域内的子组件支持正常显示。API版本26.0.0以前的版本，当List、Grid和WaterFlow组件的内容层裁剪区域大于组件自身时，完全在组件区域外但在裁剪区域内的子组件默认不会显示。 若需要显示，可将组件的cachedCount属性的show参数设置为true。但由于cachedCount属性设置的预加载子组件仅在空闲时隙执行，在组件大小变化、数据更新等场景下可能存在更新不及时导致闪烁的问题。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-clipContent(clip: ContentClipMode | RectShape): T--><!--Device-ScrollableCommonMethod-clipContent(clip: ContentClipMode | RectShape): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| clip | [ContentClipMode](arkts-arkui-contentclipmode-e.md) \| [RectShape](arkts-arkui-rectshape-t.md) | 是 | 裁剪只针对滚动容器的内容，即其子节点，背景不受影响。通过RectShape传入自定义矩形区域时仅支持设置宽高和相对于组件左上角的 [offset](../arkts-apis/arkts-arkui-arkui-shape-commonshapemethod-c.md#offset)，不支持圆角。 &lt;br&gt;默认值：Grid、Scroll的默认值为ContentClipMode.BOUNDARY，List、WaterFlow的默认值为ContentClipMode.CONTENT_ONLY。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## contentEndOffset

```TypeScript
contentEndOffset(offset: number | Resource): T
```

设置内容区末尾偏移量。滚动组件滚动到末尾位置时，内容与组件显示区域边界保留指定距离。 contentStartOffset + contentEndOffset超过滚动组件内容区长度后contentStartOffset和contentEndOffset会置0。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-contentEndOffset(offset: number | Resource): T--><!--Device-ScrollableCommonMethod-contentEndOffset(offset: number | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number \| Resource | 是 | 内容区末尾偏移量。&lt;br/&gt;默认值：0&lt;br/&gt;单位：vp &lt;br/&gt;取值范围： 0, +∞)&lt;br/&gt;设置异常值如负数、非数字Resource时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## contentStartOffset

```TypeScript
contentStartOffset(offset: number | Resource): T
```

设置内容区域起始偏移量。滚动组件滚动到起始位置时，内容与组件显示区域边界保留指定距离。 contentStartOffset + contentEndOffset超过滚动组件内容区长度后contentStartOffset和contentEndOffset会置0。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-contentStartOffset(offset: number | Resource): T--><!--Device-ScrollableCommonMethod-contentStartOffset(offset: number | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number \| Resource | 是 | 内容区域起始偏移量。&lt;br/&gt;默认值：0&lt;br/&gt;单位：vp &lt;br/&gt;取值范围： [0, +∞)&lt;br/&gt;设置异常值如负数、非数字Resource时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): T
```

设置表冠响应事件灵敏度。 组件收到[表冠事件的前提是该组件获焦，焦点控制可以通过[focusable](arkts-arkui-commonmethod-c.md#focusable)、 [defaultFocus](arkts-arkui-commonmethod-c.md#defaultFocus)、[focusOnTouch](arkts-arkui-commonmethod-c.md#focusOnTouch)进行管理。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): T--><!--Device-ScrollableCommonMethod-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-optional-t.md)&lt;CrownSensitivity&gt; | 是 | 表冠响应灵敏度。CrownSensitivity.LOW表示低灵敏度，滚动响应较慢； CrownSensitivity.MEDIUM表示中灵敏度，滚动响应适中；CrownSensitivity.HIGH表示高灵敏度，滚动响应较快。&lt;br/&gt;默认值：CrownSensitivity.MEDIUM，响应速度适 中。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## edgeEffect

```TypeScript
edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T
```

设置边缘滑动效果。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T--><!--Device-ScrollableCommonMethod-edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| edgeEffect | EdgeEffect | 是 | 滚动组件的边缘滑动效果，支持弹簧效果和阴影效果。&lt;br/&gt;默认值：Grid、Scroll、WaterFlow组件默认EdgeEffect.None，List组件 默认EdgeEffect.Spring。 |
| options | [EdgeEffectOptions](arkts-arkui-edgeeffectoptions-i.md) | 否 | 组件内容大小小于组件自身时是否开启滑动效果。从API version 18开始，支持设置边缘效果生效的边缘。设置为{ alwaysEnabled: true }会开启滑动效果，{ alwaysEnabled: false }不开启。&lt;br/&gt;默认值：&lt;br/&gt;List、Grid、WaterFlow组件默认{ alwaysEnabled: false }，Scroll组 件默认{ alwaysEnabled: true }。从API version 18开始，默认增加effectEdge字段，取值为EffectEdge.START \| EffectEdge.END。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean): T
```

设置是否支持滚动手势。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-enableScrollInteraction(value: boolean): T--><!--Device-ScrollableCommonMethod-enableScrollInteraction(value: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持手指或鼠标滚动手势。设置为true时支持，设置为false时不支持，但不影响控制器Scroller的滚动接口和 [backToTop](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#backtotop15)属性。&lt;br/&gt;默认值： true |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## enableScrollWithMouse

```TypeScript
enableScrollWithMouse(enabled: boolean | undefined): T
```

设置是否支持鼠标左键按下拖动滚动。未通过该接口设置时，默认不支持鼠标左键按下拖动滚动。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-enableScrollWithMouse(enabled: boolean | undefined): T--><!--Device-ScrollableCommonMethod-enableScrollWithMouse(enabled: boolean | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | 是否支持鼠标左键按下拖动滚动。&lt;br/&gt;true：支持鼠标左键按下拖动滚动。&lt;br/&gt;false：不支持鼠标左键按下拖动滚动。&lt;br/&gt; undefined：不支持鼠标左键按下拖动滚动。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## fadingEdge

```TypeScript
fadingEdge(enabled: Optional<boolean>, options?: FadingEdgeOptions): T
```

设置是否开启边缘渐隐效果及设置边缘渐隐长度。 > **说明：** > > fadingEdge是通过设置[overlay](arkts-arkui-commonmethod-c.md#overlay)属性和 > [blendMode](arkts-arkui-commonmethod-c.md#blendMode)属性（参数值为BlendMode.SRC_OVER， > BlendApplyType.OFFSCREEN）实现的。当fadingEdge生效时，会覆盖原组件的.overlay()属性和.blendMode()属性，并将导致当前组件和其子组件需要截屏的接口无法截取到正确的画面。需要截 > 屏的接口有：[blur](arkts-arkui-commonmethod-c.md#blur)、 > [linearGradientBlur](arkts-arkui-commonmethod-c.md#linearGradientBlur)、 > [brightness](arkts-arkui-commonmethod-c.md#brightness)、[visualEffect](arkts-arkui-commonmethod-c.md#visualEffect)、 > [grayscale](arkts-arkui-commonmethod-c.md#grayscale)、[saturate](arkts-arkui-commonmethod-c.md#saturate)、 > [contrast](arkts-arkui-commonmethod-c.md#contrast)、 > [invert](arkts-arkui-commonmethod-c.md#invert)、 > [sepia](arkts-arkui-commonmethod-c.md#sepia)、 > [hueRotate](arkts-arkui-commonmethod-c.md#hueRotate)、 > [colorBlend](arkts-arkui-commonmethod-c.md#colorBlend)、 > [lightUpEffect](arkts-arkui-commonmethod-c.md#lightUpEffect)、 > [pixelStretchEffect](arkts-arkui-commonmethod-c.md#pixelStretchEffect)、 > [blendMode](arkts-arkui-commonmethod-c.md#blendMode)、 > [backgroundBrightness](arkts-arkui-commonmethod-c.md#backgroundBrightness)。 > > fadingEdge生效时，建议不在设置fadingEdge属性的组件上设置[background](arkts-arkui-commonmethod-c.md#background)相关属性，会影响渐隐的显示效果。 > > fadingEdge生效时，建议不在设置fadingEdge属性的组件以及其子组件上设置[systemMaterial](arkts-arkui-commonmethod-c.md#systemMaterial)相关属性，会影响系统材质的显示效果， > 导致材质效果与预期效果不一致。 > > fadingEdge生效时，设置fadingEdge属性的组件会裁剪到边界，在该组件上设置[clip](arkts-arkui-commonmethod-c.md#clip)属性为false不生效。

**起始版本：** 14

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为14。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-fadingEdge(enabled: Optional<boolean>, options?: FadingEdgeOptions): T--><!--Device-ScrollableCommonMethod-fadingEdge(enabled: Optional<boolean>, options?: FadingEdgeOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启边缘渐隐效果。设置为true时开启边缘渐隐效果，设置为false时不开启边缘渐隐效果。&lt;br/&gt;默认值：false |
| options | [FadingEdgeOptions](arkts-arkui-fadingedgeoptions-i.md) | 否 | 边缘渐隐参数对象。可以通过该对象定义边缘渐隐效果属性，比如设置渐隐长度。&lt;br/&gt;如果设置小于0的值或undefined或者不设置则取默认值，默认长 度为32vp。&lt;br/&gt;如果设置的长度超过容器高度的一半时，渐隐长度取容器高度的一半。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## flingSpeedLimit

```TypeScript
flingSpeedLimit(speedLimit: number): T
```

限制跟手滑动结束后，惯性动效开始时的最大初始速度。 > **说明：** > > - 惯性动效是指手指快速滑动并离开屏幕后，滚动内容继续滚动并逐渐减速停止的效果，也称为惯性滚动。 > > - 惯性动效触发场景包括：惯性手指快速滑动并离手时，或调用fling方法。 > > - 使用鼠标滚轮、键盘方向键方式滚动，或通过scrollTo等方法直接滚动到指定位置，不会产生惯性动效。 > > - 如果惯性动效通过fling方法触发，则flingSpeedLimit设置不生效。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-flingSpeedLimit(speedLimit: number): T--><!--Device-ScrollableCommonMethod-flingSpeedLimit(speedLimit: number): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| speedLimit | number | 是 | 惯性动效开始时的最大初始速度。&lt;br/&gt;默认值：9000&lt;br/&gt;单位：vp/s &lt;br/&gt;取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## friction

```TypeScript
friction(value: number | Resource): T
```

设置摩擦系数，手动划动滚动区域时生效，仅影响惯性滚动过程，对惯性滚动过程中嵌套滚动组件间的联动效果（如List组件的链式动效chainAnimation） 有间接影响，适用于需要调整惯性滚动减速快慢的场景。设置为小于等于0的值时，按默认值处理。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-friction(value: number | Resource): T--><!--Device-ScrollableCommonMethod-friction(value: number | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 摩擦系数。&lt;br/&gt;默认值：非wearable设备为0.6，wearable设备为0.9。&lt;br/&gt;从API version 11开始，非wearable设 备默认值为0.7。&lt;br/&gt;从API version 12开始，非wearable设备默认值为0.75。 &lt;br/&gt;取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions): T
```

设置前后两个方向的嵌套滚动模式，实现与父组件的滚动联动。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-nestedScroll(value: NestedScrollOptions): T--><!--Device-ScrollableCommonMethod-nestedScroll(value: NestedScrollOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | 是 | 嵌套滚动选项。&lt;br/&gt;默认值：{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onDidScroll

```TypeScript
onDidScroll(handler: OnScrollCallback): T
```

滚动组件滑动时触发，返回当前帧滑动的偏移量和当前滑动状态。 > **说明：** > > 从API version 14开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier)中调用。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollableCommonMethod-onDidScroll(handler: OnScrollCallback): T--><!--Device-ScrollableCommonMethod-onDidScroll(handler: OnScrollCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnScrollCallback](arkts-arkui-onscrollcallback-t.md) | 是 | 滚动组件滑动时触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onDidStopDragging

```TypeScript
onDidStopDragging(handler: OnDidStopDraggingCallback): T
```

滚动组件结束拖动时触发。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollableCommonMethod-onDidStopDragging(handler: OnDidStopDraggingCallback): T--><!--Device-ScrollableCommonMethod-onDidStopDragging(handler: OnDidStopDraggingCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnDidStopDraggingCallback](arkts-arkui-ondidstopdraggingcallback-t.md) | 是 | 滚动组件结束拖动时触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onDidStopFling

```TypeScript
onDidStopFling(handler: VoidCallback): T
```

滚动组件结束惯性动效后触发，进行中的惯性动效被新的滑动事件打断时不触发。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollableCommonMethod-onDidStopFling(handler: VoidCallback): T--><!--Device-ScrollableCommonMethod-onDidStopFling(handler: VoidCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | VoidCallback | 是 | 滚动组件结束惯性动效后触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onReachEnd

```TypeScript
onReachEnd(event: () => void): T
```

滚动组件到达末尾位置时触发。 滚动组件初始化时，若已处于末尾位置则会触发一次。边缘效果为弹簧效果时，划动经过末尾位置时触发一次，回弹回末尾位置时再触发一次。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-onReachEnd(event: () => void): T--><!--Device-ScrollableCommonMethod-onReachEnd(event: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 滚动组件到达末尾位置时的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onReachStart

```TypeScript
onReachStart(event: () => void): T
```

滚动组件到达起始位置时触发。 滚动组件初始化时会触发一次，滚动到起始位置时触发一次。边缘效果为弹簧效果时，划动经过起始位置时触发一次，回弹回起始位置时再触发一次。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-onReachStart(event: () => void): T--><!--Device-ScrollableCommonMethod-onReachStart(event: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 滚动组件到达起始位置时的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onScroll

```TypeScript
onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T
```

滚动组件滑动时触发。 > **说明：** > > 从API version 11开始支持，从API version 12开始废弃。List、Grid和WaterFlow > 组件的onScroll事件在布局之后触发，

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** 12

**替代接口：** [onDidScroll](#onDidScroll)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T--><!--Device-ScrollableCommonMethod-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (scrollOffset: number, scrollState: ScrollState) =&gt; void | 是 | 滚动组件滑动时的回调。&lt;br/&gt;scrollOffset：相对于上一帧的偏移量，滚动组件的内容向上滚动时偏移量为正，向下滚动时偏移量为负。单位vp。&lt;br/&gt; scrollState：当前滑动状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onScrollStart

```TypeScript
onScrollStart(event: () => void): T
```

滚动开始时触发。手指拖动滚动组件或其滚动条触发的滚动开始时，会触发该事件。使用Scroller滚动控制器触发的带动画的滚动，动画开始时会触发该事件。 触发该事件的条件： 1. 滚动组件开始滚动时触发，支持键鼠操作等其他触发滚动的输入设置。 2. 通过滚动控制器API接口调用后开始，带过渡动效。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-onScrollStart(event: () => void): T--><!--Device-ScrollableCommonMethod-onScrollStart(event: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 滚动开始时的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onScrollStop

```TypeScript
onScrollStop(event: () => void): T
```

滚动停止时触发。手指拖动滚动组件或其滚动条触发的滚动，手指离开屏幕后滚动停止时会触发该事件。使用Scroller滚动控制器触发的带动画的滚动，动画停止时会触发该事件。 触发该事件的条件： 1. 滚动组件触发滚动后停止，支持键鼠操作等其他触发滚动的输入设置。 2. 通过调用带过渡动画的滚动控制器API接口，动画停止时。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-onScrollStop(event: () => void): T--><!--Device-ScrollableCommonMethod-onScrollStop(event: () => void): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 滚动停止时的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onWillScroll

```TypeScript
onWillScroll(handler: Optional<OnWillScrollCallback>): T
```

滚动事件回调，滚动组件滚动前触发。与 [onDidScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12)的对比： onWillScroll在滚动发生前触发，可通过返回值指定将要滚动的偏移量，适用于需要拦截或自定义滚动行为的场景；onDidScroll在滚动发生时触发，返回当前帧的实际滚动偏移量和滑动状态，适用于仅需监听滚动过程的场景。两者可同 时使用。 回调当前帧将要滚动的偏移量、当前滚动状态及滚动操作来源，其中回调的偏移量为计算得到的将要滚动的偏移量值，并非最终实际滚动偏移。可以通过该回调返回值指定滚动组件将要滚动的偏移。Scroll组件的 onWillScroll接口的参数类型是 ScrollOnWillScrollCallback。 > **说明：** > > - 从API version 14开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributeModifier)中调用。 > > - 调用不带动画的ScrollEdge和ScrollToIndex时，不触发onWillScroll。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-onWillScroll(handler: Optional<OnWillScrollCallback>): T--><!--Device-ScrollableCommonMethod-onWillScroll(handler: Optional<OnWillScrollCallback>): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-optional-t.md)&lt;[OnWillScrollCallback](arkts-arkui-onwillscrollcallback-t.md)&gt; | 是 | 滚动组件滑动前触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onWillStartDragging

```TypeScript
onWillStartDragging(handler: VoidCallback): T
```

滚动组件开始拖动时触发。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollableCommonMethod-onWillStartDragging(handler: VoidCallback): T--><!--Device-ScrollableCommonMethod-onWillStartDragging(handler: VoidCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | VoidCallback | 是 | 滚动组件开始拖动时触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onWillStartFling

```TypeScript
onWillStartFling(handler: VoidCallback): T
```

滚动组件将要开始惯性动效时触发。 > **说明：** > > - 如果惯性动效通过fling方法触发，则onWillStartFling不触发。 > > - 惯性动效的触发场景参考 > [flingSpeedLimit](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#flingspeedlimit11)方法的 > 说明。

**起始版本：** 21

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为21。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollableCommonMethod-onWillStartFling(handler: VoidCallback): T--><!--Device-ScrollableCommonMethod-onWillStartFling(handler: VoidCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | VoidCallback | 是 | 滚动组件将要开始惯性动效时触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## onWillStopDragging

```TypeScript
onWillStopDragging(handler: OnWillStopDraggingCallback): T
```

滚动组件划动离手时触发，使用鼠标滚轮划动时不会触发。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-ScrollableCommonMethod-onWillStopDragging(handler: OnWillStopDraggingCallback): T--><!--Device-ScrollableCommonMethod-onWillStopDragging(handler: OnWillStopDraggingCallback): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [OnWillStopDraggingCallback](arkts-arkui-onwillstopdraggingcallback-t.md) | 是 | 滚动组件划动离手时触发的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## scrollBar

```TypeScript
scrollBar(barState: BarState): T
```

设置滚动条状态。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-scrollBar(barState: BarState): T--><!--Device-ScrollableCommonMethod-scrollBar(barState: BarState): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| barState | BarState | 是 | 滚动条状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string): T
```

设置滚动条的颜色。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-scrollBarColor(color: Color | number | string): T--><!--Device-ScrollableCommonMethod-scrollBarColor(color: Color | number | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Color \| number \| string | 是 | 滚动条的颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string | Resource): T
```

设置滚动条的颜色。与 [scrollBarColor&lt;sup&gt;11+&lt;/sup&gt;](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#scrollbarcolor11) 相比，color参数开始支持Resource类型。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-scrollBarColor(color: Color | number | string | Resource): T--><!--Device-ScrollableCommonMethod-scrollBarColor(color: Color | number | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Color \| number \| string \| Resource | 是 | 滚动条的颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## scrollBarHeight

```TypeScript
scrollBarHeight(height: LengthMetrics | undefined): T
```

设置滚动条滑轨高度。 未设置该接口时，滚动条滑轨高度默认自适应滚动组件高度，儿童智能表的默认高度为37vp。 > **说明：** > > 应确保scrollBarHeight与 > [scrollBarMargin](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#scrollbarmargin20)的设定 > 值之和不超过滚动组件高度，否则滚动条可能无法正常显示。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-scrollBarHeight(height: LengthMetrics | undefined): T--><!--Device-ScrollableCommonMethod-scrollBarHeight(height: LengthMetrics | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | LengthMetrics \| undefined | 是 | 滚动条滑轨高度。&lt;br/&gt;值必须大于等于0。设置为undefined或小于0时，自适应滚动组件高度，儿童智能表则恢复至默认值37vp。设置 为0时，不显示滚动条。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## scrollBarMargin

```TypeScript
scrollBarMargin(margin: ScrollBarMargin): T
```

设置滚动条的边距。边距是在滚动条避让滚动组件圆角区域距离的基础上计算的，如果滚动条区域小于滚动条的最小长度，则不显示滚动条。如果设置了本属性，则 [autoAdjustScrollBarMargin](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#autoadjustscrollbarmargin) 的自动调整边距功能不生效。应注意确保 [scrollBarHeight](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#scrollbarheight)与本属性的设定 值之和不超过滚动组件高度，否则滚动条可能无法正常显示。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-scrollBarMargin(margin: ScrollBarMargin): T--><!--Device-ScrollableCommonMethod-scrollBarMargin(margin: ScrollBarMargin): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| margin | ScrollBarMargin | 是 | 滚动条起始、末尾边距。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string): T
```

设置滚动条的宽度，不支持百分比设置。宽度设置后，滚动条正常状态和按压状态宽度均为滚动条的宽度值。如果滚动条的宽度超过滚动组件主轴方向的可视尺寸，则滚动条的宽度会变为默认值4vp。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-scrollBarWidth(value: number | string): T--><!--Device-ScrollableCommonMethod-scrollBarWidth(value: number | string): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 滚动条的宽度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string | Resource): T
```

设置滚动条的宽度，不支持百分比设置。宽度设置后，滚动条正常状态和按压状态宽度均为滚动条的宽度值。如果滚动条的宽度超过滚动组件主轴方向的可视尺寸，则滚动条的宽度会变为默认值4vp，支持Resource资源类型。 未通过该接口设置时，滚动条的宽度为4vp。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollableCommonMethod-scrollBarWidth(value: number | string | Resource): T--><!--Device-ScrollableCommonMethod-scrollBarWidth(value: number | string | Resource): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 滚动条的宽度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前滚动组件。 |

