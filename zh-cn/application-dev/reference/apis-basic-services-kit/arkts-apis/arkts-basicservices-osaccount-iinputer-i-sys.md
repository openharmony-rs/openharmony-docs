# IInputer（系统接口）

凭据输入器回调。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## onGetData

```TypeScript
onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void
```

通知调用者获取数据的回调函数。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authSubType | [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md) | 是 |  |
| callback | [IInputData](arkts-basicservices-osaccount-iinputdata-i-sys.md) | 是 |  |
| options | [GetInputDataOptions](arkts-basicservices-osaccount-getinputdataoptions-i-sys.md) | 是 |  |

**示例**

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
