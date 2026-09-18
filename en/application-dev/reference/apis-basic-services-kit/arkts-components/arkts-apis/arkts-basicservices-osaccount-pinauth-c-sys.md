# PINAuth (System API)

Provides APIs for PIN authentication.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## constructor

```TypeScript
constructor()
```

Creates a PIN authentication instance.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
```

## registerInputer

```TypeScript
registerInputer(inputer: IInputer): void
```

Registers a PIN inputer.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_PIN_AUTH

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputer | [IInputer](arkts-basicservices-osaccount-iinputer-i-sys.md) | Yes | PIN inputer, which is used to obtain the PIN. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid inputer. |
| [12300103](../errorcode-account.md#12300103-credential-inputer-already-exists) | The credential inputer already exists. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
let password = new Uint8Array([0, 0, 0, 0, 0]);
try {
  pinAuth.registerInputer({
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
unregisterInputer(): void
```

Unregisters this PIN inputer.

**Since:** 8

**Required permissions:** ohos.permission.ACCESS_PIN_AUTH

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |

**Examples**

```TypeScript
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
pinAuth.unregisterInputer();
```
