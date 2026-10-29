# @ohos.file.cloudDiskManager (云盘管理)(系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->

本模块为系统文件管理应用提供获取三方云盘注册的同步根信息（包括路径、包名、状态等）的能力，适用于展示和管理三方云盘同步根目录的场景。同步根是指三方云盘应用在系统中注册的本地同步目录的根路径，系统文件管理应用可通过该信息识别和管理不同云盘的同步状态。本模块还支持系统文件管理应用对三方网盘占位符文件执行水合与脱水，并订阅水合进度，适用于在线打开网盘文件、优化本地存储空间等场景。占位符文件是三方网盘应用在同步根内创建的文件，本地仅保留文件元数据与占位数据，文件内容保存在云侧；水合指将云侧内容下载到本地使文件可正常访问，脱水指将已完全水合的文件回退为占位符，在保留文件逻辑大小的同时释放本地存储空间。

> **说明：**
>
> 本模块首批接口从API version 21开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## SyncFolderAccessor

同步根访问器，为系统文件管理应用提供获取所有已注册的同步根列表（包括路径、包名、状态等详细信息）的能力。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

### constructor

constructor()

SyncFolderAccessor的构造函数，用于创建SyncFolderAccessor类的实例。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**错误码：**

接口抛出错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |

**示例：**

  ```ts
  import { cloudDiskManager } from '@kit.CoreFileKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  @Entry
  @Component
  struct Index {
    build() {
      Column() {
        Button('constructor')
        .onClick(async() => {
            try {
              let syncFolderAccessor: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
            } catch (err) {
                let error: BusinessError = err as BusinessError;
                console.error(`SyncFolderAccessor constructor failed. Code: ${error.code}, message: ${error.message}`);
            }
        });
      }
    }
  }

  ```
  
### getAllSyncFolders

getAllSyncFolders(): Promise&lt;Array&lt;SyncFolder&gt;&gt;

获取所有注册的同步根信息，适用于系统文件管理应用展示和管理三方云盘同步根列表的场景。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**返回值：**

| 类型 | 说明 |
| --- | -- |
| Promise&lt;Array&lt;[SyncFolder](#syncfolder)&gt;&gt; | Promise对象。resolve时返回所有三方云盘应用的同步根列表，reject时返回BusinessError错误对象。 |

**错误码：**

接口抛出错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400003 | IPC communication failed. |
| 34400014 | Temporary failure. Retry is recommended (e.g., network issues). |
| 34400015 | Cloud disk is not allowed on this device. |

**示例：**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';
const TAG: string = '[cloudDiskManager]';

try {
    console.info(`${TAG}getAllSyncFolders start`);
    let syncFolderAccessor: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
    syncFolderAccessor.getAllSyncFolders().then((syncFolders) => {
        console.info(`${TAG}getAllSyncFolders success, length: ${syncFolders.length}`);
        for (let i = 0; i < syncFolders.length; ++i) {
            console.info(`${TAG}syncFolders[${i}].path: ${syncFolders[i].path}`);
            console.info(`${TAG}syncFolders[${i}].bundleName: ${syncFolders[i].bundleName}`);
            console.info(`${TAG}syncFolders[${i}].state: ${syncFolders[i].state}`);
            if (syncFolders[i].displayNameResId) {
                console.info(`${TAG}syncFolders[${i}].displayNameResId: ${syncFolders[i].displayNameResId}`);
            }
            if (syncFolders[i].customAlias) {
                console.info(`${TAG}syncFolders[${i}].customAlias: ${syncFolders[i].customAlias}`);
            }
            if (syncFolders[i].isSupportPlaceHolder) {
                console.info(`${TAG}syncFolders[${i}].isSupportPlaceHolder: ${syncFolders[i].isSupportPlaceHolder}`);
            }
        }
    }).catch((err: BusinessError<object>) => {
        console.error(`${TAG}Failed to getAllSyncFolders. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(`${TAG}getAllSyncFolders failed. Code: ${error.code}, message: ${error.message}`);
}
```

## CloudDiskSystemAccessor

网盘系统访问器，为系统文件管理应用提供对三方网盘占位符文件执行水合与脱水的能力，并支持订阅水合进度。在使用前，需要先创建CloudDiskSystemAccessor实例。

**起始版本**：26.0.1

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

### constructor

constructor()

CloudDiskSystemAccessor的构造函数，用于创建CloudDiskSystemAccessor类的实例。

**起始版本**：26.0.1

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 34400014 | Temporary failure. Failed to initialize the native accessor instance. Please try again. |

**示例：**

```ts
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

### onHydrateProgress

onHydrateProgress(callback: Callback&lt;HydrateProgress&gt;): void

订阅本实例发起的水合及取消操作的进度事件，适用于文件管理应用展示文件水合进度的场景。使用callback异步回调。

> **说明：**
>
> - 回调按发起操作的实例路由，与目标文件无关；同一实例可同时发起多个水合任务，通过[HydrateProgress](#hydrateprogress)中的filePath字段区分不同文件。
> - 同一实例同一时间仅可注册一个回调；携带有效参数重复订阅时保留已有回调，不报告重复注册错误。
> - 任务发起后订阅，或调用[offHydrateProgress](#offhydrateprogress)()取消订阅后再次订阅，仅可接收路由到本实例的后续事件，此前的进度事件不会重放。

**起始版本**：26.0.1

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[HydrateProgress](#hydrateprogress)&gt; | 是 | 回调函数，在水合任务进度或状态变化时通过此函数进行通知。 |

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 801 | This feature is not supported on the device. |
| 34400003 | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| 34400014 | Temporary failure. Failed to initialize the callback, resolve the user account, or complete an internal operation. Please try again. |

**示例：**

```ts
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

### offHydrateProgress

offHydrateProgress(callback?: Callback&lt;HydrateProgress&gt;): void

取消订阅本实例的水合进度事件。使用callback异步回调。

> **说明：**
>
> - 本操作不会取消本实例已发起的水合任务，其他实例注册的订阅不受影响。
> - 当前实例未注册回调时，本接口在通过权限和参数校验后正常返回。

**起始版本**：26.0.1

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callback | Callback&lt;[HydrateProgress](#hydrateprogress)&gt; | 否 | 回调函数，取消当前实例已注册的水合进度回调；不传入时效果相同。 |

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 801 | This feature is not supported on the device. |
| 34400003 | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried when unregistering this instance's callback from the service. |
| 34400014 | Temporary failure while unregistering the callback. Please try again. |

**示例：**

```ts
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

### hydratePlaceholder

hydratePlaceholder(filePath: string, callbackType: CallbackType, priority: HydratePriority): Promise&lt;void&gt;

对占位符文件发起水合或取消水合，适用于文件管理应用在线打开三方网盘占位文件的场景。使用Promise异步回调。

> **说明：**
>
> - callbackType取FETCH_DATA时发起水合：任务创建成功后Promise立即兑现，仅表示水合任务已创建并入队，不代表文件已开始下载或水合完成。水合进度通过发起任务的实例的[onHydrateProgress](#onhydrateprogress)()回调送达；发起或取消水合任务前无需先注册回调。文件水合状态依次经过PENDING、IN_PROGRESS，最终为COMPLETED或CANCELLED。
> - callbackType取CANCEL_FETCH_DATA时取消水合：目标文件存在进行中的水合任务时将其取消，取消成功时CANCELLED事件仅送达发起取消的实例（即使水合任务由其他实例发起）；不存在进行中的水合任务时Promise被拒绝并返回34400032错误码。发起取消的实例未注册回调时，其取消事件不会转发给其他实例，也不会事后重放。

**起始版本**：26.0.1

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| filePath | string | 是 | 占位符文件的路径，须为"/storage/Users/currentUser/"前缀的绝对路径，且位于三方网盘应用已注册的同步根目录范围内，最大长度为4096且不能为空。 |
| callbackType | [CallbackType](#callbacktype) | 是 | 回调类型。取FETCH_DATA时发起水合，取CANCEL_FETCH_DATA时取消水合；DEHYDRATE不适用于本接口，传入时返回34400001错误。 |
| priority | [HydratePriority](#hydratepriority) | 是 | 水合任务的优先级，仅callbackType为FETCH_DATA时生效。 |

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 801 | This feature is not supported on the device or file system. |
| 34400001 | The input parameter is invalid. The service rejected the path, callback type, or file metadata. CallbackType.DEHYDRATE is not supported by this operation. |
| 34400003 | IPC communication failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| 34400010 | The sync root path does not exist, or the target file or sync root mount path is missing during path resolution. |
| 34400014 | Temporary failure. Failed to resolve the user account, access the file, prepare a hydrate task, schedule the request, or complete an internal operation. Please try again. |
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

**示例：**

```ts
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

### dehydrateFile

dehydrateFile(filePath: string): Promise&lt;void&gt;

对文件进行脱水，使用Promise异步回调。

> **说明：**
>
> - 待脱水文件可以是由其他实例水合的文件，本操作不触发水合进度事件。
> - 脱水前系统会向三方网盘应用发起脱水授权请求，网盘应用拒绝授权时Promise被拒绝并返回34400029错误码，文件保持不变。
> - 文件已处于未水合状态时调用本接口为幂等操作，Promise正常兑现。
> - 文件存在进行中的水合任务时不允许脱水，Promise被拒绝并返回34400019错误码。

**起始版本**：26.0.1

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| filePath | string | 是 | 待脱水的占位符文件路径，须为"/storage/Users/currentUser/"前缀的绝对路径，且位于三方网盘应用已注册的同步根目录范围内，最大长度为4096且不能为空。 |

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 801 | This feature is not supported on the device or file system. |
| 34400001 | The input parameter is invalid. The service rejected the path or a file operation argument, the target is a directory, or the provider request could not be serialized. |
| 34400003 | IPC communication with the service or cloud disk provider failed. |
| 34400008 | No sync root is registered, or the registered sync roots cannot be queried. |
| 34400010 | The sync root path does not exist, or the target file or sync root mount path is missing during path resolution. |
| 34400014 | Temporary failure. Failed to resolve the user account, access the file, restore its logical size, schedule the request, or complete an internal operation. Please try again. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | A hydrate task for the target file is pending or in progress. |
| 34400020 | The available disk space is insufficient, or the disk quota has been exhausted. |
| 34400021 | The cloud disk provider's callback table is not registered, or no usable sync root matches the path. |
| 34400023 | A path component that must be a directory is not a directory. |
| 34400024 | A required file or directory does not exist while resolving or accessing the target path. |
| 34400025 | The file name or path is too long. |
| 34400029 | The cloud disk provider did not approve the dehydration request. |
| 34400033 | The placeholder state or its stored attribute is invalid. |

**示例：**

```ts
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

## SyncFolder

表示同步根信息，包含同步根的路径、包名、状态以及显示别名等详细信息，用于系统文件管理应用识别和管理不同云盘的同步根。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 类型   | 只读 | 可选 | 说明      |
| --------- | ------ | ---- | ---- | ---------------------------- |
| path | string | 否   | 否   | 同步根对应的本地绝对路径，表示三方云盘应用在系统中注册的本地同步目录的根路径。     |
| bundleName   | string | 否   | 否   | 注册该同步根的三方云盘应用的包名。   |
| state   | [SyncFolderState](#syncfolderstate) | 否   | 否   | 同步根的同步状态，取值为INACTIVE（未激活）或ACTIVE（激活），详见SyncFolderState。   |
| displayNameResId   | number | 否   | 是   | 资源ID，用于映射文件管理应用列表中显示的别名。当三方云盘应用通过资源ID指定显示别名时，此字段包含对应的资源ID；未指定时默认值为undefined，表示不使用资源ID指定的别名。与customAlias均可用于设置显示别名，两者同时存在时以系统实现为准。   |
| customAlias   | string | 否   | 是   | 在文件管理应用列表显示的自定义别名。当三方云盘应用直接指定自定义别名时，此字段包含对应的别名内容；未指定时默认值为undefined。与displayNameResId均可用于设置显示别名，两者同时存在时以系统实现为准。   |
| isSupportPlaceHolder   | boolean | 否   | 是   | 同步根是否支持占位符，true：表示同步根支持占位符，false：表示同步根不支持占位符。默认值为false。<br>**起始版本**：26.0.1 <br>**模型约束**：此接口仅可在Stage模型下使用。|

## SyncFolderState

枚举，三方云盘同步根的状态。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| INACTIVE  |  0   | 表示同步根处于未激活状态。|
| ACTIVE    |  1   | 表示同步根处于激活状态。  |

## HydrateProgress

描述水合任务的进度信息，通过[onHydrateProgress](#onhydrateprogress)()订阅的回调获取。

**起始版本**：26.0.1

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

| 名称      | 类型   | 只读 | 可选 | 说明      |
| --------- | ------ | ---- | ---- | ---------------------------- |
| filePath | string | 否   | 否   | 文件的原始绝对路径，即调用hydratePlaceholder()时传入的filePath。最大长度为4096且不能为空。     |
| state   | [HydrateProgressState](#hydrateprogressstate) | 否   | 否   | 水合进度状态。   |
| processedSize   | number | 否   | 否   | 已水合的字节数，仅state为IN_PROGRESS时有效。单位为字节。   |
| totalSize   | number | 否   | 否   | 正在水合的文件总大小，单位为字节。   |

## HydrateProgressState

枚举，水合任务的水合进度状态。

**起始版本**：26.0.1

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| PENDING  |  0   | 水合任务已创建，尚未开始处理。|
| IN_PROGRESS    |  1   | 水合进行中。  |
| COMPLETED    |  2   | 水合完成。  |
| CANCELLED    |  3   | 水合已取消，取消来源包括用户取消、网盘应用放弃任务。  |

## CallbackType

枚举，网盘文件数据获取及脱水授权的回调类型。

**起始版本**：26.0.1

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| FETCH_DATA  |  0   | 获取云文件数据（发起水合）。|
| CANCEL_FETCH_DATA    |  1   | 取消获取云文件数据（取消水合）。  |
| DEHYDRATE    |  2   | 脱水授权请求。脱水执行前，系统通过该类型的回调向已注册回调的三方网盘应用发起脱水授权请求，由三方网盘应用决定是否允许本次脱水。  |

## HydratePriority

枚举，水合任务的优先级。

**起始版本**：26.0.1

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**模型约束**：此接口仅可在Stage模型下使用。

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| LOW  |  0   | 低优先级。|
| NORMAL    |  1   | 普通优先级。  |
| HIGH    |  2   | 高优先级。  |
