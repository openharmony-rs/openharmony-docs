# CloudDiskSystemAccessor（系统接口）

```TypeScript
class CloudDiskSystemAccessor
```

文件管理器访问云盘系统能力的类，如补水和脱水文件。

**起始版本：** 26.0.1

<!--Device-cloudDiskManager-class CloudDiskSystemAccessor--><!--Device-cloudDiskManager-class CloudDiskSystemAccessor-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
constructor()
```

用于创建**CloudDiskSystemAccessor**实例的构造函数。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ACCESS_CLOUD_DISK_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudDiskSystemAccessor-constructor()--><!--Device-CloudDiskSystemAccessor-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-系统内部错误) | Temporary failure. Failed to initialize the native accessor instance. Please try again. |

<!--Del-->
**示例**

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
  console.info('CloudDiskSystemAccessor created successfully.');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`CloudDiskSystemAccessor constructor failed. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## dehydrateFile

```TypeScript
dehydrateFile(filePath: string): Promise<void>
```

对文件进行脱水。该接口使用promise返回结果。该文件可能已被另一个实例删除。此操作不会发出delegateProgress事件。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ACCESS_CLOUD_DISK_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudDiskSystemAccessor-dehydrateFile(filePath: string): Promise<void>--><!--Device-CloudDiskSystemAccessor-dehydrateFile(filePath: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 要去水化的文件的路径。<br>最大长度为4096且不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | This feature is not supported on the device or file system. |
| [34400001](../errorcode-clouddiskmanager-sys.md#34400001-输入参数无效) | The input parameter is invalid. The service rejected the path or a file operation argument, the target is a directory, or the provider request could not be serialized. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc通信失败) | IPC communication with the service or cloud disk provider failed. |
| [34400008](../errorcode-clouddiskmanager-sys.md#34400008-同步根路径未注册) | No sync root is registered, or the registered sync roots cannot be queried. |
| [34400010](../errorcode-clouddiskmanager-sys.md#34400010-同步根路径不存在) | The sync root path does not exist, or the target file or sync root mount path is missing during path resolution. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-系统内部错误) | Temporary failure. Failed to resolve the user account, access the file, restore its logical size, schedule the request, or complete an internal operation. Please try again. |
| [34400017](../errorcode-clouddiskmanager-sys.md#34400017-目标路径不是占位符文件) | The target path is not a placeholder file. |
| [34400019](../errorcode-clouddiskmanager-sys.md#34400019-水合任务已在进行中) | A hydrate task for the target file is pending or in progress. |
| [34400020](../errorcode-clouddiskmanager-sys.md#34400020-磁盘可用空间不足) | The available disk space is insufficient, or the disk quota has been exhausted. |
| [34400021](../errorcode-clouddiskmanager-sys.md#34400021-回调表未注册) | The cloud disk provider's callback table is not registered, or no usable sync root matches the path. |
| [34400023](../errorcode-clouddiskmanager-sys.md#34400023-路径父目录不是目录) | A path component that must be a directory is not a directory. |
| [34400024](../errorcode-clouddiskmanager-sys.md#34400024-目标路径不存在) | A required file or directory does not exist while resolving or accessing the target path. |
| [34400025](../errorcode-clouddiskmanager-sys.md#34400025-文件名或路径过长) | The file name or path is too long. |
| [34400029](../errorcode-clouddiskmanager-sys.md#34400029-网盘应用拒绝脱水) | The cloud disk provider did not approve the dehydration request. |
| [34400033](../errorcode-clouddiskmanager-sys.md#34400033-占位符状态无效) | The placeholder state or its stored attribute is invalid. |

<!--Del-->
**示例**

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
let filePath: string = '/storage/Users/currentUser/Docs/cloud/photo.jpg';

accessor.dehydrateFile(filePath).then(() => {
  console.info('dehydrate file successfully.');
}).catch((err: BusinessError) => {
  console.error(`dehydrateFile failed with error message: ${err.message}, error code: ${err.code}`);
});
```

<!--DelEnd-->

## hydratePlaceholder

```TypeScript
hydratePlaceholder(filePath: string, callbackType: CallbackType, priority: HydratePriority): Promise<void>
```

填充占位符文件。该接口使用promise返回结果。Hydration进度会传递给启动任务的实例的Hydration progress回调。如果该实例取消任务成功，则只向该实例下发CANCELLED事件。即使其他实例启动了该任务。调用的结果也通过它的promise返回。在开始或取消任务之前，无需注册回调。如果取消实例没有注册的回调，它的取消事件不会传递到另一个实例，也不会在以后重播。服务的自动取消被路由到启动任务的实例。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ACCESS_CLOUD_DISK_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudDiskSystemAccessor-hydratePlaceholder(filePath: string, callbackType: CallbackType, priority: HydratePriority): Promise<void>--><!--Device-CloudDiskSystemAccessor-hydratePlaceholder(filePath: string, callbackType: CallbackType, priority: HydratePriority): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 要添加的占位符文件的路径。<br>最大长度为4096且不能为空。 |
| callbackType | [CallbackType](arkts-corefile-clouddiskmanager-callbacktype-e-sys.md) | 是 | 云端文件取数回调类型。 |
| priority | [HydratePriority](arkts-corefile-clouddiskmanager-hydratepriority-e-sys.md) | 是 | 水合物任务的优先级。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | This feature is not supported on the device or file system. |
| [34400001](../errorcode-clouddiskmanager-sys.md#34400001-输入参数无效) | The input parameter is invalid. The service rejected the path, callback type, or file metadata. CallbackType.DEHYDRATE is not supported by this operation. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc通信失败) | IPC communication failed. |
| [34400008](../errorcode-clouddiskmanager-sys.md#34400008-同步根路径未注册) | No sync root is registered, or the registered sync roots cannot be queried. |
| [34400010](../errorcode-clouddiskmanager-sys.md#34400010-同步根路径不存在) | The sync root path does not exist, or the target file or sync root mount path is missing during path resolution. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-系统内部错误) | Temporary failure. Failed to resolve the user account, access the file, prepare a hydrate task, schedule the request, or complete an internal operation. Please try again. |
| [34400017](../errorcode-clouddiskmanager-sys.md#34400017-目标路径不是占位符文件) | The target path is not a placeholder file. |
| [34400019](../errorcode-clouddiskmanager-sys.md#34400019-水合任务已在进行中) | A hydrate task for the target file is already pending or in progress. |
| [34400021](../errorcode-clouddiskmanager-sys.md#34400021-回调表未注册) | The cloud disk provider's callback table is not registered, or no usable sync root matches the path. |
| [34400023](../errorcode-clouddiskmanager-sys.md#34400023-路径父目录不是目录) | A path component that must be a directory is not a directory. |
| [34400024](../errorcode-clouddiskmanager-sys.md#34400024-目标路径不存在) | A required file or directory does not exist while resolving or accessing the target path. |
| [34400025](../errorcode-clouddiskmanager-sys.md#34400025-文件名或路径过长) | The file name or path is too long. |
| [34400031](../errorcode-clouddiskmanager-sys.md#34400031-占位符文件已完全水合) | The placeholder is already fully hydrated. |
| [34400032](../errorcode-clouddiskmanager-sys.md#34400032-无进行中的水合任务) | Cancellation was requested, but no hydrate task is pending or in progress. |
| [34400033](../errorcode-clouddiskmanager-sys.md#34400033-占位符状态无效) | The placeholder state or its stored attribute is invalid. |
| [34400034](../errorcode-clouddiskmanager-sys.md#34400034-活跃水合任务数量达到上限) | The limit on pending hydrate tasks has been reached. |

<!--Del-->
**示例**

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
let filePath: string = '/storage/Users/currentUser/Docs/cloud/photo.jpg';

accessor.onHydrateProgress((progress: cloudDiskManager.HydrateProgress) => {
  console.info(`hydrate progress - filePath: ${progress.filePath}, state: ${progress.state}`);
  console.info(`processedSize: ${progress.processedSize}, totalSize: ${progress.totalSize}`);
});

accessor.hydratePlaceholder(filePath, cloudDiskManager.CallbackType.FETCH_DATA,
  cloudDiskManager.HydratePriority.HIGH).then(() => {
  console.info('hydrate task created successfully.');
}).catch((err: BusinessError) => {
  console.error(`hydratePlaceholder failed with error message: ${err.message}, error code: ${err.code}`);
});
```

<!--DelEnd-->

## offHydrateProgress

```TypeScript
offHydrateProgress(callback?: Callback<HydrateProgress>): void
```

取消订阅此实例的水合进度事件，而不取消其水合任务。其他实例注册的订阅不受影响。如果没有注册回调，则此方法在权限和参数检查后会成功。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ACCESS_CLOUD_DISK_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudDiskSystemAccessor-offHydrateProgress(callback?: Callback<HydrateProgress>): void--><!--Device-CloudDiskSystemAccessor-offHydrateProgress(callback?: Callback<HydrateProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HydrateProgress](arkts-corefile-clouddiskmanager-hydrateprogress-i-sys.md)&gt; | 否 | 进度变化时调用的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. This method does not accept arguments. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | This feature is not supported on the device. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc通信失败) | IPC communication failed. |
| [34400008](../errorcode-clouddiskmanager-sys.md#34400008-同步根路径未注册) | No sync root is registered, or the registered sync roots cannot be queried when unregistering this instance's callback from the service. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-系统内部错误) | Temporary failure while unregistering the callback. Please try again. |

<!--Del-->
**示例**

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();

let callback = (progress: cloudDiskManager.HydrateProgress) => {
  console.info(`hydrate progress - filePath: ${progress.filePath}, state: ${progress.state}`);
};

accessor.onHydrateProgress(callback);

try {
  accessor.offHydrateProgress(callback); // 取消指定的回调
  accessor.offHydrateProgress(); // 取消所有回调
  console.info('unsubscribe hydrateProgress successfully.');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`offHydrateProgress failed. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->

## onHydrateProgress

```TypeScript
onHydrateProgress(callback: Callback<HydrateProgress>): void
```

为在此实例上调用的初始化和取消操作订阅进度事件。回调由调用实例选择，而不考虑目标文件。一次只能为该实例注册一个回调。具有有效参数的重复订阅保留现有回调而不报告重复登记错误。在任务开始后订阅，或者在调用offHydrateProgress后再次订阅，接收后续的路由到此实例的事件。较早的事件不会重播。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ACCESS_CLOUD_DISK_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CloudDiskSystemAccessor-onHydrateProgress(callback: Callback<HydrateProgress>): void--><!--Device-CloudDiskSystemAccessor-onHydrateProgress(callback: Callback<HydrateProgress>): void-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HydrateProgress](arkts-corefile-clouddiskmanager-hydrateprogress-i-sys.md)&gt; | 是 | 进度变化时调用的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The caller is not a system application. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | This feature is not supported on the device. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc通信失败) | IPC communication failed. |
| [34400008](../errorcode-clouddiskmanager-sys.md#34400008-同步根路径未注册) | No sync root is registered, or the registered sync roots cannot be queried. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-系统内部错误) | Temporary failure. Failed to initialize the callback, resolve the user account, or complete an internal operation. Please try again. |

<!--Del-->
**示例**

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();

let callback = (progress: cloudDiskManager.HydrateProgress) => {
  console.info(`hydrate progress - filePath: ${progress.filePath}, state: ${progress.state}`);
  console.info(`processedSize: ${progress.processedSize}, totalSize: ${progress.totalSize}`);
};

try {
  accessor.onHydrateProgress(callback);
  console.info('subscribe hydrateProgress successfully.');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`onHydrateProgress failed. Code: ${error.code}, message: ${error.message}`);
}
```

<!--DelEnd-->
