# CpuDevice

```TypeScript
interface CpuDevice
```

Provides the CPU device info

**Since:** 10

<!--Device-mindSporeLite-interface CpuDevice--><!--Device-mindSporeLite-interface CpuDevice-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## Modules to Import

```TypeScript
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## precisionMode

```TypeScript
precisionMode?: string
```

The precision mode

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-CpuDevice-precisionMode?: string--><!--Device-CpuDevice-precisionMode?: string-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## threadAffinityCoreList

```TypeScript
threadAffinityCoreList?: number[]
```

The thread affinity core list

**Type:** number[]

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-CpuDevice-threadAffinityCoreList?: int[]--><!--Device-CpuDevice-threadAffinityCoreList?: int[]-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## threadAffinityMode

```TypeScript
threadAffinityMode?: ThreadAffinityMode
```

The thread affinity mode

**Type:** [ThreadAffinityMode](arkts-mindsporelite-mindsporelite-threadaffinitymode-e.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-CpuDevice-threadAffinityMode?: ThreadAffinityMode--><!--Device-CpuDevice-threadAffinityMode?: ThreadAffinityMode-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## threadNum

```TypeScript
threadNum?: number
```

The thread num

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-CpuDevice-threadNum?: int--><!--Device-CpuDevice-threadNum?: int-End-->

**System capability:** SystemCapability.AI.MindSporeLite
