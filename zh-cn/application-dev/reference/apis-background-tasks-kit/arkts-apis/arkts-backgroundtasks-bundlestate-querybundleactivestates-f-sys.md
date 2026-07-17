# queryBundleActiveStates（系统接口）

## 导入模块

```TypeScript
import { bundleState } from '@kit.BackgroundTasksKit';
```

## queryBundleActiveStates

```TypeScript
function queryBundleActiveStates(begin: number, end: number, callback: AsyncCallback<Array<BundleActiveState>>): void
```

Queries state data of all bundles within a specified period identified by the start and end time.

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-bundleState-function queryBundleActiveStates(begin: number, end: number, callback: AsyncCallback<Array<BundleActiveState>>): void--><!--Device-bundleState-function queryBundleActiveStates(begin: number, end: number, callback: AsyncCallback<Array<BundleActiveState>>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 是 | Indicates the start time of the query period, in milliseconds. |
| end | number | 是 | Indicates the end time of the query period, in milliseconds. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<BundleActiveState>> | 是 | the state data of all bundles. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryBundleActiveStates(0, 20000000000000, (err: BusinessError, res: Array<bundleState.BundleActiveState>) => {
  if (err) {
    console.error('BUNDLE_ACTIVE queryBundleActiveStates callback failed, because: ' + err.code);
  } else {
    console.info('BUNDLE_ACTIVE queryBundleActiveStates callback success.');
    for (let i = 0; i < res.length; i++) {
      console.info('BUNDLE_ACTIVE queryBundleActiveStates callback number : ' + (i + 1));
      console.info('BUNDLE_ACTIVE queryBundleActiveStates callback result ' + JSON.stringify(res[i]));
    }
  }
});

```


## queryBundleActiveStates

```TypeScript
function queryBundleActiveStates(begin: number, end: number): Promise<Array<BundleActiveState>>
```

Queries state data of all bundles within a specified period identified by the start and end time.

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-bundleState-function queryBundleActiveStates(begin: number, end: number): Promise<Array<BundleActiveState>>--><!--Device-bundleState-function queryBundleActiveStates(begin: number, end: number): Promise<Array<BundleActiveState>>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 是 | Indicates the start time of the query period, in milliseconds. |
| end | number | 是 | Indicates the end time of the query period, in milliseconds. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<BundleActiveState>> | the state data of all bundles. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryBundleActiveStates(0, 20000000000000).then((res: Array<bundleState.BundleActiveState>) => {
  console.info('BUNDLE_ACTIVE queryBundleActiveStates promise success.');
  for (let i = 0; i < res.length; i++) {
    console.info('BUNDLE_ACTIVE queryBundleActiveStates promise number : ' + (i + 1));
    console.info('BUNDLE_ACTIVE queryBundleActiveStates promise result ' + JSON.stringify(res[i]));
  }
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE queryBundleActiveStates promise failed, because: ' + err.code);
});

```

