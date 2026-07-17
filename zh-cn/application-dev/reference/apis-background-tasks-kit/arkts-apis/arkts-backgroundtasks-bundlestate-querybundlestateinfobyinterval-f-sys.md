# queryBundleStateInfoByInterval（系统接口）

## 导入模块

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

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-bundleState-function queryBundleStateInfoByInterval(
    byInterval: IntervalType,
    begin: number,
    end: number,
    callback: AsyncCallback<Array<BundleStateInfo>>
  ): void--><!--Device-bundleState-function queryBundleStateInfoByInterval(
    byInterval: IntervalType,
    begin: number,
    end: number,
    callback: AsyncCallback<Array<BundleStateInfo>>
  ): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| byInterval | [IntervalType](arkts-backgroundtasks-bundlestate-intervaltype-e.md) | 是 | Indicates the interval at which the usage statistics are queried. |
| begin | number | 是 | Indicates the start time of the query period, in milliseconds. |
| end | number | 是 | Indicates the end time of the query period, in milliseconds. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<BundleStateInfo>> | 是 | the callback of usage information about each bundle. |

**示例：**

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


## queryBundleStateInfoByInterval

```TypeScript
function queryBundleStateInfoByInterval(
    byInterval: IntervalType,
    begin: number,
    end: number
  ): Promise<Array<BundleStateInfo>>
```

Queries usage information about each bundle within a specified period at a specified interval.

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-bundleState-function queryBundleStateInfoByInterval(
    byInterval: IntervalType,
    begin: number,
    end: number
  ): Promise<Array<BundleStateInfo>>--><!--Device-bundleState-function queryBundleStateInfoByInterval(
    byInterval: IntervalType,
    begin: number,
    end: number
  ): Promise<Array<BundleStateInfo>>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| byInterval | [IntervalType](arkts-backgroundtasks-bundlestate-intervaltype-e.md) | 是 | Indicates the interval at which the usage statistics are queried. |
| begin | number | 是 | Indicates the start time of the query period, in milliseconds. |
| end | number | 是 | Indicates the end time of the query period, in milliseconds. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<BundleStateInfo>> | the usage information about each bundle. |

**示例：**

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

