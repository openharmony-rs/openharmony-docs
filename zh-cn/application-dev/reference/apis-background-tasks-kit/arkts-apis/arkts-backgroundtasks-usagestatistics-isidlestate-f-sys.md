# isIdleState（系统接口）

## isIdleState

```TypeScript
function isIdleState(bundleName: string, callback: AsyncCallback<boolean>): void
```

查询指定的应用是否为常用应用（GroupType值≤30），使用Callback形式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function isIdleState(bundleName: string, callback: AsyncCallback<boolean>): void--><!--Device-usageStatistics-function isIdleState(bundleName: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的bundleName。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示应用为常用应用；返回false表示指定应用不是常用应用或bundleName无效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameters types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [10000001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000001-内存操作失败) | Memory operation failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [10000002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; &lt;br&gt; 2. Failed to apply for memory. |
| [10000003](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000003-系统服务操作失败) | Failed to get system ability manager. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |
| [10000006](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000006-获取应用信息失败) | Failed to get the application information. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

usageStatistics.isIdleState('com.ohos.camera', (err: BusinessError, res: boolean) => {
  if (err) {
    console.error('BUNDLE_ACTIVE isIdleState callback failed. code is: ' + err.code + ',message is: ' + err.message);
  } else {
    console.info('BUNDLE_ACTIVE isIdleState callback succeeded, result: ' + JSON.stringify(res));
  }
});
```


## isIdleState

```TypeScript
function isIdleState(bundleName: string): Promise<boolean>
```

查询指定的应用是否为常用应用（GroupType值≤30），使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function isIdleState(bundleName: string): Promise<boolean>--><!--Device-usageStatistics-function isIdleState(bundleName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。 若应用为常用应用，返回true；若指定应用不是常用应用或bundleName无效，则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameters types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [10000001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000001-内存操作失败) | Memory operation failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [10000002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; &lt;br&gt; 2. Failed to apply for memory. |
| [10000003](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000003-系统服务操作失败) | Failed to get system ability manager. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |
| [10000006](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000006-获取应用信息失败) | Failed to get the application information. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

usageStatistics.isIdleState('com.ohos.camera').then((res: boolean) => {
  console.info('BUNDLE_ACTIVE isIdleState promise succeeded, result: ' + JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE isIdleState promise failed. code is: ' + err.code + ',message is: ' + err.message);
});
```

