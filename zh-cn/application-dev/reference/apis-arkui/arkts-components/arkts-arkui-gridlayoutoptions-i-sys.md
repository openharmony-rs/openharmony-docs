# GridLayoutOptions

Grid布局选项。其中，irregularIndexes和onGetIrregularSizeByIndex可对仅设置rowsTemplate或columnsTemplate的Grid使用，可以指定一个index数组，并为其中的 index对应的GridItem设置其占据的行数与列数，使用方法参见 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_；onGetRectByIndex可对同时设置 rowsTemplate和columnsTemplate的Grid使用，为指定的index对应的GridItem设置位置和大小，使用方法参见 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_。 为提高Grid在跳转、列数变化等场景的性能，应该尽量使用GridLayoutOptions。即使Grid中没有任何特殊的跨行跨列节点，也可以通过使用'Grid(this.scroller, {regularSize: [1, 1]}) '的方式提高跳转性能。参考\_\_\_MD\_COMMENT\_DESC\_USD\_3\_\_\_ \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_\_\_\_MD\_COMMENT\_DESC\_USD\_4\_\_\_。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare interface GridLayoutOptions--><!--Device-unnamed-declare interface GridLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetStartIndexByIndex

```TypeScript
onGetStartIndexByIndex?: OnGetStartIndexByIndexCallback
```

根据指定的目标索引，计算Grid滚动到该位置时页面内的起始行，用于支持[scrollToIndex]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_等操作。不设置时不启用该回调，需与 onGetStartIndexByOffset同时设置才能生效。 **系统接口：** 此接口为系统接口。

**类型：** OnGetStartIndexByIndexCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridLayoutOptions-onGetStartIndexByIndex?: OnGetStartIndexByIndexCallback--><!--Device-GridLayoutOptions-onGetStartIndexByIndex?: OnGetStartIndexByIndexCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onGetStartIndexByOffset

```TypeScript
onGetStartIndexByOffset?: OnGetStartIndexByOffsetCallback
```

根据Grid滚动的总偏移量，计算Grid当前页面起始行位置，用于快速滑动或反向滑动场景。不设置时不启用该回调，需与onGetStartIndexByIndex同时设置才能生效。 **系统接口：** 此接口为系统接口。

**类型：** OnGetStartIndexByOffsetCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridLayoutOptions-onGetStartIndexByOffset?: OnGetStartIndexByOffsetCallback--><!--Device-GridLayoutOptions-onGetStartIndexByOffset?: OnGetStartIndexByOffsetCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

