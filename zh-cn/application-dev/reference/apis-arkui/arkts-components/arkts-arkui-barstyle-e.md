# BarStyle

标题栏或工具栏的布局样式。NavDestination的工具栏不支持设置该属性。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

指定该模式的标题栏或工具栏与内容区采用上下布局。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## STACK

```TypeScript
STACK = 1
```

指定该模式的标题栏或工具栏与内容区采用层叠布局，标题栏或工具栏布局在内容区上层。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SAFE_AREA_PADDING

```TypeScript
SAFE_AREA_PADDING = 2
```

将指定该模式的标题栏或工具栏设置为[组件级安全区](arkts-arkui-commonmethod-c.md#safeareapadding-1)。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

