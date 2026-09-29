# FilterParams

```TypeScript
export declare class FilterParams
```

This parameter is used to define the input of each filtering dimension.

**Since:** 10

<!--Device-unnamed-export declare class FilterParams--><!--Device-unnamed-export declare class FilterParams-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Filter, FilterParams, FilterResult, FilterType } from '@kit.ArkUI';
```

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

<!--Device-FilterParams-name: ResourceStr--><!--Device-FilterParams-name: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
options: Array<ResourceStr>
```

Options of the filter criterion.

The default value is an empty array.

**NOTE:** 

The text is truncated with an ellipsis (...) if it is too long.

**Type:** Array&lt;[ResourceStr](arkts-arkui-resourcestr-t.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FilterParams-options: Array<ResourceStr>--><!--Device-FilterParams-options: Array<ResourceStr>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
