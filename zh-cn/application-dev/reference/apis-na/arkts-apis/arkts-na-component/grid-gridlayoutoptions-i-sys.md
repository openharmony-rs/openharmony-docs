# GridLayoutOptions

Grid布局选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface GridLayoutOptions--><!--Device-unnamed-export declare interface GridLayoutOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetStartIndexByIndex

```TypeScript
onGetStartIndexByIndex?: OnGetStartIndexByIndexCallback
```

根据指定的目标索引，计算Grid滚动到该位置时页面内的起始行，用于支持[scrollToIndex]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_等操作。

**类型：** OnGetStartIndexByIndexCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridLayoutOptions-onGetStartIndexByIndex?: OnGetStartIndexByIndexCallback--><!--Device-GridLayoutOptions-onGetStartIndexByIndex?: OnGetStartIndexByIndexCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## onGetStartIndexByOffset

```TypeScript
onGetStartIndexByOffset?: OnGetStartIndexByOffsetCallback
```

根据Grid滚动的总偏移量，计算Grid当前页面起始行位置，用于快速滑动或反向滑动场景。

**类型：** OnGetStartIndexByOffsetCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridLayoutOptions-onGetStartIndexByOffset?: OnGetStartIndexByOffsetCallback--><!--Device-GridLayoutOptions-onGetStartIndexByOffset?: OnGetStartIndexByOffsetCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

