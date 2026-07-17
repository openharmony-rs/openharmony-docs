# Grid属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)和[滚动组件通用属性](../../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#属性)外，还支持以下属性：  
> **说明：**  
>  
> Grid组件使用通用属性[clip<sup>12+</sup>](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clip12)和通用属性[clip<sup>18+</sup>](../../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clip18)时默认值都为true。  
>  
> 设置Grid的padding后，如果子组件部分位于Grid内容区且部分位于padding区域内，则会显示；如果子组件完全位于padding区域内，则不会显示。如下图所示，GridItem1显示，而GridItem2不显示。  
>  
> ![GridPadding示意图](figures/gridPadding.png)

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)和[滚动组件通用事件](../../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#事件)外，还支持以下事件：

**继承/实现关系：** GridAttribute extends [ScrollableCommonMethod<GridAttribute>](ScrollableCommonMethod<GridAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class GridAttribute extends ScrollableCommonMethod<GridAttribute>--><!--Device-unnamed-declare class GridAttribute extends ScrollableCommonMethod<GridAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(alignment: Optional<GridItemAlignment>)
```

设置Grid中GridItem的对齐方式， 使用方法可以参考[示例9](../../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例9以当前行最高的griditem的高度为其他griditem的高度)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-alignItems(alignment: Optional<GridItemAlignment>): GridAttribute--><!--Device-GridAttribute-alignItems(alignment: Optional<GridItemAlignment>): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alignment | [Optional](arkts-arkui-optional-t.md)<GridItemAlignment> | 是 | 设置Grid中GridItem的对齐方式。<br/>默认值：GridItemAlignment.DEFAULT |

## cachedCount

```TypeScript
cachedCount(value: number)
```

设置预加载的GridItem的数量，只在[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和开启了[virtualScroll](../arkts-apis/arkts-arkui-repeat-repeatattribute-c.md#virtualscroll-1)开关的[Repeat](../../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)中生效。<!--Del-->具体使用可参考[减少应用白块说明](../../../../performance/arkts-performance-improvement-recommendation.md#减少应用滑动白块)。<!--DelEnd-->

设置缓存后会在Grid显示区域上下各缓存cachedCount*列数个GridItem。

[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和开启了[virtualScroll](../arkts-apis/arkts-arkui-repeat-repeatattribute-c.md#virtualscroll-1)开关的[Repeat](../../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)超出显示和缓存范围的GridItem会被释放。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-cachedCount(value: number): GridAttribute--><!--Device-GridAttribute-cachedCount(value: number): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 预加载的GridItem的数量。<br/>默认值：垂直滚动时为一个屏幕内可显示的行数，水平滚动时为一个屏幕内可显示的列数，最大值为16。<br/>取值范围：[0, +∞)，设置为小于0的值时，按1处理。<br/>通过状态变量单独更新value值时，Grid组件不会触发布局更新，缓存节点数量仅会在下次布局时更新。 |

## cachedCount

```TypeScript
cachedCount(count: number, show: boolean)
```

设置预加载的GridItem数量，并配置是否显示预加载节点。

设置缓存后会在Grid显示区域上下各缓存cachedCount*列数个GridItem。配合裁剪[clip](arkts-arkui-common-commonmethod-c.md#clip-1)或内容裁剪[clipContent](../../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14)属性可以显示出预加载节点。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-cachedCount(count: number, show: boolean): GridAttribute--><!--Device-GridAttribute-cachedCount(count: number, show: boolean): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 预加载的GridItem的数量。<br/>默认值：垂直滚动时为一个屏幕内可显示的行数，水平滚动时为一个屏幕内可显示的列数，最大值为16。<br/>取值范围：[0, +∞)，设置为小于0的值时，按1处理。<br/>通过状态变量单独更新count值时，Grid组件不会触发布局更新，缓存节点数量仅会在下次布局时更新。 |
| show | boolean | 是 | 被预加载的GridItem是否需要显示。设置为true时显示预加载的GridItem，设置为false时不显示预加载的GridItem。 <br/> 默认值：false |

## cellLength

```TypeScript
cellLength(value: number)
```

设置一行的高度或者一列的宽度。

当layoutDirection是Row/RowReverse时，表示一行的高度。

当layoutDirection是Column/ColumnReverse时，表示一列的宽度。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-cellLength(value: number): GridAttribute--><!--Device-GridAttribute-cellLength(value: number): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 一行的高度或者一列的宽度。<br/>默认值：第一个元素的大小 <br/>单位：vp <br/>取值范围：(0, +∞)，设置为小于等于0的值时，按默认值显示。 |

## columnsGap

```TypeScript
columnsGap(value: Length)
```

设置列与列的间距。设置为小于0的值时，按默认值显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-columnsGap(value: Length): GridAttribute--><!--Device-GridAttribute-columnsGap(value: Length): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 列与列的间距。<br/>默认值：0 <br/>取值范围：[0, +∞) |

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

设置当前网格布局列的数量、固定列宽或最小列宽值，不设置时默认1列。

例如，&nbsp;'1fr&nbsp;1fr&nbsp;2fr'&nbsp;是将父组件分3列，将父组件允许的宽分为4等份，第1列占1份，第2列占1份，第3列占2份。

columnsTemplate('repeat(auto-fit, track-size)')是设置最小列宽值为track-size，自动计算列数和实际列宽。

columnsTemplate('repeat(auto-fill, track-size)')是设置固定列宽值为track-size，自动计算列数。

columnsTemplate('repeat(auto-stretch, track-size)')是设置固定列宽值为track-size，使用columnsGap作为最小列间距，自动计算列数和实际列间距。

其中repeat、auto-fit、auto-fill、auto-stretch为关键字。track-size为列宽，支持的单位包括px、vp、%或有效数字，默认单位为vp，track-size至少包括一个有效列宽。

auto-fit模式和auto-stretch模式只支持track-size为一个有效列宽值，并且auto-stretch模式中的track-size只支持px、vp和有效数字，不支持%。auto-fill模式支持一个或多个有效列宽，如columnsTemplate('repeat(auto-fill, 20)')、columnsTemplate('repeat(auto-fill, 20 80px)')。

使用效果可以参考[示例8](../../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例8设置自适应列数)。

设置为'0fr'时，该列的列宽为0，不显示GridItem。设置为其他非法值时，GridItem显示为固定1列。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-columnsTemplate(value: string): GridAttribute--><!--Device-GridAttribute-columnsTemplate(value: string): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 |  |

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy)
```

设置当前网格组件布局列的数量，不设置时默认1列。

当value设置为string类型时，使用方法参考[columnsTemplate(value: string)](GridAttribute#columnsTemplate(value: string))。

当value设置为ItemFillPolicy类型时，将根据Grid组件宽度对应[断点类型](../../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)确定列数。

例如，ItemFillPolicy.BREAKPOINT_DEFAULT在组件宽度属于sm及更小的断点区间时显示2列，属于md断点区间时显示3列，属于lg及更大的断点区间时显示5列，且每列均为1fr。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-columnsTemplate(value: string | ItemFillPolicy): GridAttribute--><!--Device-GridAttribute-columnsTemplate(value: string | ItemFillPolicy): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| ItemFillPolicy | 是 | 当前网格组件布局列的数量。 |

## edgeEffect

```TypeScript
edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions)
```

设置边缘滑动效果。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions): GridAttribute--><!--Device-GridAttribute-edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [EdgeEffect](../arkts-apis/arkts-arkui-enums-edgeeffect-e.md) | 是 | Grid组件的边缘滑动效果，支持弹簧效果和阴影效果。<br/>默认值：EdgeEffect.None |
| options | [EdgeEffectOptions](arkts-arkui-common-edgeeffectoptions-i.md) | 否 | 组件内容大小小于组件自身时，是否开启滑动效果。设置为{ alwaysEnabled: true }会开启滑动效果，{ alwaysEnabled:false }不开启。<br/>默认值：{ alwaysEnabled: false }<br>**起始版本：** 11 |

## editMode

```TypeScript
editMode(value: boolean)
```

设置Grid是否进入编辑模式，进入编辑模式可以拖拽Grid组件内部[GridItem](arkts-arkui-griditem.md)。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-editMode(value: boolean): GridAttribute--><!--Device-GridAttribute-editMode(value: boolean): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | Grid是否进入编辑模式。设置为true时当前Grid组件处于可编辑模式，设置为false时当前Grid组件处于不可编辑模式。<br/>默认值：false |

## editModeOptions

```TypeScript
editModeOptions(options?: EditModeOptions)
```

配置编辑模式选项参数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-editModeOptions(options?: EditModeOptions): GridAttribute--><!--Device-GridAttribute-editModeOptions(options?: EditModeOptions): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [EditModeOptions](arkts-arkui-common-editmodeoptions-i.md) | 否 | 编辑模式选项。 |

## enableEditMode

```TypeScript
enableEditMode(enabled: boolean | undefined)
```

设置Grid是否启用编辑模式，启用编辑模式后可以在Grid组件内滑动多选[GridItem](arkts-arkui-griditem.md)。未通过该接口设置时，不启用编辑模式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-enableEditMode(enabled: boolean | undefined): GridAttribute--><!--Device-GridAttribute-enableEditMode(enabled: boolean | undefined): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | 是否启用编辑模式。设置为true时启用编辑模式，可以滑动多选，设置为false或undefined时关闭编辑模式，不可滑动多选。 |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

设置是否支持滚动手势。

**说明：**

组件无法通过鼠标按下拖动操作进行滚动。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-enableScrollInteraction(value: boolean): GridAttribute--><!--Device-GridAttribute-enableScrollInteraction(value: boolean): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持滚动手势。设置为true时可以通过手指或者鼠标滚动，设置为false时无法通过手指或者鼠标滚动，但不影响控制器[Scroller](arkts-arkui-scroll-scroller-c.md)的滚动接口。<br/>默认值：true |

## focusWrapMode

```TypeScript
focusWrapMode(mode: Optional<FocusWrapMode>)
```

设置交叉轴方向键走焦模式。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-focusWrapMode(mode: Optional<FocusWrapMode>): GridAttribute--><!--Device-GridAttribute-focusWrapMode(mode: Optional<FocusWrapMode>): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)<FocusWrapMode> | 是 | 交叉轴方向键走焦模式。<br/>默认值：FocusWrapMode.DEFAULT<br/>**说明：** <br/>异常值按默认值处理，即交叉轴方向键不能换行。 |

## friction

```TypeScript
friction(value: number | Resource)
```

设置摩擦系数，手动划动滚动区域时生效，仅影响惯性滚动过程，对惯性滚动过程中的链式效果有间接影响。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-friction(value: number | Resource): GridAttribute--><!--Device-GridAttribute-friction(value: number | Resource): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 摩擦系数。<br/>默认值：非可穿戴设备为0.6，可穿戴设备为0.9。<br/>从API version 11开始，非可穿戴设备默认值为0.7。<br/>从API version 12开始，非可穿戴设备默认值为0.75。<br/>取值范围：(0, +∞)，设置为小于等于0的值时，按默认值处理。 |

## layoutDirection

```TypeScript
layoutDirection(value: GridDirection)
```

设置布局的主轴方向。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-layoutDirection(value: GridDirection): GridAttribute--><!--Device-GridAttribute-layoutDirection(value: GridDirection): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GridDirection](arkts-arkui-grid-griddirection-e.md) | 是 | 布局的主轴方向。<br/>默认值：GridDirection.Row |

## maxCount

```TypeScript
maxCount(value: number)
```

设置可显示的最大行数或列数。设置为小于1的值时，按默认值显示。

当layoutDirection是Row/RowReverse时，表示可显示的最大列数。

当layoutDirection是Column/ColumnReverse时，表示可显示的最大行数。

当maxCount小于minCount时，maxCount和minCount都按默认值处理。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-maxCount(value: number): GridAttribute--><!--Device-GridAttribute-maxCount(value: number): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 可显示的最大行数或列数。<br/>默认值：Infinity |

## minCount

```TypeScript
minCount(value: number)
```

设置可显示的最小行数或列数。设置为小于1的值时，按默认值显示。

当layoutDirection是Row/RowReverse时，表示可显示的最小列数。

当layoutDirection是Column/ColumnReverse时，表示可显示的最小行数。

当minCount大于maxCount时，minCount和maxCount都按默认值处理。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-minCount(value: number): GridAttribute--><!--Device-GridAttribute-minCount(value: number): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 可显示的最小行数或列数。<br/>默认值：1 |

## multiSelectable

```TypeScript
multiSelectable(value: boolean)
```

设置是否开启鼠标框选。开启框选后，可以配合GridItem的selected属性和onSelect事件获取GridItem的选中状态，还可以通过[多态样式](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)设置GridItem的选中态样式（GridItem默认无选中态样式）。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-multiSelectable(value: boolean): GridAttribute--><!--Device-GridAttribute-multiSelectable(value: boolean): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启鼠标框选。<br/>默认值：false<br/>false：关闭框选。true：开启框选。 |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

设置嵌套滚动选项。设置前后两个方向的嵌套滚动模式，实现与父组件的滚动联动。当组件内容大小小于组件自身，且[edgeEffect](GridAttribute#edgeEffect)的options为{alwaysEnabled: false }时，组件自身滑动手势不会触发，嵌套滚动属性不会生效，如果其父滚动组件有滑动手势，则会触发父组件的滑动手势。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-nestedScroll(value: NestedScrollOptions): GridAttribute--><!--Device-GridAttribute-nestedScroll(value: NestedScrollOptions): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-common-nestedscrolloptions-i.md) | 是 | 嵌套滚动选项。 |

## onEditModeChange

```TypeScript
onEditModeChange(callback: Callback<boolean> | undefined)
```

编辑模式状态变化时触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onEditModeChange(callback: Callback<boolean> | undefined): GridAttribute--><!--Device-GridAttribute-onEditModeChange(callback: Callback<boolean> | undefined): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<boolean> \| undefined | 是 | 编辑模式状态变化时触发的回调。<br>传入undefined会取消注册回调。 |

## onItemDragEnter

```TypeScript
onItemDragEnter(event: (event: ItemDragInfo) => void)
```

拖拽进入网格元素范围内时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onItemDragEnter(event: (event: ItemDragInfo) => void): GridAttribute--><!--Device-GridAttribute-onItemDragEnter(event: (event: ItemDragInfo) => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo) => void | 是 | 拖拽点的信息。 |

## onItemDragLeave

```TypeScript
onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void)
```

拖拽离开网格元素时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void): GridAttribute--><!--Device-GridAttribute-onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number) => void | 是 |  |

## onItemDragMove

```TypeScript
onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void)
```

拖拽在网格元素范围内移动时触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void): GridAttribute--><!--Device-GridAttribute-onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void | 是 |  |

## onItemDragStart

```TypeScript
onItemDragStart(event: OnItemDragStartCallback)
```

开始拖拽网格元素时触发。

手指长按GridItem时触发该事件。

由于拖拽检测也需要长按，且事件处理机制优先触发子组件事件，GridItem上绑定[LongPressGesture](../arkts-apis/arkts-arkui-gesture-longpressgestureinterface-i.md)时无法触发拖拽。如有长按和拖拽同时使用的需求可以使用通用拖拽事件。

拖拽浮起的网格元素可在应用窗口内移动，若需限制移动范围，可通过自定义手势实现，具体参考[示例16（实现GridItem自定义拖拽）](../../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例16实现griditem自定义拖拽)。

不支持拖动到Grid边缘时自动滚动，可使用通用拖拽实现，具体参考[示例17（通过拖拽事件实现griditem拖拽）](../../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例17通过拖拽事件实现griditem拖拽)。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onItemDragStart(event: OnItemDragStartCallback): GridAttribute--><!--Device-GridAttribute-onItemDragStart(event: OnItemDragStartCallback): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md) | 是 | 网格元素拖拽开始时触发的回调。<br>API version 22及之前版本，该参数类型为(event: ItemDragInfo,itemIndex: number) =&gt; (() =&gt; any) \| void，其中event和itemIndex参数含义参考[OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md)。<br>**起始版本：** 23 |

## onItemDrop

```TypeScript
onItemDrop(
    event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void,
  )
```

绑定该事件的网格元素可作为拖拽释放目标，当GridItem停止拖拽时触发。

当拖拽释放位置在网格元素之内时，isSuccess会返回true；在网格元素之外时，isSuccess会返回false。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onItemDrop(
    event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void,
  ): GridAttribute--><!--Device-GridAttribute-onItemDrop(
    event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void,
  ): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void | 是 |  |

## onReachEnd

```TypeScript
onReachEnd(event: () => void)
```

网格到达末尾位置时触发。不满一屏并且最后一个子组件末端在Grid内时触发。

Grid边缘效果为弹簧效果时，划动经过末尾位置时触发一次，回弹回末尾位置时再触发一次。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onReachEnd(event: () => void): GridAttribute--><!--Device-GridAttribute-onReachEnd(event: () => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () => void | 是 | 网格到达末尾位置时触发的回调。 |

## onReachStart

```TypeScript
onReachStart(event: () => void)
```

网格到达起始位置时触发。

Grid初始化时会触发一次，Grid滚动到起始位置时触发一次。Grid边缘效果为弹簧效果时，划动经过起始位置时触发一次，回弹回起始位置时再触发一次。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onReachStart(event: () => void): GridAttribute--><!--Device-GridAttribute-onReachStart(event: () => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () => void | 是 | 网格到达起始位置时触发的回调。 |

## onScroll

```TypeScript
onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void)
```

网格滑动时触发。

**起始版本：** 10

**废弃版本：** 12

**替代接口：** onDidScroll

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): GridAttribute--><!--Device-GridAttribute-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (scrollOffset: number, scrollState: ScrollState) => void | 是 | 网格滚动回调，scrollOffset为每帧滚动偏移量，ScrollState为当前滑动状态。 |

## onScrollBarUpdate

```TypeScript
onScrollBarUpdate(event: (index: number, offset: number) => ComputedBarAttribute)
```

在Grid每帧布局结束时触发，可通过该回调设置滚动条的位置及长度。

该接口只用作设置Grid的滚动条位置，不建议开发者在此接口中做业务逻辑处理。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onScrollBarUpdate(event: (index: number, offset: number) => ComputedBarAttribute): GridAttribute--><!--Device-GridAttribute-onScrollBarUpdate(event: (index: number, offset: number) => ComputedBarAttribute): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (index: number, offset: number) => ComputedBarAttribute | 是 | 网格滚动回调，index为当前显示的网格起始位置的索引值，offset为当前显示的网格起始位置元素相对网格显示起始位置的偏移（单位vp），返回ComputedBarAttribute更新滚动条位置和高度。 |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

该接口回调时，事件参数传入即将发生的滑动量，事件处理函数中可根据应用场景计算实际需要的滑动量并作为事件处理函数的返回值返回，网格将按照返回值的实际滑动量进行滑动。

满足以下任一条件时触发该事件：

1. 用户交互（如手指滑动、键鼠操作等）触发滚动。2. Grid惯性滚动。3. 调用[fling](arkts-arkui-scroll-scroller-c.md#fling-1)接口触发滚动。

不触发该事件的条件：

1. 调用除[fling](arkts-arkui-scroll-scroller-c.md#fling-1)接口外的其他滚动控制接口。2. 越界回弹。3. 拖动滚动条。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): GridAttribute--><!--Device-GridAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | 是 | 每帧滚动开始回调函数。<br>**起始版本：** 20 |

## onScrollIndex

```TypeScript
onScrollIndex(event: (first: number, last: number) => void)
```

当前网格显示的起始位置/终止位置的item发生变化时触发。网格初始化时会触发一次。Grid显示区域上第一个子组件/最后一个组件的索引值有变化就会触发。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onScrollIndex(event: (first: number, last: number) => void): GridAttribute--><!--Device-GridAttribute-onScrollIndex(event: (first: number, last: number) => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | (first: number, last: number) => void | 是 | 网格滚动回调，first为当前显示的网格起始位置的索引值，last为当前显示的网格终止位置的索引值。 |

## onScrollStart

```TypeScript
onScrollStart(event: () => void)
```

网格滑动开始时触发。手指拖动网格或网格的滚动条触发的滑动开始时，会触发该事件。使用[Scroller](arkts-arkui-scroll-scroller-c.md)滑动控制器触发的带动画的滑动，动画开始时会触发该事件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onScrollStart(event: () => void): GridAttribute--><!--Device-GridAttribute-onScrollStart(event: () => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () => void | 是 | 网格滑动开始时触发的回调。 |

## onScrollStop

```TypeScript
onScrollStop(event: () => void)
```

网格滑动停止时触发。手指拖动网格或网格的滚动条触发的滑动，手指离开屏幕后滑动停止时会触发该事件。使用[Scroller](arkts-arkui-scroll-scroller-c.md)滑动控制器触发的带动画的滑动，动画停止会触发该事件。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-onScrollStop(event: () => void): GridAttribute--><!--Device-GridAttribute-onScrollStop(event: () => void): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () => void | 是 | 网格滑动停止时触发的回调。 |

## rowsGap

```TypeScript
rowsGap(value: Length)
```

设置行与行的间距。设置为小于0的值时，按默认值显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-rowsGap(value: Length): GridAttribute--><!--Device-GridAttribute-rowsGap(value: Length): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 行与行的间距。<br/>默认值：0 <br/>取值范围：[0, +∞) |

## rowsTemplate

```TypeScript
rowsTemplate(value: string)
```

设置当前网格布局行的数量、固定行高或最小行高值，不设置时默认1行。

例如，&nbsp;'1fr&nbsp;1fr&nbsp;2fr'是将父组件分3行，将父组件允许的高分为4等份，第1行占1份，第2行占1份，第3行占2份。

rowsTemplate('repeat(auto-fit, track-size)')是设置最小行高值为track-size，自动计算行数和实际行高。

rowsTemplate('repeat(auto-fill, track-size)')是设置固定行高值为track-size，自动计算行数。

rowsTemplate('repeat(auto-stretch, track-size)')是设置固定行高值为track-size，使用rowsGap为最小行间距，自动计算行数和实际行间距。

其中repeat、auto-fit、auto-fill、auto-stretch为关键字。track-size为行高，支持的单位包括px、vp、%或有效数字，默认单位为vp，track-size至少包括一个有效行高。

auto-fit模式和auto-stretch模式只支持track-size为一个有效行高值，并且auto-stretch模式中的track-size只支持px、vp和有效数字，不支持%。auto-fill模式支持一个或多个有效行高，如rowsTemplate('repeat(auto-fill, 20)')、rowsTemplate('repeat(auto-fill, 20 80px)')。

设置为'0fr'，则这一行的行高为0，这一行GridItem不显示。设置为其他非法值，按固定1行处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-rowsTemplate(value: string): GridAttribute--><!--Device-GridAttribute-rowsTemplate(value: string): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 |  |

## scrollBar

```TypeScript
scrollBar(value: BarState)
```

设置滚动条状态。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-scrollBar(value: BarState): GridAttribute--><!--Device-GridAttribute-scrollBar(value: BarState): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-enums-barstate-e.md) | 是 | 滚动条状态。<br/>默认值：BarState.Auto<br/>**说明：** <br/>API version 9及以下版本默认值为BarState.Off，API version 10及以上版本的默认值为BarState.Auto。 |

## scrollBarColor

```TypeScript
scrollBarColor(value: Color | number | string)
```

设置滚动条的颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-scrollBarColor(value: Color | number | string): GridAttribute--><!--Device-GridAttribute-scrollBarColor(value: Color | number | string): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Color \| number \| string | 是 | 滚动条的颜色。<br/>默认值：'#182431'（40%不透明度）<br/>number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。<br/>string为rgb或者argb格式颜色，示例：'#ffffff'。 |

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string | Resource)
```

设置滚动条的颜色。与[scrollBarColor](GridAttribute#scrollBarColor(value: Color | number | string))相比， 参数名改为color，并开始支持Resource类型。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-scrollBarColor(color: Color | number | string | Resource): GridAttribute--><!--Device-GridAttribute-scrollBarColor(color: Color | number | string | Resource): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Color \| number \| string \| Resource | 是 | 滚动条的颜色。<br/>默认值：'#182431'（40%不透明度）<br/>number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。 |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string)
```

设置滚动条的宽度，不支持百分比设置。宽度设置后，滚动条正常状态和按压状态宽度均为滚动条的宽度值。如果滚动条的宽度超过Grid组件主轴方向的高度，则滚动条的宽度会变为默认值。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-scrollBarWidth(value: number | string): GridAttribute--><!--Device-GridAttribute-scrollBarWidth(value: number | string): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 滚动条的宽度。<br/>默认值：4<br/>单位：vp<br/>取值范围：设置为小于0的值时，按默认值处理。设置为0时，不显示滚动条。 |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string | Resource)
```

设置滚动条的宽度，不支持百分比设置。宽度设置后，滚动条正常状态和按压状态宽度均为滚动条的宽度值。如果滚动条的宽度超过Grid组件主轴方向的高度，则滚动条的宽度会变为4vp。支持Resource资源类型。

未通过该接口设置时，设置滚动条的宽度为4vp。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-scrollBarWidth(value: number | string | Resource): GridAttribute--><!--Device-GridAttribute-scrollBarWidth(value: number | string | Resource): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 滚动条的宽度。<br/>单位：vp<br/>取值范围：[0, +∞)。设置为小于0的值时，按4vp处理。设置为0时，不显示滚动条。 |

## supportAnimation

```TypeScript
supportAnimation(value: boolean)
```

设置是否支持动画。当前支持GridItem拖拽动画。仅在滚动模式下（只设置rowsTemplate、columnsTemplate其中一个）支持动画。

仅在大小规则的Grid中支持拖拽动画，跨行或跨列场景不支持。

supportAnimation动画效果参考[示例5（Grid拖拽场景）](../../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例5grid拖拽场景)，其他动画效果需要应用自定义拖拽实现。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-supportAnimation(value: boolean): GridAttribute--><!--Device-GridAttribute-supportAnimation(value: boolean): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否支持动画。设置为true时支持GridItem拖拽动画，设置为false时不支持GridItem拖拽动画。<br/>默认值：false |

## supportEmptyBranchInLazyLoading

```TypeScript
supportEmptyBranchInLazyLoading(supported: boolean | undefined)
```

设置当前Grid组件是否支持在LazyForEach或Repeat中使用if/else渲染控制语法生成不包含任何子组件的空分支节点。未设置时不支持空分支节点。此属性初次赋值后不支持更新，所以赋值后无法在支持空分支、不支持空分支行为之间切换。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): GridAttribute--><!--Device-GridAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| supported | boolean \| undefined | 是 | 当前Grid组件是否支持在[LazyForEach](../../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)或[Repeat](../../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)中使用[if/else](../../../../ui/rendering-control/arkts-rendering-control-ifelse.md)渲染控制语法生成一个不含任何子节点的空分支节点。&lt;/br&gt;true表示支持空分支节点；false表示不支持空分支节点。&lt;/br&gt;值为undefined时，按false处理。 |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

设置是否同步加载Grid区域内所有子组件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-GridAttribute-syncLoad(enable: boolean): GridAttribute--><!--Device-GridAttribute-syncLoad(enable: boolean): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否同步加载Grid区域内所有子组件。<br/> true表示同步加载，false表示异步加载。默认值：true。<br/> **说明：** <br/>设置为false时，在首次显示、不带动画scrollToIndex跳转场景，若当帧布局耗时超过50ms，会将Grid区域内尚未布局的子组件延后到下一帧进行布局。 |

