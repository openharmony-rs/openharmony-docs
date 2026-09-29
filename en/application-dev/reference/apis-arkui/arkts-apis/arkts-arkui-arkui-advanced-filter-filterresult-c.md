# FilterResult

```TypeScript
export declare class FilterResult
```

This parameter specifies the selection result of a filtering dimension. The index starts from 0.

**Since:** 10

<!--Device-unnamed-export declare class FilterResult--><!--Device-unnamed-export declare class FilterResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Filter, FilterParams, FilterResult, FilterType } from '@kit.ArkUI';
```

## index

```TypeScript
index: number
```

Index of the selected option of the filter criterion.

Value range: an integer no less than -1

The default value is **-1**, indicating that there is no selected option. Values less than -1 are treated as no selected option.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FilterResult-index: number--><!--Device-FilterResult-index: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: ResourceStr
```

Name of the filter criterion.

The default value is an empty string.

**NOTE:** 

If the text length exceeds the column width, it will be truncated.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FilterResult-name: ResourceStr--><!--Device-FilterResult-name: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: ResourceStr
```

Value of the selected option of the filter criterion.

The default value is an empty string.

**NOTE:** 

If the text length exceeds the column width, it will be truncated.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FilterResult-value: ResourceStr--><!--Device-FilterResult-value: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
