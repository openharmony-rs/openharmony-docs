# InterruptEvent

```TypeScript
interface InterruptEvent
```

Describes the interruption event received by the application when the audio is interrupted.

**Since:** 9

<!--Device-audio-interface InterruptEvent--><!--Device-audio-interface InterruptEvent-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## eventType

```TypeScript
eventType: InterruptType
```

Whether the audio interruption has started or ended.

**Type:** [InterruptType](arkts-audio-audio-interrupttype-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-InterruptEvent-eventType: InterruptType--><!--Device-InterruptEvent-eventType: InterruptType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## forceType

```TypeScript
forceType: InterruptForceType
```

Whether the audio interruption is forcibly taken by the system or taken by an application.

**Type:** [InterruptForceType](arkts-audio-audio-interruptforcetype-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-InterruptEvent-forceType: InterruptForceType--><!--Device-InterruptEvent-forceType: InterruptForceType-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## hintType

```TypeScript
hintType: InterruptHint
```

Hint provided along the interruption to provide information related to the interruption event.

**Type:** [InterruptHint](arkts-audio-audio-interrupthint-e.md)

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-InterruptEvent-hintType: InterruptHint--><!--Device-InterruptEvent-hintType: InterruptHint-End-->

**System capability:** SystemCapability.Multimedia.Audio.Renderer
