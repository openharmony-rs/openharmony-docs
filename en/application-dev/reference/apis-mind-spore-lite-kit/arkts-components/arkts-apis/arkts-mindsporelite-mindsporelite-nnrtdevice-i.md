# NNRTDevice

```TypeScript
interface NNRTDevice
```

Provides the NNRT device info

**Since:** 10

<!--Device-mindSporeLite-interface NNRTDevice--><!--Device-mindSporeLite-interface NNRTDevice-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## Modules to Import

```TypeScript
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## deviceID

```TypeScript
deviceID?: bigint
```

NNRT device id.

**Type:** bigint

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-NNRTDevice-deviceID?: bigint--><!--Device-NNRTDevice-deviceID?: bigint-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## extensions

```TypeScript
extensions?: Extension[]
```

NNRT device extension array.

**Type:** [Extension](arkts-mindsporelite-mindsporelite-extension-i.md)[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-NNRTDevice-extensions?: Extension[]--><!--Device-NNRTDevice-extensions?: Extension[]-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## performanceMode

```TypeScript
performanceMode?: PerformanceMode
```

NNRT device performance mode.

**Type:** [PerformanceMode](arkts-mindsporelite-mindsporelite-performancemode-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-NNRTDevice-performanceMode?: PerformanceMode--><!--Device-NNRTDevice-performanceMode?: PerformanceMode-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## priority

```TypeScript
priority?: Priority
```

NNRT device priority.

**Type:** [Priority](arkts-mindsporelite-mindsporelite-priority-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-NNRTDevice-priority?: Priority--><!--Device-NNRTDevice-priority?: Priority-End-->

**System capability:** SystemCapability.AI.MindSporeLite
