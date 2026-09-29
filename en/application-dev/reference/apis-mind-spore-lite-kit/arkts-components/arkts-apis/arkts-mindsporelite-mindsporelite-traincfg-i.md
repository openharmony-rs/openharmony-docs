# TrainCfg

```TypeScript
interface TrainCfg
```

Provides the train configuration

**Since:** 12

<!--Device-mindSporeLite-interface TrainCfg--><!--Device-mindSporeLite-interface TrainCfg-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## Modules to Import

```TypeScript
import { mindSporeLite } from '@kit.MindSporeLiteKit';
```

## lossName

```TypeScript
lossName?: string[]
```

Array of loss name

**Type:** string[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-TrainCfg-lossName?: string[]--><!--Device-TrainCfg-lossName?: string[]-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## optimizationLevel

```TypeScript
optimizationLevel?: OptimizationLevel
```

Train optimization level

**Type:** [OptimizationLevel](arkts-mindsporelite-mindsporelite-optimizationlevel-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-TrainCfg-optimizationLevel?: OptimizationLevel--><!--Device-TrainCfg-optimizationLevel?: OptimizationLevel-End-->

**System capability:** SystemCapability.AI.MindSporeLite
