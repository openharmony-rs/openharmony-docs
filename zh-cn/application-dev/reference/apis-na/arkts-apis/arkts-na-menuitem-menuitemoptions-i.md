# MenuItemOptions

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface MenuItemOptions--><!--Device-unnamed-export declare interface MenuItemOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

用于构建二级菜单。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemOptions-builder?: CustomBuilder--><!--Device-MenuItemOptions-builder?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

MenuItem的内容。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemOptions-content?: ResourceStr--><!--Device-MenuItemOptions-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endIcon

```TypeScript
endIcon?: ResourceStr
```

MenuItem的末尾图标。不支持Symbol图标。使用Symbol图标时，须使用symbolEndIcon。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemOptions-endIcon?: ResourceStr--><!--Device-MenuItemOptions-endIcon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## labelInfo

```TypeScript
labelInfo?: ResourceStr
```

MenuItem结束的标签信息，如快捷方式Ctrl+C等。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemOptions-labelInfo?: ResourceStr--><!--Device-MenuItemOptions-labelInfo?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startIcon

```TypeScript
startIcon?: ResourceStr
```

MenuItem的起始图标。不支持Symbol图标。使用Symbol图标时，须使用symbolStartIcon。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemOptions-startIcon?: ResourceStr--><!--Device-MenuItemOptions-startIcon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolEndIcon

```TypeScript
symbolEndIcon?: SymbolGlyphModifier
```

MenuItem末尾的Symbol图标。配置该项时，原先endIcon图标不显示。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [SymbolGlyphModifier](../../apis-arkui/arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemOptions-symbolEndIcon?: SymbolGlyphModifier--><!--Device-MenuItemOptions-symbolEndIcon?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStartIcon

```TypeScript
symbolStartIcon?: SymbolGlyphModifier
```

MenuItem起始的Symbol图标。配置该项时，原先startIcon图标不显示。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [SymbolGlyphModifier](../../apis-arkui/arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MenuItemOptions-symbolStartIcon?: SymbolGlyphModifier--><!--Device-MenuItemOptions-symbolStartIcon?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

