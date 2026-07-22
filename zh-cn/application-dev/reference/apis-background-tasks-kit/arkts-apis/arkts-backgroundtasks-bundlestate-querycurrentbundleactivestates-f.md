# queryCurrentBundleActiveStates

## 导入模块

```TypeScript
import { bundleState } from '@kit.BackgroundTasksKit';
```

## queryCurrentBundleActiveStates

```TypeScript
function queryCurrentBundleActiveStates(
    begin: number,
    end: number,
    callback: AsyncCallback<Array<BundleActiveState>>
  ): void
```

Queries state data of the current bundle within a specified period.

**起始版本：** 7

**废弃版本：** 9

<!--Device-bundleState-function queryCurrentBundleActiveStates(    begin: number,    end: number,    callback: AsyncCallback<Array<BundleActiveState>>  ): void--><!--Device-bundleState-function queryCurrentBundleActiveStates(    begin: number,    end: number,    callback: AsyncCallback<Array<BundleActiveState>>  ): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 是 | Indicates the start time of the query period, in milliseconds. |
| end | number | 是 | Indicates the end time of the query period, in milliseconds. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;BundleActiveState&gt;&gt; | 是 | the state data of the current bundle. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryCurrentBundleActiveStates(0, 20000000000000, (err: BusinessError, res: Array<bundleState.BundleActiveState>) => {
  if (err) {
    console.error('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback failed, because: ' + err.code);
  } else {
    console.info('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback success.');
    for (let i = 0; i < res.length; i++) {
      console.info('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback number : ' + (i + 1));
      console.info('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback result ' + JSON.stringify(res[i]));
    }
  }
});

```


## queryCurrentBundleActiveStates

```TypeScript
function queryCurrentBundleActiveStates(begin: number, end: number): Promise<Array<BundleActiveState>>
```

Queries state data of the current bundle within a specified period.

**起始版本：** 7

**废弃版本：** 9

<!--Device-bundleState-function queryCurrentBundleActiveStates(begin: number, end: number): Promise<Array<BundleActiveState>>--><!--Device-bundleState-function queryCurrentBundleActiveStates(begin: number, end: number): Promise<Array<BundleActiveState>>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | number | 是 | Indicates the start time of the query period, in milliseconds. |
| end | number | 是 | Indicates the end time of the query period, in milliseconds. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BundleActiveState&gt;&gt; | the state data of the current bundle. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleState } from '@kit.BackgroundTasksKit';

bundleState.queryCurrentBundleActiveStates(0, 20000000000000).then((res: Array<bundleState.BundleActiveState>) => {
  console.info('BUNDLE_ACTIVE queryCurrentBundleActiveStates promise success.');
  for (let i = 0; i < res.length; i++) {
    console.info('BUNDLE_ACTIVE queryCurrentBundleActiveStates promise number : ' + (i + 1));
    console.info('BUNDLE_ACTIVE queryCurrentBundleActiveStates promise result ' + JSON.stringify(res[i]));
  }
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE queryCurrentBundleActiveStates promise failed, because: ' + err.code);
});

```

