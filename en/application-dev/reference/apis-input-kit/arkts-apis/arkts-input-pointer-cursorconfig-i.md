# CursorConfig

```TypeScript
interface CursorConfig
```

Defines custom cursor configuration.

**Since:** 15

<!--Device-pointer-interface CursorConfig--><!--Device-pointer-interface CursorConfig-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## followSystem

```TypeScript
followSystem : boolean
```

Whether to adjust the cursor size based on system settings. The value **false** indicates using the custom cursor style size, and **true** indicates adjusting the cursor size based on system settings. The adjustable range is [cursor resource image size, 256×256].

**Type:** boolean

**Since:** 15

<!--Device-CursorConfig-followSystem : boolean--><!--Device-CursorConfig-followSystem : boolean-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Pointer
