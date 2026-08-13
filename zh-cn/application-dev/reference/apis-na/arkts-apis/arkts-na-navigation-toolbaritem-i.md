# ToolbarItem

工具栏可配置参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ToolbarItem--><!--Device-unnamed-export declare interface ToolbarItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: () => void
```

当前选项被选中的事件回调。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItem-action?: () => void--><!--Device-ToolbarItem-action?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activeIcon

```TypeScript
activeIcon?: ResourceStr
```

工具栏单个选项处于ACTIVE态时的图标资源路径。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItem-activeIcon?: ResourceStr--><!--Device-ToolbarItem-activeIcon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activeSymbolIcon

```TypeScript
activeSymbolIcon?: SymbolGlyphModifier
```

工具栏单个选项处于ACTIVE态时的symbol资源（优先级高于activeIcon）。 **说明：** 不支持通过SymbolGlyphModifier对象的 [fontSize](../../../reference/apis-arkui/arkui-ts/ts-basic-components-symbolGlyph.md#fontsize)属性修改图标大小、 [effectStrategy](../../../reference/apis-arkui/arkui-ts/ts-basic-components-symbolGlyph.md#effectstrategy)属性修改动效 、[symbolEffect](../../../reference/apis-arkui/arkui-ts/ts-basic-components-symbolGlyph.md#symboleffect12)属性修改动效类 型。

**类型：** [SymbolGlyphModifier](../../apis-arkui/arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItem-activeSymbolIcon?: SymbolGlyphModifier--><!--Device-ToolbarItem-activeSymbolIcon?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: ResourceStr
```

工具栏单个选项的图标资源路径。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItem-icon?: ResourceStr--><!--Device-ToolbarItem-icon?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status?: ToolbarItemStatus
```

工具栏单个选项的状态。 默认值： ToolbarItemStatus.NORMAL。

**类型：** [ToolbarItemStatus](arkts-na-navigation-toolbaritemstatus-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItem-status?: ToolbarItemStatus--><!--Device-ToolbarItem-status?: ToolbarItemStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

工具栏单个选项的symbol资源（优先级高于icon）。

**类型：** [SymbolGlyphModifier](../../apis-arkui/arkts-components/arkts-arkui-symbolglyphmodifier-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItem-symbolIcon?: SymbolGlyphModifier--><!--Device-ToolbarItem-symbolIcon?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr | undefined
```

工具栏单个选项的显示文本。

**类型：** [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolbarItem-value: ResourceStr | undefined--><!--Device-ToolbarItem-value: ResourceStr | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

