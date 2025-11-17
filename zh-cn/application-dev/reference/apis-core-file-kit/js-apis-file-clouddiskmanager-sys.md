# @ohos.file.cloudDiskManager (云盘管理)(系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wang_zhangjun; @zhuangzhuang-->
<!--Designer: @wang_zhangjun; @zhuangzhuang; @renguang1116-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @foryourself-->

本模块是为系统文件管理应用提供获取三方网盘注册的同步根信息的能力。

> **说明：**
>
> 本模块首批接口从API version 21开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## SyncFolderAccessor

同步根管理类，负责为系统文件管理应用提供获取三方网盘注册的同步根信息的能力。

### constructor

constructor()

SyncFolderAccessor的构造函数，用于获取SyncFolderAccessor类的实例。

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
  import { BusinessError } from '@kit.BasicServicesKit';

  @Entry
  @Component
  struct Index {
    build() {
      Column() {
        Button('constructor')
        .onClick(async() => {
            try {
              let SyncFolderAccessor: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
            } catch (error) {
              console.error(`register failed. Code: ${error.code}, message: ${error.message}`);
            }
        });
      }
    }
  }

  ```
  
### getAllSyncFolders

getAllSyncFolders(): Promise&lt;Array&lt;SyncFolder&gt;&gt;

注册同步根信息。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

**需要权限**：ohos.permission.ACCESS_CLOUD_DISK_INFO

**返回值：**

| 类型 | 说明 |
| --- | -- |
| Promise&lt;Array&lt;[SyncFolder](#syncfolder)&gt;&gt; | Promise对象。返回所有网盘应用的同步根列表。 |

**错误码：**

接口抛出错误码的详细介绍请参见[云盘管理错误码](errorcode-clouddiskmanager-sys.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 801 | Device not supported. |
| 34400003 | IPC communication failed. |
| 34400014  | Temporary failure, Retry is recommended (e.g., network issues). |
| 34400015  | Cloud disk not allowed on this device.|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
const TAG: string = '[cloudDiskManager]';

try {
    console.log(TAG + `getAllRoots start`);
    let syncFolerAccess: cloudDiskManager.SyncFolderAccessor = new cloudDiskManager.SyncFolderAccessor();
    let syncInfoList: Array<string> = [];
    syncFolerAccess.getAllSyncFolders().then((syncFolderExts) => {
        if (syncFolderExts) {
            console.info(TAG + `getAllRoots success`);
            this.syncExtList = syncFolderExts;
            syncInfoList.push('syncFolderExts length: ' + syncFolderExts.length);
            this.firstLevelTitle = 'query syncfolder info';
            this.secondLevelTitle = 'result';
            this.getSyncRootRet = JSON.stringify(syncInfoList);
            this.dialogControllerConfirm.open();
        } else {
            console.info(TAG + `getAllRoots failed`);
        }
    }).catch((e: BusinessError<object>) => {
        console.error(TAG + `then catch err, err is: ${e.code}, message: ${e.message}`);
    })
} catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(TAG + `getLocalCapabilities failed. Code: ${error.code}, message: ${error.message}`);
}
```

## SyncFolder

表示同步根信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 类型   | 只读 | 可选 | 说明      |
| --------- | ------ | ---- | ---- | ---------------------------- |
| path | string | 否   | 否   | 同步根对应的URI。     |
| bundleNme   | string | 否   | 否   | 同步根对应的包名。   |
| state   | [SyncFolderState](#syncfolderstate) | 否   | 否   | 同步根对应的状态信息。   |
| displayNameResId   | number | 否   | 是   | 资源ID，可以映射到文管列表显示的别名。默认值为0。   |
| customAlias   | string | 否   | 是   | 在文管列表显示的别名。默认值为空串。   |

## SyncFolderState

枚举，云盘的同步根的状态。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.CloudDiskManager

| 名称      | 值  | 说明      |
| --------- | -----| ------------------------|
| INACTIVE  |  0   | 表示同步根处于未激活状态。|
| ACTIVE    |  1   | 表示同步根处于激活状态。  |
