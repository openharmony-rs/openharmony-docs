# createAbilityConnectionSession

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## createAbilityConnectionSession

```TypeScript
function createAbilityConnectionSession(serviceName: string, context: Context, peerInfo: PeerInfo,
        connectOptions: ConnectOptions): number
```

Creates a collaboration session between applications.

**Since:** 18

**Required permissions:** ohos.permission.INTERNET and ohos.permission.GET_NETWORK_INFO and ohos.permission.SET_NETWORK_INFO and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceName | string | Yes | Service name for the application. The service name must be the same on the local end and peer end. The value contains a maximum of 256 characters. |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. |
| peerInfo | [PeerInfo](arkts-distributedservice-abilityconnectionmanager-peerinfo-i.md) | Yes | Collaboration information of the peer end. |
| connectOptions | [ConnectOptions](arkts-distributedservice-abilityconnectionmanager-connectoptions-i.md) | Yes | Connection options for the application. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID of the collaboration session. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
On device A, an application calls createAbilityConnectionSession() to create a collaboration session and return the session ID.
```

```TypeScript
On device B, createAbilityConnectionSession can be called in onCollaborate, which is triggered when the application is started.
```
