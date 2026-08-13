# killProcessWithAccount（系统接口）

## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: int): Promise<void>
```

终止account进程。使用Promise异步回调。 > **说明：** > > 当accountId为当前用户时，不需要校验ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本14+：ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES
- API版本9 - 13：ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

<!--Device-appManager-function killProcessWithAccount(bundleName: string, accountId: int): Promise<void>--><!--Device-appManager-function killProcessWithAccount(bundleName: string, accountId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Bundle名称。 |
| accountId | int | 是 | 系统账号的账号ID，详情参考 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let accountId = 0;

try {
  appManager.killProcessWithAccount(bundleName, accountId).then(() => {
    console.info('killProcessWithAccount success');
  }).catch((e: Error) => {
    let err = e as BusinessError;
    console.error(`killProcessWithAccount fail, err: ${err.code}, ${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: int, clearPageStack: boolean, appIndex?: int):
    Promise<void>
```

终止account进程。使用Promise异步回调。 > **说明：** > > 当accountId为当前用户时，不需要校验ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

<!--Device-appManager-function killProcessWithAccount(bundleName: string, accountId: int, clearPageStack: boolean, appIndex?: int):    Promise<void>--><!--Device-appManager-function killProcessWithAccount(bundleName: string, accountId: int, clearPageStack: boolean, appIndex?: int):    Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Bundle名称。 |
| accountId | int | 是 | 系统账号的账号ID，详情参考 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 。 |
| clearPageStack | boolean | 是 | 表示是否清除页面堆栈。true表示清除，false表示不清除。 |
| appIndex | int | 否 | 应用分身ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | If the input parameter is not valid parameter. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let accountId = 0;
let isClearPageStack = false;
let appIndex = 1;

try {
  appManager.killProcessWithAccount(bundleName, accountId, isClearPageStack, appIndex).then(() => {
    console.info('killProcessWithAccount success');
  }).catch((e: Error) => {
    let err = e as BusinessError;
    console.error(`killProcessWithAccount fail, err: ${err.code}, ${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: int, callback: AsyncCallback<void>): void
```

终止account进程。使用callback异步回调。 > **说明：** > > 当accountId为当前用户时，不需要校验ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** 
- API版本14+：ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.KILL_APP_PROCESSES or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES
- API版本9 - 13：ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

<!--Device-appManager-function killProcessWithAccount(bundleName: string, accountId: int, callback: AsyncCallback<void>): void--><!--Device-appManager-function killProcessWithAccount(bundleName: string, accountId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| accountId | int | 是 | 系统账号的账号ID，详情参考 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 以回调方式返回接口运行结果，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let accountId = 0;

function killProcessWithAccountCallback(err: BusinessError | null) {
  if (err) {
    console.error(`killProcessWithAccountCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('killProcessWithAccountCallback success.');
  }
}

appManager.killProcessWithAccount(bundleName, accountId, killProcessWithAccountCallback);
```

