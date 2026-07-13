# SelectionMenuOptions

菜单的选项。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuType

```TypeScript
menuType?: MenuType
```

自定义选择菜单类型。

默认值：MenuType.SELECTION_MENU。

**类型：** MenuType

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本13开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onAppear

```TypeScript
onAppear?: MenuOnAppearCallback
```

自定义选择菜单弹出时回调。

**类型：** MenuOnAppearCallback

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: Callback<void>
```

自定义选择菜单关闭时回调。

**类型：** Callback<void>

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMenuHide

```TypeScript
onMenuHide?: MenuCallback
```

自定义选择菜单隐藏时回调。

**类型：** MenuCallback

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMenuShow

```TypeScript
onMenuShow?: MenuCallback
```

自定义选择菜单显示时回调。

**类型：** MenuCallback

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewMenuOptions

```TypeScript
previewMenuOptions?: PreviewMenuOptions
```

预览菜单的选项。该参数只在RichEditor中生效。

**类型：** PreviewMenuOptions

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

