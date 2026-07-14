# GridLayoutOptions

Grid布局选项。其中，irregularIndexes和onGetIrregularSizeByIndex可对仅设置rowsTemplate或columnsTemplate的Grid使用，可以指定一个index数组，并为其中的
index对应的GridItem设置其占据的行数与列数，使用方法参见
[示例3](../../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例3可滚动grid设置跨行跨列节点)；onGetRectByIndex可对同时设置
rowsTemplate和columnsTemplate的Grid使用，为指定的index对应的GridItem设置位置和大小，使用方法参见
[示例1](../../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#示例1固定行列grid)。

为提高Grid在包含大小不规则节点场景布局性能和准确性，可以使用onGetStartIndexByOffset和onGetStartIndexByIndex两个回调类型参数，两个回调必须同时
设置才能生效。该场景下，建议设置[onScrollBarUpdate](#onscrollbarupdate)来精准定位滚动条的位置。

为提高Grid在跳转、列数变化等场景的性能，应该尽量使用GridLayoutOptions。即使Grid中没有任何特殊的跨行跨列节点，也可以通过使用
'Grid(this.scroller, {regularSize: [1, 1]})'的方式提高跳转性能。参考<!--RP1-->
[使用GridLayoutOptions提升Grid性能](../../../../performance/grid_optimization.md#使用gridlayoutoptions提升grid性能)<!--RP1End-->。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetStartIndexByIndex

```TypeScript
onGetStartIndexByIndex?: OnGetStartIndexByIndexCallback
```

根据指定的目标索引，计算Grid滚动到该位置时页面内的起始行，用于支持[scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex-1)等操作。

**类型：** OnGetStartIndexByIndexCallback

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onGetStartIndexByOffset

```TypeScript
onGetStartIndexByOffset?: OnGetStartIndexByOffsetCallback
```

根据Grid滚动的总偏移量，计算Grid当前页面起始行位置，用于快速滑动或反向滑动场景。

**类型：** OnGetStartIndexByOffsetCallback

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

