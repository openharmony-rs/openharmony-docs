# GridLayoutOptions

Grid布局选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface GridLayoutOptions--><!--Device-unnamed-export declare interface GridLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## irregularIndexes

```TypeScript
irregularIndexes?: int[]
```

指定索引的GridItem在Grid中的大小是不规则的。

**类型：** int[]

**默认值：** int[] no irregular grid item

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridLayoutOptions-irregularIndexes?: int[]--><!--Device-GridLayoutOptions-irregularIndexes?: int[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetIrregularSizeByIndex

```TypeScript
onGetIrregularSizeByIndex?: (index: int) => [
        int,
        int
    ]
```

配合irregularIndexes使用，设置不规则GridItem占用的行数和列数。开发者可为irregularIndexes中指明的index对应的GridItem设置占用的行数和列数。在API version 12之前，垂直滚动Grid不支持GridItem占多行，水平滚动Grid不支持GridItem占多列。

**类型：** (index: int) =&gt; [         int,         int     ]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridLayoutOptions-onGetIrregularSizeByIndex?: (index: int) => [        int,        int    ]--><!--Device-GridLayoutOptions-onGetIrregularSizeByIndex?: (index: int) => [        int,        int    ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetRectByIndex

```TypeScript
onGetRectByIndex?: (index: int) => [
        int,
        int,
        int,
        int
    ]
```

设置指定索引index对应的GridItem的位置及大小[rowStart,columnStart,rowSpan,columnSpan]。

**类型：** (index: int) =&gt; [         int,         int,         int,         int     ]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridLayoutOptions-onGetRectByIndex?: (index: int) => [        int,        int,        int,        int    ]--><!--Device-GridLayoutOptions-onGetRectByIndex?: (index: int) => [        int,        int,        int,        int    ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## regularSize

```TypeScript
regularSize: [
        int,
        int
    ]
```

大小规则的GridItem在Grid中占的行数和列数，只支持占1行1列即[1, 1]。

**类型：** [         int,         int     ]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridLayoutOptions-regularSize: [        int,        int    ]--><!--Device-GridLayoutOptions-regularSize: [        int,        int    ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

