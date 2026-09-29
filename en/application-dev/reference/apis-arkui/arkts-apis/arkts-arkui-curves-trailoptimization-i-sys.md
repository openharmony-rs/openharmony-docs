# TrailOptimization (System API)

```TypeScript
interface TrailOptimization
```

Trail optimization configuration for spring animations. When the animation progress reaches the threshold, the response value decays each frame to accelerate convergence and optimize the trail duration.

**Since:** 26.0.0

<!--Device-curves-interface TrailOptimization--><!--Device-curves-interface TrailOptimization-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## progressThreshold

```TypeScript
progressThreshold?: number
```

Animation progress threshold. When the animation progress reaches this threshold, rapid convergence starts to optimize the trail duration. For underdamped spring curves, rapid convergence starts when the envelope of the spring curve reaches the progress threshold.

<br> Value range: &lt;0, 1&gt;.

**Type:** number

**Default:** 1

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TrailOptimization-progressThreshold?: number--><!--Device-TrailOptimization-progressThreshold?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## responseDecayFactor

```TypeScript
responseDecayFactor?: number
```

Response decay factor. After rapid convergence starts, the response of each frame becomes the previous frame's response multiplied by this factor to accelerate convergence. Value range: &lt;0, 1&gt;.

**Type:** number

**Default:** 1

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TrailOptimization-responseDecayFactor?: number--><!--Device-TrailOptimization-responseDecayFactor?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
