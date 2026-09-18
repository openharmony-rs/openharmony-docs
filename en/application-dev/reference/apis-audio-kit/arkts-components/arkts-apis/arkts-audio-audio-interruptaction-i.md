# InterruptAction

Describes the callback invoked for audio interruption or focus gain events.When the audio of an application is interrupted by another application, the callback is invoked to notify the former application.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [InterruptEvent](arkts-audio-audio-interruptevent-i.md)

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## actionType

```TypeScript
actionType: InterruptActionType
```

Event type. The value TYPE_ACTIVATED means the focus gain event, and TYPE_INTERRUPT means the audio interruption event.

**Type:** [InterruptActionType](arkts-audio-audio-interruptactiontype-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** eventType

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## activated

```TypeScript
activated?: boolean
```

Whether the focus is gained or released. **true** if the focus is gained or released, **false** if the focus fails to be gained or released.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [hintType](arkts-audio-audio-interruptevent-i.md#hinttype)

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## hint

```TypeScript
hint?: InterruptHint
```

Hint provided along with the audio interruption event.

**Type:** [InterruptHint](arkts-audio-audio-interrupthint-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [hintType](arkts-audio-audio-interruptevent-i.md#hinttype)

**System capability:** SystemCapability.Multimedia.Audio.Renderer

## type

```TypeScript
type?: InterruptType
```

Type of the audio interruption event.

**Type:** [InterruptType](arkts-audio-audio-interrupttype-e.md)

**Since:** 7

**Deprecated since:** 9

**Substitutes:** eventType

**System capability:** SystemCapability.Multimedia.Audio.Renderer
