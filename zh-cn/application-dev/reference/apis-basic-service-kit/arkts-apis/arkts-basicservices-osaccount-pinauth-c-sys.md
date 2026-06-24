# PINAuth（系统接口）

PIN码认证基类。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## constructor

```TypeScript
constructor()
```

创建PIN码认证的实例。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |

**示例：**

```TypeScript
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();

```

## registerInputer

```TypeScript
registerInputer(inputer: IInputer): void
```

注册PIN码输入器。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_PIN_AUTH

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputer | IInputer | 是 | PIN码输入器，用于获取PIN码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameter types. |
| [12300001](../../errorcode-universal.md#12300001-The) | The system service works abnormally. |
| [12300002](../../errorcode-universal.md#12300002-Invalid) | Invalid inputer. |
| [12300103](../../errorcode-universal.md#12300103-The) | The credential inputer already exists. |

**示例：**

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

解注册PIN码输入器。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_PIN_AUTH

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not system application. |

**示例：**

```TypeScript
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
pinAuth.unregisterInputer();

```

