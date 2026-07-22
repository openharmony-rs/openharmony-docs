# isSharedBundleRunning（系统接口）

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## isSharedBundleRunning

```TypeScript
function isSharedBundleRunning(bundleName: string, versionCode: number): Promise<boolean>
```

检查共享库是否正在使用。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-appManager-function isSharedBundleRunning(bundleName: string, versionCode: long): Promise<boolean>--><!--Device-appManager-function isSharedBundleRunning(bundleName: string, versionCode: long): Promise<boolean>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要查询的共享库包名。 |
| versionCode | number | 是 | 表示要查询的共享库版本号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示共享库正在使用，返回false表示共享库不在使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const bundleName = "this is a bundleName";
const versionCode = 1;

appManager.isSharedBundleRunning(bundleName, versionCode).then((data) => {
  console.info(`The shared bundle running is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});

```


## isSharedBundleRunning

```TypeScript
function isSharedBundleRunning(bundleName: string, versionCode: number, callback: AsyncCallback<boolean>): void
```

检查共享库是否正在使用。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-appManager-function isSharedBundleRunning(bundleName: string, versionCode: long, callback: AsyncCallback<boolean>): void--><!--Device-appManager-function isSharedBundleRunning(bundleName: string, versionCode: long, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示要查询的共享库包名。 |
| versionCode | number | 是 | 表示要查询的共享库版本号。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示共享库正在使用，返回false表示共享库不在使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';

const bundleName = "this is a bundleName";
const versionCode = 1;

appManager.isSharedBundleRunning(bundleName, versionCode, (err, data) => {
  if (err) {
    console.error(`err: ${JSON.stringify(err)}`);
  } else {
    console.info(`The shared bundle running is: ${JSON.stringify(data)}`);
  }
});

```

