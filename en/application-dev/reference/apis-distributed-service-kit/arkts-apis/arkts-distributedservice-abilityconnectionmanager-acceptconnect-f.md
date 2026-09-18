# acceptConnect

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## acceptConnect

```TypeScript
function acceptConnect(sessionId: number, token: string): Promise<void>
```

Accepts the UIAbility connection after a collaboration session is set up and the session ID is obtained.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | ID of the collaboration session. |
| token | string | Yes | Token value passed by the application on device A. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
After createAbilityConnectionSession is called on device A to create a collaboration session and the session ID is obtained, the application on device B can call acceptConnect to accept the connection.
```
