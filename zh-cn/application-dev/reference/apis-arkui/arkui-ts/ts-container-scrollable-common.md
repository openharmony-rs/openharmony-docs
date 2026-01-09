# 滚动组件通用接口

滚动组件通用属性和事件目前只支持[List](ts-container-list.md)、[Grid](ts-container-grid.md)、[Scroll](ts-container-scroll.md)和[WaterFlow](ts-container-waterflow.md)组件。

>  **说明：**
>
>  - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
>  - 本模块从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 属性

### scrollBar<sup>11+</sup>

ArkTS-Dyn: scrollBar(barState: BarState): T

ArkTS-Sta: scrollBar(barState: BarState | undefined): this

设置滚动条状态。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名   | 类型                                      | 必填 | 说明                                   |
| -------- | ----------------------------------------- | ---- | -------------------------------------- |
| barState | ArkTS-Dyn: [BarState](ts-appendix-enums.md#barstate)<br/>ArkTS-Sta: [BarState](ts-appendix-enums.md#barstate)&nbsp;\|&nbsp;undefined | 是   | 滚动条状态。<br/>默认值：List、Grid、Scroll组件默认BarState.Auto，WaterFlow组件默认BarState.Off。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### scrollBarColor<sup>11+</sup>

scrollBarColor(color: Color | number | string): T

设置滚动条的颜色。未通过该接口设置时，默认颜色为'\#182431'（40%不透明度）。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明           |
| ------ | ------------------------------------------------------------ | ---- | -------------- |
| color  | [Color](ts-appendix-enums.md#color)&nbsp;\|&nbsp;number&nbsp;\|&nbsp;string | 是   | 滚动条的颜色。<br/>number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前滚动组件。 |

### scrollBarColor<sup>22+</sup>

ArkTS-Dyn: scrollBarColor(color: Color | number | string | Resource): T

ArkTS-Sta: scrollBarColor(color: Color | int | string | Resource | undefined): this

设置滚动条的颜色。与[scrollBarColor<sup>11+</sup>](#scrollbarcolor11)相比，color参数开始支持Resource类型。未通过该接口设置时，默认颜色为'\#182431'（40%不透明度）。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明           |
| ------ | ------------------------------------------------------------ | ---- | -------------- |
| color  | ArkTS-Dyn: [Color](ts-appendix-enums.md#color)&nbsp;\|&nbsp;number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource)<br/>ArkTS-Sta: [Color](ts-appendix-enums.md#color)&nbsp;\|&nbsp;int&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource)&nbsp;\|&nbsp;undefined | 是   | 滚动条的颜色。<br/>number或int为HEX格式颜色，支持rgb或者argb，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。<br/>取值为undefined时，滚动条的颜色为'\#182431'（40%不透明度）。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### scrollBarWidth<sup>11+</sup>

ArkTS-Dyn: scrollBarWidth(value: number | string): T

ArkTS-Sta: scrollBarWidth(value: double | string | undefined): this

设置滚动条的宽度，不支持百分比设置。宽度设置后，滚动条正常状态和按压状态宽度均为滚动条的宽度值。如果滚动条的宽度超过滚动组件主轴方向的高度，则滚动条的宽度会变为默认值。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                       | 必填 | 说明                                      |
| ------ | -------------------------- | ---- | ----------------------------------------- |
| value  | ArkTS-Dyn: string&nbsp;\|&nbsp;number<br/>ArkTS-Sta: string&nbsp;\|&nbsp;double&nbsp;\|&nbsp;undefined | 是   | 滚动条的宽度。<br/>默认值：4<br/>单位：vp <br/>取值范围：设置为小于0的值时，按默认值处理。设置为0时，不显示滚动条。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### edgeEffect<sup>11+</sup>

ArkTS-Dyn: edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T

ArkTS-Sta: edgeEffect(edgeEffect: EdgeEffect | undefined, options?: EdgeEffectOptions): this

设置边缘滑动效果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名                | 类型                                              | 必填 | 说明                                                         |
| --------------------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| edgeEffect            | ArkTS-Dyn: [EdgeEffect](ts-appendix-enums.md#edgeeffect)<br/>ArkTS-Sta: [EdgeEffect](ts-appendix-enums.md#edgeeffect)&nbsp;\|&nbsp;undefined | 是   | 滚动组件的边缘滑动效果，支持弹簧效果和阴影效果。<br/>默认值：Grid、Scroll、WaterFlow组件默认EdgeEffect.None，List组件默认EdgeEffect.Spring。|
| options | [EdgeEffectOptions](#edgeeffectoptions11对象说明) | 否   | 组件内容大小小于组件自身时，是否开启滑动效果。设置为{ alwaysEnabled: true }会开启滑动效果，{ alwaysEnabled: false }不开启。<br/>默认值：<br/>List、Grid、WaterFlow组件默认{ alwaysEnabled: false }，Scroll组件默认{ alwaysEnabled: true }。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### nestedScroll<sup>11+</sup>

ArkTS-Dyn: nestedScroll(value: NestedScrollOptions): T

ArkTS-Sta: nestedScroll(value: NestedScrollOptions | undefined): this

设置前后两个方向的嵌套滚动模式，实现与父组件的滚动联动。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                                                  | 必填 | 说明           |
| ------ | ----------------------------------------------------- | ---- | -------------- |
| value  | ArkTS-Dyn: [NestedScrollOptions](#nestedscrolloptions10对象说明)<br/>ArkTS-Sta: [NestedScrollOptions](#nestedscrolloptions10对象说明)&nbsp;\|&nbsp;undefined | 是   | 嵌套滚动选项。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### enableScrollInteraction<sup>11+</sup>

ArkTS-Dyn: enableScrollInteraction(value: boolean): T

ArkTS-Sta: enableScrollInteraction(value: boolean | undefined): this

设置是否支持滚动手势。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                |
| ------ | ------- | ---- | ----------------------------------- |
| value  | ArkTS-Dyn: boolean<br/>ArkTS-Sta: boolean&nbsp;\|&nbsp;undefined | 是   | 是否支持滚动手势。设置为true时可以通过手指或者鼠标滚动，设置为false时无法通过手指或者鼠标滚动，但不影响控制器[Scroller](ts-container-scroll.md#scroller)的滚动接口。<br/>默认值：true |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### friction<sup>11+</sup>

ArkTS-Dyn: friction(value: number | Resource): T

ArkTS-Sta: friction(value: double | Resource | undefined): this

设置摩擦系数，手动划动滚动区域时生效，仅影响惯性滚动过程，对惯性滚动过程中的链式效果有间接影响。设置为小于等于0的值时，按默认值处理。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型                                                 | 必填 | 说明                                                      |
| ------ | ---------------------------------------------------- | ---- | --------------------------------------------------------- |
| value  | ArkTS-Dyn: number&nbsp;\|&nbsp;[Resource](ts-types.md#resource)<br/>ArkTS-Sta: double&nbsp;\|&nbsp;[Resource](ts-types.md#resource)&nbsp;\|&nbsp;undefined | 是   | 摩擦系数。<br/>默认值：非wearable设备为0.6，wearable设备为0.9。<br/>从API version 11开始，非wearable设备默认值为0.7。<br/>从API version 12开始，非wearable设备默认值为0.75。 <br/>取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### flingSpeedLimit<sup>11+</sup>

ArkTS-Dyn: flingSpeedLimit(speedLimit: number): T

ArkTS-Sta: flingSpeedLimit(speedLimit: double | undefined): this

限制跟手滑动结束后，Fling动效开始时的最大初始速度。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名     | 类型   | 必填 | 说明                            |
| ---------- | ------ | ---- | ------------------------------- |
| speedLimit | ArkTS-Dyn: number<br/>ArkTS-Sta: double&nbsp;\|&nbsp;undefined | 是   | Fling动效开始时的最大初始速度。<br/>默认值：9000<br/>单位：vp/s <br/>取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### fadingEdge<sup>14+</sup>

ArkTS-Dyn: fadingEdge(enabled: Optional&lt;boolean&gt;, options?: FadingEdgeOptions): T

ArkTS-Sta: fadingEdge(enabled: boolean | undefined, options?: FadingEdgeOptions): this

设置是否开启边缘渐隐效果及设置边缘渐隐长度。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名  | 类型                                              | 必填 | 说明                                                         |
| ------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| enabled | ArkTS-Dyn: Optional&lt;boolean&gt;ArkTS-Sta: boolean&nbsp;\|&nbsp;undefined | 是   | fadingEdge生效时，会覆盖原组件的.overlay()属性。<br/>fadingEdge生效时，建议不在该组件上设置background相关属性，会影响渐隐的显示效果。<br/>fadingEdge生效时，组件会裁剪到边界，设置组件的clip属性为false不生效。<br/>设置为true时开启边缘渐隐效果，设置为false时不开启边缘渐隐效果。<br/>默认值：false |
| options | [FadingEdgeOptions](#fadingedgeoptions14对象说明) | 否   | 边缘渐隐参数对象。可以通过该对象定义边缘渐隐效果属性，比如设置渐隐长度。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### clipContent<sup>14+</sup>

ArkTS-Dyn: clipContent(clip: ContentClipMode | RectShape): T

ArkTS-Sta: clipContent(clip: ContentClipMode | RectShape | undefined): this

设置滚动容器的内容层裁剪区域。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名  | 类型                                              | 必填 | 说明                                                         |
| ------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| clip | ArkTS-Dyn: [ContentClipMode](#contentclipmode14枚举说明)&nbsp;\|&nbsp;[RectShape](../js-apis-arkui-shape.md#rectshape)<br/>ArkTS-Sta: [ContentClipMode](#contentclipmode14枚举说明)&nbsp;\|&nbsp;[RectShape](../js-apis-arkui-shape.md#rectshape)&nbsp;\|&nbsp;undefined | 是   | 裁剪只针对滚动容器的内容，即其子节点，背景不受影响。通过RectShape传入自定义矩形区域时仅支持设置宽高和相对于组件左上角的[offset](../js-apis-arkui-shape.md#offset)，不支持圆角。<br></div>默认值：Grid、Scroll的默认值为ContentClipMode.BOUNDARY，List、WaterFlow的默认值为ContentClipMode.CONTENT_ONLY。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### backToTop<sup>15+</sup>

ArkTS-Dyn: backToTop(backToTop: boolean): T

ArkTS-Sta: backToTop(backToTop: boolean | undefined): this

设置滚动组件是否支持点击状态栏回到顶部。

支持当前页面的滚动组件收到点击状态栏事件后，滚动回到顶部。点击状态栏后，后台应用的滚动组件不受影响，不做回到顶部的动作。本属性不受[enableScrollInteraction](#enablescrollinteraction11)设置的影响。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                           |
| ------ | ------- | ---- | ---------------------------------------------- |
| backToTop  | ArkTS-Dyn: boolean<br/>ArkTS-Sta: boolean&nbsp;\|&nbsp;undefined | 是   | 设置滚动组件是否支持点击状态栏回到顶部。设置为true支持点击状态栏回到顶部，设置为false不支持点击状态栏回到顶部。<br/>默认值：<br/>API version 18之前：false。 <br/>API version 18及以后：滚动方向是水平方向时为false，是垂直方向时为true。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### scrollBarMargin<sup>20+</sup>

ArkTS-Dyn: scrollBarMargin(margin: ScrollBarMargin): T

ArkTS-Sta: scrollBarMargin(margin: ScrollBarMargin | undefined): this

设置滚动条的边距。边距是在滚动条避让圆角距离的基础上计算的，如果滚动条区域小于滚动条的最小长度，则不显示滚动条。未通过该接口设置时，滚动条起始、末尾默认边距为0。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                  |
| ------ | ------- | ---- | ------------------------------------- |
| margin  | ArkTS-Dyn: [ScrollBarMargin](#scrollbarmargin20对象说明)<br/>ArkTS-Sta: [ScrollBarMargin](#scrollbarmargin20对象说明)&nbsp;\|&nbsp;undefined  | 是   |滚动条起始、末尾边距。<br/>取值为undefined时，滚动条起始、末尾边距默认为0。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### digitalCrownSensitivity<sup>18+</sup>

digitalCrownSensitivity(sensitivity: Optional\<CrownSensitivity>): T

设置表冠响应事件灵敏度。

组件收到[表冠事件](ts-universal-events-crown.md)的前提是该组件获焦，焦点控制可以通过[focusable](ts-universal-attributes-focus.md#focusable)、[defaultFocus](ts-universal-attributes-focus.md#defaultfocus9)、[focusOnTouch](ts-universal-attributes-focus.md#focusontouch9)进行管理。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名      | 类型                                                         | 必填 | 说明                                                         |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensitivity | [Optional&lt;CrownSensitivity&gt;](ts-appendix-enums.md#crownsensitivity18) | 是   | 表冠响应灵敏度。<br/>默认值：CrownSensitivity.MEDIUM，响应速度适中。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前滚动组件。 |

### contentStartOffset<sup>22+</sup>

ArkTS-Dyn: contentStartOffset(offset: number | Resource): T

ArkTS-Sta: contentStartOffset(offset: double | Resource | undefined): this

设置内容区域起始偏移量。滚动组件滚动到起始位置时，内容与组件显示区域边界保留指定距离。未通过该接口设置时，内容区域起始默认不偏移。

contentStartOffset + contentEndOffset超过滚动组件内容区长度后contentStartOffset和contentEndOffset会置0。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型   | 必填 | 说明                                            |
| ------ | ------ | ---- | ----------------------------------------------- |
| offset  | ArkTS-Dyn: number&nbsp;\|&nbsp;[Resource](ts-types.md#resource)<br/>ArkTS-Sta: double&nbsp;\|&nbsp;[Resource](ts-types.md#resource)&nbsp;\|&nbsp;undefined | 是   | 内容区域起始偏移量。<br/>设置异常值如负数、非数字Resource与undefined时，按0vp处理。|

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### contentEndOffset<sup>22+</sup>

ArkTS-Dyn: contentEndOffset(offset: number | Resource): T

ArkTS-Sta: contentEndOffset(offset: double | Resource | undefined): this

设置内容区末尾偏移量。滚动组件滚动到末尾位置时，内容与组件显示区域边界保留指定距离。未通过该接口设置时，内容区域末尾默认不偏移。

contentStartOffset + contentEndOffset超过滚动组件内容区长度后contentStartOffset和contentEndOffset会置0。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型   | 必填 | 说明                                          |
| ------ | ------ | ---- | --------------------------------------------- |
| offset  | ArkTS-Dyn: number&nbsp;\|&nbsp;[Resource](ts-types.md#resource)<br/>ArkTS-Sta: double&nbsp;\|&nbsp;[Resource](ts-types.md#resource)&nbsp;\|&nbsp;undefined | 是   | 内容区末尾偏移量。<br/>设置异常值如负数、非数字Resource与undefined时，按0vp处理。|

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |


## 事件

### onReachStart<sup>11+</sup>

ArkTS-Dyn: onReachStart(event: () => void): T

ArkTS-Sta: onReachStart(event: (() => void) | undefined): this

滚动组件到达起始位置时触发。

滚动组件初始化时会触发一次，滚动到起始位置时触发一次。边缘效果为弹簧效果时，划动经过起始位置时触发一次，回弹回起始位置时再触发一次。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型   | 必填 | 说明                 |
| ------ | ------ | ---- | -------------------- |
| event  | ArkTS-Dyn: () => void<br/>ArkTS-Sta: () => void&nbsp;\|&nbsp;undefined | 是   | 滚动组件到达起始位置时的回调。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### onReachEnd<sup>11+</sup>

ArkTS-Dyn: onReachEnd(event: () => void): T

ArkTS-Sta: onReachEnd(event: (() => void) | undefined): this

滚动组件到达末尾位置时触发。

滚动组件边缘效果为弹簧效果时，划动经过末尾位置时触发一次，回弹回末尾位置时再触发一次。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型   | 必填 | 说明                 |
| ------ | ------ | ---- | -------------------- |
| event  | ArkTS-Dyn: () => void<br/>ArkTS-Sta: () => void&nbsp;\|&nbsp;undefined | 是   | 滚动组件到达末尾位置时的回调。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### onScrollStart<sup>11+</sup>

ArkTS-Dyn: onScrollStart(event: () => void): T

ArkTS-Sta: onScrollStart(event: (() => void) | undefined): this

滚动开始时触发。手指拖动滚动组件或拖动滚动组件的滚动条触发的滚动开始时，会触发该事件。使用[Scroller](ts-container-scroll.md#scroller)滚动控制器触发的带动画的滚动，动画开始时会触发该事件。

触发该事件的条件：

1、滚动组件开始滚动时触发，支持键鼠操作等其他触发滚动的输入设置。

2、通过滚动控制器API接口调用后开始，带过渡动效。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型   | 必填 | 说明                 |
| ------ | ------ | ---- | -------------------- |
| event  | ArkTS-Dyn: () => void<br/>ArkTS-Sta: () => void&nbsp;\|&nbsp;undefined | 是   | 滚动开始时的回调。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### onScrollStop<sup>11+</sup>

ArkTS-Dyn: onScrollStop(event: () => void): T

ArkTS-Sta: onScrollStop(event: (() => void) | undefined): this

滚动停止时触发。手拖动滚动组件或拖动滚动组件的滚动条触发的滚动，手离开屏幕并且滚动停止时会触发该事件。使用[Scroller](ts-container-scroll.md#scroller)滚动控制器触发的带动画的滚动，动画停止时会触发该事件。

触发该事件的条件：

1、滚动组件触发滚动后停止，支持键鼠操作等其他触发滚动的输入设置。

2、通过滚动控制器API接口调用后开始，带过渡动效。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 22

**参数：** 

| 参数名 | 类型   | 必填 | 说明                 |
| ------ | ------ | ---- | -------------------- |
| event  | ArkTS-Dyn: () => void<br/>ArkTS-Sta: () => void&nbsp;\|&nbsp;undefined | 是   | 滚动停止时的回调。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| ArkTS-Dyn: T <br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### onWillScroll<sup>12+</sup> 

onWillScroll(handler: Optional&lt;OnWillScrollCallback&gt;): T

滚动事件回调，滚动组件滚动前触发。

回调当前帧将要滚动的偏移量和当前滚动状态和滚动操作来源，其中回调的偏移量为计算得到的将要滚动的偏移量值，并非最终实际滚动偏移。可以通过该回调返回值指定滚动组件将要滚动的偏移。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------|
| handler | Optional&lt;[OnWillScrollCallback](#onwillscrollcallback12)&gt; | 是 | 滚动组件滑动前触发的回调。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前滚动组件。 |

> **说明：** 
> 
> 调用不带动画的ScrollEdge和ScrollToIndex时，不触发onWillScroll。


### onDidScroll<sup>12+</sup> 

onDidScroll(handler: OnScrollCallback): T

滚动组件滑动时触发，返回当前帧滑动的偏移量和当前滑动状态。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------|
| handler | [OnScrollCallback](#onscrollcallback12) | 是 | 滚动组件滑动时触发的回调。 |

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前滚动组件。 |

### onScroll<sup>(deprecated)</sup>

onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T

滚动组件滑动时触发。

从API version 11开始使用。

从API version 12开始废弃不再使用，Scroll组件的onScroll事件在布局之前触发，建议使用[onWillScroll](#onwillscroll12)替代；List、Grid和WaterFlow组件的onScroll事件在布局之后触发，建议使用[onDidScroll](#ondidscroll12)替代。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------|
| event  | (scrollOffset: number, scrollState: [ScrollState](ts-container-list.md#scrollstate枚举说明)) => void | 是 | 滚动组件滑动时的回调。<br/>scrollOffset：每帧滚动的偏移量，滚动组件的内容向上滚动时偏移量为正，向下滚动时偏移量为负。单位vp。<br/>scrollState：当前滑动状态。|

**返回值：**

| 类型 | 说明           |
| --- | -------------- |
| T | 返回当前滚动组件。 |

### onWillStartDragging<sup>21+</sup>

ArkTS-Dyn: onWillStartDragging(handler: VoidCallback): T

ArkTS-Sta: onWillStartDragging(handler: VoidCallback | undefined): this

滚动组件开始拖动时触发。

**卡片能力：** 从API version 21开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 21开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 21

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                        | 必填 | 说明                         |
| ------- | ------------------------------------------ | ---- | ---------------------------- |
| handler | ArkTS-Dyn: [VoidCallback](ts-types.md#voidcallback12)<br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)&nbsp;\|&nbsp;undefined | 是   | 滚动组件开始拖动时触发的回调。<br/>当设置为undefined时，重置该事件回调。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### onWillStopDragging<sup>20+</sup>

ArkTS-Dyn: onWillStopDragging(handler: OnWillStopDraggingCallback): T

ArkTS-Sta: onWillStopDragging(handler: OnWillStopDraggingCallback | undefined): this

滚动组件划动离手时触发，使用鼠标滚轮划动时不会触发。

**卡片能力：** 从API version 20开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                                        | 必填 | 说明                         |
| ------- | ----------------------------------------------------------- | ---- | ---------------------------- |
| handler | ArkTS-Dyn: [OnWillStopDraggingCallback](#onwillstopdraggingcallback20)<br/>ArkTS-Sta: [OnWillStopDraggingCallback](#onwillstopdraggingcallback20)&nbsp;\|&nbsp;undefined | 是   | 滚动组件划动离手时触发的回调。<br/>当设置为undefined时，重置该事件回调。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### onDidStopDragging<sup>21+</sup>

ArkTS-Dyn: onDidStopDragging(handler: OnDidStopDraggingCallback): T

ArkTS-Sta: onDidStopDragging(handler: OnDidStopDraggingCallback | undefined): this

滚动组件结束拖拽时触发。

**卡片能力：** 从API version 21开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 21开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 21

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                                       | 必填 | 说明                         |
| ------- | --------------------------------------------------------- | ---- | --------------------------- |
| handler | ArkTS-Dyn: [OnDidStopDraggingCallback](#ondidstopdraggingcallback21)<br/>ArkTS-Sta: [OnDidStopDraggingCallback](#ondidstopdraggingcallback21)&nbsp;\|&nbsp;undefined | 是   | 滚动组件结束拖动时触发的回调。<br/>当设置为undefined时，重置该事件回调。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### onWillStartFling<sup>21+</sup>

ArkTS-Dyn: onWillStartFling(handler: VoidCallback): T

ArkTS-Sta: onWillStartFling(handler: VoidCallback | undefined): this

滚动组件将要开始Fling动效时触发。

**卡片能力：** 从API version 21开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 21开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 21

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                        | 必填 | 说明                         |
| ------- | ------------------------------------------ | ---- | ---------------------------- |
| handler | ArkTS-Dyn: [VoidCallback](ts-types.md#voidcallback12)<br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)&nbsp;\|&nbsp;undefined | 是   | 滚动组件将要开始Fling动效时触发的回调。<br/>当设置为undefined时，重置该事件回调。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前滚动组件。 |

### onDidStopFling<sup>21+</sup>

ArkTS-Dyn: onDidStopFling(handler: VoidCallback): T

ArkTS-Sta: onDidStopFling(handler: VoidCallback | undefined): this

滚动组件结束Fling动效后触发，进行中的Fling动效被新的滑动事件打断时不触发。

**卡片能力：** 从API version 21开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 21开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 21

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                        | 必填 | 说明                         |
| ------- | ------------------------------------------ | ---- | ---------------------------- |
| handler | ArkTS-Dyn: [VoidCallback](ts-types.md#voidcallback12)<br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)&nbsp;\|&nbsp;undefined | 是   | 滚动组件结束Fling动效后触发的回调。<br/>当设置为undefined时，重置该事件回调。 |

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| ArkTS-Dyn: T<br/>ArkTS-Sta: this | 返回当前滚动组件。 |

## ItemDragInfo对象说明

拖拽点信息对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称         | 类型         |   描述         |
| ---------- | ---------- | ---------- |
| x | number |  当前拖拽点的x坐标，单位vp。    |
| y | number |  当前拖拽点的y坐标，单位vp。    |

## NestedScrollOptions<sup>10+</sup>对象说明

[nestedScroll](#nestedscroll11)属性参数对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型  | 必填 | 描述              |
| ----- | ------ | ------ | ----------------- |
| scrollForward | [NestedScrollMode](ts-appendix-enums.md#nestedscrollmode10) | 是 | 滚动组件往末尾端滚动时的嵌套滚动选项。 |
| scrollBackward | [NestedScrollMode](ts-appendix-enums.md#nestedscrollmode10) | 是 | 滚动组件往起始端滚动时的嵌套滚动选项。 |

## EdgeEffectOptions<sup>11+</sup>对象说明

[edgeEffect](#edgeeffect11)属性参数对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名   | 类型  | 必填 | 描述              |
| ----- | ------| ------- | ----------------- |
| alwaysEnabled | boolean | 是 | 组件内容大小小于组件自身时，设置是否开启滑动效果。设置为true开启滑动效果，设置为false关闭滑动效果。<br/>**ArkTS-Dyn起始版本：** 11 <br/>**ArkTS-Sta起始版本：** 22 |
| effectEdge<sup>18+</sup> | ArkTS-Dyn: number<br/> ArkTS-Sta: int | 否 | 设置边缘效果生效的边缘。<br/>如果设置[EffectEdge](#effectedge18枚举说明).START表示只有起始边生效。如果设置[EffectEdge](#effectedge18枚举说明).END表示只有末尾边生效。<br/>默认值为[EffectEdge](#effectedge18枚举说明).START \| [EffectEdge](#effectedge18枚举说明).END表示双边同时生效。当设置为其它异常值时，则默认双边同时生效。<br/>如果需要双边都不生效，可将edgeEffect设置为EdgeEffect.None。<br/>**ArkTS-Dyn起始版本：** 18 <br/>**ArkTS-Sta起始版本：** 22 |

## FadingEdgeOptions<sup>14+</sup>对象说明

[fadingEdge](#fadingedge14)属性边缘渐隐参数对象。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 参数名           | 类型                                                         | 必填 | 描述                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| fadingEdgeLength | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否   | 设置边缘渐隐长度。如果设置小于0的值则取默认值，默认长度为32vp。<br/>如果设置的长度超过容器高度的一半时，渐隐长度取容器高度的一半。 |

## EffectEdge<sup>18+</sup>枚举说明

表示当前边缘效果要生效的边缘。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 值   | 说明         |
| ----- | ---- | ------------ |
| START | 1    | 起始边生效。 |
| END   | 2    | 末尾边生效。 |

## ScrollBarMargin<sup>20+</sup>对象说明

滚动条边距。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 类型                                                         | 必填 | 说明                                   |
| ----- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| start | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否   | 滚动条起始边距。<br/>默认值：0，单位：vp |
| end   | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | 否   | 滚动条末尾边距。<br/>默认值：0，单位：vp |

## ContentClipMode<sup>14+</sup>枚举说明

表示滚动容器的内容裁剪模式。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

下图是组件配置了边距属性后的示意图，可理解每种枚举对应的裁剪区域。

![ContentClipMode示意图](figures/ContentClipMode.png)

| 名称     |  值  | 说明                                       |
| ------ | ------ | ---------------------------------------- |
| CONTENT_ONLY   |  0  | 按内容区裁剪，对应图中的绿色区域。 |
| BOUNDARY |  1  | 按组件区域裁剪，对应图中的整个蓝色区域。 |
| SAFE_AREA  |  2  | 按组件配置的SafeArea区域裁剪，对应图中的整个黄色区域。 |

## OnWillScrollCallback<sup>12+</sup>

ArkTS-Dyn：type OnWillScrollCallback = (scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult

ArkTS-Sta：type OnWillScrollCallback = (scrollOffset: double, scrollState: ScrollState, scrollSource: ScrollSource) => undefined | ScrollResult

滚动组件滑动前触发的回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------|
| scrollOffset | ArkTS-Dyn: number<br/> ArkTS-Sta: double | 是 | 每帧滑动的偏移量，滚动组件的内容向上滚动时偏移量为正，向下滚动时偏移量为负。<br/>单位vp。 |
| scrollState | [ScrollState](ts-container-list.md#scrollstate枚举说明) | 是 | 当前滑动状态。 |
| scrollSource | [ScrollSource](ts-appendix-enums.md#scrollsource12) | 是 | 当前滑动操作的来源。 |

**返回值：** 

| 类型                          | 说明                                  |
| ----------------------------- | ------------------------------------ |
| ArkTS-Dyn: void \| [ScrollResult](#scrollresult12对象说明)<br/> ArkTS-Sta: undefined \| [ScrollResult](#scrollresult12对象说明) |  返回ScrollResult时按照开发者指定的偏移量滑动；不返回时按回调参数scrollOffset滑动。  <br/>取值范围：(-∞, +∞)|

## OnScrollCallback<sup>12+</sup>

ArkTS-Dyn: type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void

ArkTS-Sta: type OnScrollCallback = (scrollOffset: double, scrollState: ScrollState) => void

滚动组件滑动时触发的回调。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------|
| scrollOffset | ArkTS-Dyn: number<br/> ArkTS-Sta: double | 是 | 每帧滚动的偏移量，滚动组件的内容向上滚动时偏移量为正，向下滚动时偏移量为负。<br/>单位vp。 |
| scrollState | [ScrollState](ts-container-list.md#scrollstate枚举说明) | 是 | 当前滑动状态。 |

## ScrollResult<sup>12+</sup>对象说明

[OnWillScrollCallback](#onwillscrollcallback12)返回值对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------|
| offsetRemain | ArkTS-Dyn: number<br/> ArkTS-Sta: double | 是 | 将要滑动偏移量，单位vp。 |

## ChildrenMainSize<sup>12+</sup>对象说明

维护List组件或ListItemGroup组件的子组件在主轴方向的大小信息，仅支持一对一绑定到List组件或ListItemGroup组件。

**说明：**
>
> - 提供的主轴方向大小信息必须与子组件实际在主轴方向的大小一致，子组件在主轴方向大小变化或者增删子组件时都必须通过ChildrenMainSize对象方法通知List组件或ListItemGroup组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

### constructor<sup>12+</sup>

ArkTS-Dyn: constructor(childDefaultSize: number): void

ArkTS-Sta: constructor(childDefaultSize: double): void

ChildrenMainSize有参构造函数。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 名称   | 类型                            | 必填   | 描述                   |
| ---- | ----------------------------- | ---- | -------------------- |
| childDefaultSize | ArkTS-Dyn: number<br/> ArkTS-Sta: double | 是    | 子组件在主轴方向的默认大小。<br/>单位：vp<br/>**说明：** <br/>必须是有限的非负数值，否则抛出异常。|


### childDefaultSize<sup>12+</sup>

ArkTS-Dyn: set childDefaultSize(value: number): void

ArkTS-Sta: set childDefaultSize(value: double): void

修改子组件在主轴方向的默认大小。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 名称   | 类型                            | 必填   | 描述                   |
| ---- | ----------------------------- | ---- | -------------------- |
| value | ArkTS-Dyn: number<br/> ArkTS-Sta: double | 是    | 子组件在主轴方向的默认大小。<br/>单位：vp<br/>**说明：** <br/>必须是有限的非负数值，否则抛出异常。|

**错误码**：

以下错误码详细介绍请参考[通用错误码](../../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |

ArkTS-Dyn: get childDefaultSize(): number

ArkTS-Sta: get childDefaultSize(): double

获取子组件在主轴方向的默认大小。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**返回值：** 

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ArkTS-Dyn: number<br/> ArkTS-Sta: double | 子组件在主轴方向的默认大小。<br/>单位：vp <br/>取值范围：[0, +∞)|

### splice<sup>12+</sup>

ArkTS-Dyn: splice(start: number, deleteCount?: number, childrenSize?: Array\<number>): void

ArkTS-Dyn: splice(start: int, deleteCount?: int, childrenSize?: Array\<double>): void

批量增删改子组件在主轴方向的大小信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 名称   | 类型                            | 必填   | 描述                   |
| ---- | ----------------------------- | ---- | -------------------- |
| start | ArkTS-Dyn: number<br/> ArkTS-Sta: int | 是    | 从0开始计算的索引值，表示要开始修改子组件在主轴方向大小信息的位置。<br/>**说明：** <br/>1. 必须是有限的非负数值，否则抛出异常。<br/>2. 非整数会被截断为整数。<br/>3. 超过最大索引值不生效。<br/>取值范围：[0, +∞) |
| deleteCount | ArkTS-Dyn: number<br/> ArkTS-Sta: int | 否    | 从start开始删除的大小信息的数量。<br/>**说明：** <br/>1.  必须是有限的非负数值，否则处理为0。<br/>2. 非整数会被截断为整数。<br/>3. start + deleteCount - 1可以超过最大索引值，会删除索引值start开始之后的所有子组件的大小信息。<br/>默认值为+∞。 <br/>取值范围：[0, +∞) |
| childrenSize | ArkTS-Dyn: Array\<number><br/> ArkTS-Sta: Array\<double> | 否    | 要在start位置插入的所有子组件的主轴方向的大小。<br/>Array中各个数值单位：vp <br/>**说明：** <br/>1.数组中数值如果是有限的非负值，则认为是指定的大小，后续不随默认大小的变化而变化。<br/>2. 数组中数值如果不是有限的非负值，会被处理成默认大小，后续会随默认大小的变化而变化。<br/>默认值为空数组。 <br/>取值范围：[0, +∞) |


**错误码**：

以下错误码详细介绍请参考[通用错误码](../../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |


> **说明：**
>
> - 如果仅使用start参数，表示删除索引值start及之后的子组件的大小信息。
> - 如果仅使用start和deleteCount参数，表示删除索引值start开始的deleteCount数量的子组件的大小信息。一般在删除子组件时使用。
> - 如果使用3个参数，表示删除索引值start开始的deleteCount数量的子组件的大小信息，再在start位置插入childrenSize中所有的大小信息。一般在增加子组件或者批量更新子组件主轴方向大小的时候使用，如果仅是增加子组件，deleteCount为0，childrenSize的元素数量和增加子组件的个数应该相等；如果仅是批量更新子组件主轴方向的大小，childrenSize的元素数量应该和deleteCount相等，即为批量更新的数量。
> - 如果想要通知某个子组件的大小为默认大小，childrenSize中对应的值不应该给一个有限的非负值，而应该给NaN，任意负值等能被处理成默认大小的值。

### update<sup>12+</sup>

ArkTS-Dyn: update(index: number, childSize: number): void

ArkTS-Sta: update(index: int, childSize: double): void

修改指定索引值对应的子组件的主轴方向的大小信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 名称   | 类型                            | 必填   | 描述                   |
| ---- | ----------------------------- | ---- | -------------------- |
| index | ArkTS-Dyn: number<br/> ArkTS-Sta: int | 是    | 从0开始计算的索引值，表示要开始修改子组件在主轴方向大小信息的位置。<br/>**说明：** <br/>1. 必须是有限的非负数值，否则抛出异常。<br/>2. 非整数会被截断为整数。<br/>3. 超过最大索引值不生效。 <br/>取值范围：[0, +∞)|
| childSize | ArkTS-Dyn: number<br/> ArkTS-Sta: double | 是    | 要更新成的大小。<br/>单位：vp <br/>**说明：** <br/>1.数值如果是有限的非负值，则认为是指定的大小，后续不随默认大小的变化而变化。<br/>2. 数值如果不是有限的非负值，会被处理成默认大小，后续会随默认大小的变化而变化。  <br/>取值范围：[0, +∞)|

**错误码**：

以下错误码详细介绍请参考[通用错误码](../../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3. Parameter verification failed.   |

## UIScrollableCommonEvent<sup>19+</sup>
用于设置滚动事件回调。
### setOnReachStart<sup>19+</sup>

ArkTS-Dyn: setOnReachStart(callback: Callback\<void> | undefined): void

ArkTS-Sta: setOnReachStart(callback: VoidCallback | undefined): void

设置[onReachStart](./ts-container-scrollable-common.md#onreachstart11)事件的回调。

方法入参为undefined的时候，重置对应的事件回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| callback  | ArkTS-Dyn: [Callback](./ts-types.md#callback12)\<void> &nbsp;\|&nbsp;undefined<br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)&nbsp;\|&nbsp;undefined | 是   | onReachStart事件的回调函数。 |

### setOnReachEnd<sup>19+</sup>

ArkTS-Dyn: setOnReachEnd(callback: Callback\<void> | undefined): void

ArkTS-Sta: setOnReachEnd(callback: VoidCallback | undefined): void

设置[onReachEnd](./ts-container-scrollable-common.md#onreachend11)事件的回调。

方法入参为undefined时，会重置事件回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| callback  | ArkTS-Dyn: [Callback](./ts-types.md#callback12)\<void> &nbsp;\|&nbsp;undefined<br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)&nbsp;\|&nbsp;undefined | 是   | onReachEnd事件的回调函数。 |


### setOnScrollStart<sup>19+</sup>

ArkTS-Dyn: setOnScrollStart(callback: Callback\<void> | undefined): void

ArkTS-Sta: setOnScrollStart(callback: VoidCallback | undefined): void

设置[onScrollStart](./ts-container-scrollable-common.md#onscrollstart11)事件的回调。

方法入参为undefined时，会重置事件回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| callback  | ArkTS-Dyn: [Callback](./ts-types.md#callback12)\<void> &nbsp;\|&nbsp; undefined<br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)&nbsp;\|&nbsp;undefined | 是   | onScrollStart事件的回调函数。|


### setOnScrollStop<sup>19+</sup>

ArkTS-Dyn: setOnScrollStop(callback: Callback\<void> | undefined): void

ArkTS-Sta: setOnScrollStop(callback: VoidCallback | undefined): void

设置[onScrollStop](./ts-container-scrollable-common.md#onscrollstop11)事件的回调。

方法入参为undefined时，会重置事件回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| callback  | ArkTS-Dyn: [Callback](./ts-types.md#callback12)\<void> &nbsp;\|&nbsp;undefined<br/>ArkTS-Sta: [VoidCallback](ts-types.md#voidcallback12)&nbsp;\|&nbsp;undefined | 是   | onScrollStop事件的回调函数。 |

### setOnScrollFrameBegin<sup>19+</sup>

setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void

设置[onScrollFrameBegin](./ts-container-scroll.md#onscrollframebegin9)事件的回调。

方法入参为undefined时，会重置事件回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| callback  | [OnScrollFrameBeginCallback](./ts-container-scroll.md#onscrollframebegincallback18)&nbsp;\|&nbsp;undefined | 是   | onScrollFrameBegin事件的回调函数。 |


## OnWillStopDraggingCallback<sup>20+</sup>

ArkTS-Dyn: type OnWillStopDraggingCallback = (velocity: number) => void

ArkTS-Sta: type OnWillStopDraggingCallback = (velocity: double) => void

滚动组件划动离手时触发的回调。

**卡片能力：** 从API version 20开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| velocity | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | 划动离手速度，滚动组件的内容向上滚动时速度为正，向下滚动时速度为负。<br/>单位vp/s。 |

## OnDidStopDraggingCallback<sup>21+</sup>

type OnDidStopDraggingCallback = (willFling: boolean) => void

滚动组件在结束拖拽时触发的回调。

**卡片能力：** 从API version 21开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 21开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 21

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型    | 必填 | 说明                                                                              |
| --------  | ------- | ---- | -------------------------------------------------------------------------------- |
| willFling | boolean | 是   | 结束拖拽后是否会有Fling动效。返回true代表拖拽结束后有Fling动效，返回false代表没有Fling动效。 |