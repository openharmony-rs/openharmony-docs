# notifyDebugAssertResult (System API)

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## notifyDebugAssertResult

```TypeScript
function notifyDebugAssertResult(sessionId: string, status: UserStatus): Promise<void>
```

Notifies the application of the assertion result. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.NOTIFY_DEBUG_ASSERT_RESULT

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | Session ID of the AssertFault. |
| status | [UserStatus](arkts-ability-abilitymanager-userstatus-e-sys.md) | Yes | Assertion result of the user operation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { abilityManager, UIExtensionAbility, wantConstant, Want, UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UiExtAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession): void {
    let sessionId: string = '';
    if (want.parameters) {
      sessionId = want.parameters[wantConstant.Params.ASSERT_FAULT_SESSION_ID] as string;
    }
    // Set the user operation status to terminated.
    let status = abilityManager.UserStatus.ASSERT_TERMINATE;
    abilityManager.notifyDebugAssertResult(sessionId, status).then(() => {
      console.info('notifyDebugAssertResult success.');
    }).catch((err: BusinessError) => {
      console.error(`notifyDebugAssertResult failed, error: ${JSON.stringify(err)}`);
    });
  }
}
```
