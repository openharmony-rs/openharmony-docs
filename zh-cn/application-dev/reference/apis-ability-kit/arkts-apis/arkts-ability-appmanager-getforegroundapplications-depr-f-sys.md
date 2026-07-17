# getForegroundApplications（系统接口）

## getForegroundApplications

```TypeScript
function getForegroundApplications(callback: AsyncCallback<Array<AppStateData>>): void
```

获取所有当前处于前台的应用信息。该应用信息由[AppStateData](application/AppStateData:AppStateData)定义。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getForegroundApplications

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-appManager-function getForegroundApplications(callback: AsyncCallback<Array<AppStateData>>): void--><!--Device-appManager-function getForegroundApplications(callback: AsyncCallback<Array<AppStateData>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<AppStateData>> | 是 | 回调函数，返回所有当前处于前台的应用信息。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.getForegroundApplications((err, data) => {
  if (err) {
    console.error(`GetForegroundApplications failed, error code: ${err.code}, error msg: ${err.message}.`);
  } else {
    console.info(`GetForegroundApplications success, data: ${JSON.stringify(data)}.`);
  }
});

```


## getForegroundApplications

```TypeScript
function getForegroundApplications(): Promise<Array<AppStateData>>
```

获取所有当前处于前台的应用信息。该应用信息由[AppStateData](application/AppStateData:AppStateData)定义。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getForegroundApplications

**需要权限：** ohos.permission.GET_RUNNING_INFO

<!--Device-appManager-function getForegroundApplications(): Promise<Array<AppStateData>>--><!--Device-appManager-function getForegroundApplications(): Promise<Array<AppStateData>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<AppStateData>> | Promise对象，返回所有当前处于前台的应用信息。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.getForegroundApplications()
  .then((data) => {
    console.info(`GetForegroundApplications success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`GetForegroundApplications failed, error code: ${err.code}, error msg: ${err.message}.`);
  });

```

