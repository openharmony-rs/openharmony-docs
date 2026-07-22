# getRunningProcessInformation

## 导入模块

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## getRunningProcessInformation

```TypeScript
function getRunningProcessInformation(): Promise<Array<ProcessInformation>>
```

获取当前应用运行进程的相关信息。使用Promise异步回调。
> **说明：**  
>  
> - 对于API version 11之前的版本，该接口需要申请权限ohos.permission.GET_RUNNING_INFO（该权限仅系统应用可申请）。  
>  
> - 从API version 11开始，该接口仅用于获取调用方自身的进程信息，不再需要申请权限。

**起始版本：** 9

**需要权限：** 
- API版本9 - 10：ohos.permission.GET_RUNNING_INFO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-appManager-function getRunningProcessInformation(): Promise<Array<ProcessInformation>>--><!--Device-appManager-function getRunningProcessInformation(): Promise<Array<ProcessInformation>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ProcessInformation&gt;&gt; | Promise对象，返回接口运行结果及有关运行进程的信息，可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

appManager.getRunningProcessInformation().then((data) => {
  console.info(`The running process information is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});

```


## getRunningProcessInformation

```TypeScript
function getRunningProcessInformation(callback: AsyncCallback<Array<ProcessInformation>>): void
```

获取当前应用运行进程的相关信息。使用callback异步回调。
> **说明：**  
>  
> - 对于API version 11之前的版本，该接口需要申请权限ohos.permission.GET_RUNNING_INFO（该权限仅系统应用可申请）。  
>  
> - 从API version 11开始，该接口仅用于获取调用方自身的进程信息，不再需要申请权限。

**起始版本：** 9

**需要权限：** 
- API版本9 - 10：ohos.permission.GET_RUNNING_INFO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-appManager-function getRunningProcessInformation(callback: AsyncCallback<Array<ProcessInformation>>): void--><!--Device-appManager-function getRunningProcessInformation(callback: AsyncCallback<Array<ProcessInformation>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;ProcessInformation&gt;&gt; | 是 | 回调函数。当接口调用成功，err为undefined，data为当前应用运行进程的信息；否则为错误对象。可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例：**

```TypeScript
import { appManager } from '@kit.AbilityKit';

appManager.getRunningProcessInformation((err, data) => {
  if (err) {
    console.error(`getRunningProcessInformation fail, err: ${JSON.stringify(err)}`);
  } else {
    console.info(`The running process information is: ${JSON.stringify(data)}`);
  }
});

```

