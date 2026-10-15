# OptimizationLevel

```TypeScript
export enum OptimizationLevel
```

Enum for optimization level

**Since:** 12

<!--Device-mindSporeLite-export enum OptimizationLevel--><!--Device-mindSporeLite-export enum OptimizationLevel-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## AUTO

```TypeScript
AUTO = 4
```

Choose optimization based on device

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OptimizationLevel-AUTO = 4--><!--Device-OptimizationLevel-AUTO = 4-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## O0

```TypeScript
O0 = 0
```

Do not change

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OptimizationLevel-O0 = 0--><!--Device-OptimizationLevel-O0 = 0-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## O2

```TypeScript
O2 = 2
```

Cast network to float16, keep batch norm and loss in float32

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OptimizationLevel-O2 = 2--><!--Device-OptimizationLevel-O2 = 2-End-->

**System capability:** SystemCapability.AI.MindSporeLite

## O3

```TypeScript
O3 = 3
```

Cast network to float16, including batch norm

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-OptimizationLevel-O3 = 3--><!--Device-OptimizationLevel-O3 = 3-End-->

**System capability:** SystemCapability.AI.MindSporeLite
