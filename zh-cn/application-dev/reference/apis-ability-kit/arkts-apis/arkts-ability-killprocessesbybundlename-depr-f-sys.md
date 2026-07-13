# killProcessesByBundleName（系统接口）

## killProcessesByBundleName

```TypeScript
function killProcessesByBundleName(bundleName: string): Promise<void>
```

通过Bundle名称终止进程。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** killProcessesByBundleName

**需要权限：** ohos.permission.CLEAN_BACKGROUND_PROCESSES

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'com.example.myapplication';
appManager.killProcessesByBundleName(bundleName)
  .then((data) => {
    console.info(`KillProcessesByBundleName success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`KillProcessesByBundleName failed, error code: ${err.code}, error msg: ${err.message}.`);
  });

```


## killProcessesByBundleName

```TypeScript
function killProcessesByBundleName(bundleName: string, callback: AsyncCallback<void>)
```

通过Bundle名称终止进程。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** killProcessesByBundleName

**需要权限：** ohos.permission.CLEAN_BACKGROUND_PROCESSES

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当通过Bundle名称终止进程成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';

function killProcessesByBundleNameCallback(err: BusinessError, data: void) {
  if (err) {
    console.error(`KillProcessesByBundleNameCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
  } else {
    console.info(`KillProcessesByBundleNameCallback success, data: ${JSON.stringify(data)}.`);
  }
}

appManager.killProcessesByBundleName(bundleName, killProcessesByBundleNameCallback);

```

