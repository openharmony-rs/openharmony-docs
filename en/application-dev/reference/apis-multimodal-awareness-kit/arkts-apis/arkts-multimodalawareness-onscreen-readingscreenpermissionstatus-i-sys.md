# ReadingScreenPermissionStatus (System API)

Returns the status of the permission for reading screen information.

**Since:** 23

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## readingCode

```TypeScript
readingCode?: number
```

If the screen information cannot be read, the corresponding status code will be returned.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## readingState

```TypeScript
readingState: number
```

Whether screen reading is allowed. **0**: no; **1**: yes.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
