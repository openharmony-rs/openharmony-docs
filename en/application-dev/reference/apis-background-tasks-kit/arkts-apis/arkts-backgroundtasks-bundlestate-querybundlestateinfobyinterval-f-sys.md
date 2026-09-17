# queryBundleStateInfoByInterval (System API)

## Modules to Import

```TypeScript
import { bundleState } from '@kit.BackgroundTasksKit';
```

## queryBundleStateInfoByInterval

```TypeScript
function queryBundleStateInfoByInterval(
    byInterval: IntervalType,
    begin: number,
    end: number,
    callback: AsyncCallback<Array<BundleStateInfo>>
  ): void
```

Queries usage information about each bundle within a specified period at a specified interval.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.BUNDLE_ACTIVE_INFO

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byInterval | [IntervalType](arkts-backgroundtasks-bundlestate-intervaltype-e.md) | Yes | Indicates the interval at which the usage statistics are queried. The value can be BY_OPTIMIZED, BY_DAILY, BY_WEEKLY, BY_MONTHLY, or BY_ANNUALLY. |
| begin | number | Yes | Indicates the start time of the query period, in milliseconds.<br> Unit:ms |
| end | number | Yes | Indicates the end time of the query period, in milliseconds.<br> Unit:ms |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[BundleStateInfo](arkts-backgroundtasks-bundlestate-bundlestateinfo-i.md)&gt;&gt; | Yes | the callback of usage information about each bundle. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryBundleStateInfoByInterval(bundleState.IntervalType.BY_OPTIMIZED, 0, 20000000000000, (err: BusinessError, res: Array<bundleState.BundleStateInfo>) => {
  if (err) {
    console.error('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback failed, because: ' + err.code);
  } else {
    console.info('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback success.');
    for (let i = 0; i < res.length; i++) {
      console.info('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback number : ' + (i + 1));
      console.info('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback result ' + JSON.stringify(res[i]));
    }
  }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryBundleStateInfoByInterval(bundleState.IntervalType.BY_OPTIMIZED, 0, 20000000000000).then((res: Array<bundleState.BundleStateInfo>) => {
  console.info('BUNDLE_ACTIVE queryBundleStateInfoByInterval promise success.');
  for (let i = 0; i < res.length; i++) {
    console.info('BUNDLE_ACTIVE queryBundleStateInfoByInterval promise number : ' + (i + 1));
    console.info('BUNDLE_ACTIVE queryBundleStateInfoByInterval promise result ' + JSON.stringify(res[i]));
  }
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE queryBundleStateInfoByInterval promise failed, because: ' + err.code);
});
```


## queryBundleStateInfoByInterval

```TypeScript
function queryBundleStateInfoByInterval(
    byInterval: IntervalType,
    begin: number,
    end: number
  ): Promise<Array<BundleStateInfo>>
```

Queries usage information about each bundle within a specified period at a specified interval.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.BUNDLE_ACTIVE_INFO

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.App

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| byInterval | [IntervalType](arkts-backgroundtasks-bundlestate-intervaltype-e.md) | Yes | Indicates the interval at which the usage statistics are queried. The value can be BY_OPTIMIZED, BY_DAILY, BY_WEEKLY, BY_MONTHLY, or BY_ANNUALLY. |
| begin | number | Yes | Indicates the start time of the query period, in milliseconds.<br> Unit:ms |
| end | number | Yes | Indicates the end time of the query period, in milliseconds.<br> Unit:ms |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BundleStateInfo](arkts-backgroundtasks-bundlestate-bundlestateinfo-i.md)&gt;&gt; | the usage information about each bundle. |

**Examples**

See [queryBundleStateInfoByInterval](#querybundlestateinfobyinterval)
