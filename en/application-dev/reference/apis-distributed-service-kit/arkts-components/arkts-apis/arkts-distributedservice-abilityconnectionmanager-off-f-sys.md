# off (System API)

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## off('receiveImage')

```TypeScript
function off(type: 'receiveImage', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void
```

Unregisters receiveImage event.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'receiveImage' | Yes | Registration Type, 'receiveImage'. |
| sessionId | number | Yes | Ability connection Session id. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EventCallbackInfo](arkts-distributedservice-abilityconnectionmanager-eventcallbackinfo-i.md)&gt; | No | Used to handle ('receiveImage') command. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';

let sessionId = 100;
abilityConnectionManager.off("receiveImage", sessionId);
```


## off('collaborateEvent')

```TypeScript
function off(type: 'collaborateEvent', sessionId: number,
        callback?: Callback<CollaborateEventInfo>): void
```

Unregisters collaborateEvent event.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'collaborateEvent' | Yes | Registration Type, 'collaborateEvent'. |
| sessionId | number | Yes | Ability connection Session id. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CollaborateEventInfo](arkts-distributedservice-abilityconnectionmanager-collaborateeventinfo-i.md)&gt; | No | Called when an error event comes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';

let sessionId = 100;
abilityConnectionManager.off("collaborateEvent", sessionId);
```
