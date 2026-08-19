# EditModeOptions

Define edit mode options.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface EditModeOptions--><!--Device-unnamed-export declare interface EditModeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableGatherSelectedItemsAnimation

```TypeScript
enableGatherSelectedItemsAnimation?: boolean
```

Define whether to gather selected items in grid or list when item is long pressed for context menu.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditModeOptions-enableGatherSelectedItemsAnimation?: boolean--><!--Device-EditModeOptions-enableGatherSelectedItemsAnimation?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableTwoFingerMultiSelect

```TypeScript
enableTwoFingerMultiSelect?: boolean
```

Enable two-finger swipe multi-selection. {@code true} indicates that two-finger swiping can enter edit mode and perform multi-selection. {@code false} indicates that two-finger swiping cannot perform multi-selection.

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditModeOptions-enableTwoFingerMultiSelect?: boolean--><!--Device-EditModeOptions-enableTwoFingerMultiSelect?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetPreviewBadge

```TypeScript
onGetPreviewBadge?: OnGetPreviewBadgeCallback
```

Called to return whether to display the number badge or the number displayed on the badge for the context menu preview. If not set, the number of selected items within the display range will be used. Returning false means not displaying the badge. Returning true means using the number of selected items within the display range. Returning a number to include selected items outside the display range.

**类型：** [OnGetPreviewBadgeCallback](arkts-na-ongetpreviewbadgecallback-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditModeOptions-onGetPreviewBadge?: OnGetPreviewBadgeCallback--><!--Device-EditModeOptions-onGetPreviewBadge?: OnGetPreviewBadgeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useDefaultMultiSelectStyle

```TypeScript
useDefaultMultiSelectStyle?: boolean
```

Use default multi-select style. {@code true} indicates that the check box is displayed for GridItem or ListItem after entering the multi-select state. {@code false} indicates that there is no default style after entering the multi-select state.

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EditModeOptions-useDefaultMultiSelectStyle?: boolean--><!--Device-EditModeOptions-useDefaultMultiSelectStyle?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

