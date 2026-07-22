# WaterFlow属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)和[滚动组件通用属性](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#属性)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)和[滚动组件通用事件](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#事件)外，还支持以下事件：

**继承/实现关系：** WaterFlowAttribute extends [ScrollableCommonMethod<WaterFlowAttribute>](ScrollableCommonMethod<WaterFlowAttribute>)

**起始版本：** 9

<!--Device-unnamed-declare class WaterFlowAttribute extends ScrollableCommonMethod<WaterFlowAttribute>--><!--Device-unnamed-declare class WaterFlowAttribute extends ScrollableCommonMethod<WaterFlowAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## cachedCount

```TypeScript
cachedCount(value: number)
```

设置预加载的FlowItem数量。

只在[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和开启了[virtualScroll](../../../reference/apis-arkui/arkui-ts/ts-rendering-control-repeat.md#virtualscroll)开关的[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)中生效，超出显示及缓存范围的FlowItem会被释放。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-cachedCount(value: number): WaterFlowAttribute--><!--Device-WaterFlowAttribute-cachedCount(value: number): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 预加载的FlowItem的数量。 <br/>默认值：根据屏幕内显示的节点个数设置，最大值为16。<br/>取值范围：[0, +∞)，设置为小于0的值时，按1处理。 |

## cachedCount

```TypeScript
cachedCount(count: number, show: boolean)
```

设置预加载的FlowItem数量，并配置是否显示预加载节点。

配合[clip](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clip12)或[clipContent](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14)属性可以显示出预加载节点。

只在[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和开启了virtualScroll开关的[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)中生效，超出显示及缓存范围的FlowItem会被释放。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-cachedCount(count: number, show: boolean): WaterFlowAttribute--><!--Device-WaterFlowAttribute-cachedCount(count: number, show: boolean): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 预加载的FlowItem的数量。 <br/>默认值：根据屏幕内显示的节点个数设置，最大值为16。<br/>取值范围：[0, +∞)，设置为小于0的值时，按1处理。 |
| show | boolean | 是 | 被预加载的FlowItem是否需要显示。设置为true时显示预加载的FlowItem，设置为false时不显示预加载的FlowItem。 <br/> 默认值：false |

## columnsGap

```TypeScript
columnsGap(value: Length)
```

设置列与列的间距。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-columnsGap(value: Length): WaterFlowAttribute--><!--Device-WaterFlowAttribute-columnsGap(value: Length): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 列与列的间距。 <br/>默认值：0<br/>取值范围：[0, +∞)，小于0时按0处理。 |

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

设置当前瀑布流组件布局列的数量，不设置时默认1列。

例如，'1fr 1fr 2fr' 是将父组件分3列，将父组件允许的宽分为4等份，第1列占1份，第2列占1份，第3列占2份。

可使用columnsTemplate('repeat(auto-fill,track-size)')根据给定的列宽track-size自动计算列数，其中repeat、auto-fill为关键字，track-size为可设置的宽度，支持的单位包括px、vp、%或有效数字，默认单位为vp，使用方法参见[示例2](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#示例2自动计算列数)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-columnsTemplate(value: string): WaterFlowAttribute--><!--Device-WaterFlowAttribute-columnsTemplate(value: string): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 当前瀑布流组件布局列的数量。<br/>默认值：'1fr' |

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy)
```

设置当前瀑布流组件布局列的数量，不设置时默认1列。

当value设置为string类型时，使用方法参考[columnsTemplate(value: string)](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#columnstemplate)。

当value设置为ItemFillPolicy类型时，将根据WaterFlow组件宽度对应[断点类型](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)确定列数。

例如，ItemFillPolicy.BREAKPOINT_DEFAULT在组件宽度属于sm及更小的断点区间时显示2列，属于md断点区间时显示3列，属于lg及更大的断点区间时显示5列，且每列均为1fr。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-columnsTemplate(value: string | ItemFillPolicy): WaterFlowAttribute--><!--Device-WaterFlowAttribute-columnsTemplate(value: string | ItemFillPolicy): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| ItemFillPolicy | 是 | 当前瀑布流组件布局列的数量。 |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

设置是否支持滚动手势。
> **说明：**  
>  
> 组件无法通过鼠标按下拖动操作进行滚动。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-enableScrollInteraction(value: boolean): WaterFlowAttribute--><!--Device-WaterFlowAttribute-enableScrollInteraction(value: boolean): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持滚动手势。设置为true时可以通过手指或者鼠标滚动，设置为false时无法通过手指或者鼠标滚动，但不影响控制器[Scroller](arkts-arkui-scroller-c.md)的滚动接口。<br/>默认值：true |

## friction

```TypeScript
friction(value: number | Resource)
```

设置摩擦系数，手动划动滚动区域时生效，仅影响惯性滚动过程，对惯性滚动过程中的链式效果有间接影响。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-friction(value: number | Resource): WaterFlowAttribute--><!--Device-WaterFlowAttribute-friction(value: number | Resource): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 摩擦系数。<br/>默认值：非可穿戴设备为0.6，可穿戴设备为0.9。<br/>从API version 11开始，非可穿戴设备默认值为0.7。<br/>从API version 12开始，非可穿戴设备默认值为0.75。<br/>取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。 |

## itemConstraintSize

```TypeScript
itemConstraintSize(value: ConstraintSizeOptions)
```

设置约束尺寸，子组件布局时，进行尺寸范围限制。使用方法参考[示例1](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#示例1使用基本瀑布流)。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-itemConstraintSize(value: ConstraintSizeOptions): WaterFlowAttribute--><!--Device-WaterFlowAttribute-itemConstraintSize(value: ConstraintSizeOptions): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | 是 | 约束尺寸。设置小于0的值，参数不生效。 <br/>**说明：**<br/>1.同时设置itemConstraintSize和FlowItem的[constraintSize](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#constraintsize)属性时，minWidth/minHeight会取其中的最大值，maxWidth/maxHeight会取其中的最小值，调整后的值作为FlowItem的constraintSize处理。<br/>2.只设置itemConstraintSize时，相当于对WaterFlow所有子组件设置了相同的constraintSize。<br/>3.itemConstraintSize通过以上两种方式转换成FlowItem的constraintSize后的生效规则与通用属性[constraintSize](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#constraintsize)相同。 |

## layoutDirection

```TypeScript
layoutDirection(value: FlexDirection)
```

设置布局的主轴方向。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-layoutDirection(value: FlexDirection): WaterFlowAttribute--><!--Device-WaterFlowAttribute-layoutDirection(value: FlexDirection): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FlexDirection](../arkts-apis/arkts-arkui-flexdirection-e.md) | 是 | 布局的主轴方向。<br/>默认值：FlexDirection.Column |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

设置前后两个方向的嵌套滚动模式，实现与父组件的滚动联动。使用方法参考[嵌套滚动实现方式二](../../../reference/apis-arkui/arkui-ts/ts-container-scroll.md#示例3嵌套滚动实现方式二)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-nestedScroll(value: NestedScrollOptions): WaterFlowAttribute--><!--Device-WaterFlowAttribute-nestedScroll(value: NestedScrollOptions): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | 是 | 嵌套滚动选项。 |

## onReachEnd

```TypeScript
onReachEnd(event: () => void)
```

瀑布流内容到达末尾位置时触发。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-onReachEnd(event: () => void): WaterFlowAttribute--><!--Device-WaterFlowAttribute-onReachEnd(event: () => void): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 瀑布流内容到达末尾位置时触发的回调。 |

## onReachStart

```TypeScript
onReachStart(event: () => void)
```

瀑布流内容到达起始位置时触发。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-onReachStart(event: () => void): WaterFlowAttribute--><!--Device-WaterFlowAttribute-onReachStart(event: () => void): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 瀑布流内容到达起始位置时触发的回调。 |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

该接口回调时，事件参数传入即将发生的滑动量，事件处理函数中可根据应用场景计算实际需要的滑动量并作为事件处理函数的返回值返回，瀑布流将按照返回值的实际滑动量进行滑动。

满足以下任一条件时触发该事件：

1. 用户交互（如手指滑动、键鼠操作等）触发滚动。2. WaterFlow惯性滚动。3. 调用[fling](arkts-arkui-scroller-c.md#fling)接口触发滚动。

不触发该事件的条件：

1. 调用除[fling](arkts-arkui-scroller-c.md#fling)接口外的其他滚动控制接口。2. 越界回弹。3. 拖动滚动条。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): WaterFlowAttribute--><!--Device-WaterFlowAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | 是 | 每帧滚动开始回调函数。<br>**起始版本：** 20 |

## onScrollIndex

```TypeScript
onScrollIndex(event: (first: number, last: number) => void)
```

当前瀑布流显示的起始位置/终止位置的子组件发生变化时触发。瀑布流初始化时会触发一次。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-onScrollIndex(event: (first: number, last: number) => void): WaterFlowAttribute--><!--Device-WaterFlowAttribute-onScrollIndex(event: (first: number, last: number) => void): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (first: number, last: number) =&gt; void | 是 | 回调函数，瀑布流显示的起始位置/终止位置的子组件发生变化时触发。"first"：当前显示的瀑布流起始位置的索引值，"last"：当前显示的瀑布流终止位置的索引值。 |

## rowsGap

```TypeScript
rowsGap(value: Length)
```

设置行与行的间距。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-rowsGap(value: Length): WaterFlowAttribute--><!--Device-WaterFlowAttribute-rowsGap(value: Length): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 行与行的间距。 <br/>默认值：0<br/>取值范围：[0, +∞)，小于0时按0处理。 |

## rowsTemplate

```TypeScript
rowsTemplate(value: string)
```

设置当前瀑布流组件布局行的数量，不设置时默认1行。

例如，'1fr 1fr 2fr'是将父组件分3行，将父组件允许的高分为4等份，第1行占1份，第2行占1份，第3行占2份。

可使用rowsTemplate('repeat(auto-fill,track-size)')根据给定的行高track-size自动计算行数，其中repeat、auto-fill为关键字，track-size为可设置的高度，支持的单位包括px、vp、%或有效数字，默认单位为vp。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-rowsTemplate(value: string): WaterFlowAttribute--><!--Device-WaterFlowAttribute-rowsTemplate(value: string): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 当前瀑布流组件布局行的数量。<br/>默认值：'1fr' |

## supportEmptyBranchInLazyLoading

```TypeScript
supportEmptyBranchInLazyLoading(supported: boolean | undefined)
```

设置当前WaterFlow组件是否支持在LazyForEach或Repeat中使用if/else渲染控制语法生成不包含任何子组件的空分支节点。未设置时不支持空分支节点。此属性初次赋值后不支持更新，所以赋值后无法在支持空分支、不支持空分支行为之间切换。
> **说明：**  
>  
> 当通过[sections](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowoptions对象说明)参数设置了  
> [WaterFlowSections](arkts-arkui-waterflowsections-c.md)分组，或通过  
> [layoutMode](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#waterflowoptions对象说明)设置  
> [SLIDING_WINDOW](arkts-arkui-waterflowlayoutmode-e.md)布局模式时，supportEmptyBranchInLazyLoading设为true、false、undefined或不设置  
> supportEmptyBranchInLazyLoading，空分支后的FlowItem都会显示。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): WaterFlowAttribute--><!--Device-WaterFlowAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| supported | boolean \| undefined | 是 | 当前WaterFlow组件是否支持在[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)或[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)中使用[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)渲染控制语法生成一个不含任何子节点的空分支节点。</br>true表示显示空分支后的FlowItem；false表示不显示空分支后的FlowItem。</br>值为undefined时，按false处理。 |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

设置是否同步加载WaterFlow区域内所有子组件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-WaterFlowAttribute-syncLoad(enable: boolean): WaterFlowAttribute--><!--Device-WaterFlowAttribute-syncLoad(enable: boolean): WaterFlowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否同步加载WaterFlow区域内所有子组件。<br/>true表示同步加载，false表示异步加载。<br/>默认值：true。<br/>**说明：** <br/>设置为false时，在首次显示、不带动画[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)跳转场景，若当帧布局耗时超过50ms，会将WaterFlow区域内尚未布局的子组件延后到下一帧进行布局。 |

