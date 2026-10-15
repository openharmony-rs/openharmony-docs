# CloudDiskSystemAccessor (System API)

```TypeScript
class CloudDiskSystemAccessor
```

A class that enables the File Manager to access cloud disk system capabilities, such as hydrating and dehydrating files.

**Since:** 26.0.1

<!--Device-cloudDiskManager-class CloudDiskSystemAccessor--><!--Device-cloudDiskManager-class CloudDiskSystemAccessor-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
constructor()
```

A constructor used to create a **CloudDiskSystemAccessor** instance.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ACCESS_CLOUD_DISK_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudDiskSystemAccessor-constructor()--><!--Device-CloudDiskSystemAccessor-constructor()-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-system-internal-error) | Temporary failure. Failed to initialize the native accessor instance. Please try again. |

## dehydrateFile

```TypeScript
dehydrateFile(filePath: string): Promise<void>
```

Dehydrates a file. This API uses a promise to return the result. The file can have been hydrated by another instance. This operation does not emit hydrateProgress events.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ACCESS_CLOUD_DISK_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudDiskSystemAccessor-dehydrateFile(filePath: string): Promise<void>--><!--Device-CloudDiskSystemAccessor-dehydrateFile(filePath: string): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Path of the file to dehydrate.<br>The maximum length is 4096 and cannot be empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This feature is not supported on the device or file system. |
| 34400001 | The input parameter is invalid. The service rejected the path or a file operation argument, the target is a directory, or the provider request could not be serialized. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc-failed) | IPC communication with the service or cloud disk provider failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| 34400010 | The sync root path does not exist, or the target file or sync root mount path is missing during path resolution. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-system-internal-error) | Temporary failure. Failed to resolve the user account, access the file, restore its logical size, schedule the request, or complete an internal operation. Please try again. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | A hydrate task for the target file is pending or in progress. |
| 34400020 | The available disk space is insufficient, or the disk quota has been exhausted. |
| 34400021 | The cloud disk provider's callback table is not registered, or no usable sync root matches the path. |
| 34400023 | A path component that must be a directory is not a directory. |
| 34400024 | A required file or directory does not exist while resolving or accessing the target path. |
| 34400025 | The file name or path is too long. |
| 34400029 | The cloud disk provider did not approve the dehydration request. |
| 34400033 | The placeholder state or its stored attribute is invalid. |

## hydratePlaceholder

```TypeScript
hydratePlaceholder(filePath: string, callbackType: CallbackType, priority: HydratePriority): Promise<void>
```

Hydrates a placeholder file. This API uses a promise to return the result. Hydration progress is delivered to the hydrateProgress callback of the instance that starts the task. If this instance successfully cancels a task, the CANCELLED event is delivered only to this instance, even if another instance started the task. The call's result is also returned through its promise. A callback does not have to be registered before starting or cancelling a task. If the cancelling instance has no registered callback, its cancellation event is not delivered to another instance or replayed later. Automatic cancellation by the service is routed to the instance that started the task.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ACCESS_CLOUD_DISK_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudDiskSystemAccessor-hydratePlaceholder(filePath: string, callbackType: CallbackType, priority: HydratePriority): Promise<void>--><!--Device-CloudDiskSystemAccessor-hydratePlaceholder(filePath: string, callbackType: CallbackType, priority: HydratePriority): Promise<void>-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Path of the placeholder file to hydrate.<br>The maximum length is 4096 and cannot be empty. |
| callbackType | [CallbackType](arkts-corefile-clouddiskmanager-callbacktype-e-sys.md) | Yes | Callback type for cloud file data fetching. |
| priority | [HydratePriority](arkts-corefile-clouddiskmanager-hydratepriority-e-sys.md) | Yes | Priority of the hydrate task. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This feature is not supported on the device or file system. |
| 34400001 | The input parameter is invalid. The service rejected the path, callback type, or file metadata. CallbackType.DEHYDRATE is not supported by this operation. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc-failed) | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| 34400010 | The sync root path does not exist, or the target file or sync root mount path is missing during path resolution. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-system-internal-error) | Temporary failure. Failed to resolve the user account, access the file, prepare a hydrate task, schedule the request, or complete an internal operation. Please try again. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | A hydrate task for the target file is already pending or in progress. |
| 34400021 | The cloud disk provider's callback table is not registered, or no usable sync root matches the path. |
| 34400023 | A path component that must be a directory is not a directory. |
| 34400024 | A required file or directory does not exist while resolving or accessing the target path. |
| 34400025 | The file name or path is too long. |
| 34400031 | The placeholder is already fully hydrated. |
| 34400032 | Cancellation was requested, but no hydrate task is pending or in progress. |
| 34400033 | The placeholder state or its stored attribute is invalid. |
| 34400034 | The limit on pending hydrate tasks has been reached. |

## offHydrateProgress

```TypeScript
offHydrateProgress(callback?: Callback<HydrateProgress>): void
```

Unsubscribes this instance from hydrate progress events without cancelling its hydrate tasks. Subscriptions registered by other instances are not affected. If no callback is registered, this method succeeds after permission and parameter checks.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ACCESS_CLOUD_DISK_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudDiskSystemAccessor-offHydrateProgress(callback?: Callback<HydrateProgress>): void--><!--Device-CloudDiskSystemAccessor-offHydrateProgress(callback?: Callback<HydrateProgress>): void-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HydrateProgress](arkts-corefile-clouddiskmanager-hydrateprogress-i-sys.md)&gt; | No | Callback invoked when the hydrate progress changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. This method does not accept arguments. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This feature is not supported on the device. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc-failed) | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried when unregistering this instance's callback from the service. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-system-internal-error) | Temporary failure while unregistering the callback. Please try again. |

## onHydrateProgress

```TypeScript
onHydrateProgress(callback: Callback<HydrateProgress>): void
```

Subscribes to progress events for hydration and cancellation operations invoked on this instance. The callback is selected by the calling instance, regardless of the target file. Only one callback can be registered for this instance at a time. Repeated subscriptions with valid arguments retain the existing callback without reporting a duplicate-registration error. Subscribing after a task starts, or subscribing again after calling offHydrateProgress, receives subsequent events routed to this instance. Earlier events are not replayed.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ACCESS_CLOUD_DISK_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudDiskSystemAccessor-onHydrateProgress(callback: Callback<HydrateProgress>): void--><!--Device-CloudDiskSystemAccessor-onHydrateProgress(callback: Callback<HydrateProgress>): void-End-->

**System capability:** SystemCapability.FileManagement.CloudDiskManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HydrateProgress](arkts-corefile-clouddiskmanager-hydrateprogress-i-sys.md)&gt; | Yes | Callback invoked when the hydrate progress changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The caller is not a system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | This feature is not supported on the device. |
| [34400003](../errorcode-clouddiskmanager-sys.md#34400003-ipc-failed) | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| [34400014](../errorcode-clouddiskmanager-sys.md#34400014-system-internal-error) | Temporary failure. Failed to initialize the callback, resolve the user account, or complete an internal operation. Please try again. |
