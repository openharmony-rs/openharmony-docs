# @ohos.file.cloudSyncManager (端云同步管理能力)(系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @Hermits; @reminder2352-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @zsyztt-->
<!--Adviser: @jinqiuheng-->

该模块向云盘管理应用提供端云同步管理能力，包括使能/去使能端云协同能力、修改应用同步开关、云端数据变化通知、账号退出时清理或保留云相关文件，以及全量下载等。开发者可在云盘管理应用中使用该模块管理应用端云协同开关、同步云端数据变更、处理账号退出后的本地云数据，并执行云文件全量下载和搬迁。

> **说明：**
>
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.file.cloudSyncManager (端云同步管理能力)](js-apis-file-cloudsyncmanager.md)。

## 导入模块

```ts
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## cloudSyncManager.changeAppCloudSwitch

changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise&lt;void&gt;

异步方法修改应用的端云文件同步开关。适用于需要为指定应用打开或关闭云同步能力的场景。使用Promise异步回调。

**系统接口**：该接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。 |
| bundleName | string | 是   | 应用包名。|
| status | boolean | 是   | 修改的应用云同步开关状态。true为打开；false为关闭。|

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.changeAppCloudSwitch(accountId, bundleName, true).then(() => {
  console.info("changeAppCloudSwitch successfully");
}).catch((err: BusinessError) => {
  console.error(`changeAppCloudSwitch failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.changeAppCloudSwitch

changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean, callback: AsyncCallback&lt;void&gt;): void

异步方法修改应用的端云文件同步开关。适用于需要为指定应用打开或关闭云同步能力的场景。使用callback异步回调。

**系统接口**：该接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|
| bundleName | string | 是   | 应用包名。|
| status | boolean | 是   | 修改的应用云同步开关状态。true为打开；false为关闭。|
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。异步修改应用的端云文件同步开关后的结果回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.changeAppCloudSwitch(accountId, bundleName, true, (err: BusinessError) => {
  if (err) {
    console.error(`changeAppCloudSwitch failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("changeAppCloudSwitch successfully");
  }
});
```

## cloudSyncManager.notifyDataChange

notifyDataChange(accountId: string, bundleName: string): Promise&lt;void&gt;

通知端云服务指定账号下的特定应用云数据已发生变更。适用于应用云端数据发生变化后，需要主动通知端云服务同步变更的场景。使用Promise异步回调。

**系统接口**：该接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|
| bundleName | string | 是   | 应用包名。|

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.notifyDataChange(accountId, bundleName).then(() => {
  console.info("notifyDataChange successfully");
}).catch((err: BusinessError) => {
  console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.notifyDataChange

notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback&lt;void&gt;): void

通知端云服务指定账号下的特定应用云数据已发生变更。适用于应用云端数据发生变化后，需要主动通知端云服务同步变更的场景。使用callback异步回调。

**系统接口**：该接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|
| bundleName | string | 是   | 应用包名。|
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。异步通知端云服务应用的云数据变更后的结果回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.notifyDataChange(accountId, bundleName, (err: BusinessError) => {
  if (err) {
    console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("notifyDataChange successfully");
  }
});
```

## ExtraData<sup>11+</sup>

云端数据变更信息。

**系统接口**：该接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| 名称     | 类型   | 只读 | 可选 | 说明 |
| ---------- | ------ | ---- | ---- | ---- |
| eventId | string | 否   | 否   | 变更事件ID。|
| extraData | string | 否   | 否   | 云端数据变更信息。|

## cloudSyncManager.notifyDataChange<sup>11+</sup>

notifyDataChange(userId: number, extraData: ExtraData): Promise&lt;void&gt;

通知端云服务应用指定用户的云数据变更信息。使用Promise异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| userId | number | 是   | 用户ID。|
| extraData | [ExtraData](#extradata11) | 是   | 云端数据变更信息。|

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. Possible causes: 1. IPC failed or timed out. 2. Failed to load the service. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let extraData: cloudSyncManager.ExtraData = {eventId: "eventId", extraData: "data"};
cloudSyncManager.notifyDataChange(userId, extraData).then(() => {
  console.info("notifyDataChange successfully");
}).catch((err: BusinessError) => {
  console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.notifyDataChange<sup>11+</sup>

notifyDataChange(userId: number, extraData: ExtraData, callback: AsyncCallback&lt;void&gt;): void

通知端云服务应用指定用户的云数据变更信息。使用callback异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| userId | number | 是   | 用户ID。|
| extraData | [ExtraData](#extradata11) | 是   | 云端数据变更信息。|
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。异步通知端云服务应用的云数据变更后的结果回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. Possible causes: 1. IPC failed or timed out. 2. Failed to load the service. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let extraData: cloudSyncManager.ExtraData = {eventId: "eventId", extraData: "data"};
cloudSyncManager.notifyDataChange(userId, extraData, (err: BusinessError) => {
  if (err) {
    console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("notifyDataChange successfully");
  }
});
```

## cloudSyncManager.enableCloud

enableCloud(accountId: string, switches: Record<string, boolean>): Promise&lt;void&gt;

异步方法使能端云协同能力。适用于需要开启指定账号下应用端云协同能力的场景，可与[disableCloud](#cloudsyncmanagerdisablecloud)配合使用。使用Promise异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|
| switches | Record<string, boolean> | 是   | 应用的端云协同特性使能开关，string类型为应用包名，boolean类型为开关状态。true为打开；false为关闭。|

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let switches: Record<string, boolean> = {
  'com.example.bundleName1': true,
  'com.example.bundleName2': false
}
cloudSyncManager.enableCloud(accountId, switches).then(() => {
  console.info("enableCloud successfully.");
}).catch((err: BusinessError) => {
  console.error(`enableCloud failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.enableCloud

enableCloud(accountId: string, switches: Record<string, boolean>, callback: AsyncCallback&lt;void&gt;): void

异步方法使能端云协同能力。适用于需要开启指定账号下应用端云协同能力的场景，可与[disableCloud](#cloudsyncmanagerdisablecloud)配合使用。使用callback异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|
| switches | Record<string, boolean> | 是   | 应用的端云协同特性使能开关，string类型为应用包名，boolean类型为开关状态。true为打开；false为关闭。|
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。异步使能端云协同能力后的结果回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let switches: Record<string, boolean> = {
  'com.example.bundleName1': true,
  'com.example.bundleName2': false
}
cloudSyncManager.enableCloud(accountId, switches, (err: BusinessError) => {
  if (err) {
    console.error(`enableCloud failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("enableCloud successfully");
  }
});
```

## cloudSyncManager.disableCloud

disableCloud(accountId: string): Promise&lt;void&gt;

异步方法去使能端云协同能力。适用于需要关闭指定账号下应用端云协同能力的场景，可与[enableCloud](#cloudsyncmanagerenablecloud)配合使用。使用Promise异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
cloudSyncManager.disableCloud(accountId).then(() => {
  console.info("disableCloud successfully");
}).catch((err: BusinessError) => {
  console.error(`disableCloud failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.disableCloud

disableCloud(accountId: string, callback: AsyncCallback&lt;void&gt;): void

异步方法去使能端云协同能力。适用于需要关闭指定账号下应用端云协同能力的场景，可与[enableCloud](#cloudsyncmanagerenablecloud)配合使用。使用callback异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。异步去使能端云协同能力后的结果回调。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
cloudSyncManager.disableCloud(accountId, (err: BusinessError) => {
  if (err) {
    console.error(`disableCloud failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("disableCloud successfully");
  }
});
```

## Action

清理本地云相关数据时的枚举。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| 名称 |  值|  说明 |
| ----- |  ---- |  ---- |
| RETAIN_DATA |  0 |  仅清除云端标识，保留本地缓存文件。|
| CLEAR_DATA |  1 |  清除云端标识信息，若存在本地缓存文件，一并删除。|

## cloudSyncManager.clean

clean(accountId: string, appActions: Record<string, Action>): Promise&lt;void&gt;

异步方法清理本地云相关数据。适用于账号退出或应用云数据清理时，需要按应用配置保留或删除本地云相关数据的场景。使用Promise异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|
| appActions | Record<string, [Action](#action)> | 是   | string类型为待清理应用包名，[Action](#action)为清理动作类型。|

**返回值：**

| 类型                  | 说明             |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = {
  'com.example.bundleName1': cloudSyncManager.Action.RETAIN_DATA,
  'com.example.bundleName2': cloudSyncManager.Action.CLEAR_DATA
};
cloudSyncManager.clean(accountId, appActions).then(() => {
  console.info("clean successfully");
}).catch((err: BusinessError) => {
  console.error(`clean failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.clean

clean(accountId: string, appActions: Record<string, Action>, callback: AsyncCallback&lt;void&gt;): void

异步方法清理本地云相关数据。适用于账号退出或应用云数据清理时，需要按应用配置保留或删除本地云相关数据的场景。使用callback异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明 |
| ---------- | ------ | ---- | ---- |
| accountId | string | 是   | 账号ID。|
| appActions | Record<string, [Action](#action)> | 是   | string类型为待清理应用包名，[Action](#action)为清理动作类型。|
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。异步清理本地云相关数据后的结果回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID                     | 错误信息        |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = {
  'com.example.bundleName1': cloudSyncManager.Action.RETAIN_DATA,
  'com.example.bundleName2': cloudSyncManager.Action.CLEAR_DATA
};
cloudSyncManager.clean(accountId, appActions, (err: BusinessError) => {
  if (err) {
    console.error(`clean failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("clean successfully");
  }
});
```

## DowngradeDownload<sup>20+</sup>

全量下载：为云盘管理应用提供集中下载云端数据的能力。

云盘全量下载对象，用于支撑云盘管理应用完成云盘文件的全量下载流程。

**系统接口**：该接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

### constructor<sup>20+</sup>

constructor(bundleName: string)

全量下载对象的构造函数，用于获取指定包名的DowngradeDownload类的实例。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名     | 类型   | 必填 | 说明       |
| ---------- | ------ | ---- | ---------- |
| bundleName | string | 是   | 应用包名。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)以及[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                                                                                          |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.                                                                                                 |
| 202      | Permission verification failed, application which is not a system application uses system API.                                                                                    |
| 13900020 | Invalid argument. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.                                                                     |
| 22400005 | Inner error. Possible causes: 1.Failed to access the database or execute the SQL statement. 2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.demo.a';
try {
  let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to create downgrade manager object, error code: ${error.code}, message: ${error.message}`);
}
```

### getCloudFileInfo<sup>20+</sup>

getCloudFileInfo(): Promise&lt;CloudFileInfo&gt;

获取需要全量下载的应用仅位于本地、仅位于云端或者本地和云端均有的文件个数和大小信息。使用Promise异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**返回值：**

  | 类型                              | 说明                     |
  | --------------------------------- | ------------------------ |
  | Promise&lt;[CloudFileInfo](js-apis-file-cloudsyncmanager.md#cloudfileinfo20)&gt; | Promise对象，返回携带本地与云端文件信息的对象。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)以及[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                                                                                          |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.                                                                                                 |
| 202      | Permission verification failed, application which is not a system application uses system API.                                                                                    |
| 13600001 | IPC error. Possible causes: 1.IPC failed or timed out. 2.Failed to load the service.                                                                                              |
| 13900010 | Try again.                                                                                                                                                                        |
| 22400005 | Inner error. Possible causes: 1.Failed to access the database or execute the SQL statement. 2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
downgradeMgr.getCloudFileInfo().then((fileInfo: cloudSyncManager.CloudFileInfo) => {
  console.info("cloud file info: " + JSON.stringify(fileInfo));
}).catch((err: BusinessError) => {
  console.error(`Failed to get downgrade info, error message: ${err.message}, error code: ${err.code}`);
});
```

### startDownload<sup>20+</sup>

startDownload(callback: Callback&lt;DownloadProgress&gt;): Promise&lt;void&gt;

启动指定应用的云文件全量下载，适用于云盘管理应用需要集中下载指定应用云端数据的场景。使用Promise异步回调，并通过callback参数返回下载进度。

同一应用存在正在执行的全量下载任务的情况下，重复触发会返回错误信息（22400006）。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名   | 类型                             | 必填 | 说明                                                                                |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------------------------------- |
| callback | Callback&lt;[DownloadProgress](js-apis-file-cloudsyncmanager.md#downloadprogress20)&gt; | 是   | 回调函数。在全量下载过程中返回下载进度，参数为DownloadProgress，返回值为void。 |

**返回值：**

  | 类型                | 说明                      |
  | ------------------- | ------------------------- |
  | Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)以及[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                                                                                          |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.                                                                                                 |
| 202      | Permission verification failed, application which is not a system application uses system API.                                                                                    |
| 13600001 | IPC error. Possible causes: 1.IPC failed or timed out. 2.Failed to load the service.                                                                                              |
| 13900010 | Try again.                                                                                                                                                                        |
| 13900020 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.                                                                     |
| 22400005 | Inner error. Possible causes: 1.Failed to access the database or execute the SQL statement. 2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 22400006 | The same task is already in progress.                                                                                                                                             |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
let callback = (data: cloudSyncManager.DownloadProgress) => {
  console.info(`Downgrade progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSyncManager.DownloadState.COMPLETED) {
    console.info('Downgrade finished.');
  } else if (data.state == cloudSyncManager.DownloadState.STOPPED) {
    console.info(`Downgrade stopped, reason: ${data.stopReason}.`);
  }
};
downgradeMgr.startDownload(callback).then(() => {
  console.info("Downgrade started successfully.");
}).catch((err: BusinessError) => {
  console.error(`Failed to start downgrade, error message: ${err.message}, error code: ${err.code}`);
});
```

### stopDownload<sup>20+</sup>

stopDownload(): Promise&lt;void&gt;

停止由[startDownload](#startdownload20)触发的全量下载任务，使用Promise异步回调。

**系统接口**：该接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**返回值：**

  | 类型                | 说明                      |
  | ------------------- | ------------------------- |
  | Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)以及[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                                                                                          |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.                                                                                                 |
| 202      | Permission verification failed, application which is not a system application uses system API.                                                                                    |
| 13600001 | IPC error. Possible causes: 1.IPC failed or timed out. 2.Failed to load the service.                                                                                              |
| 22400005 | Inner error. Possible causes: 1.Failed to access the database or execute the SQL statement. 2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
downgradeMgr.startDownload((data: cloudSyncManager.DownloadProgress) => {
  console.info(`Downgrade progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
}).then(() => {
  console.info("Downgrade started successfully.");
  let needStop = true;
  if (needStop) {
    downgradeMgr.stopDownload().then(() => {
      console.info("Downgrade stopped successfully.");
    }).catch((err: BusinessError) => {
      console.error(`Failed to stop downgrade, error message: ${err.message}, error code: ${err.code}`);
    });
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to start downgrade, error message: ${err.message}, error code: ${err.code}`);
});
```

### startTransfer

startTransfer(targetUri: string, callback: Callback&lt;TransferProgress&gt;): void

将云盘目录下已完成本地下载的文件搬迁至指定目录，适用于需要将云盘文件导出到本地其他目录进行管理的场景。过程中通过回调上报搬迁进度。使用callback异步回调。

同一应用存在正在执行的搬迁任务的情况下，重复触发会返回错误信息（22400006）。

**起始版本**：26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名   | 类型                             | 必填 | 说明                                                                                |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------------------------------- |
| targetUri | string | 是  | 用于存放搬迁后的文件路径URI，必须以“file://docs/storage/Users/currentUser/”为前缀。 |
| callback | Callback&lt;[TransferProgress](#transferprogress)&gt; | 是   | 回调函数。在文件搬迁过程中返回搬迁进度，参数为TransferProgress，返回值为void。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)以及[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                                                                                                                                          |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed.                                                                                                                                                   |
| 202      | The caller is not a system application.                                                                                                                                           |
| 13900001 | Operation not permitted. Possible causes:<br>1.The DowngradeDownload task is running.<br>2.The full data synchronization task is running.                                         |
| 13900002 | No such file or directory.                                                                                                                                                        |
| 13900010 | Try again.                                                                                                                                                                        |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified.<br>2.The length of the input uri does not meet the value range requirement.<br>3.The input uri does not belong to a File Manager public directory. |
| 22400006 | The same task is already in progress.                                                                                                                                             |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let targetPath: string = "file://docs/storage/Users/currentUser/Download/";
try {
    let downgradeMgr = new cloudSyncManager.DowngradeDownload("com.demo");
    downgradeMgr.startTransfer(targetPath, (data: cloudSyncManager.TransferProgress) => {
        console.info(`Transfer progress: successfulCount: ${data.successfulCount}, totalCount: ${data.totalCount}`);
    });
} catch (err) {
    let e = err as BusinessError;
    console.error(`transfer files failed with error message: ${e.message}, error code: ${e.code}`);
}
```

## TransferProgress

搬迁任务的进度信息。

**起始版本**：26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| 名称            | 类型                                        | 只读 | 可选 | 说明                                                                          |
| --------------- | ------------------------------------------- | ---- | ---- | ----------------------------------------------------------------------------- |
| state           | [TransferState](#transferstate)             | 否   | 否   | 搬迁任务的状态。                                                              |
| successfulCount | number                                      | 否   | 否   | 已搬迁的文件个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。        |
| failedCount     | number                                      | 否   | 否   | 搬迁失败的文件个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。      |
| totalCount      | number                                      | 否   | 否   | 待搬迁文件总个数，取值范围[0, INT32_MAX]，单位：个。进度异常时返回-1。        |
| transferredSize | number                                      | 否   | 否   | 已搬迁的数据大小，取值范围[0, INT64_MAX)，单位：Byte。进度异常时返回INT64_MAX。 |
| totalSize       | number                                      | 否   | 否   | 需要搬迁的文件总大小，取值范围[0, INT64_MAX)，单位：Byte。进度异常时返回INT64_MAX。 |
| stopReason      | [TransferStopReason](#transferstopreason)   | 否   | 否   | 搬迁停止的原因。                                                              |

## TransferState

搬迁任务状态的枚举。

**起始版本**：26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| 名称      | 值  | 说明       |
| --------- | --- | ---------- |
| RUNNING   | 0   | 搬迁中。   |
| COMPLETED | 1   | 搬迁完成。 |
| STOPPED   | 2   | 搬迁停止。 |

## TransferStopReason

搬迁停止原因的枚举。

**起始版本**：26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| 名称                | 值  | 说明                                                   |
| ------------------- | --- | ------------------------------------------------------ |
| SWITCH_OFF          | 0   | 搬迁过程中，云服务开关关闭。                                         |
| ACCOUNT_LOGOUT      | 1   | 搬迁过程中，账户登出。               |
| OTHER_REASON        | 2   | 搬迁过程中，其他原因导致停止。                         |

  ## LocalFilePresentStatus<sup>23+</sup>

  检测结果对象，包含应用包名及其在云盘存储空间内是否存在未上云文件的状态信息。

  **系统接口**：该接口为系统接口。

  **系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager


  | 名称 | 类型 | 只读 | 可选 | 说明 |
  | ---- | ---- | ---- | ---- | ---- |
  | bundleName | string | 否 | 否 | 应用包名。 |
  | isLocalFilePresent | boolean | 否 | 否 | 该应用在云盘存储空间内是否存在尚未同步至云端的本地文件。true 表示存在， false 表示不存在。 |

  ## cloudSyncManager.getBundlesLocalFilePresentStatus<sup>23+</sup>

  getBundlesLocalFilePresentStatus(bundleNames: Array&lt;string&gt;): Promise&lt;Array&lt;LocalFilePresentStatus&gt;&gt;

  对接入云盘的应用，检测其在云盘存储空间内是否存在未上云文件，支持同时查询多个应用。使用Promise异步回调。

  **需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

  **系统接口**：该接口为系统接口。

  **系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

  **参数：**

  | 参数名 | 类型 | 必填 | 说明 |
  | ------ | ---- | ---- | ---- |
  | bundleNames | Array&lt;string&gt; | 是 | 需要检测的应用包名数组。每个元素为应用的包名字符串。 |

  **返回值：**

  | 类型 | 说明 |
  | ---- | ---- |
  | Promise&lt;Array&lt;[LocalFilePresentStatus](#localfilepresentstatus23)&gt;&gt; | Promise对象，返回对象数组，数组内每个对象包含指定检测的应用包名及其本地文件存在状态。 |

  **错误码：**

  以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)以及[通用错误码](../errorcode-universal.md)。

  | 错误码ID | 错误信息 |
  | -------- | -------- |
  | 201 | Permission verification failed. |
  | 202 | The caller is not a system application. |
  | 13600001 | IPC error. Possible causes: 1. IPC failed or timed out. 2. Failed to load the service. |
  | 13900010 | Try again. |
  | 13900020 | Invalid argument. Possible causes: 1. Mandatory parameters are left unspecified. 2. The length of the input parameter exceeds the upper limit. 3. The input parameter contains an invalid bundleName. |
  | 22400005 | Inner error. Possible causes: 1. Failed to access the database or execute the SQL statement. 2. System error, such as a null pointer, insufficient memory or a JS engine exception. |

  **示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundles: Array<string> = ['com.example.app1', 'com.example.app2'];
cloudSyncManager.getBundlesLocalFilePresentStatus(bundles).then((results: Array<cloudSyncManager.LocalFilePresentStatus>) => {
  results.forEach((item) => {
    console.info(`bundle: ${item.bundleName}, hasLocalUncloudedFiles: ${item.isLocalFilePresent}`);
  });
}).catch((err: BusinessError) => {
  console.error(`getBundlesLocalFilePresentStatus failed, code: ${err.code}, message: ${err.message}`);
});
```
## cloudSyncManager.getDowngradeDownloadTaskState

getDowngradeDownloadTaskState(bundleNames: Array&lt;string&gt;): Promise&lt;Array&lt;DownloadProgress&gt;&gt;

查询接入云盘的应用的全量下载任务状态。使用Promise异步回调。

由于返回的DownloadProgress对象中不包含包名信息，因此在批量查询多个应用时，调用方需自行记录应用包名。

**起始版本**：26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.CLOUDFILE_SYNC_MANAGER

**系统接口**：该接口为系统接口。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| bundleNames | Array&lt;string&gt; | 是 | 需要查询的应用包名数组，每个元素为应用的包名字符串，包名数组大小上限为20个。超过上限时返回错误码13900020。 |

**返回值**：

| 类型 | 说明 |
| ---- | ---- |
| Promise&lt;Array&lt;[DownloadProgress](js-apis-file-cloudsyncmanager.md#downloadprogress20)&gt;&gt; | Promise对象，返回查询的全量下载任务的状态信息数组。|

**错误码**：

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)以及[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes: 1. Mandatory parameters are left unspecified. 2. The length of the input parameter exceeds the upper limit. 3. The input parameter contains an invalid bundleName. |


**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundles: Array<string> = ['com.example.app1', 'com.example.app2'];
cloudSyncManager.getDowngradeDownloadTaskState(bundles).then((results: Array<cloudSyncManager.DownloadProgress>) => {
  results.forEach((item) => {
    console.info(`state: ${item.state}, downloadedSize: ${item.downloadedSize}, totalSize: ${item.totalSize}`);
    console.info(`successfulCount: ${item.successfulCount}, failedCount: ${item.failedCount}, totalCount: ${item.totalCount}`);
    if (item.state == cloudSyncManager.DownloadState.STOPPED) {
      console.info(`stopReason: ${item.stopReason}`);
    }
  });
}).catch((err: BusinessError) => {
  console.error(`getDowngradeDownloadTaskState failed, code: ${err.code}, message: ${err.message}`);
});
```

## DownloadState<sup>20+</sup>

全量下载任务状态的枚举。

**系统能力**：SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| 名称      | 值  | 说明                                    |
| --------- | --- | -------------------------------------- |
| MISSING   | 3   | 下载任务不存在。<br>**起始版本**：26.0.0<br>**模型约束**：此接口仅可在Stage模型下使用。<br>**系统接口**：此接口为系统接口。 |
