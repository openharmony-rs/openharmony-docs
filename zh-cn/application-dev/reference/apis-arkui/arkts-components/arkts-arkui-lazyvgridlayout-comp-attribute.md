# LazyVGridLayout属性/事件

```TypeScript
declare class LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>
```

除支持[通用属性](arkts-arkui-common-comp.md)外，还支持以下属性：

除支持[通用事件](arkts-arkui-common-comp.md)外，还支持以下事件：

**继承/实现关系：** LazyVGridLayoutAttribute extends LazyGridLayoutAttribute&lt;LazyVGridLayoutAttribute&gt;

**起始版本：** 19

<!--Device-unnamed-declare class LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>--><!--Device-unnamed-declare class LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

设置当前网格布局列的数量、固定列宽或最小列宽值，不设置时默认1列。

例如，'1fr&nbsp;1fr&nbsp;2fr'&nbsp;表示将父组件分为3列，将父组件允许的宽度分为4等份，第一列占1份，第二列占1份，第三列占2份。

columnsTemplate('repeat(auto-fit, track-size)')是设置最小列宽值为track-size，自动计算列数和实际列宽。

columnsTemplate('repeat(auto-fill, track-size)')是设置固定列宽值为track-size，自动计算列数。

columnsTemplate('repeat(auto-stretch, track-size)')是设置固定列宽值为track-size，使用columnsGap作为最小列间距，自动计算列数和实际列间距。

其中repeat、auto-fit、auto-fill、auto-stretch为关键字。track-size为列宽，支持的单位包括px、vp、%或有效数字，默认单位为vp，track-size至少包括一个有效列宽。

auto-fit模式和auto-stretch模式只支持track-size为一个有效列宽值，并且auto-stretch模式中的track-size只支持px、vp和有效数字，不支持%。auto-fill模式支持一个或多个有效列宽，如columnsTemplate('repeat(auto-fill, 20)')、columnsTemplate('repeat(auto-fill, 20 80px)')。

非repeat形式的模板串中每项仅支持'数字+fr'、'数字+px'、'数字+%'三种格式，不支持vp（如columnsTemplate('100vp 100vp')）。需要按固定vp尺寸自动计算列数时，应使用repeat(auto-fill, track-size)。

使用效果可以参考[示例3](../../../reference/apis-arkui/arkui-ts/ts-container-lazyvgridlayout.md#示例3设置自适应列数)。

设置为'0fr'时，该列的列宽为0，不显示子组件。设置为其他非法值时，子组件显示为固定1列。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

<!--Device-LazyVGridLayoutAttribute-columnsTemplate(value: string): LazyVGridLayoutAttribute--><!--Device-LazyVGridLayoutAttribute-columnsTemplate(value: string): LazyVGridLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 当前网格布局列的数量、固定列宽或最小列宽值。 |

## columnsTemplate

```TypeScript
columnsTemplate(template: string | ItemFillPolicy)
```

设置当前网格布局列的数量、固定列宽或最小列宽值，不设置时默认1列。

当template设置为string类型时，使用方法参考[columnsTemplate(value: string)](#columnstemplate-1)。

当template设置为ItemFillPolicy类型时，将根据LazyVGridLayout内容区宽度对应的[断点类型](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)确定列数。

断点判断使用的内容区宽度：内容区宽度 = 组件宽度 − 左右内边距（padding）− 占用布局的左右边框（border）宽度。

例如，ItemFillPolicy的fillType属性设置为PresetFillType.BREAKPOINT_DEFAULT时，在内容区宽度属于sm及更小的断点区间时显示2列，属于md断点区间时显示3列，属于lg及更大的断点区间时显示5列，且每列均为1fr。

> **说明：** 
> 
> string类型和ItemFillPolicy类型设置的是同一个属性，多次设置时以最后一次设置为准。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-LazyVGridLayoutAttribute-columnsTemplate(template: string | ItemFillPolicy): LazyVGridLayoutAttribute--><!--Device-LazyVGridLayoutAttribute-columnsTemplate(template: string | ItemFillPolicy): LazyVGridLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| template | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | 是 | 当前网格布局列的数量。 |
