# IInputer (System API)

Provides callbacks to obtain credential inputer data.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## onGetData

```TypeScript
onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void
```

Called to notify the caller that data is obtained.

**Since:** 8

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authSubType | [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md) | Yes |  |
| callback | [IInputData](arkts-basicservices-osaccount-iinputdata-i-sys.md) | Yes |  |
| options | [GetInputDataOptions](arkts-basicservices-osaccount-getinputdataoptions-i-sys.md) | Yes |  |

**Examples**

```TypeScript
let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0]);
let passwordNumber: Uint8Array = new Uint8Array([1, 2, 3, 4]);
let inputer: osAccount.IInputer = {
  onGetData: (authSubType: osAccount.AuthSubType,
    callback: osAccount.IInputData, options: osAccount.GetInputDataOptions) => {
      if (authSubType == osAccount.AuthSubType.PIN_NUMBER) {
        callback.onSetData(authSubType, passwordNumber);
      } else {
        callback.onSetData(authSubType, password);
      }
  }
};
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
let result = pinAuth.registerInputer(inputer);
console.info('registerInputer result: ' + result);
```
