# PINAuth（系统接口）

PIN码认证基类。

**起始版本：** 8

<!--Device-osAccount-class PINAuth--><!--Device-osAccount-class PINAuth-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

创建PIN码认证的实例。

**起始版本：** 8

<!--Device-PINAuth-constructor()--><!--Device-PINAuth-constructor()-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();

```

<a id="registerinputer"></a>
## registerInputer

```TypeScript
registerInputer(inputer: IInputer): void
```

注册PIN码输入器。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_PIN_AUTH

<!--Device-PINAuth-registerInputer(inputer: IInputer): void--><!--Device-PINAuth-registerInputer(inputer: IInputer): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputer | [IInputer](arkts-basicservices-osaccount-iinputer-i-sys.md) | 是 | PIN码输入器，用于获取PIN码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid inputer. |
| [12300103](../../apis-basic-services-kit/errorcode-account.md#12300103-凭据输入器已注册) | The credential inputer already exists. |

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

<a id="unregisterinputer"></a>
## unregisterInputer

```TypeScript
unregisterInputer(): void
```

解注册PIN码输入器。

**起始版本：** 8

**需要权限：** ohos.permission.ACCESS_PIN_AUTH

<!--Device-PINAuth-unregisterInputer(): void--><!--Device-PINAuth-unregisterInputer(): void-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

**示例：**

```TypeScript
let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
pinAuth.unregisterInputer();

```

