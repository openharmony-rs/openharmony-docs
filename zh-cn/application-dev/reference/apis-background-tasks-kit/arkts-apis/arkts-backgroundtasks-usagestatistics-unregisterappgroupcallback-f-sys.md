# unregisterAppGroupCallBack（系统接口）

## unregisterAppGroupCallBack

```TypeScript
function unregisterAppGroupCallBack(callback: AsyncCallback<void>): void
```

应用解除分组变化监听。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function unregisterAppGroupCallBack(callback: AsyncCallback<void>): void--><!--Device-usageStatistics-function unregisterAppGroupCallBack(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。 当解除监听成功，err为undefined；否则为错误对象。 |

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
| [10100001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10100001-应用分组信息操作重复) | Repeated operation on the application group. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

usageStatistics.unregisterAppGroupCallBack((err: BusinessError) => {
  if(err) {
    console.error('BUNDLE_ACTIVE unregisterAppGroupCallBack callback failed. code is: ' + err.code + ',message is: ' + err.message);
  } else {
    console.info('BUNDLE_ACTIVE unregisterAppGroupCallBack callback success.');
  }
});
```


## unregisterAppGroupCallBack

```TypeScript
function unregisterAppGroupCallBack(): Promise<void>
```

应用解除分组变化监听。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function unregisterAppGroupCallBack(): Promise<void>--><!--Device-usageStatistics-function unregisterAppGroupCallBack(): Promise<void>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

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
| [10100001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10100001-应用分组信息操作重复) | Repeated operation on the application group. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

usageStatistics.unregisterAppGroupCallBack().then( () => {
  console.info('BUNDLE_ACTIVE unregisterAppGroupCallBack promise succeeded.');
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE unregisterAppGroupCallBack promise failed. code is: ' + err.code + ',message is: ' + err.message);
});
```

