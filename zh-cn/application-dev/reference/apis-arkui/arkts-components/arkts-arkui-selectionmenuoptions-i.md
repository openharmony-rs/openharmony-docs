# SelectionMenuOptions

菜单的选项。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## onAppear

```TypeScript
onAppear?: MenuOnAppearCallback
```

自定义选择菜单弹出时回调。若需在菜单弹出时执行自定义逻辑（如记录用户操作、动态调整菜单内容），可传入此参数；不传入则无额外回调触发。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMenuHide

```TypeScript
onMenuHide?: MenuCallback
```

自定义选择菜单隐藏时回调。若需在菜单隐藏时执行自定义逻辑，可传入此参数；不传入则无回调触发。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onMenuShow

```TypeScript
onMenuShow?: MenuCallback
```

自定义选择菜单显示时回调。若需在菜单显示时执行自定义逻辑，可传入此参数；不传入则无回调触发。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## menuType

```TypeScript
menuType?: MenuType
```

自定义选择菜单类型。默认值：MenuType.SELECTION_MENU。

**类型：** [MenuType](../arkts-apis/arkts-arkui-menutype-e.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDisappear

```TypeScript
onDisappear?: Callback<void>
```

自定义选择菜单关闭时回调。若需在菜单关闭时执行自定义逻辑（如恢复界面状态、清理临时数据），可传入此参数；不传入则无额外回调触发。

**类型：** Callback&lt;void&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## previewMenuOptions

```TypeScript
previewMenuOptions?: PreviewMenuOptions
```

预览菜单的选项。该参数只在RichEditor中生效。从API版本26.0.0开始，该参数在Text组件中也生效。不传入时，预览菜单使用默认配置。

**类型：** [PreviewMenuOptions](arkts-arkui-previewmenuoptions-i.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
