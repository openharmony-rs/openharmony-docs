# Material

```TypeScript
class Material
```

Base class for system material objects.

**Since:** 26.0.0

<!--Device-uiMaterial-class Material--><!--Device-uiMaterial-class Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## empty

```TypeScript
static get empty(): Material
```

Returns an empty material object, which is used to disable the immersive system material effect for a component. The usage method is **uiMaterial.Material.empty**.

In enabled mode, you can set `systemMaterial(uiMaterial.Material.empty)` to individually disable the immersive system material effect for a specific component. If the component does not support the component-level immersive system material API, the material effect cannot be disabled through this method.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-Material-static get empty(): Material--><!--Device-Material-static get empty(): Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
