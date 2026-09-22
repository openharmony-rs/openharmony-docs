# queryAppUsagePriorityGroup

## Modules to Import

```TypeScript
import { bundleState } from '@kit.BackgroundTasksKit';
```

## queryAppUsagePriorityGroup

```TypeScript
function queryAppUsagePriorityGroup(callback: AsyncCallback<number>): void
```

Queries the usage priority group of the calling application.

The priority defined in a priority group restricts the resource usage of an application, for example, restricting the running of background tasks.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | the callback of queryAppUsagePriorityGroup. Returns the app group of the calling application. |

**Examples**

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


<a id="queryappusageprioritygroup-1"></a>

## queryAppUsagePriorityGroup

```TypeScript
function queryAppUsagePriorityGroup(): Promise<number>
```

Queries the usage priority group of the calling application.

The priority defined in a priority group restricts the resource usage of an application, for example, restricting the running of background tasks.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | the promise returned by queryAppUsagePriorityGroup. Returns the app group of the calling application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryAppUsagePriorityGroup().then((res: number) => {
  console.info('BUNDLE_ACTIVE QueryPackageGroup promise succeeded. result: ' + JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE QueryPackageGroup promise failed. because: ' + err.code);
});
```
