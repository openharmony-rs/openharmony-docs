# queryAppStatsInfos（系统接口）

## 导入模块

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## queryAppStatsInfos

```TypeScript
function queryAppStatsInfos(begin: long, end: long): Promise<AppStatsMap>
```

通过指定起始和结束时间，查询应用使用时长的具体信息（包含分身应用），统计的最小颗粒度是天。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function queryAppStatsInfos(begin: long, end: long): Promise<AppStatsMap>--><!--Device-usageStatistics-function queryAppStatsInfos(begin: long, end: long): Promise<AppStatsMap>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.App

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| begin | long | 是 | 起始时间，单位：ms。 |
| end | long | 是 | 结束时间，单位：ms。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AppStatsMap](arkts-backgroundtasks-usagestatistics-appstatsmap-t-sys.md)&gt; | Promise对象。返回指定时间段内应用使用的具体信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [10000001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000001-内存操作失败) | Memory operation failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [10000002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; <br> 2. Failed to apply for memory. |
| [10000003](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000003-系统服务操作失败) | Failed to get system ability manager. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |
| [10000006](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000006-获取应用信息失败) | Failed to get the application information. |
| [10000007](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000007-时间操作失败) | Failed to get the system time. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

usageStatistics.queryAppStatsInfos(0, 20000000000000).then((res:usageStatistics.AppStatsMap) => {
  console.info('queryAppStatsInfos promise success.');
  console.info('queryAppStatsInfos promise result ' + JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('queryAppStatsInfos promise failed. code is: ' + err.code + ',message is: ' + err.message);
});
```

