# registerAppGroupCallBack（系统接口）

## 导入模块

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## registerAppGroupCallBack

```TypeScript
function registerAppGroupCallBack(groupCallback: Callback<AppGroupCallbackInfo>, callback: AsyncCallback<void>): void
```

应用注册分组变化监听，即用户名下的某个应用分组发生变化时，向所有已注册分组变化监听的应用返回[AppGroupCallbackInfo](arkts-backgroundtasks-usagestatistics-appgroupcallbackinfo-i-sys.md)信息。使用Callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function registerAppGroupCallBack(groupCallback: Callback<AppGroupCallbackInfo>, callback: AsyncCallback<void>): void--><!--Device-usageStatistics-function registerAppGroupCallBack(groupCallback: Callback<AppGroupCallbackInfo>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AppGroupCallbackInfo> | 是 | 返回的应用分组变化信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当注册监听成功，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [10000001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000001-内存操作失败) | Memory operation failed. |
| [10000002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000003-系统服务操作失败) | Failed to get system ability manager. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |
| [10100001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10100001-应用分组信息操作重复) | Repeated operation on the application group. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

function onBundleGroupChanged(res: usageStatistics.AppGroupCallbackInfo) {
  console.info('BUNDLE_ACTIVE onBundleGroupChanged RegisterGroupCallBack callback success.');
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result appOldGroup is : ' + res.appOldGroup);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result appNewGroup is : ' + res.appNewGroup);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result changeReason is : ' + res.changeReason);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result userId is : ' + res.userId);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result bundleName is : ' + res.bundleName);
};
usageStatistics.registerAppGroupCallBack(onBundleGroupChanged, (err: BusinessError) => {
  if(err) {
    console.error('BUNDLE_ACTIVE registerAppGroupCallBack callback failed. code is: ' + err.code + ',message is: ' + err.message);
  } else {
    console.info('BUNDLE_ACTIVE registerAppGroupCallBack callback success.');
  }
});

```


## registerAppGroupCallBack

```TypeScript
function registerAppGroupCallBack(groupCallback: Callback<AppGroupCallbackInfo>): Promise<void>
```

注册应用分组变化监听，即用户名下的某个应用分组发生变化时，向所有已注册分组变化监听的应用返回[AppGroupCallbackInfo](arkts-backgroundtasks-usagestatistics-appgroupcallbackinfo-i-sys.md)信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.BUNDLE_ACTIVE_INFO

<!--Device-usageStatistics-function registerAppGroupCallBack(groupCallback: Callback<AppGroupCallbackInfo>): Promise<void>--><!--Device-usageStatistics-function registerAppGroupCallBack(groupCallback: Callback<AppGroupCallbackInfo>): Promise<void>-End-->

**系统能力：** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| groupCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AppGroupCallbackInfo> | 是 | 返回的应用分组变化信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [10000001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000001-内存操作失败) | Memory operation failed. |
| [10000002](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failed) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000003-系统服务操作失败) | Failed to get system ability manager. |
| [10000004](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10000004-通信失败) | Failed to access the device usage service. |
| [10100001](../../apis-backgroundtasks-kit/errorcode-DeviceUsageStatistics.md#10100001-应用分组信息操作重复) | Repeated operation on the application group. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

function onBundleGroupChanged(res: usageStatistics.AppGroupCallbackInfo) {
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack RegisterGroupCallBack callback success.');
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result appOldGroup is : ' + res.appOldGroup);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result appNewGroup is : ' + res.appNewGroup);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result changeReason is : ' + res.changeReason);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result userId is : ' + res.userId);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result bundleName is : ' + res.bundleName);
};
usageStatistics.registerAppGroupCallBack(onBundleGroupChanged).then( () => {
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack promise succeeded.');
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE registerAppGroupCallBack promise failed. code is: ' + err.code + ',message is: ' + err.message);
});

```

