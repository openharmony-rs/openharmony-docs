# @ohos.update (升级)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Update-->
<!--Owner: @RainyDay_005; @huangsiping3-->
<!--Designer: @zhangzhengxue; @jackd320-->
<!--Tester: @mamba-ting-->
<!--Adviser: @zhang_yixin13-->

升级范围：升级整个系统，包括内置资源和预置应用，不包括三方应用。

升级类型：SD卡升级、在线升级。

- SD卡升级依赖升级包和SD卡安装。

- 在线升级依赖设备厂商部署的用于管理升级包的服务器。服务器由设备厂商部署，IP由调用者传入，请求的request接口是固定的，由设备厂商开发。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口为系统接口。

## 导入模块

```js
import { update } from '@kit.BasicServicesKit';
```

## update.getOnlineUpdater

getOnlineUpdater(upgradeInfo: UpgradeInfo): Updater

获取在线升级对象。

**系统能力**：SystemCapability.Update.UpdateService

**参数：**

| 参数名         | 类型                          | 必填   | 说明     |
| ----------- | --------------------------- | ---- | ------ |
| upgradeInfo | [UpgradeInfo](#upgradeinfo) | 是    | 升级对象信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**返回值：**

| 类型                  | 说明   |
| ------------------- | ---- |
| [Updater](#updater) | 升级对象。 |

**示例：**

```ts
try {
      const upgradeInfo: update.UpgradeInfo = {
        upgradeApp: "com.ohos.ota.updateclient",
        businessType: {
          vendor: update.BusinessVendor.PUBLIC,
          subType: update.BusinessSubType.FIRMWARE
        }
      };
      let updater = update.getOnlineUpdater(upgradeInfo);
    } catch(error) {
      console.error(`Fail to get updater error: ${error}`);
    }
```

## update.getRestorer

getRestorer(): Restorer

获取恢复出厂设置对象。

**系统能力**：SystemCapability.Update.UpdateService

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**返回值：**

| 类型                    | 说明     |
| --------------------- | ------ |
| [Restorer](#restorer) | 恢复出厂对象。 |


**示例：**

```ts
try {
  let restorer = update.getRestorer();
} catch(error) {
  console.error(`Fail to get restorer: ${error}`);
}
```

## update.getLocalUpdater

getLocalUpdater(): LocalUpdater

获取本地升级对象。

**系统能力**：SystemCapability.Update.UpdateService

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**返回值：**

| 类型                            | 说明     |
| ----------------------------- | ------ |
| [LocalUpdater](#localupdater) | 本地升级对象。 |


**示例：**

```ts
try {
  let localUpdater = update.getLocalUpdater();
} catch(error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

## Updater

### checkNewVersion

checkNewVersion(callback: AsyncCallback\<CheckResult>): void

检查新版本信息。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名      | 类型                                       | 必填   | 说明             |
| -------- | ---------------------------------------- | ---- | -------------- |
| callback | AsyncCallback\<[CheckResult](#checkresult)> | 是    | 回调函数，返回搜包结果对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.checkNewVersion((err: BusinessError, result: update.CheckResult) => {
      console.info(`checkNewVersion isExistNewVersion  ${result?.isExistNewVersion}`);
    });
```

### checkNewVersion

checkNewVersion(): Promise\<CheckResult>

检查新版本信息。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**返回值：**

| 类型                                    | 说明                  |
| ------------------------------------- | ------------------- |
| Promise\<[CheckResult](#checkresult)> | Promise对象，返回搜包结果对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.checkNewVersion()
      .then((result: update.CheckResult) => {
        console.info(`checkNewVersion isExistNewVersion: ${result.isExistNewVersion}`);
        // 版本摘要信息
        console.info(`checkNewVersion versionDigestInfo: ${result.newVersionInfo.versionDigestInfo.versionDigest}`);
      })
      .catch((err: BusinessError)=>{
        console.error(`checkNewVersion promise error ${JSON.stringify(err)}`);
      });
```

###  getNewVersionInfo

getNewVersionInfo(callback: AsyncCallback\<NewVersionInfo>): void

获取新版本信息。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名      | 类型                                       | 必填   | 说明              |
| -------- | ---------------------------------------- | ---- | --------------- |
| callback | AsyncCallback\<[NewVersionInfo](#newversioninfo)> | 是    | 回调函数，返回新版本信息对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.getNewVersionInfo((err: BusinessError, info: update.NewVersionInfo) => {
      console.info(`info displayVersion = ${info?.versionComponents[0].displayVersion}`);
      console.info(`info innerVersion = ${info?.versionComponents[0].innerVersion}`);
});
```

### getNewVersionInfo

getNewVersionInfo(): Promise\<NewVersionInfo>

获取新版本信息。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**返回值：**

| 类型                                       | 说明                   |
| ---------------------------------------- | -------------------- |
| Promise\<[NewVersionInfo](#newversioninfo)> | Promise对象，返回新版本信息对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.getNewVersionInfo().then((info: update.NewVersionInfo) => {
    console.info(`info displayVersion = ${info.versionComponents[0].displayVersion}`);
    console.info(`info innerVersion = ${info.versionComponents[0].innerVersion}`);
}).catch((err: BusinessError) => {
    console.error(`getNewVersionInfo promise error ${JSON.stringify(err)}`);
});
```

###  getNewVersionDescription

getNewVersionDescription(versionDigestInfo: VersionDigestInfo, descriptionOptions: DescriptionOptions, callback: AsyncCallback\<Array\<ComponentDescription>>): void

获取新版本描述文件。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名                | 类型                                       | 必填   | 说明             |
| ------------------ | ---------------------------------------- | ---- | -------------- |
| versionDigestInfo  | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息。         |
| descriptionOptions | [DescriptionOptions](#descriptionoptions) | 是    | 描述文件选项。        |
| callback           | AsyncCallback\<Array\<[ComponentDescription](#componentdescription)>> | 是    | 回调函数，返回新版本描述文件。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: "zh-cn" // 中文
};

updater.getNewVersionDescription(versionDigestInfo, descriptionOptions).then((info: Array<update.ComponentDescription>)=> {
  console.info(`getNewVersionDescription promise info ${JSON.stringify(info)}`);
}).catch((err: BusinessError) => {
  console.error(`getNewVersionDescription promise error ${JSON.stringify(err)}`);
});
```

### getNewVersionDescription

getNewVersionDescription(versionDigestInfo: VersionDigestInfo, descriptionOptions: DescriptionOptions): Promise\<Array\<ComponentDescription>>

获取新版本描述文件。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名                | 类型                                       | 必填   | 说明     |
| ------------------ | ---------------------------------------- | ---- | ------ |
| versionDigestInfo  | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息。 |
| descriptionOptions | [DescriptionOptions](#descriptionoptions) | 是    | 描述文件选项。 |

**返回值：**

| 类型                                       | 说明                  |
| ---------------------------------------- | ------------------- |
| Promise\<Array\<[ComponentDescription](#componentdescription)>> | Promise对象，返回新版本描述文件。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: "zh-cn" // 中文
};

updater.getNewVersionDescription(versionDigestInfo, descriptionOptions).then((info: Array<update.ComponentDescription>)=> {
  console.info(`getNewVersionDescription promise info ${JSON.stringify(info)}`);
}).catch((err: BusinessError) => {
  console.error(`getNewVersionDescription promise error ${JSON.stringify(err)}`);
});
```

###  getCurrentVersionInfo

getCurrentVersionInfo(callback: AsyncCallback\<CurrentVersionInfo>): void

获取当前版本信息。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名      | 类型                                       | 必填   | 说明               |
| -------- | ---------------------------------------- | ---- | ---------------- |
| callback | AsyncCallback\<[CurrentVersionInfo](#currentversioninfo)> | 是    | 回调函数，返回当前版本信息对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.getCurrentVersionInfo((err: BusinessError, info: update.CurrentVersionInfo) => {
  console.info(`info osVersion = ${info?.osVersion}`);
  console.info(`info deviceName = ${info?.deviceName}`);
  console.info(`info displayVersion = ${info?.versionComponents[0].displayVersion}`);
});
```

### getCurrentVersionInfo

getCurrentVersionInfo(): Promise\<CurrentVersionInfo>

获取当前版本信息。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**返回值：**

| 类型                                       | 说明                  |
| ---------------------------------------- | ------------------- |
| Promise\<[CurrentVersionInfo](#currentversioninfo)> | Promise对象，返回当前版本信息对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.getCurrentVersionInfo().then((info: update.CurrentVersionInfo) => {
  console.info(`info osVersion = ${info.osVersion}`);
  console.info(`info deviceName = ${info.deviceName}`);
  console.info(`info displayVersion = ${info.versionComponents[0].displayVersion}`);
}).catch((err: BusinessError) => {
  console.error(`getCurrentVersionInfo promise error ${JSON.stringify(err)}`);
});
```

###  getCurrentVersionDescription

getCurrentVersionDescription(descriptionOptions: DescriptionOptions, callback: AsyncCallback\<Array\<ComponentDescription>>): void

获取当前版本描述文件。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名                | 类型                                       | 必填   | 说明              |
| ------------------ | ---------------------------------------- | ---- | --------------- |
| descriptionOptions | [DescriptionOptions](#descriptionoptions) | 是    | 描述文件选项。          |
| callback           | AsyncCallback\<Array\<[ComponentDescription](#componentdescription)>> | 是    | 回调函数，返回当前版本描述文件。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: "zh-cn" // 中文
};

updater.getCurrentVersionDescription(descriptionOptions, (err, info) => {
  console.info(`getCurrentVersionDescription info ${JSON.stringify(info)}`);
  console.info(`getCurrentVersionDescription err ${JSON.stringify(err)}`);
});
```

### getCurrentVersionDescription

getCurrentVersionDescription(descriptionOptions: DescriptionOptions): Promise\<Array\<ComponentDescription>>

获取当前版本描述文件。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名                | 类型                                       | 必填   | 说明     |
| ------------------ | ---------------------------------------- | ---- | ------ |
| descriptionOptions | [DescriptionOptions](#descriptionoptions) | 是    | 描述文件选项。 |

**返回值：**

| 类型                                       | 说明                   |
| ---------------------------------------- | -------------------- |
| Promise\<Array\<[ComponentDescription](#componentdescription)>> | Promise对象，返回当前版本描述文件。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: "zh-cn" // 中文
};
updater.getCurrentVersionDescription(descriptionOptions).then((info: Array<update.ComponentDescription>) => {
  console.info(`getCurrentVersionDescription promise info ${JSON.stringify(info)}`);
}).catch((err: BusinessError) => {
  console.error(`getCurrentVersionDescription promise error ${JSON.stringify(err)}`);
});
```

###  getTaskInfo

getTaskInfo(callback: AsyncCallback\<TaskInfo>): void

获取升级任务信息。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名      | 类型                                    | 必填   | 说明               |
| -------- | ------------------------------------- | ---- | ---------------- |
| callback | AsyncCallback\<[TaskInfo](#taskinfo)> | 是    | 回调函数，返回升级任务信息对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.getTaskInfo((err: BusinessError, info: update.TaskInfo) => {
  console.info(`getTaskInfo isexistTask= ${info?.existTask}`);
});
```

### getTaskInfo

getTaskInfo(): Promise\<TaskInfo>

获取升级任务信息。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**返回值：**

| 类型                              | 说明                  |
| ------------------------------- | ------------------- |
| Promise\<[TaskInfo](#taskinfo)> | Promise对象，返回任务信息对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.getTaskInfo().then((info: update.TaskInfo) => {
  console.info(`getTaskInfo isexistTask= ${info.existTask}`);
}).catch((err: BusinessError) => {
  console.error(`getTaskInfo promise error ${JSON.stringify(err)}`);
});
```

###  download

download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions, callback: AsyncCallback\<void>): void

下载新版本。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名               | 类型                                      | 必填   | 说明                                 |
| ----------------- | --------------------------------------- | ---- | ---------------------------------- |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息。                             |
| downloadOptions   | [DownloadOptions](#downloadoptions)     | 是    | 下载选项。                               |
| callback          | AsyncCallback\<void>                    | 是    | 回调函数。当下载成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 下载选项
const downloadOptions: update.DownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // 允许数据网络下载
  order: update.Order.DOWNLOAD // 下载
};
updater.download(versionDigestInfo, downloadOptions, (err: BusinessError) => {
  console.info(`download error ${JSON.stringify(err)}`);
});
```

### download

download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions): Promise\<void>

下载新版本。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名               | 类型                                      | 必填   | 说明     |
| ----------------- | --------------------------------------- | ---- | ------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息。 |
| downloadOptions   | [DownloadOptions](#downloadoptions)     | 是    | 下载选项。   |

**返回值：**

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 下载选项
const downloadOptions: update.DownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // 允许数据网络下载
   order: update.Order.DOWNLOAD // 下载
};
updater.download(versionDigestInfo, downloadOptions).then(() => {
  console.info(`download start`);
}).catch((err: BusinessError) => {
  console.error(`download error ${JSON.stringify(err)}`);
});
```

###  resumeDownload

resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions, callback: AsyncCallback\<void>): void

恢复下载新版本。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名                   | 类型                                       | 必填   | 说明                                   |
| --------------------- | ---------------------------------------- | ---- | ------------------------------------ |
| versionDigestInfo     | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息。                               |
| resumeDownloadOptions | [ResumeDownloadOptions](#resumedownloadoptions) | 是    | 恢复下载选项。                               |
| callback              | AsyncCallback\<void>                     | 是    | 回调函数。当恢复下载成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo : update.VersionDigestInfo= {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 恢复下载选项
const resumeDownloadOptions : update.ResumeDownloadOptions= {
  allowNetwork: update.NetType.CELLULAR, // 允许数据网络下载
};
updater.resumeDownload(versionDigestInfo, resumeDownloadOptions, (err: BusinessError) => {
  console.info(`resumeDownload error ${JSON.stringify(err)}`);
});
```

### resumeDownload

resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions): Promise\<void>

恢复下载新版本。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名                   | 类型                                       | 必填   | 说明     |
| --------------------- | ---------------------------------------- | ---- | ------ |
| versionDigestInfo     | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息。 |
| resumeDownloadOptions | [ResumeDownloadOptions](#resumedownloadoptions) | 是    | 恢复下载选项。 |

**返回值：**

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 恢复下载选项
const resumeDownloadOptions: update.ResumeDownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // 允许数据网络下载
};
updater.resumeDownload(versionDigestInfo, resumeDownloadOptions).then(() => {
  console.info(`resumeDownload start`);
}).catch((err: BusinessError) => {
  console.error(`resumeDownload error ${JSON.stringify(err)}`);
});
```

###  pauseDownload

pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions, callback: AsyncCallback\<void>): void

暂停下载新版本。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名                  | 类型                                       | 必填   | 说明                                   |
| -------------------- | ---------------------------------------- | ---- | ------------------------------------ |
| versionDigestInfo    | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息。                               |
| pauseDownloadOptions | [PauseDownloadOptions](#pausedownloadoptions) | 是    | 暂停下载选项。                               |
| callback             | AsyncCallback\<void>                     | 是    | 回调函数。当暂停下载成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 暂停下载选项
const pauseDownloadOptions: update.PauseDownloadOptions = {
  isAllowAutoResume: true // 允许自动恢复下载
};
updater.pauseDownload(versionDigestInfo, pauseDownloadOptions, (err: BusinessError) => {
  console.info(`pauseDownload error ${JSON.stringify(err)}`);
});
```

### pauseDownload

pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions): Promise\<void>

暂停下载新版本。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名                  | 类型                                       | 必填   | 说明     |
| -------------------- | ---------------------------------------- | ---- | ------ |
| versionDigestInfo    | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息。 |
| pauseDownloadOptions | [PauseDownloadOptions](#pausedownloadoptions) | 是    | 暂停下载选项。 |

**返回值：**

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 暂停下载选项
const pauseDownloadOptions: update.PauseDownloadOptions = {
  isAllowAutoResume: true // 允许自动恢复下载
};
updater.pauseDownload(versionDigestInfo, pauseDownloadOptions).then(() => {
  console.info(`pauseDownload`);
}).catch((err: BusinessError)  => {
  console.error(`pauseDownload error ${JSON.stringify(err)}`);
});
```

###  upgrade

upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions, callback: AsyncCallback\<void>): void

升级新版本。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名               | 类型                                      | 必填   | 说明                                   |
| ----------------- | --------------------------------------- | ---- | ------------------------------------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息。                               |
| upgradeOptions    | [UpgradeOptions](#upgradeoptions)       | 是    | 更新选项。                                 |
| callback          | AsyncCallback\<void>                    | 是    | 回调函数。当升级执行成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 安装选项
const upgradeOptions: update.UpgradeOptions = {
  order: update.Order.INSTALL // 安装指令
};
updater.upgrade(versionDigestInfo, upgradeOptions, (err: BusinessError) => {
  console.info(`upgrade error ${JSON.stringify(err)}`);
});
```

### upgrade

upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions): Promise\<void>

升级新版本。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名               | 类型                                      | 必填   | 说明     |
| ----------------- | --------------------------------------- | ---- | ------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息。 |
| upgradeOptions    | [UpgradeOptions](#upgradeoptions)       | 是    | 更新选项。   |

**返回值：**

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 安装选项
const upgradeOptions: update.UpgradeOptions = {
  order: update.Order.INSTALL // 安装指令
};
updater.upgrade(versionDigestInfo, upgradeOptions).then(() => {
  console.info(`upgrade start`);
}).catch((err: BusinessError) => {
  console.error(`upgrade error ${JSON.stringify(err)}`);
});
```

###  clearError

clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions, callback: AsyncCallback\<void>): void

清除异常状态。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名               | 类型                                      | 必填   | 说明                                   |
| ----------------- | --------------------------------------- | ---- | ------------------------------------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息。                               |
| clearOptions      | [ClearOptions](#clearoptions)           | 是    | 清除选项。                                 |
| callback          | AsyncCallback\<void>                    | 是    | 回调函数。当清除异常成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 清除选项
const clearOptions: update.ClearOptions = {
  status: update.UpgradeStatus.UPGRADE_FAIL,
};
updater.clearError(versionDigestInfo, clearOptions, (err: BusinessError) => {
  console.info(`clearError error ${JSON.stringify(err)}`);
});
```

### clearError

clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions): Promise\<void>

清除异常状态。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名               | 类型                                      | 必填   | 说明     |
| ----------------- | --------------------------------------- | ---- | ------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息。 |
| clearOptions      | [ClearOptions](#clearoptions)           | 是    | 更新选项。   |

**返回值：**

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 检测结果中的版本摘要信息
};

// 清除选项
const clearOptions: update.ClearOptions = {
  status: update.UpgradeStatus.UPGRADE_FAIL,
};
updater.clearError(versionDigestInfo, clearOptions).then(() => {
  console.info(`clearError success`);
}).catch((err: BusinessError) => {
  console.error(`clearError error ${JSON.stringify(err)}`);
});
```

### getUpgradePolicy

getUpgradePolicy(callback: AsyncCallback\<UpgradePolicy>): void

获取升级策略信息。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名      | 类型                                       | 必填   | 说明              |
| -------- | ---------------------------------------- | ---- | --------------- |
| callback | AsyncCallback\<[UpgradePolicy](#upgradepolicy)> | 是    | 回调函数，返回升级策略信息对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.getUpgradePolicy((err: BusinessError, policy: update.UpgradePolicy) => {
  console.info(`policy downloadStrategy = ${policy?.downloadStrategy}`);
  console.info(`policy autoUpgradeStrategy = ${policy?.autoUpgradeStrategy}`);
});
```

### getUpgradePolicy

getUpgradePolicy(): Promise\<UpgradePolicy>

获取升级策略。通过promise方式作为异步方法。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**返回值：**

| 类型                                       | 说明                    |
| ---------------------------------------- | --------------------- |
| Promise\<[UpgradePolicy](#upgradepolicy)> | Promise对象，返回升级策略信息对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.getUpgradePolicy().then((policy: update.UpgradePolicy) => {
  console.info(`policy downloadStrategy = ${policy.downloadStrategy}`);
  console.info(`policy autoUpgradeStrategy = ${policy.autoUpgradeStrategy}`);
}).catch((err: BusinessError)  => {
  console.error(`getUpgradePolicy promise error ${JSON.stringify(err)}`);
});
```

### setUpgradePolicy

setUpgradePolicy(policy: UpgradePolicy, callback: AsyncCallback\<void>): void

设置升级策略。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名      | 类型                              | 必填   | 说明            |
| -------- | ------------------------------- | ---- | ------------- |
| policy   | [UpgradePolicy](#upgradepolicy) | 是    | 升级策略。          |
| callback | AsyncCallback\<void>            | 是    | 回调函数，返回设置结果对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const policy: update.UpgradePolicy = {
  downloadStrategy: false,
  autoUpgradeStrategy: false,
  autoUpgradePeriods: [{ start: 120, end: 240 }] // 自动升级时间段，用分钟表示
};
updater.setUpgradePolicy(policy, (err: BusinessError) => {
  console.info(`setUpgradePolicy result: ${err}`);
});
```

### setUpgradePolicy

setUpgradePolicy(policy: UpgradePolicy): Promise\<void>

设置升级策略。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名    | 类型                              | 必填   | 说明   |
| ------ | ------------------------------- | ---- | ---- |
| policy | [UpgradePolicy](#upgradepolicy) | 是    | 升级策略。 |

**返回值：**

| 类型             | 说明                  |
| -------------- | ------------------- |
| Promise\<void> | Promise对象。 无返回结果的Promise对象。|

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const policy: update.UpgradePolicy = {
  downloadStrategy: false,
  autoUpgradeStrategy: false,
  autoUpgradePeriods: [ { start: 120, end: 240 } ] // 自动升级时间段，用分钟表示
};
updater.setUpgradePolicy(policy).then(() => {
  console.info(`setUpgradePolicy success`);
}).catch((err: BusinessError) => {
  console.error(`setUpgradePolicy promise error ${JSON.stringify(err)}`);
});
```

###  terminateUpgrade

terminateUpgrade(callback: AsyncCallback\<void>): void

终止升级。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名      | 类型                   | 必填   | 说明                                     |
| -------- | -------------------- | ---- | -------------------------------------- |
| callback | AsyncCallback\<void> | 是    | 回调函数。当清除升级缓存成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.terminateUpgrade((err: BusinessError) => {
  console.info(`terminateUpgrade error ${JSON.stringify(err)}`);
});
```

### terminateUpgrade

terminateUpgrade(): Promise\<void>

终止升级。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**返回值：**

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

updater.terminateUpgrade().then(() => {
  console.info(`terminateUpgrade success`);
}).catch((err: BusinessError) => {
  console.error(`terminateUpgrade error ${JSON.stringify(err)}`);
});
```


### on
on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void

注册事件监听。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**参数：**

| 参数名               | 类型                                       | 必填   | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |
| eventClassifyInfo | [EventClassifyInfo](#eventclassifyinfo)  | 是    | 事件信息。 |
| taskCallback      | [UpgradeTaskCallback](#upgradetaskcallback) | 是    | 事件回调。 |


**示例：**

```ts
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 订阅升级更新事件
  extraInfo: ""
};

updater.on(eventClassifyInfo, (eventInfo: update.EventInfo) => {
  console.info(`updater on ${JSON.stringify(eventInfo)}`);
});
```

### off
off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void

取消注册事件监听。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**参数：**

| 参数名               | 类型                                       | 必填   | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |
| eventClassifyInfo | [EventClassifyInfo](#eventclassifyinfo)  | 是    | 事件信息。 |
| taskCallback      | [UpgradeTaskCallback](#upgradetaskcallback) | 否    | 事件回调。 |


**示例：**

```ts
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 订阅升级更新事件
  extraInfo: ""
};

updater.off(eventClassifyInfo, (eventInfo: update.EventInfo) => {
  console.info(`updater off ${JSON.stringify(eventInfo)}`);
});
```

## Restorer

### factoryReset

factoryReset(callback: AsyncCallback\<void>): void

恢复出厂设置。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.FACTORY_RESET

**参数：**

| 参数名      | 类型                   | 必填   | 说明                                     |
| -------- | -------------------- | ---- | -------------------------------------- |
| callback | AsyncCallback\<void> | 是    | 回调函数。当恢复出厂执行失败时，err为错误对象，有回调；执行成功时，err为undefined，无回调。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
restorer.factoryReset((err) => {
  console.info(`factoryReset error ${JSON.stringify(err)}`);
});
```

### factoryReset

factoryReset(): Promise\<void>

恢复出厂设置。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.FACTORY_RESET

**返回值：**

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。当恢复出厂执行失败时，有回调；执行成功无回调。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

restorer.factoryReset().then(() => {
  console.info(`factoryReset success`);
}).catch((err: BusinessError) => {
  console.error(`factoryReset error ${JSON.stringify(err)}`);
});
```

## LocalUpdater

### verifyUpgradePackage

verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback\<void>): void

校验升级包。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名         | 类型                          | 必填   | 说明               |
| ----------- | --------------------------- | ---- | ---------------- |
| upgradeFile | [UpgradeFile](#upgradefile) | 是    | 升级文件。             |
| certsFile   | string                      | 是    | 证书文件路径。           |
| callback    | AsyncCallback\<void>        | 是    | 回调函数，返回升级包校验结果对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
const upgradeFile: update.UpgradeFile = {
  fileType: update.ComponentType.OTA, // OTA包
  filePath: "path" // 本地升级包路径
};

localUpdater.verifyUpgradePackage(upgradeFile, "cerstFilePath", (err) => {
  console.info(`factoryReset error ${JSON.stringify(err)}`);
});
```

### verifyUpgradePackage

verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise\<void>

校验升级包。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名         | 类型                          | 必填   | 说明     |
| ----------- | --------------------------- | ---- | ------ |
| upgradeFile | [UpgradeFile](#upgradefile) | 是    | 升级文件。   |
| certsFile   | string                      | 是    | 证书文件路径。 |

**返回值：**

| 类型             | 说明                     |
| -------------- | ---------------------- |
| Promise\<void> | Promise对象，返回升级包校验结果对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const upgradeFile: update.UpgradeFile = {
  fileType: update.ComponentType.OTA, // OTA包
  filePath: "path" // 本地升级包路径
};
localUpdater.verifyUpgradePackage(upgradeFile, "cerstFilePath").then(() => {
  console.info(`verifyUpgradePackage success`);
}).catch((err: BusinessError) => {
  console.error(`verifyUpgradePackage error ${JSON.stringify(err)}`);
});
```

### applyNewVersion
applyNewVersion(upgradeFiles: Array<[UpgradeFile](#upgradefile)>, callback: AsyncCallback\<void>): void

安装升级包。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**参数：**

| 参数名         | 类型                                 | 必填   | 说明                                      |
| ----------- | ---------------------------------- | ---- | --------------------------------------- |
| upgradeFile | Array<[UpgradeFile](#upgradefile)> | 是    | 升级文件。                                    |
| callback    | AsyncCallback\<void>               | 是    | 回调函数。当安装升级包执行成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
const upgradeFiles: Array<update.UpgradeFile> = [{
  fileType: update.ComponentType.OTA, // OTA包
  filePath: "path" // 本地升级包路径
}];

localUpdater.applyNewVersion(upgradeFiles, (err) => {
  console.info(`applyNewVersion error ${JSON.stringify(err)}`);
});
```

### applyNewVersion

applyNewVersion(upgradeFiles: Array<[UpgradeFile](#upgradefile)>): Promise\<void>

安装升级包。使用Promise异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.UPDATE_SYSTEM

**返回值：**

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const upgradeFiles: Array<update.UpgradeFile> = [{
  fileType: update.ComponentType.OTA, // OTA包
  filePath: "path" // 本地升级包路径
}];
localUpdater.applyNewVersion(upgradeFiles).then(() => {
  console.info(`applyNewVersion success`);
}).catch((err: BusinessError) => {
  console.error(`applyNewVersion error ${JSON.stringify(err)}`);
});
```

### on
on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void

注册事件监听。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**参数：**

| 参数名               | 类型                                       | 必填   | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |
| eventClassifyInfo | [EventClassifyInfo](#eventclassifyinfo)  | 是    | 事件信息。 |
| taskCallback      | [UpgradeTaskCallback](#upgradetaskcallback) | 是    | 事件回调。 |


**示例：**

```ts
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 订阅升级更新事件
  extraInfo: ""
};

let onTaskUpdate: update.UpgradeTaskCallback = (eventInfo: update.EventInfo) => {
  console.info(`on eventInfo id `, eventInfo.eventId);
};

localUpdater.on(eventClassifyInfo, onTaskUpdate);
```

### off
off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void

取消注册事件监听。使用callback异步回调。

**系统能力**：SystemCapability.Update.UpdateService

**参数：**

| 参数名               | 类型                                       | 必填   | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |
| eventClassifyInfo | [EventClassifyInfo](#eventclassifyinfo)  | 是    | 事件信息。 |
| taskCallback      | [UpgradeTaskCallback](#upgradetaskcallback) | 否    | 事件回调。 |


**示例：**

```ts
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 订阅升级更新事件
  extraInfo: ""
};

let onTaskUpdate: update.UpgradeTaskCallback = (eventInfo: update.EventInfo) => {
  console.info(`on eventInfo id `, eventInfo.eventId);
};

localUpdater.off(eventClassifyInfo, onTaskUpdate);
```

## UpgradeInfo

升级信息。

**系统能力**：SystemCapability.Update.UpdateService

| 名称           | 类型                          | 只读 | 可选 | 说明     |
| ------------ | ----------------------------- | ---- | ---- | ------ |
| upgradeApp   | string                        | 否 | 否 | 调用方包名。  |
| businessType | [BusinessType](#businesstype) | 否 | 否 | 升级业务类型。 |

## BusinessType

升级业务类型。

**系统能力**：SystemCapability.Update.UpdateService

| 名称      | 类型                                | 只读 | 可选 |  说明   |
| ------- | ----------------------------------- | ---- | ---- | ---- |
| vendor  | [BusinessVendor](#businessvendor)   | 否 | 否 | 供应商/厂家。  |
| subType | [BusinessSubType](#businesssubtype) | 否 | 否 | 升级类型。  |

## CheckResult

搜包结果。

**系统能力**：SystemCapability.Update.UpdateService

| 名称                | 类型                              | 只读 | 可选 | 说明     |
| ----------------- | --------------------------------- | ---- | ---- | ------ |
| isExistNewVersion | boolean                              | 否 | 否 | 是否有新版本。<br>ture表示有新版本，false表示没有新版本。|
| newVersionInfo    | [NewVersionInfo](#newversioninfo) | 否 | 否 | 新版本数据。  |

## NewVersionInfo

新版本数据。

**系统能力**：SystemCapability.Update.UpdateService

| 名称                | 类型                                     | 只读 | 可选 | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |---- |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo)  | 否 | 否 | 版本摘要。 |
| versionComponents | Array\<[VersionComponent](#versioncomponent)> | 否 | 否 | 版本组件。 |

## VersionDigestInfo

版本摘要。

**系统能力**：SystemCapability.Update.UpdateService

| 名称            | 类型   | 只读 | 可选 | 说明   |
| ------------- | ------ | ---- | ---- | ---- |
| versionDigest | string | 否 | 否 | 版本摘要。 |

## VersionComponent

版本组件。

**系统能力**：SystemCapability.Update.UpdateService

| 名称              | 类型                                | 只读 | 可选 | 说明       |
| --------------- | ----------------------------------- | ---- | ---- | -------- |
| componentId     | string                              | 否 | 否 | 组件标识。     |
| componentType   | [ComponentType](#componenttype)     | 否 | 否 | 组件类型。     |
| upgradeAction   | [UpgradeAction](#upgradeaction)     | 否 | 否 | 升级方式。     |
| displayVersion  | string                              | 否 | 否 | 显示版本号。    |
| innerVersion    | string                              | 否 | 否 | 版本号。      |
| size            | number                              | 否 | 否 | 升级包大小，单位为B。    |
| effectiveMode   | [EffectiveMode](#effectivemode)     | 否 | 否 | 生效模式。     |
| descriptionInfo | [DescriptionInfo](#descriptioninfo) | 否 | 否 | 版本描述文件信息。 |
| otaMode<sup>20+</sup> | [OtaMode](#otamode20)                 | 否 | 是 | 升级模式。     |

## DescriptionOptions

描述文件选项。

**系统能力**：SystemCapability.Update.UpdateService

| 名称       | 类型                                    | 只读 | 可选 | 说明     |
| -------- | --------------------------------------- | ---- | ---- | ------ |
| format   | [DescriptionFormat](#descriptionformat) | 否 | 否 | 描述文件格式。 |
| language | string                                  | 否 | 否 | 描述文件语言。 |

## ComponentDescription

组件描述文件。

**系统能力**：SystemCapability.Update.UpdateService

| 名称              | 类型                                | 只读 | 可选 | 说明     |
| --------------- | ----------------------------------- | ---- | ---- | ------ |
| componentId     | string                              | 否 | 否 | 组件标识。   |
| descriptionInfo | [DescriptionInfo](#descriptioninfo) | 否 | 否 | 描述文件信息。 |

## DescriptionInfo

版本描述文件信息。

**系统能力**：SystemCapability.Update.UpdateService

| 名称              | 类型                                | 只读 | 可选 | 说明     |
| --------------- | ----------------------------------- | ---- | ---- | ------ |
| descriptionType | [DescriptionType](#descriptiontype) | 否 | 否 | 描述文件类型。 |
| content         | string                              | 否 | 否 | 描述文件内容。 |

## CurrentVersionInfo

当前版本信息。

**系统能力**：SystemCapability.Update.UpdateService

| 名称                | 类型                                     | 只读 | 可选 | 说明    |
| ----------------- | ---------------------------------------- | ---- | ---- | ----- |
| osVersion         | string                                   | 否 | 否 | 系统版本号。 |
| deviceName        | string                                   | 否 | 否 | 设备名。   |
| versionComponents | Array\<[VersionComponent](#versioncomponent)> | 否 | 否 | 版本组件。  |

## DownloadOptions

下载选项。

**系统能力**：SystemCapability.Update.UpdateService

| 名称           | 类型                | 只读 | 可选   | 说明   |
| ------------ | ------------------- | ---- | ---- | ---- |
| allowNetwork | [NetType](#nettype) | 否  | 否 | 网络类型。 |
| order        | [Order](#order)     | 否  | 否 | 升级指令。 |

## ResumeDownloadOptions

恢复下载选项。

**系统能力**：SystemCapability.Update.UpdateService

| 名称           | 类型                | 只读 | 可选 | 说明   |
| ------------ | ------------------- | ---- | ---- | ---- |
| allowNetwork | [NetType](#nettype) | 否 | 否 | 网络类型。 |

## PauseDownloadOptions

暂停下载选项。

**系统能力**：SystemCapability.Update.UpdateService

| 名称                | 类型 | 只读 | 可选 | 说明       |
| ----------------- | ---- | ---- |---- | -------- |
| isAllowAutoResume | boolean | 否 | 否 | 是否允许自动恢复。<br>ture表示允许自动恢复，false表示不允许。 |

## UpgradeOptions

升级选项。

**系统能力**：SystemCapability.Update.UpdateService

| 名称    | 类型            | 只读 | 可选 | 说明   |
| ----- | --------------- | ---- | ---- |---- |
| order | [Order](#order) | 否 | 否 | 升级指令。 |

## ClearOptions

清除异常选项。

**系统能力**：SystemCapability.Update.UpdateService

| 名称     | 类型                            | 只读 | 可选 | 说明   |
| ------ | ------------------------------- | ---- | ---- | ---- |
| status | [UpgradeStatus](#upgradestatus) | 否 | 否 | 异常状态。 |

## UpgradePolicy

升级策略。

**系统能力**：SystemCapability.Update.UpdateService

| 名称                  | 类型                                    | 只读 | 可选 | 说明      |
| ------------------- | --------------------------------------- | ---- | ---- | ------- |
| downloadStrategy    | boolean                        | 否 | 否 | 自动下载策略。 <br>ture表示可自动下载，false表示不可自动下载。 |
| autoUpgradeStrategy | boolean                        | 否 | 否 | 自动升级策略。 <br>ture表示可自动升级，false表示不可自动升级。 |
| autoUpgradePeriods  | Array\<[UpgradePeriod](#upgradeperiod)> | 否 | 否  | 自动升级时间段。 |

## UpgradePeriod

升级时间段。

**系统能力**：SystemCapability.Update.UpdateService

| 名称    | 类型   | 只读 | 可选 | 说明 |
| ----- | ------ | ---- | ---- | ---- |
| start | number | 否 | 否 | 开始时间。 |
| end   | number | 否 | 否 | 结束时间。 |

## TaskInfo

任务信息。

**系统能力**：SystemCapability.Update.UpdateService

| 名称        | 类型                  | 只读 | 可选 | 说明 |
| --------- | --------------------- | ---- | ------ |------ |
| existTask |  boolean                  | 否 | 否 | 是否存在任务。<br>ture表示存在，false表示不存在。 |
| taskBody  | [TaskBody](#taskbody) | 否 | 否 | 任务数据。   |

## EventInfo

事件信息。

**系统能力**：SystemCapability.Update.UpdateService

| 名称       | 类型                  | 只读 | 可选 | 说明 |
| -------- | --------------------- | ---- | ---- | ---- |
| eventId  | [EventId](#eventid)   | 否 | 否 | 事件ID。 |
| taskBody | [TaskBody](#taskbody) | 否 | 否 | 任务数据。 |

## TaskBody

任务数据。

**系统能力**：SystemCapability.Update.UpdateService

| 名称                | 类型                                     | 只读 | 可选 | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- | ---- |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo)  | 否 |  否    | 版本摘要。 |
| status            | [UpgradeStatus](#upgradestatus)          | 否 |  否    | 升级状态。 |
| subStatus         | number                                   | 否 |  否    | 子状态。  |
| progress          | number                                   | 否 |  否    | 进度。   |
| installMode       | number                                   | 否 |  否    | 安装模式。 |
| errorMessages     | Array\<[ErrorMessage](#errormessage)>    | 否 |  否    | 错误信息。 |
| versionComponents | Array\<[VersionComponent](#versioncomponent)> | 否 | 否    | 版本组件。 |

## ErrorMessage

错误信息。

**系统能力**：SystemCapability.Update.UpdateService

| 名称           | 类型   | 只读 | 可选  | 说明   |
| ------------ | ------ | ---- | ---- | ---- |
| errorCode    | number | 否 | 否  | 错误码。  |
| errorMessage | string | 否 | 否  | 错误描述。 |

## EventClassifyInfo

事件信息。

**系统能力**：SystemCapability.Update.UpdateService

| 名称            | 类型                            | 只读 | 可选  | 说明   |
| ------------- | ------------------------------- | ---- | ---- | ---- |
| eventClassify | [EventClassify](#eventclassify) | 否  | 否  | 事件类型。 |
| extraInfo     | string                          | 否  | 否  | 额外信息。 |

## UpgradeFile

升级文件。

**系统能力**：SystemCapability.Update.UpdateService

| 名称       | 类型                            | 只读 | 可选 | 说明   |
| -------- | ------------------------------- | ---- | ---- | ---- |
| fileType | [ComponentType](#componenttype) | 否    | 否 | 文件类型。 |
| filePath | string                          | 否    | 否 | 文件路径。 |

## UpgradeTaskCallback

(eventInfo: EventInfo): void

事件回调。

**系统能力**：SystemCapability.Update.UpdateService

| 名称        | 类型                    | 必填   | 说明   |
| --------- | ----------------------- | ---- | ---- |
| eventInfo | [EventInfo](#eventinfo) | 是    | 事件信息。 |

## BusinessVendor

设备厂家。

**系统能力**：SystemCapability.Update.UpdateService

| 名称    | 值      | 说明   |
| ------ | -------- | ---- |
| PUBLIC | "public" | 开源。   |

## BusinessSubType

升级类型。

**系统能力**：SystemCapability.Update.UpdateService

| 名称      | 值  | 说明   |
| -------- | ---- | ---- |
| FIRMWARE | 1    | 固件。   |

## ComponentType

组件类型。

**系统能力**：SystemCapability.Update.UpdateService

| 名称  | 值  | 说明   |
| ---- | ---- | ---- |
| OTA  | 1    | 固件。   |

## UpgradeAction

升级方式。

**系统能力**：SystemCapability.Update.UpdateService

| 名称      | 值        | 说明   |
| -------- | ---------- | ---- |
| UPGRADE  | "upgrade"  | 差分包。  |
| RECOVERY | "recovery" | 修复包。  |

## EffectiveMode

生效模式。

**系统能力**：SystemCapability.Update.UpdateService

| 名称           | 值  | 说明   |
| ------------- | ---- | ---- |
| COLD          | 1    | 冷升级。  |
| LIVE          | 2    | 热升级。  |
| LIVE_AND_COLD | 3    | 融合升级。 |

## OtaMode<sup>20+</sup>

升级模式。

**系统能力**：SystemCapability.Update.UpdateService

| 名称           | 值  | 说明   |
| ------------- | ---- | ---- |
| REGULAR_OTA   | 0    | 正常升级。|
| STREAM_OTA    | 1    | 流式升级。|
| AB_REGULAR_OTA | 2    | AB正常升级。 |
| AB_STREAM_OTA  | 3    | AB流式升级。 |

## DescriptionType

描述文件类型。

**系统能力**：SystemCapability.Update.UpdateService

| 名称     | 值  | 说明   |
| ------- | ---- | ---- |
| CONTENT | 0    | 内容。   |
| URI     | 1    | 链接。   |

## DescriptionFormat

描述文件格式。

**系统能力**：SystemCapability.Update.UpdateService

| 名称        | 值  | 说明   |
| ---------- | ---- | ---- |
| STANDARD   | 0    | 标准格式。 |
| SIMPLIFIED | 1    | 简易格式。 |

## NetType

网络类型。

**系统能力**：SystemCapability.Update.UpdateService

| 名称               | 值  | 说明        |
| ----------------- | ---- | --------- |
| CELLULAR          | 1    | 数据网络。      |
| METERED_WIFI      | 2    | 热点WIFI。    |
| NOT_METERED_WIFI  | 4    | 非热点WIFI。   |
| WIFI              | 6    | WIFI。      |
| CELLULAR_AND_WIFI | 7    | 数据网络和WIFI。 |

## Order

升级指令。

**系统能力**：SystemCapability.Update.UpdateService

| 名称                  | 值  | 说明    |
| -------------------- | ---- | ----- |
| DOWNLOAD             | 1    | 下载。    |
| INSTALL              | 2    | 安装。    |
| DOWNLOAD_AND_INSTALL | 3    | 下载并安装。 |
| APPLY                | 4    | 生效。    |
| INSTALL_AND_APPLY    | 6    | 安装并生效。 |

## UpgradeStatus

升级状态。

**系统能力**：SystemCapability.Update.UpdateService

| 名称              | 值  | 说明   |
| ---------------- | ---- | ---- |
| WAITING_DOWNLOAD | 20   | 待下载。  |
| DOWNLOADING      | 21   | 下载中。  |
| DOWNLOAD_PAUSED  | 22   | 下载暂停。 |
| DOWNLOAD_FAIL    | 23   | 下载失败。 |
| WAITING_INSTALL  | 30   | 待安装。  |
| UPDATING         | 31   | 更新中。  |
| WAITING_APPLY    | 40   | 待生效。  |
| APPLYING         | 41   | 生效中。  |
| UPGRADE_SUCCESS  | 50   | 升级成功。 |
| UPGRADE_FAIL     | 51   | 升级失败。 |

## EventClassify

事件类型。

**系统能力**：SystemCapability.Update.UpdateService

| 名称   | 值        | 说明   |
| ---- | ---------- | ---- |
| TASK | 0x01000000 | 任务事件。 |

## EventId

事件ID。

**系统能力**：SystemCapability.Update.UpdateService

| 名称                     | 值        | 说明     |
| ---------------------- | ---------- | ------ |
| EVENT_TASK_BASE        | EventClassify.TASK | 任务事件。   |
| EVENT_TASK_RECEIVE     | 0x01000001 | 收到任务。   |
| EVENT_TASK_CANCEL      | 0x01000002 | 取消任务。   |
| EVENT_DOWNLOAD_WAIT    | 0x01000003 | 待下载。    |
| EVENT_DOWNLOAD_START   | 0x01000004 | 开始下载。   |
| EVENT_DOWNLOAD_UPDATE  | 0x01000005 | 下载进度更新。 |
| EVENT_DOWNLOAD_PAUSE   | 0x01000006 | 下载暂停。   |
| EVENT_DOWNLOAD_RESUME  | 0x01000007 | 恢复下载。   |
| EVENT_DOWNLOAD_SUCCESS | 0x01000008 | 下载成功。   |
| EVENT_DOWNLOAD_FAIL    | 0x01000009 | 下载失败。   |
| EVENT_UPGRADE_WAIT     | 0x0100000A | 待升级。    |
| EVENT_UPGRADE_START    | 0x0100000B | 开始升级。   |
| EVENT_UPGRADE_UPDATE   | 0x0100000C | 升级中。    |
| EVENT_APPLY_WAIT       | 0x0100000D | 待生效。    |
| EVENT_APPLY_START      | 0x0100000E | 开始生效。   |
| EVENT_UPGRADE_SUCCESS  | 0x0100000F | 更新成功。   |
| EVENT_UPGRADE_FAIL     | 0x01000010 | 更新失败。   |
