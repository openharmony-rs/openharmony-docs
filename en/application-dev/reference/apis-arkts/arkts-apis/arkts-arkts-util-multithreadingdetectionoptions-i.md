# MultithreadingDetectionOptions

Multi-thread detection functional parameter configuration

**Since:** 26.0.0

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## abort

```TypeScript
abort?: boolean
```

If abort is **true**, the application will crash, if abort is **false**, the application will not crash. Default **true**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

## frequency

```TypeScript
frequency?: number
```

The sampling frequency of multi-thread detection The value must be an integer, minimum is **100**, maximum is **2147483647**. (default **100**) The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

## interval

```TypeScript
interval?: number
```

The interval of multi-thread detection(min) Errors will be reported again only if the time since the last detection exceeds this interval. The value must be an integer within [0,1440] (default 5min).

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang
