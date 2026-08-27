# MenuItemOptions

Menu中的菜单项信息。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## builder

```TypeScript
builder?: CustomBuilder
```

用于构建二级菜单。默认不显示二级菜单。

**类型：** [CustomBuilder](arkts-arkui-custombuilder-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

MenuItem的内容。默认为空字符串。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endIcon

```TypeScript
endIcon?: ResourceStr
```

MenuItem的末尾图标。不支持Symbol图标。使用Symbol图标时，须使用symbolEndIcon。默认不显示末尾图标。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## labelInfo

```TypeScript
labelInfo?: ResourceStr
```

MenuItem结束的标签信息，如快捷方式Ctrl+C等。默认不显示标签信息。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startIcon

```TypeScript
startIcon?: ResourceStr
```

MenuItem的起始图标。不支持Symbol图标。使用Symbol图标时，须使用symbolStartIcon。默认不显示起始图标。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolEndIcon

```TypeScript
symbolEndIcon?: SymbolGlyphModifier
```

MenuItem末尾的Symbol图标。配置该项时，原先endIcon图标不显示。默认不显示Symbol末尾图标。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStartIcon

```TypeScript
symbolStartIcon?: SymbolGlyphModifier
```

MenuItem起始的Symbol图标。配置该项时，原先startIcon图标不显示。默认不显示Symbol起始图标。

**类型：** SymbolGlyphModifier

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
