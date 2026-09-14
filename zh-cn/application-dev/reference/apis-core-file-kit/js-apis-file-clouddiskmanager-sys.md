# @ohos.file.cloudDiskManager (云盘管理)(系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->

本模块为系统文件管理应用提供获取三方云盘注册的同步根信息（包括路径、包名、状态等）的能力，适用于展示和管理三方云盘同步根目录的场景。同步根是指三方云盘应用在系统中注册的本地同步目录的根路径，系统文件管理应用可通过该信息识别和管理不同云盘的同步状态。

本模块还支持系统文件管理应用对三方云盘占位符文件执行水合与脱水，并订阅水合进度，适用于在线打开云盘文件、优化本地存储空间等场景。占位符文件是三方云盘应用在同步根内创建的文件，本地仅保留文件元数据与占位数据，文件内容保存在云端；水合指将云端内容下载到本地使文件可正常访问，脱水指将已完全水合的文件回退为占位符，在保留文件逻辑大小的同时释放本地存储空间。


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
        }
    }).catch((err: BusinessError<object>) => {
        console.error(`${TAG}Failed to getAllSyncFolders. Code: ${err.code}, message: ${err.message}`);
    });
} catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(`${TAG}getAllSyncFolders failed. Code: ${error.code}, message: ${error.message}`);
}
```

## CloudDiskSystemAccessor<sup>26+</sup>

云盘系统访问器，为系统文件管理应用提供对三方云盘占位符文件执行水合与脱水的能力，并支持订阅水合进度。在使用前，需要先创建CloudDiskSystemAccessor实例。

**起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

### constructor<sup>26+</sup>

constructor()

CloudDiskSystemAccessor的构造函数，用于创建CloudDiskSystemAccessor类的实例。

**起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**示例：**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
  console.info('CloudDiskSystemAccessor created successfully');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`CloudDiskSystemAccessor constructor failed. Code: ${error.code}, message: ${error.message}`);
}
```

### on('hydrateProgress')<sup>26+</sup>

on(type: 'hydrateProgress', callback: Callback&lt;[HydrateProgress](#hydrateprogress26)&gt;): void

订阅水合进度事件，适用于文件管理应用展示文件水合进度的场景。订阅后可接收当前用户下所有水合任务（包括三方云盘应用通过CAPI发起的）的进度通知，通过[HydrateProgress](#hydrateprogress26)中的filePath字段区分不同文件。同一实例可注册多个回调，重复注册已注册的回调不生效。可通过[off('hydrateProgress')](#offhydrateprogress26)取消订阅。

**起始版本：** 26.1.0

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | 'hydrateProgress' | 是 | 订阅的事件类型，取值为'hydrateProgress'（水合进度事件）。 |
| callback | Callback&lt;[HydrateProgress](#hydrateprogress26)&gt; | 是 | 回调函数。水合任务进度变化时触发，返回水合进度信息。 |

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400001 | Invalid argument. |
| 34400003 | IPC communication failed. |
| 34400014 | Temporary failure. Retry is recommended. |

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
  accessor.on('hydrateProgress', callback);
  console.info('subscribe hydrateProgress successfully');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`on hydrateProgress failed. Code: ${error.code}, message: ${error.message}`);
}
```

### off('hydrateProgress')<sup>26+</sup>

off(type: 'hydrateProgress', callback?: Callback&lt;[HydrateProgress](#hydrateprogress26)&gt;): void

取消订阅水合进度事件。传入callback时仅取消指定的回调；不传入callback时取消当前实例已注册的所有'hydrateProgress'回调。

**起始版本：** 26.1.0

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| type | 'hydrateProgress' | 是 | 取消订阅的事件类型，取值为'hydrateProgress'（水合进度事件）。 |
| callback | Callback&lt;[HydrateProgress](#hydrateprogress26)&gt; | 否 | 待取消的回调函数。缺省时取消当前实例已注册的所有'hydrateProgress'回调。 |

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400001 | Invalid argument. |
| 34400003 | IPC communication failed. |
| 34400014 | Temporary failure. Retry is recommended. |

**示例：**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();

let callback = (progress: cloudDiskManager.HydrateProgress) => {
  console.info(`hydrate progress - filePath: ${progress.filePath}, state: ${progress.state}`);
};

accessor.on('hydrateProgress', callback);

try {
  accessor.off('hydrateProgress', callback); // 取消指定的回调
  accessor.off('hydrateProgress'); // 取消所有回调
  console.info('unsubscribe hydrateProgress successfully');
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`off hydrateProgress failed. Code: ${error.code}, message: ${error.message}`);
}
```

### hydratePlaceholder<sup>26+</sup>

hydratePlaceholder(filePath: string, callbackType: [CallbackType](#callbacktype26), priority: [HydratePriority](#hydratepriority26)): Promise&lt;void&gt;

对占位符文件发起水合或取消水合，适用于文件管理应用在线打开三方云盘占位文件的场景。使用Promise异步回调。

> **说明：**
>
> - callbackType取FETCH_DATA时发起水合：任务创建成功后Promise立即兑现，仅表示水合任务已创建并入队，不代表文件已开始下载或水合完成。实际进度需通过[on('hydrateProgress')](#onhydrateprogress26)订阅获取，文件水合状态依次经过PENDING、IN_PROGRESS，最终为COMPLETED或CANCELLED。
> - callbackType取CANCEL_FETCH_DATA时取消水合：目标文件存在进行中的水合任务时将其取消（进度回调最终收到CANCELLED状态）；不存在进行中的水合任务时Promise被拒绝并返回34400032错误码。
> - 水合任务数量存在上限（单个云盘应用5个、全局10个），达到上限时Promise被拒绝并返回34400034错误码，可等待部分任务完成或取消后再重试。

**起始版本：** 26.1.0

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| filePath | string | 是 | 占位符文件的路径，须为"/storage/Users/currentUser/"前缀的绝对路径，且位于三方云盘应用已注册的同步根目录范围内。 |
| callbackType | [CallbackType](#callbacktype26) | 是 | 回调类型。取FETCH_DATA时发起水合，取CANCEL_FETCH_DATA时取消水合。 |
| priority | [HydratePriority](#hydratepriority26) | 是 | 水合任务的优先级，仅callbackType为FETCH_DATA时生效。 |

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。发起水合时，水合任务创建成功后兑现；取消水合时，取消请求受理后兑现。 |

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400001 | Invalid argument. |
| 34400003 | IPC communication failed. |
| 34400014 | Temporary failure. Retry is recommended. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | Hydration in progress. |
| 34400021 | The callback table is not registered. |
| 34400031 | The placeholder file is already fully hydrated. |
| 34400032 | No hydration task is in progress for the target file. |
| 34400034 | The number of active placeholder hydration tasks has reached the limit. |

**示例：**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
let filePath: string = '/storage/Users/currentUser/Docs/cloud/photo.jpg';

accessor.on('hydrateProgress', (progress: cloudDiskManager.HydrateProgress) => {
  console.info(`hydrate progress - filePath: ${progress.filePath}, state: ${progress.state}`);
  console.info(`processedSize: ${progress.processedSize}, totalSize: ${progress.totalSize}`);
});

accessor.hydratePlaceholder(filePath, cloudDiskManager.CallbackType.FETCH_DATA,
  cloudDiskManager.HydratePriority.HIGH).then(() => {
  console.info('hydrate task created successfully');
}).catch((err: BusinessError) => {
  console.error(`hydratePlaceholder failed with error message: ${err.message}, error code: ${err.code}`);
});
```

### dehydrateFile<sup>26+</sup>

dehydrateFile(filePath: string): Promise&lt;void&gt;

对已完全水合的占位符文件执行脱水，将其回退为未水合占位符以释放本地存储空间，适用于文件管理应用空间优化场景。使用Promise异步回调。

> **说明：**
>
> - 脱水前系统会向三方云盘应用发起脱水授权请求，云盘应用拒绝授权时Promise被拒绝并返回34400029错误码，文件保持不变。
> - 文件已处于未水合状态时调用本接口为幂等操作，Promise正常兑现。
> - 文件存在进行中的水合任务时不允许脱水，Promise被拒绝并返回34400019错误码。

**起始版本：** 26.1.0

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| filePath | string | 是 | 待脱水的占位符文件路径，须为"/storage/Users/currentUser/"前缀的绝对路径，且位于三方云盘应用已注册的同步根目录范围内。 |

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。脱水完成（或授权被拒绝）后兑现或拒绝。 |

**错误码：**

以下错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400001 | Invalid argument. |
| 34400003 | IPC communication failed. |
| 34400014 | Temporary failure. Retry is recommended. |
| 34400017 | The target path is not a placeholder file. |
| 34400019 | Hydration in progress. |
| 34400021 | The callback table is not registered. |
| 34400028 | The placeholder file is not fully hydrated. |
| 34400029 | The application denied placeholder dehydration. |

**示例：**

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let accessor: cloudDiskManager.CloudDiskSystemAccessor = new cloudDiskManager.CloudDiskSystemAccessor();
let filePath: string = '/storage/Users/currentUser/Docs/cloud/photo.jpg';

accessor.dehydrateFile(filePath).then(() => {
  console.info('dehydrate file successfully');
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

## SyncFolderState

枚举，三方云盘同步根的状态。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| INACTIVE  |  0   | 表示同步根处于未激活状态。|
| ACTIVE    |  1   | 表示同步根处于激活状态。  |

## HydrateProgress<sup>26+</sup>

描述水合任务的进度信息，通过[on('hydrateProgress')](#onhydrateprogress26)订阅的回调获取。

**起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 类型   | 只读 | 可选 | 说明      |
| --------- | ------ | ---- | ---- | ---------------------------- |
| filePath | string | 否   | 否   | 文件路径，与调用[hydratePlaceholder](#hydrateplaceholder26)时传入的文件路径一致。     |
| state   | [HydrateProgressState](#hydrateprogressstate26) | 否   | 否   | 水合进度状态。   |
| processedSize   | number | 否   | 否   | 已水合的字节数，仅state为IN_PROGRESS时有效。   |
| totalSize   | number | 否   | 否   | 正在水合的文件总大小，单位为字节。   |

## HydrateProgressState<sup>26+</sup>

枚举，水合任务的水合进度状态。

**起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| PENDING  |  0   | 水合任务已创建，尚未开始处理。|
| IN_PROGRESS    |  1   | 水合进行中。  |
| COMPLETED    |  2   | 水合完成。  |
| CANCELLED    |  3   | 水合已取消，取消来源包括用户取消、云盘应用放弃任务、任务超时或系统内部终止。  |

## CallbackType<sup>26+</sup>

枚举，云盘文件数据获取的回调类型。

**起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| FETCH_DATA  |  0   | 获取云文件数据（发起水合）。|
| CANCEL_FETCH_DATA    |  1   | 取消获取云文件数据（取消水合）。  |
| DEHYDRATE    |  2   | 脱水授权。  |

## HydratePriority<sup>26+</sup>

枚举，水合任务的优先级。

**起始版本：** 26.1.0

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| LOW  |  0   | 低优先级。|
| NORMAL    |  1   | 普通优先级。  |
| HIGH    |  2   | 高优先级。  |
