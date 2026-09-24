# connect

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## connect

```TypeScript
function connect(sessionId: number): Promise<ConnectResult>
```

Sets up a UIAbility connection after a collaboration session is created and the session ID is obtained. This API uses a promise to return the result.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | ID of the collaboration session. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ConnectResult](arkts-distributedservice-abilityconnectionmanager-connectresult-i.md)&gt; | Promise used to return the [connection result](arkts-distributedservice-abilityconnectionmanager-connectresult-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

After an application sets up a collaboration session and obtains the session ID on device A, it calls connect() to set up a UIAbility connection and start the application on device B.

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let sessionId = 100;
abilityConnectionManager.connect(sessionId).then((ConnectResult) => {
  if (!ConnectResult.isConnected) {
    hilog.info(0x0000, 'testTag', 'connect failed');
    return;
  }
}).catch(() => {
  hilog.error(0x0000, 'testTag', "connect failed");
})
```
