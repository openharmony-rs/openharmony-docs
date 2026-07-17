# MenuElement

菜单项的图标、文本和交互信息。

**起始版本：** 7

<!--Device-unnamed-declare interface MenuElement--><!--Device-unnamed-declare interface MenuElement-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: () => void
```

点击菜单项的事件回调。

**类型：** () => void

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuElement-action: () => void--><!--Device-MenuElement-action: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

菜单条目是否可进行交互。

true：菜单条目可以进行交互；false：菜单条目不可以进行交互。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuElement-enabled?: boolean--><!--Device-MenuElement-enabled?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

菜单项图标。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuElement-icon?: ResourceStr--><!--Device-MenuElement-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

设置菜单项图标。通过Modifier配置菜单项图标，若同时配置symbolIcon和icon的情况下，icon图标不显示。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MenuElement-symbolIcon?: SymbolGlyphModifier--><!--Device-MenuElement-symbolIcon?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

菜单项文本。

**类型：** ResourceStr

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-MenuElement-value: ResourceStr--><!--Device-MenuElement-value: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

