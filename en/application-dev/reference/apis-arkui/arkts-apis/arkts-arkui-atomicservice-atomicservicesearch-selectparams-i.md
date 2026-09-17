# SelectParams

Provides optional attributes for the selection area.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## onSelect

```TypeScript
onSelect?: OnSelectCallback
```

Callback when the select is selected.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowPosition

```TypeScript
arrowPosition?: ArrowPosition
```

Set the layout direction for text and arrow in select.

**Type:** [ArrowPosition](../arkts-components/arkts-arkui-arrowposition-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## divider

```TypeScript
divider?: Optional<DividerOptions> | null
```

Sets the divider of select.

**Type:** [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[DividerOptions](../arkts-components/arkts-arkui-divideroptions-i.md)&gt; &#124; null

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

Sets the text properties of the select button itself.

**Type:** Font

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

Sets the text color of the select button itself.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuAlign

```TypeScript
menuAlign?: MenuAlignParams
```

Set the alignment between select and menu.

**Type:** [MenuAlignParams](arkts-arkui-atomicservice-atomicservicesearch-menualignparams-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuBackgroundBlurStyle

```TypeScript
menuBackgroundBlurStyle?: BlurStyle
```

Set menu background blur Style.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-blurstyle-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuBackgroundColor

```TypeScript
menuBackgroundColor?: ResourceColor
```

Set the menu's background color.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## menuItemContentModifier

```TypeScript
menuItemContentModifier?: ContentModifier<MenuItemConfiguration>
```

Register a ContentModifier for each menu item.

**Type:** [ContentModifier](../arkts-components/arkts-arkui-contentmodifier-i.md)&lt;[MenuItemConfiguration](../arkts-components/arkts-arkui-menuitemconfiguration-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## optionBgColor

```TypeScript
optionBgColor?: ResourceColor
```

Sets the background color of the select item.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## optionFont

```TypeScript
optionFont?: Font
```

Sets the text style for select items.

**Type:** Font

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## optionFontColor

```TypeScript
optionFontColor?: ResourceColor
```

Sets the text color for select items.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## optionHeight

```TypeScript
optionHeight?: Dimension
```

Set the height of each option.

**Type:** [Dimension](arkts-arkui-dimension-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options?: Array<SelectOption>
```

SubOption array of the select.

**Type:** Array&lt;[SelectOption](../arkts-components/arkts-arkui-selectoption-i.md)&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## optionWidth

```TypeScript
optionWidth?: Dimension | OptionWidthMode
```

Set the width of each option and set whether the option width fit the trigger.

**Type:** [Dimension](arkts-arkui-dimension-t.md) &#124; [OptionWidthMode](arkts-arkui-optionwidthmode-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: number
```

The default selected index.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedOptionBgColor

```TypeScript
selectedOptionBgColor?: ResourceColor
```

Sets the background color of the selected items in the select.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedOptionFont

```TypeScript
selectedOptionFont?: Font
```

Sets the text style of the selected items in the select.

**Type:** Font

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedOptionFontColor

```TypeScript
selectedOptionFontColor?: ResourceColor
```

Sets the text color of the selected item in the select.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectValue

```TypeScript
selectValue?: ResourceStr
```

The default text value.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: Length
```

Set the space for text and icon in select.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
