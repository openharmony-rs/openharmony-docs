# getRunningProcessInfoByBundleName（系统接口）

## getRunningProcessInfoByBundleName

```TypeScript
function getRunningProcessInfoByBundleName(bundleName: string, callback: AsyncCallback<Array<ProcessInformation>>): void
```

通过bundleName获取有关运行进程的信息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-appManager-function getRunningProcessInfoByBundleName(bundleName: string, callback: AsyncCallback<Array<ProcessInformation>>): void--><!--Device-appManager-function getRunningProcessInfoByBundleName(bundleName: string, callback: AsyncCallback<Array<ProcessInformation>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;ProcessInformation&gt;&gt; | 是 | 以回调方式返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = "bundleName";

function getRunningProcessInfoByBundleNameCallback(err: BusinessError | null,
  data: Array<appManager.ProcessInformation> | undefined) {
  if (err) {
    console.error(`getRunningProcessInfoByBundleNameCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('getRunningProcessInfoByBundleNameCallback success.');
  }
}

try {
  appManager.getRunningProcessInfoByBundleName(bundleName, getRunningProcessInfoByBundleNameCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## getRunningProcessInfoByBundleName

```TypeScript
function getRunningProcessInfoByBundleName(bundleName: string, userId: int, callback: AsyncCallback<Array<ProcessInformation>>): void
```

通过bundleName和userId获取有关运行进程的信息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-appManager-function getRunningProcessInfoByBundleName(bundleName: string, userId: int, callback: AsyncCallback<Array<ProcessInformation>>): void--><!--Device-appManager-function getRunningProcessInfoByBundleName(bundleName: string, userId: int, callback: AsyncCallback<Array<ProcessInformation>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |
| userId | int | 是 | 表示用户Id。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;ProcessInformation&gt;&gt; | 是 | 以回调方式返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = "bundleName";
let userId = 0;
function getRunningProcessInfoByBundleNameCallback(err: BusinessError | null, data: Array<appManager.ProcessInformation>|undefined) {
  if (err) {
    console.error(`getRunningProcessInfoByBundleNameCallback fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info('getRunningProcessInfoByBundleNameCallback success.');
  }
}

try {
  appManager.getRunningProcessInfoByBundleName(bundleName, userId, getRunningProcessInfoByBundleNameCallback);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## getRunningProcessInfoByBundleName

```TypeScript
function getRunningProcessInfoByBundleName(bundleName: string): Promise<Array<ProcessInformation>>
```

通过bundleName获取有关运行进程的信息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-appManager-function getRunningProcessInfoByBundleName(bundleName: string): Promise<Array<ProcessInformation>>--><!--Device-appManager-function getRunningProcessInfoByBundleName(bundleName: string): Promise<Array<ProcessInformation>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ProcessInformation&gt;&gt; | 以Promise方式返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';

try {
  appManager.getRunningProcessInfoByBundleName(bundleName).then((data) => {
    console.info('getRunningProcessInfoByBundleName success.');
  }).catch((e: Error) => {
    let err = e as BusinessError;
    console.error(`getRunningProcessInfoByBundleName fail, err: ${err.code} ${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```


## getRunningProcessInfoByBundleName

```TypeScript
function getRunningProcessInfoByBundleName(bundleName: string, userId: int): Promise<Array<ProcessInformation>>
```

通过bundleName和userId获取有关运行进程的信息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-appManager-function getRunningProcessInfoByBundleName(bundleName: string, userId: int): Promise<Array<ProcessInformation>>--><!--Device-appManager-function getRunningProcessInfoByBundleName(bundleName: string, userId: int): Promise<Array<ProcessInformation>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |
| userId | int | 是 | 表示用户Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ProcessInformation&gt;&gt; | 以Promise方式返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'bundleName';
let userId = 0;

try {
  appManager.getRunningProcessInfoByBundleName(bundleName, userId).then((data) => {
    console.info('getRunningProcessInfoByBundleName success.');
  }).catch((e: Error) => {
    let err = e as BusinessError;
    console.error(`getRunningProcessInfoByBundleName fail, err: ${err.code} ${err.message}`);
  });
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

