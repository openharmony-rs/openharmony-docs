# GridLayoutOptions

Grid布局选项。其中，irregularIndexes和onGetIrregularSizeByIndex可对仅设置rowsTemplate或columnsTemplate的Grid使用，可以指定一个index数组，并为其中的index对应的GridItem设置其占据的行数与列数，使用方法参见[示例3](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)；onGetRectByIndex可对同时设置rowsTemplate和columnsTemplate的Grid使用，为指定的index对应的GridItem设置位置和大小，使用方法参见[示例1](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例1固定行列grid)。

为提高Grid在包含大小不规则节点场景布局性能和准确性，可以使用onGetStartIndexByOffset和onGetStartIndexByIndex两个回调类型参数，两个回调必须同时设置才能生效。该场景下，建议设置[onScrollBarUpdate](#onscrollbarupdate)来精准定位滚动条的位置。

为提高Grid在跳转、列数变化等场景的性能，应该尽量使用GridLayoutOptions。即使Grid中没有任何特殊的跨行跨列节点，也可以通过使用'Grid(this.scroller, {regularSize: [1, 1]})'的方式提高跳转性能。参考<!--RP1-->[使用GridLayoutOptions提升Grid性能](../../../performance/grid_optimization.md#使用gridlayoutoptions提升grid性能)<!--RP1End-->。

**起始版本：** 10

<!--Device-unnamed-declare interface GridLayoutOptions--><!--Device-unnamed-declare interface GridLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## irregularIndexes

```TypeScript
irregularIndexes?: number[]
```

指定索引的GridItem在Grid中的大小是不规则的。当不设置onGetIrregularSizeByIndex时，irregularIndexes中GridItem的默认大小为垂直滚动Grid的一整行或水平滚动Grid的一整列。

**类型：** number[]

**默认值：** number[] no irregular grid item

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutOptions-irregularIndexes?: number[]--><!--Device-GridLayoutOptions-irregularIndexes?: number[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetIrregularSizeByIndex

```TypeScript
onGetIrregularSizeByIndex?: (index: number) => [number, number]
```

Called to return the size of the irregular grid items with the specified index in [rows, columns].

**类型：** (index: number) =&gt; [number, number]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutOptions-onGetIrregularSizeByIndex?: (index: number) => [number, number]--><!--Device-GridLayoutOptions-onGetIrregularSizeByIndex?: (index: number) => [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetRectByIndex

```TypeScript
onGetRectByIndex?: (index: number) => [number, number, number, number]
```

Called to return the size of the grid items with the specified index in [rowStart, columnStart, rowSpan, columnSpan].

**类型：** (index: number) =&gt; [number, number, number, number]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutOptions-onGetRectByIndex?: (index: number) => [number, number, number, number]--><!--Device-GridLayoutOptions-onGetRectByIndex?: (index: number) => [number, number, number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## regularSize

```TypeScript
regularSize: [number, number]
```

大小规则的GridItem在Grid中占的行数和列数，只支持占1行1列即[1, 1]。

**类型：** [number, number]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutOptions-regularSize: [number, number]--><!--Device-GridLayoutOptions-regularSize: [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

