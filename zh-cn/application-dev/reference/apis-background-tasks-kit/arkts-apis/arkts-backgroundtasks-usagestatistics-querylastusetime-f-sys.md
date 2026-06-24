# queryLastUseTime（系统接口）

## queryLastUseTime

```TypeScript
function queryLastUseTime(appInfo: Record<string, Array<number>>): Promise<AppStatsMap>
```

通过指定bundleName和应用的index，查询应用使用具体信息，统计的最小颗粒度是天，使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appInfo | Record&lt;string, Array&lt;number&gt;&gt; | 是 | 参数为map结构，key是bundleName，value是查询应用的index（可以有多个，通过Array传入）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AppStatsMap&gt; | Promise对象。返回指定bundleName和index应用使用的具体信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Not) | Not System App. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible cause: Parameter verification failed. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |
| [10000001](../../errorcode-universal.md#10000001-Memory) | Memory operation failed. |
| [10000002](../../errorcode-universal.md#10000002-Failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br/><br/>2. Failed to apply for memory. |
| [10000003](../../errorcode-universal.md#10000003-Failed) | Failed to get system ability manager. |
| [10000004](../../errorcode-universal.md#10000004-Failed) | Failed to access the device usage service. |
| [10000006](../../errorcode-universal.md#10000006-Failed) | Failed to get the application information. |
| [10000007](../../errorcode-universal.md#10000007-Failed) | Failed to get the system time. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

// 查询时将com.ohos.camera替换为实际查询的包名
usageStatistics.queryLastUseTime({"com.ohos.camera": [0]}).then((res:usageStatistics.AppStatsMap) => {
  console.info('queryLastUseTime promise success.');
  console.info('queryLastUseTime promise result ' + JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('queryLastUseTime promise failed. code is: ' + err.code + ',message is: ' + err.message);
});

```

