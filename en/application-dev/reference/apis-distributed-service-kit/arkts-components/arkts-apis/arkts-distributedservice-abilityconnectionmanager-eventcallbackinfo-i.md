# EventCallbackInfo

```TypeScript
interface EventCallbackInfo
```

Defines the event callback information.

**Since:** 18

<!--Device-abilityConnectionManager-interface EventCallbackInfo--><!--Device-abilityConnectionManager-interface EventCallbackInfo-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## data

```TypeScript
data?: ArrayBuffer
```

Received byte stream.

**Type:** ArrayBuffer

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventCallbackInfo-data?: ArrayBuffer--><!--Device-EventCallbackInfo-data?: ArrayBuffer-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## msg

```TypeScript
msg?: string
```

Received message.

**Type:** string

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventCallbackInfo-msg?: string--><!--Device-EventCallbackInfo-msg?: string-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## reason

```TypeScript
reason?: DisconnectReason
```

Disconnection reason.

**Type:** [DisconnectReason](arkts-distributedservice-abilityconnectionmanager-disconnectreason-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventCallbackInfo-reason?: DisconnectReason--><!--Device-EventCallbackInfo-reason?: DisconnectReason-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## sessionId

```TypeScript
sessionId: number
```

Collaboration session ID.

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventCallbackInfo-sessionId: int--><!--Device-EventCallbackInfo-sessionId: int-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration
