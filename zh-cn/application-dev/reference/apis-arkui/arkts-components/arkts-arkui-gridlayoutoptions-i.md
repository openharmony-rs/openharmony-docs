# GridLayoutOptions

Grid布局选项。其中，irregularIndexes和onGetIrregularSizeByIndex可对仅设置rowsTemplate或columnsTemplate的Grid使用，可以指定一个index数组，并为其中的 index对应的GridItem设置其占据的行数与列数，使用方法参见 [示例3](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)；onGetRectByIndex可对同时设置 rowsTemplate和columnsTemplate的Grid使用，为指定的index对应的GridItem设置位置和大小，使用方法参见 [示例1](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例1固定行列grid)。 为提高Grid在跳转、列数变化等场景的性能，应该尽量使用GridLayoutOptions。即使Grid中没有任何特殊的跨行跨列节点，也可以通过使用'Grid(this.scroller, {regularSize: [1, 1]}) '的方式提高跳转性能。参考&lt;!--RP1--&gt; [使用GridLayoutOptions提升Grid性能](../../../performance/grid_optimization.md#使用gridlayoutoptions提升grid性能)&lt;!--RP1End--&gt;。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare interface GridLayoutOptions--><!--Device-unnamed-declare interface GridLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## irregularIndexes

```TypeScript
irregularIndexes?: number[]
```

指定索引的GridItem在Grid中的大小是不规则的。当不设置onGetIrregularSizeByIndex时，irregularIndexes中GridItem的默认大小为垂直滚动Grid的一整行或水平滚动Grid的一整 列。

**类型：** number[]

**默认值：** number[] no irregular grid item

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutOptions-irregularIndexes?: number[]--><!--Device-GridLayoutOptions-irregularIndexes?: number[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetIrregularSizeByIndex

```TypeScript
onGetIrregularSizeByIndex?: (index: number) => [number, number]
```

配合irregularIndexes使用，设置不规则GridItem占用的行数和列数。开发者可为irregularIndexes中指明的index对应的GridItem设置占用的行数和列数。在API version 12之前，垂直 滚动Grid不支持GridItem占多行，水平滚动Grid不支持GridItem占多列。

**类型：** (index: number) =&gt; [number, number]

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutOptions-onGetIrregularSizeByIndex?: (index: number) => [number, number]--><!--Device-GridLayoutOptions-onGetIrregularSizeByIndex?: (index: number) => [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetRectByIndex

```TypeScript
onGetRectByIndex?: (index: number) => [number, number, number, number]
```

设置指定索引index对应的GridItem的位置及大小[rowStart,columnStart,rowSpan,columnSpan]。 其中rowStart为行起始位置，columnStart为列起始位置，无单位。 rowSpan为GridItem占用的行数，columnSpan为GridItem占用的列数，无单位。 rowStart和columnStart取大于等于0的自然数，若取负数时，rowStart和columnStart默认为0。 rowSpan和columnSpan取大于等于1的自然数，若取小数则向下取整，若小于1则按1计算。 **说明：** 第一种情况：某个GridItem发现给它指定的起始位置被占据了，则从起始位置[0,0]开始按顺序从左到右，从上到下寻找起始的放置位置。 第二种情况：如果起始位置没有被占据，但其他位置被占据了，无法显示全部的GridItem大小，则只会布局一部分。

**类型：** (index: number) =&gt; [number, number, number, number]

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-GridLayoutOptions-regularSize: [number, number]--><!--Device-GridLayoutOptions-regularSize: [number, number]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

