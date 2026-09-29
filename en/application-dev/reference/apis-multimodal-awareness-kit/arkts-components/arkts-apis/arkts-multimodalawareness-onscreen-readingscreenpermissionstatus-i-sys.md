# ReadingScreenPermissionStatus (System API)

```TypeScript
export interface ReadingScreenPermissionStatus
```

Returns the status of the permission for reading screen information.

**Since:** 23

<!--Device-onScreen-export interface ReadingScreenPermissionStatus--><!--Device-onScreen-export interface ReadingScreenPermissionStatus-End-->

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

<!--Device-ReadingScreenPermissionStatus-readingCode?: int--><!--Device-ReadingScreenPermissionStatus-readingCode?: int-End-->

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

<!--Device-ReadingScreenPermissionStatus-readingState: int--><!--Device-ReadingScreenPermissionStatus-readingState: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
