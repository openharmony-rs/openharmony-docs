# InputerManager（系统接口）

凭据输入管理器。

**起始版本：** 9

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## registerInputer

```TypeScript
static registerInputer(authType: AuthType, inputer: IInputer): void
```

注册凭据输入器。

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL or ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | AuthType | 是 | 认证类型。 |
| inputer | IInputer | 是 | 凭据输入器，用于获取凭据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [12300001](../../errorcode-universal.md#12300001-The) | The system service works abnormally. |
| [12300002](../../errorcode-universal.md#12300002-Invalid) | Invalid authType or inputer. |
| [12300103](../../errorcode-universal.md#12300103-The) | The credential inputer already exists. |
| [12300106](../../errorcode-universal.md#12300106-The) | The authentication type is not supported. |

**示例：**

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

解注册凭据输入器。

**起始版本：** 9

**需要权限：** ohos.permission.ACCESS_USER_AUTH_INTERNAL or ohos.permission.MANAGE_USER_IDM

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| authType | AuthType | 是 | 认证类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [12300002](../../errorcode-universal.md#12300002-Invalid) | Invalid authType. |

**示例：**

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

