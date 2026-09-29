# OnscreenAwarenessCap (System API)

```TypeScript
export interface OnscreenAwarenessCap
```

Defines onscreen awareness capabilities (including but not limited to awareness in a reading scenario and OCR).

**Since:** 23

<!--Device-onScreen-export interface OnscreenAwarenessCap--><!--Device-onScreen-export interface OnscreenAwarenessCap-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## capList

```TypeScript
capList?: string[]
```

Capability list, including the capabilities for obtaining page content, page link, and text selection.

**Type:** string[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OnscreenAwarenessCap-capList?: string[]--><!--Device-OnscreenAwarenessCap-capList?: string[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## groupId

```TypeScript
groupId?: string
```

Service group ID.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-OnscreenAwarenessCap-groupId?: string--><!--Device-OnscreenAwarenessCap-groupId?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
