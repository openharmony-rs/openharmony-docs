# ControlEvent (System API)

Defines a control event.

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## eventType

```TypeScript
eventType: EventType
```

Control event type.

**Type:** [EventType](arkts-multimodalawareness-onscreen-eventtype-e-sys.md)

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## hookId

```TypeScript
hookId?: number
```

Hook ID corresponding to the control event. The hook ID and the session ID can be obtained from [PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md) of a session.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## sessionId

```TypeScript
sessionId: number
```

ID of the session to be operated. The hook ID and the session ID can be obtained from [PageContent](arkts-multimodalawareness-onscreen-pagecontent-i-sys.md) of a session.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## windowId

```TypeScript
windowId: number
```

ID of the window to be operated.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
