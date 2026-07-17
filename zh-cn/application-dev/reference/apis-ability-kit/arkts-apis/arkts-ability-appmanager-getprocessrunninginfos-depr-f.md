# getProcessRunningInfos

## getProcessRunningInfos

```TypeScript
function getProcessRunningInfos(): Promise<Array<ProcessRunningInfo>>
```

获取有关运行进程的信息。使用Promise异步回调。

> 从 API Version 9 开始废弃，建议使用  
> [appManager.getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md#getrunningprocessinformation-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getRunningProcessInformation

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-appManager-function getProcessRunningInfos(): Promise<Array<ProcessRunningInfo>>--><!--Device-appManager-function getProcessRunningInfos(): Promise<Array<ProcessRunningInfo>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<ProcessRunningInfo>> | Promise对象，返回有关运行进程的信息。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getProcessRunningInfos().then((data) => {
  console.info(`The process running infos is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});

```


## getProcessRunningInfos

```TypeScript
function getProcessRunningInfos(callback: AsyncCallback<Array<ProcessRunningInfo>>): void
```

获取有关运行进程的信息。使用callback异步回调。

> 从 API Version 9 开始废弃，建议使用  
> [appManager.getRunningProcessInformation](arkts-ability-appmanager-getrunningprocessinformation-f.md#getrunningprocessinformation-1)  
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getRunningProcessInformation

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-appManager-function getProcessRunningInfos(callback: AsyncCallback<Array<ProcessRunningInfo>>): void--><!--Device-appManager-function getProcessRunningInfos(callback: AsyncCallback<Array<ProcessRunningInfo>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<ProcessRunningInfo>> | 是 | 回调函数，返回有关运行进程的信息。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.getProcessRunningInfos((error, data) => {
  if (error && error.code !== 0) {
    console.error(`getProcessRunningInfos fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`getProcessRunningInfos success, data: ${JSON.stringify(data)}`);
  }
});

```

