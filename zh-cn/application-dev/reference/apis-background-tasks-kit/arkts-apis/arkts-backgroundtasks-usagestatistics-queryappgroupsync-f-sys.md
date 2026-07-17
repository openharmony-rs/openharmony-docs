# queryAppGroupSync（系统接口）

## 导入模块

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## queryAppGroupSync

```TypeScript
function queryAppGroupSync(): number
```

查询当前应用的优先级分组，使用同步方式返回。

**起始版本：** 10

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function queryAppGroupSync(): int--><!--Device-usageStatistics-function queryAppGroupSync(): int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回当前应用优先级分组结果，值越小，优先级越高。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [10000001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000001-内存操作失败) | Memory operation failed. |
| [10000002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000003-系统服务操作失败) | Failed to get system ability manager. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |
| [10000005](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000005-应用未安装) | Application is not installed. |
| [10000006](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000006-获取应用信息失败) | Failed to get the application information. |
| [10100002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10100002-获取应用分组信息失败) | Failed to get the application group information. |

**示例：**

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';

let priorityGroup: number = usageStatistics.queryAppGroupSync();

```


## queryAppGroupSync

```TypeScript
function queryAppGroupSync(bundleName: string): number
```

查询指定bundleName应用的优先级分组，使用同步方式返回。

**起始版本：** 10

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function queryAppGroupSync(bundleName: string): int--><!--Device-usageStatistics-function queryAppGroupSync(bundleName: string): int-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回应用的优先级分组结果，值越小，优先级越高。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [10000001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000001-内存操作失败) | Memory operation failed. |
| [10000002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000003-系统服务操作失败) | Failed to get system ability manager. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |
| [10000005](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000005-应用未安装) | Application is not installed. |
| [10000006](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000006-获取应用信息失败) | Failed to get the application information. |
| [10100002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10100002-获取应用分组信息失败) | Failed to get the application group information. |

**示例：**

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';

let priorityGroup: number = usageStatistics.queryAppGroupSync("com.ohos.camera");

```

