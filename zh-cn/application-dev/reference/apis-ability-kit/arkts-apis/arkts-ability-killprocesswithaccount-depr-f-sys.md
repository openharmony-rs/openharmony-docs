# killProcessWithAccount（系统接口）

## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: number): Promise<void>
```

切断account进程。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** killProcessWithAccount

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| accountId | number | 是 | 系统账号的账号ID，详情参考[getOsAccountCount](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountcount-1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';
let accountId = 0;
appManager.killProcessWithAccount(bundleName, accountId)
  .then((data) => {
    console.info(`KillProcessWithAccount success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`KillProcessWithAccount failed, error code: ${err.code}, error msg: ${err.message}.`);
  });

```


## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: number, callback: AsyncCallback<void>): void
```

切断account进程。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** killProcessWithAccount

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用Bundle名称。 |
| accountId | number | 是 | 系统账号的账号ID，详情参考[getOsAccountCount](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-accountmanager-i.md#getosaccountcount-1)。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当切断account进程成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';
let accountId = 0;

function killProcessWithAccountCallback(err: BusinessError, data: void) {
  if (err) {
    console.error(`KillProcessWithAccountCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
  } else {
    console.info(`KillProcessWithAccountCallback success, data: ${JSON.stringify(data)}`);
  }
}

appManager.killProcessWithAccount(bundleName, accountId, killProcessWithAccountCallback);

```

