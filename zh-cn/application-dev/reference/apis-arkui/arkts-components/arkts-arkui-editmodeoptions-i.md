# EditModeOptions

定义编辑模式选项

**起始版本：** 23

<!--Device-unnamed-declare interface EditModeOptions--><!--Device-unnamed-declare interface EditModeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableGatherSelectedItemsAnimation

```TypeScript
enableGatherSelectedItemsAnimation?: boolean
```

定义当项目被长按上下文菜单时，是否在网格或列表中收集选定项目。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-EditModeOptions-enableGatherSelectedItemsAnimation?: boolean--><!--Device-EditModeOptions-enableGatherSelectedItemsAnimation?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableTwoFingerMultiSelect

```TypeScript
enableTwoFingerMultiSelect?: boolean
```

启用双指滑动多选。{@code true}表示双指滑动可以进入编辑模式，进行多选操作。{@code false}表示两指滑动不支持多指滑动。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditModeOptions-enableTwoFingerMultiSelect?: boolean--><!--Device-EditModeOptions-enableTwoFingerMultiSelect?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onGetPreviewBadge

```TypeScript
onGetPreviewBadge?: OnGetPreviewBadgeCallback
```

调用以返回是否显示数字脚本或在上下文菜单预览的角标上显示的数字。如果未设置，将使用显示范围内的选定项的数量作为角标。返回false表示不显示角标。返回true表示使用显示范围内的选定项的数量。返回一个数字以包括显示范围之外的选定项。

**类型：** OnGetPreviewBadgeCallback

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-EditModeOptions-onGetPreviewBadge?: OnGetPreviewBadgeCallback--><!--Device-EditModeOptions-onGetPreviewBadge?: OnGetPreviewBadgeCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useDefaultMultiSelectStyle

```TypeScript
useDefaultMultiSelectStyle?: boolean
```

使用默认的多选样式。{@code true}表示进入多选状态后为GridItem或ListItem显示复选框。{@code false}表示进入多选状态后没有默认样式。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EditModeOptions-useDefaultMultiSelectStyle?: boolean--><!--Device-EditModeOptions-useDefaultMultiSelectStyle?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

