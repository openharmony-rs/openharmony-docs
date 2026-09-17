# InputerManager (System API)

Provides APIs for managing credential inputers.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## registerInputer

```TypeScript
static registerInputer(authType: AuthType, inputer: IInputer): void
```

Registers a credential inputer.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL or ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Authentication credential type. |
| inputer | [IInputer](arkts-basicservices-osaccount-iinputer-i-sys.md) | Yes | Credential inputer to register. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid authType or inputer. |
| [12300103](../errorcode-account.md#12300103-credential-inputer-already-exists) | The credential inputer already exists. |
| [12300106](../errorcode-account.md#12300106-authentication-type-not-supported) | The authentication type is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let authType: osAccount.AuthType = osAccount.AuthType.DOMAIN;
let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0]);
try {
  osAccount.InputerManager.registerInputer(authType, {
    onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
      callback.onSetData(authSubType, password);
    }
  });
  console.info('registerInputer success.');
} catch (e) {
  const err = e as BusinessError;
  console.error(`registerInputer exception = code is ${err.code}, message is ${err.message}`);
}
```

## unregisterInputer

```TypeScript
static unregisterInputer(authType: AuthType): void
```

Unregisters a credential inputer.

**Since:** 9

**Required permissions:** ohos.permission.ACCESS_USER_AUTH_INTERNAL or ohos.permission.MANAGE_USER_IDM

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authType | [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Yes | Authentication credential type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid authType. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let authType: osAccount.AuthType = osAccount.AuthType.DOMAIN;
try {
  osAccount.InputerManager.unregisterInputer(authType);
  console.info('unregisterInputer success.');
} catch (e) {
  const err = e as BusinessError;
  console.error(`unregisterInputer code is ${err.code}, message is ${err.message}`);
}
```
