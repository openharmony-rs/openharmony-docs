# NavigationMenuItem

导航菜单项，包括菜单图标和菜单信息。

**起始版本：** 8

<!--Device-unnamed-declare interface NavigationMenuItem--><!--Device-unnamed-declare interface NavigationMenuItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: () => void
```

当前选项被选中的事件回调。

**类型：** () =&gt; void

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMenuItem-action?: () => void--><!--Device-NavigationMenuItem-action?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: string | Resource
```

菜单栏单个选项的图标资源路径。

**类型：** string \| Resource

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMenuItem-icon?: string | Resource--><!--Device-NavigationMenuItem-icon?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isEnabled

```TypeScript
isEnabled?: boolean
```

使能状态，默认使能（false未使能，true使能）。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMenuItem-isEnabled?: boolean--><!--Device-NavigationMenuItem-isEnabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

菜单栏单个选项的symbol资源（优先级高于icon）。

**说明：**

不支持通过[SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-t.md)对象的[fontSize](SymbolGlyphAttribute#fontSize)属性修改图标大小、[effectStrategy](SymbolGlyphAttribute#effectStrategy)属性修改动效、[symbolEffect](SymbolGlyphAttribute#symbolEffect(symbolEffect: SymbolEffect, isActive?: boolean))属性修改动效类型。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMenuItem-symbolIcon?: SymbolGlyphModifier--><!--Device-NavigationMenuItem-symbolIcon?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: string | Resource
```

API version 9：显示菜单栏单个选项的文本。

从API version 10开始，不显示菜单栏单个选项的文本。

**类型：** string \| Resource

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-NavigationMenuItem-value: string | Resource--><!--Device-NavigationMenuItem-value: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

