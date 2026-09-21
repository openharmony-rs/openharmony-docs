# getPasswordPolicy (System API)

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

<a id="getpasswordpolicy-2"></a>

## getPasswordPolicy

```TypeScript
function getPasswordPolicy(): PasswordPolicy
```

Obtains the device screen lock password policy.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [PasswordPolicy](arkts-mdm-securitymanager-passwordpolicy-i.md) | Device screen lock password policy. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { securityManager } from '@kit.MDMKit';

try {
  let result: securityManager.PasswordPolicy = securityManager.getPasswordPolicy();
  console.info(`Succeeded in getting password policy, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get password policy. Code: ${err.code}, message: ${err.message}`);
}
```
