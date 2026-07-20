# IInputData（系统接口）

密码数据回调。

**起始版本：** 8

<!--Device-osAccount-interface IInputData--><!--Device-osAccount-interface IInputData-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

<a id="onsetdata"></a>
## onSetData

```TypeScript
onSetData(authSubType: AuthSubType, data: Uint8Array): void
```

通知设置数据。

**起始版本：** 8

<!--Device-IInputData-onSetData(authSubType: AuthSubType, data: Uint8Array): void--><!--Device-IInputData-onSetData(authSubType: AuthSubType, data: Uint8Array): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authSubType | [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md) | 是 | 用于认证的凭据子类型。 |
| data | Uint8Array | 是 | 要设置的数据是凭据，用来在认证、添加、修改凭据操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid pinSubType. |

**示例：**

```TypeScript
let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0]);
let passwordNumber: Uint8Array = new Uint8Array([1, 2, 3, 4]);
let inputer: osAccount.IInputer = {
  onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
      if (authSubType == osAccount.AuthSubType.PIN_NUMBER) {
        callback.onSetData(authSubType, passwordNumber);
      } else {
        callback.onSetData(authSubType, password);
      }
  }
};

```

