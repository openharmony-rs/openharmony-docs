# InputEvent

```TypeScript
export declare interface InputEvent
```

The **inputEvent** module provides the basic events reported by the device.

@interface InputEvent [since 9 - 11]

**Since:** 9

<!--Device-unnamed-export declare interface InputEvent--><!--Device-unnamed-export declare interface InputEvent-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## Modules to Import

```TypeScript
import { InputEvent } from '@kit.InputKit';
```

## actionTime

```TypeScript
actionTime: number
```

Time when an input event is reported, in microseconds (μs) since the system starts.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-InputEvent-actionTime: long--><!--Device-InputEvent-actionTime: long-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## deviceId

```TypeScript
deviceId: number
```

Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-InputEvent-deviceId: int--><!--Device-InputEvent-deviceId: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## id

```TypeScript
id: number
```

Enumerates event IDs.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-InputEvent-id: int--><!--Device-InputEvent-id: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## screenId

```TypeScript
screenId: number
```

Target screen ID.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-InputEvent-screenId: int--><!--Device-InputEvent-screenId: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core

## windowId

```TypeScript
windowId: number
```

Target window ID.

**Type:** number

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-InputEvent-windowId: int--><!--Device-InputEvent-windowId: int-End-->

**System capability:** SystemCapability.MultimodalInput.Input.Core
