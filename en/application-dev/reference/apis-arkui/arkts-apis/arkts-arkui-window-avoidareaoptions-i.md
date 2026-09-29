# AvoidAreaOptions

```TypeScript
interface AvoidAreaOptions
```

Describes the new area where the window cannot be displayed. The new area is returned when the corresponding event is triggered.

**Since:** 12

<!--Device-window-interface AvoidAreaOptions--><!--Device-window-interface AvoidAreaOptions-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## area

```TypeScript
area: AvoidArea
```

New area returned.

**Type:** [AvoidArea](arkts-arkui-window-avoidarea-i.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AvoidAreaOptions-area: AvoidArea--><!--Device-AvoidAreaOptions-area: AvoidArea-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## type

```TypeScript
type: AvoidAreaType
```

Type of the new area returned.

**Type:** [AvoidAreaType](arkts-arkui-window-avoidareatype-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AvoidAreaOptions-type: AvoidAreaType--><!--Device-AvoidAreaOptions-type: AvoidAreaType-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core
