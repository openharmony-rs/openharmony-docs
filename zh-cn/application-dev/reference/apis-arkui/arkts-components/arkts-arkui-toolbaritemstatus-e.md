# ToolbarItemStatus

工具栏单个选项的状态。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NORMAL

```TypeScript
NORMAL = 0
```

设置工具栏单个选项为NORMAL态，该选项显示默认样式，可以触发Hover，Press，Focus事件并显示对应的多态样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DISABLED

```TypeScript
DISABLED = 1
```

设置工具栏单个选项为DISABLED态， 该选项显示DISABLED态样式，并且不可交互。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ACTIVE

```TypeScript
ACTIVE = 2
```

设置工具栏单个选项为ACTIVE态， 该选项通过点击事件可以将icon图标更新为activeIcon对应的图片资源。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

