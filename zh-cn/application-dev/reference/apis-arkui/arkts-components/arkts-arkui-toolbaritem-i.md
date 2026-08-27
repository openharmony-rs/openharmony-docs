# ToolbarItem

工具栏可配置参数。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## action

```TypeScript
action?: () => void
```

当前选项被选中的事件回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activeIcon

```TypeScript
activeIcon?: ResourceStr
```

工具栏单个选项处于ACTIVE态时的图标资源路径。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activeSymbolIcon

```TypeScript
activeSymbolIcon?: SymbolGlyphModifier
```

工具栏单个选项处于ACTIVE态时的symbol资源（优先级高于activeIcon）。  
**说明：**不支持通过[SymbolGlyphModifier](../arkts-apis/arkts-arkui-symbolglyphmodifier-c.md)对象的 fontSize属性修改图标大小、effectStrategy 属性修改动效、[symbolEffect](arkts-arkui-symbolglyph-attribute.md#symboleffect)属性修改动 效类型。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

工具栏单个选项的图标资源路径。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status?: ToolbarItemStatus
```

工具栏单个选项的状态。默认值：ToolbarItemStatus.NORMAL

**类型：** [ToolbarItemStatus](arkts-arkui-toolbaritemstatus-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

工具栏单个选项的symbol资源（优先级高于icon）。  
**说明：**不支持通过[SymbolGlyphModifier](../arkts-apis/arkts-arkui-symbolglyphmodifier-c.md)对象的 fontSize属性修改图标大小、effectStrategy 属性修改动效、[symbolEffect](arkts-arkui-symbolglyph-attribute.md#symboleffect)属性修改动 效类型。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

工具栏单个选项的显示文本。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
