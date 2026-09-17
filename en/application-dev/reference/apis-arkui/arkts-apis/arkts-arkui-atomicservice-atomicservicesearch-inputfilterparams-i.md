# InputFilterParams

Sets regular expression for input filtering.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## error

```TypeScript
error?: Callback<string>
```

Callback used to return the filtered-out content when regular expression matching fails. Default value: **undefined**.

**Type:** Callback&lt;string&gt;

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## inputFilterValue

```TypeScript
inputFilterValue: ResourceStr
```

Regular expression.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
