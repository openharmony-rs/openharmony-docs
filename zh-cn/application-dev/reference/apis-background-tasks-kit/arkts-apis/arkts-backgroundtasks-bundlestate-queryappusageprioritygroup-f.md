# queryAppUsagePriorityGroup

## 导入模块

```TypeScript
import { bundleState } from '@kit.BackgroundTasksKit';
```

## queryAppUsagePriorityGroup

```TypeScript
function queryAppUsagePriorityGroup(callback: AsyncCallback<number>): void
```

Queries the usage priority group of the calling application.

The priority defined in a priority group restricts the resource usage of an application,for example, restricting the running of background tasks.

**起始版本：** 7

**废弃版本：** 9

<!--Device-bundleState-function queryAppUsagePriorityGroup(callback: AsyncCallback<number>): void--><!--Device-bundleState-function queryAppUsagePriorityGroup(callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | the callback of queryAppUsagePriorityGroup.Returns the app group of the calling application. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryAppUsagePriorityGroup((err: BusinessError, res: number) => {
  if(err) {
    console.error('BUNDLE_ACTIVE QueryPackageGroup callback failed. because: ' + err.code);
  } else {
    console.info('BUNDLE_ACTIVE QueryPackageGroup callback succeeded. result: ' + JSON.stringify(res));
  }
});

```


## queryAppUsagePriorityGroup

```TypeScript
function queryAppUsagePriorityGroup(): Promise<number>
```

Queries the usage priority group of the calling application.

The priority defined in a priority group restricts the resource usage of an application,for example, restricting the running of background tasks.

**起始版本：** 7

**废弃版本：** 9

<!--Device-bundleState-function queryAppUsagePriorityGroup(): Promise<number>--><!--Device-bundleState-function queryAppUsagePriorityGroup(): Promise<number>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | the promise returned by queryAppUsagePriorityGroup.Returns the app group of the calling application. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryAppUsagePriorityGroup().then((res: number) => {
  console.info('BUNDLE_ACTIVE QueryPackageGroup promise succeeded. result: ' + JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE QueryPackageGroup promise failed. because: ' + err.code);
});

```

