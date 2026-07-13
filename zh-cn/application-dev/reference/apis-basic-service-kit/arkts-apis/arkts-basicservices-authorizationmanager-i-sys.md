# AuthorizationManager（系统接口）

系统账号授权管理类，用于管理系统账号授权。

**起始版本：** 24

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## acquireAuthorization

```TypeScript
acquireAuthorization(privilege: string, options?: AcquireAuthorizationOptions): Promise<AcquireAuthorizationResult>
```

为当前进程获取授权。

**起始版本：** 24

**需要权限：** ohos.permission.ACQUIRE_LOCAL_ACCOUNT_AUTHORIZATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| privilege | string | 是 | 目标权限，详见[配置文件](https://gitcode.com/openharmony/account_os_account/blob/master/services/accountmgr/authorization_manager/config/privileges.json)。 |
| options | AcquireAuthorizationOptions | 否 | 获取授权的选项，默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AcquireAuthorizationResult&gt; | Promise对象，返回获取授权的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid privilege or options. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let authorizationManager: osAccount.AuthorizationManager = osAccount.getAuthorizationManager();
let privilege: string = 'testPrivilege';
let options: osAccount.AcquireAuthorizationOptions = {
  challenge: new Uint8Array([1, 2, 3]),
  isReuseNeeded: true,
  isInteractionAllowed: true,
};
try {
  authorizationManager.acquireAuthorization(privilege, options).then((result: osAccount.AcquireAuthorizationResult) => {
    console.info(`acquireAuthorization successfully, resultCode: ${result.resultCode}`);
  }).catch((err: BusinessError) => {
    console.error(`acquireAuthorization failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`acquireAuthorization exception: code is ${err.code}, message is ${err.message}`);
}

```

## hasAuthorization

```TypeScript
hasAuthorization(privilege: string): Promise<boolean>
```

检查当前进程是否已获得指定特权的授权。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| privilege | string | 是 | 目标权限，详见[配置文件](https://gitcode.com/openharmony/account_os_account/blob/master/services/accountmgr/authorization_manager/config/privileges.json)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回true表示已获得指定特权的授权；返回false表示未获得指定特权的授权。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid privilege. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let authorizationManager: osAccount.AuthorizationManager = osAccount.getAuthorizationManager();
let privilege: string = 'testPrivilege';

try {
  authorizationManager.hasAuthorization(privilege).then((isAuthorized: boolean) => {
    console.info(`Privilege: ${privilege} has been authorized: ${isAuthorized}`);
  }).catch((e:Error) => {
    const err = e as BusinessError;
    console.error(`hasAuthorization failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`hasAuthorization exception: code is ${err.code}, message is ${err.message}`);
}

```

## releaseAuthorization

```TypeScript
releaseAuthorization(privilege: string): Promise<void>
```

为当前进程撤销指定特权的授权。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| privilege | string | 是 | 目标权限，详见[配置文件](https://gitcode.com/openharmony/account_os_account/blob/master/services/accountmgr/authorization_manager/config/privileges.json)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [12300001](../../apis-basic-services-kit/errorcode-account.md#12300001-系统服务异常) | The system service works abnormally. |
| [12300002](../../apis-basic-services-kit/errorcode-account.md#12300002-无效参数) | Invalid privilege. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let authorizationManager: osAccount.AuthorizationManager = osAccount.getAuthorizationManager();
let privilege: string = 'testPrivilege';

try {
  authorizationManager.releaseAuthorization(privilege).then(() => {
    console.info('releaseAuthorization success');
  }).catch((e:Error) => {
    const err = e as BusinessError;
    console.error(`releaseAuthorization failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`releaseAuthorization exception: code is ${err.code}, message is ${err.message}`);
}

```

