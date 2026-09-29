# PatternOptions

```TypeScript
export interface PatternOptions
```

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

Mandatory. Callback invoked when the pattern option changes.

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

Optional. Default selected pattern.

**Type:** number

**Since:** 11

<!--Device-PatternOptions-defaultSelected?: int--><!--Device-PatternOptions-defaultSelected?: int-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## patterns

```TypeScript
patterns: Array<Pattern>
```

Mandatory. Resource of the pattern option.

**Type:** Array&lt;[Pattern](arkts-ime-inputmethodlist-pattern-i.md)&gt;

**Since:** 11

<!--Device-PatternOptions-patterns: Array<Pattern>--><!--Device-PatternOptions-patterns: Array<Pattern>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework
