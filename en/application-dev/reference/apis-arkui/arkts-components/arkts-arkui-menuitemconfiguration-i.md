# MenuItemConfiguration

You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md).

**Inheritance/Implementation:** MenuItemConfiguration extends CommonConfiguration<MenuItemConfiguration>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## triggerSelect

```TypeScript
triggerSelect(index: number, value: string): void
```

Invoked when a drop-down menu option is selected. <br>**NOTE:** <br>The value of **index** will be assigned to the **index** parameter in the [onSelect](arkts-arkui-select-comp-attribute.md#onselect) callback; the value of **value** will be returned to the **Select** component for display and will also be assigned to the **value** parameter in the [onSelect](arkts-arkui-select-comp-attribute.md#onselect) callback.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | index of the selected option. |
| value | string | Yes | text of the selected option. |

## icon

```TypeScript
icon?: ResourceStr
```

Icon of the drop-down menu option.

**NOTE:** 

The string type can be used to load network images and local images.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the drop-down menu option. The index is zero-based.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected: boolean
```

Whether the drop-down menu option is selected. The value **true** means that the option is selected, and **false** means the opposite.

Default value: **false**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## symbolIcon

```TypeScript
symbolIcon?: SymbolGlyphModifier
```

Symbol icon of drop-down menu option.

**symbolIcon** takes precedence over **icon**.

**Type:** [SymbolGlyphModifier](arkts-arkui-symbolglyphmodifier-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Text content of the drop-down menu option.

**NOTE:** 

If the length of the text exceeds the width of the menu item text area, the text will be truncated.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
