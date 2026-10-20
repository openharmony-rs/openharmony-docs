# PatternOptions

```TypeScript
export interface PatternOptions
```

Represents the configuration of input method mode options, used to define the switching options for keyboard modes.

**Since:** 11

<!--Device-unnamed-export interface PatternOptions--><!--Device-unnamed-export interface PatternOptions-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
```

## action

```TypeScript
action: (index: number) => void
```

Callback function invoked when the mode option changes. <br> <br>Usage scenario: Set this callback when corresponding logic (such as updating the keyboard layout or saving user preferences) needs to be executed when the user switches the keyboard mode. <br> <br>Use effect: When the user taps a mode option in the input method list dialog, the system invokes this callback and passes the index value of the selected mode in the **patterns** array. <br> <br>Note: The callback parameter index is the index value of the selected mode in the **patterns** array, consistent with the value range of **defaultSelected**. In the callback, **defaultSelected** can be updated based on the index value to keep the selected state consistent with the user's choice the next time the dialog opens.

**Since:** 11

<!--Device-PatternOptions-action: (index: int) => void--><!--Device-PatternOptions-action: (index: int) => void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes |  |

## defaultSelected

```TypeScript
defaultSelected?: number
```

Index of the mode selected by default, corresponding to the index value in the patterns array. <br> <br>Usage scenario: Use this parameter when the default input method needs to preset an initially selected keyboard mode. <br> <br>Use effect: After being set, the mode option corresponding to this index is selected by default when the input method list dialog opens. <br> <br>Value range: [0, **patterns.length** - 1]. If the value is out of this range, it does not take effect, and no mode option is selected when the dialog opens. <br> <br>Default value: If not set, no mode option is selected when the dialog opens. <br> <br>Note: This index value must be within the valid range of the **patterns** array; otherwise, the setting does not take effect.

**Type:** number

**Since:** 11

<!--Device-PatternOptions-defaultSelected?: int--><!--Device-PatternOptions-defaultSelected?: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## patterns

```TypeScript
patterns: Array<Pattern>
```

Array of mode option resources. Each **Pattern** defines the icon and selected-state icon of a keyboard mode. <br> <br>Usage scenario: Configure this parameter when the default input method needs to provide multiple keyboard modes (such as one-handed mode and full-screen mode) for users to choose from. <br> <br>Use effect: After being set, all mode options defined in this array are displayed in the default input method area of the input method list dialog for users to select. <br> <br>Note: The **icon** and **selectedIcon** of each **Pattern** in the **patterns** array must be valid [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-i.md) resource references. It is recommended that you configure at least two mode options to provide a meaningful selection function.

**Type:** Array&lt;[Pattern](arkts-ime-inputmethodlist-pattern-i.md)&gt;

**Since:** 11

<!--Device-PatternOptions-patterns: Array<Pattern>--><!--Device-PatternOptions-patterns: Array<Pattern>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
