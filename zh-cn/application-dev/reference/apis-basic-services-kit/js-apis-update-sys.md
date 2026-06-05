# @ohos.update (升级)(系统接口)
<!--Kit: Basic Services Kit-->
<!--Subsystem: Update-->
<!--Owner: @RainyDay_005; @huangsiping3-->
<!--Designer: @zhangzhengxue; @jackd320-->
<!--Tester: @mamba-ting-->
<!--Adviser: @fang-jinxu-->

升级范围：升级整个系统，包括内置资源和预置应用，不包括第三方应用。

升级类型：SD卡升级、在线升级。

各升级类型的设计逻辑和适用场景如下：

- **SD卡升级**：

适用于需要从本地存储设备进行系统升级的场景。

升级流程为：开发者准备SD卡和升级包 → 系统校验升级包 → 系统安装升级包 → 设备重启系统以应用新版本。

- **在线升级**：

适用于需要通过网络自动检查和升级系统的场景。

升级流程为：调用者检查新版本 → 系统下载升级包 → 系统安装升级包 → 设备重启系统以应用新版本。

通过Updater接口实现，依赖设备厂商部署的升级包管理服务器（用于存储和管理升级包的服务端系统，提供版本检查、升级包下载等功能），接口由设备厂商实现。

**恢复出厂设置：**

适用于需要清除用户数据、恢复设备出厂状态的场景。通过清除用户数据和系统设置，帮助用户快速解决系统异常、释放存储空间、保护隐私数据等问题。通过Restorer接口实现恢复出厂设置功能。

恢复出厂流程

设备恢复出厂设置需遵循以下标准流程：

1. **验证权限**
   - 系统首先验证当前调用方是否具备执行恢复操作的权限。

2. **选择恢复方式**
   - 调用方根据业务需求，从以下三种模式中选择其一：
     - `factoryReset`：仅清除用户数据分区，保留系统文件。
     - `forceFactoryReset`：清除用户数据分区，并同步清除文件密钥（用于加密用户数据的密钥，清除后加密数据无法被恢复）。
     - `deepFactoryReset`：可配置清除范围（仅清除用户数据分区或同时清除用户数据分区和操作系统分区）。

3. **执行清除**
   - 系统调用对应的恢复方法，执行数据擦除操作。

4. **重启设备**
   - 系统自动重启设备，恢复至出厂初始状态。

> **说明**：
>
> 本模块首批接口从API version 9开始支持，不带版本上标标记的接口均为首批接口。
> 后续版本的新增接口，采用上标单独标记接口的起始版本。
>
> 本模块接口为系统接口。

## 导入模块

```js
import { update } from '@kit.BasicServicesKit';
```

## update.getOnlineUpdater

getOnlineUpdater(upgradeInfo: UpgradeInfo): Updater

获取在线升级对象，可用于在线检查新版本、下载升级包、安装升级包等操作。适用于设备厂商的OTA（Over-The-Air，空中下载）升级客户端应用、在线系统升级等场景。解决无法自动检查新版本、手动升级繁琐等问题，帮助用户及时获取系统更新，提升升级效率和用户体验。

**原理说明**：

该方法通过系统服务接口获取在线升级工具对象，该对象提供检查新版本、下载升级包、安装升级包等核心功能。

**约束和限制**：

- 检查新版本和下载升级包都必须依赖设备厂商部署的升级包管理服务器。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**参数**：

| 参数名         | 类型                          | 必填   | 说明     |
| ----------- | --------------------------- | ---- | ------ |
| upgradeInfo | [UpgradeInfo](#upgradeinfo) | 是    | 升级对象信息，用于标识调用方和升级业务类型。详见UpgradeInfo定义。 |

**返回值**：

| 类型                  | 说明   |
| ------------------- | ---- |
| [Updater](#updater) | 用于执行在线升级相关操作的工具类对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例**：

```ts
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
```

## update.getRestorer

getRestorer(): Restorer

获取恢复出厂设置对象，用于执行恢复出厂设置相关操作。调用此方法后，系统返回Restorer工具类对象，该对象提供三种恢复出厂方式：

- factoryReset（普通恢复，仅清除用户数据分区）。
- forceFactoryReset（强制恢复，清除用户数据分区并同步清除文件密钥）。
- deepFactoryReset（深度恢复，可通过scope参数指定清除范围：DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据和操作系统分区）。

获取对象后可调用相应方法执行恢复出厂操作，清除范围因方法而异，设备将重启恢复到出厂初始状态。

**原理说明**：

该方法通过系统服务接口获取恢复出厂设置工具对象，对象内封装了数据分区清除、密钥清除、系统分区清理等核心功能。

**约束和限制**：

- 恢复出厂操作不可逆，将永久删除用户数据，需提前提醒用户备份重要数据。
- 需要系统权限 ohos.permission.FACTORY_RESET 或 ohos.permission.FORCE_FACTORY_RESET。
- 操作过程中设备会自动重启，应用需做好状态保存。
- 建议仅在用户明确确认后执行恢复出厂操作。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**返回值**：

| 类型                    | 说明     |
| --------------------- | ------ |
| [Restorer](#restorer) | 用于执行恢复出厂设置相关操作的工具类对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例**：

```ts
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
```

## update.getLocalUpdater

getLocalUpdater(): LocalUpdater

获取本地升级对象，用于从本地存储设备（如SD卡）执行系统升级。调用此方法后，系统返回LocalUpdater工具类对象，该对象提供本地升级包校验、安装等功能。

典型流程为：准备升级包（从设备厂商官网下载，格式为.zip或.bin）和证书文件（用于验证升级包签名，格式为.cert或.der） → 校验包签名和完整性 → 安装升级包 → 设备重启以应用新版本。

**原理说明**：

该方法获取本地升级工具对象，对象内封装了升级包校验机制（验证数字签名、文件完整性、版本兼容性）和安装机制（解压写入系统分区）。本地升级不依赖网络，从设备本地存储读取升级包。

**约束和限制**：

- 升级包必须从设备厂商官网或官方渠道下载，确保来源可信。
- 安装前必须先校验升级包（调用verifyUpgradePackage），未校验的包可能导致系统损坏。
- 升级过程中设备会重启，应用需做好状态保存。
- 需要系统权限 ohos.permission.UPDATE_SYSTEM。
- 升级包文件路径长度不超过255字符。超出范围时抛出异常。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**返回值**：

| 类型                            | 说明     |
| ----------------------------- | ------ |
| [LocalUpdater](#localupdater) | 用于执行本地升级相关操作的工具类对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例**：

```ts
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
```

## Updater

提供在线检查新版本、下载升级包、安装升级包、管理升级策略、获取版本信息等系统在线更新功能的工具类。

**在线升级流程**：

1. 开发者调用getOnlineUpdater方法获取Updater对象，传入升级应用信息和业务类型。
2. 开发者调用checkNewVersion方法检查是否有新版本，获取返回结果 CheckResult。
3. 开发者检查返回结果的isExistNewVersion字段，如为true则调用getNewVersionInfo获取新版本详细信息。
4. 开发者调用download方法下载升级包到设备本地存储，下载过程中可暂停和恢复。
5. 开发者调用upgrade方法执行升级安装，设备将重启以应用新版本。
6. 开发者通过on方法注册事件监听，实时监控下载和安装进度。

**实现机制**：

- 版本检查：向升级包管理服务器查询新版本信息。
- 下载管理：支持网络类型选择、暂停/恢复下载、断点续传。
- 安装机制：升级包下载完成后解压并写入系统分区，准备重启应用。
- 状态管理：维护升级任务状态，支持查询任务信息、清除异常状态、终止升级。

### checkNewVersion

checkNewVersion(callback: AsyncCallback\<CheckResult>): void

检查新版本信息，返回是否有新版本、新版本号、版本摘要信息等。调用成功后，返回版本检查结果对象，可用于判断是否需要升级，为后续下载、升级等操作提供版本标识。使用callback异步回调。

使用场景：适用于需要快速检查是否有新版本并获取版本摘要的场景。解决无法判断是否有新版本、无法获取版本信息等问题，帮助用户及时了解系统更新状态，为升级决策提供依据。

> **说明**：

本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名      | 类型                                       | 必填   | 说明             |
| -------- | ---------------------------------------- | ---- | -------------- |
| callback | AsyncCallback\<[CheckResult](#checkresult)> | 是    | 回调函数，返回版本检查结果对象。详见CheckResult 定义。|

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 创建在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 检查新版本，通过回调函数获取检查结果
  onlineUpdater.checkNewVersion((checkError: BusinessError,      
    checkResult: update.CheckResult) => {
      if (checkError) {
        console.error(`checkNewVersion error: ${JSON.stringify(checkError)}`);
        return; 
      }
      console.info(`checkNewVersion isExistNewVersion  ${checkResult?.isExistNewVersion}`);
    });
} catch(error) {
  console.error(`Fail to get updater error: ${error}`);
}
```

### checkNewVersion

checkNewVersion(): Promise\<CheckResult>

检查新版本信息，返回是否有新版本、新版本号、版本摘要信息等。调用成功后，返回版本检查结果对象，可用于判断是否需要升级，为后续下载、升级等操作提供版本标识。使用Promise异步回调。

使用场景：适用于需要快速检查是否有新版本并获取版本摘要的场景。解决无法判断是否有新版本、无法获取版本信息等问题，帮助用户及时了解系统更新状态，为升级决策提供依据。

> **说明**：

本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**返回值**：

| 类型                                    | 说明                  |
| ------------------------------------- | ------------------- |
| Promise\<[CheckResult](#checkresult)> | Promise对象。成功时resolve返回版本检查结果对象，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  onlineUpdater.checkNewVersion().then((result: update.CheckResult) => {
    console.info(`checkNewVersion isExistNewVersion: ${result.isExistNewVersion}`);
    // 版本摘要信息
    console.info(`checkNewVersion versionDigestInfo: ${result.newVersionInfo.versionDigestInfo.versionDigest}`);
    }).catch((checkNewVersionError: BusinessError) => {
      console.error(`checkNewVersion promise error ${JSON.stringify(checkNewVersionError)}`);
    });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getNewVersionInfo

getNewVersionInfo(callback: AsyncCallback\<NewVersionInfo>): void

获取新版本信息，向升级包管理服务器查询新版本的详细信息，包括版本号、版本摘要、版本组件等。调用成功后，返回新版本信息对象，包含版本摘要和完整的版本组件列表，可用于向用户展示完整版本信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。使用callback异步回调。

使用场景：适用于需要向用户展示完整版本信息（如版本号、升级包大小、组件详情）的场景。解决用户无法获取详细版本信息、无法了解升级内容等问题，帮助用户全面了解新版本特性，辅助用户做出升级决策。

**调用顺序**：

- 必须先调用checkNewVersion检查是否有新版本。
- 只有当checkNewVersion返回isExistNewVersion为true时，才能调用此方法获取新版本详细信息。
- 如果 isExistNewVersion 为 false，表示无新版本，调用此方法会返回空数据。

**相关方法**：

- checkNewVersion()：检查是否有新版本（前置方法）。
- getNewVersionDescription()：获取新版本描述信息 。
- download()：下载升级包（后续方法）。  

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名      | 类型                                       | 必填   | 说明              |
| -------- | ---------------------------------------- | ---- | --------------- |
| callback | AsyncCallback\<[NewVersionInfo](#newversioninfo)> | 是    | 回调函数，用于接收新版本信息。回调参数包括： err（错误对象，成功时为null）和newInfo（新版本信息对象，包含versionDigestInfo和versionComponents字段）。调用前须先调用checkNewVersion检查新版本，且仅当isExistNewVersion为true时newInfo有效；若为false，则newInfo为空数据。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取新版本信息，通过回调函数接收版本详情
  onlineUpdater.getNewVersionInfo((checkError: BusinessError, newInfo: update.NewVersionInfo) => {
    if (checkError) {
      console.error(`getNewVersionInfo error: ${JSON.stringify(checkError)}`);
      return;
    }
    console.info(`info displayVersion = ${newInfo?.versionComponents[0].displayVersion}`);
    console.info(`info innerVersion = ${newInfo?.versionComponents[0].innerVersion}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getNewVersionInfo

getNewVersionInfo(): Promise\<NewVersionInfo>

获取新版本信息，向升级包管理服务器查询新版本的详细信息，包括版本号、版本摘要、版本组件等。调用成功后，返回新版本信息对象，包含版本摘要和完整的版本组件列表，可用于向用户展示完整版本信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。使用Promise异步回调。

使用场景：适用于需要向用户展示完整版本信息（如版本号、升级包大小、组件详情）的场景。解决用户无法获取详细版本信息、无法了解升级内容等问题，帮助用户全面了解新版本特性，辅助用户做出升级决策。

**调用顺序**：

- 必须先调用checkNewVersion检查是否有新版本。
- 只有当checkNewVersion返回isExistNewVersion为true时，才能调用此方法获取新版本详细信息。
- 如果 isExistNewVersion 为 false，表示无新版本，调用此方法会返回空数据。

**相关方法**：

- checkNewVersion()：检查是否有新版本（前置方法）。
- getNewVersionDescription()：获取新版本描述信息。
- download()：下载升级包（后续方法）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**返回值**：

| 类型                                       | 说明                   |
| ---------------------------------------- | -------------------- |
| Promise\<[NewVersionInfo](#newversioninfo)> | Promise对象。成功时resolve返回新版本详细信息对象，用于向用户展示完整版本信息；失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  onlineUpdater.getNewVersionInfo().then((info: update.NewVersionInfo) => {
    console.info(`info displayVersion = ${info.versionComponents[0].displayVersion}`);
    console.info(`info innerVersion = ${info.versionComponents[0].innerVersion}`);
  }).catch((getNewVersionInfoError: BusinessError) => {
    console.error(`getNewVersionInfo promise error ${JSON.stringify(getNewVersionInfoError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getNewVersionDescription

getNewVersionDescription(versionDigestInfo: VersionDigestInfo, descriptionOptions: DescriptionOptions, callback: AsyncCallback\<Array\<ComponentDescription>>): void

获取新版本描述信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。调用成功后，返回新版本描述信息数组，包含各组件的版本说明内容。使用callback异步回调。

使用场景：适用于向用户展示版本更新内容、确认是否升级等场景。解决用户无法了解版本更新内容、无法确认升级价值等问题，帮助用户了解新版本的功能改进和修复内容，辅助用户做出升级决策。

**调用说明**：

- 需先调用checkNewVersion检查是否有新版本，并获取版本摘要信息。
- versionDigestInfo参数从checkNewVersion返回结果中获取。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名                | 类型                                       | 必填   | 说明             |
| ------------------ | ---------------------------------------- | ---- | -------------- |
| versionDigestInfo  | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。|
| descriptionOptions | [DescriptionOptions](#descriptionoptions) | 是    | 描述文件选项，用于指定描述文件的格式和语言。详见DescriptionOptions定义。 |
| callback           | AsyncCallback\<Array\<[ComponentDescription](#componentdescription)>> | 是    | 回调函数，用于接收新版本描述信息。回调参数包括： err（错误对象，成功时为null）和descriptionInfo（新版本描述信息数组，包含各组件的版本说明内容）。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: "versionDigest" // 从checkNewVersion结果中获取版本摘要信息
};

// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: "zh-cn" // 中文
};

try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  onlineUpdater.getNewVersionDescription(versionDigestInfo, descriptionOptions, (descriptionErr, descriptionInfo) => {
    console.info(`getNewVersionDescription info ${JSON.stringify(descriptionInfo)}`);
    console.info(`getNewVersionDescription error ${JSON.stringify(descriptionErr)}`);
  });
} catch(error) {
  console.error(`Fail to get updater error: ${error}`);
}
```

### getNewVersionDescription

获取新版本描述信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。调用成功后，返回新版本描述信息数组，包含各组件的版本说明内容。使用Promise异步回调。

使用场景：适用于向用户展示版本更新内容、确认是否升级等场景。解决用户无法了解版本更新内容、无法确认升级价值等问题，帮助用户了解新版本的功能改进和修复内容，辅助用户做出升级决策。

**调用说明**：

- 需先调用checkNewVersion检查是否有新版本，并获取版本摘要信息。
- versionDigestInfo参数从checkNewVersion返回结果中获取。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名                | 类型                                       | 必填   | 说明     |
| ------------------ | ---------------------------------------- | ---- | ------ |
| versionDigestInfo  | [VersionDigestInfo](#versiondigestinfo)  | 是    |  版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。 |
| descriptionOptions | [DescriptionOptions](#descriptionoptions) | 是    | 描述文件选项，用于指定描述文件的格式和语言。对象包含format（描述文件格式，可选STANDARD或SIMPLIFIED）和language（语言代码，如'zh-cn'）字段。STANDARD适合需要完整描述信息的场景，SIMPLIFIED适合仅需精简描述信息的场景。 |

**返回值**：

| 类型                                       | 说明                  |
| ---------------------------------------- | ------------------- |
| Promise\<Array\<[ComponentDescription](#componentdescription)>> | Promise对象。成功时resolve返回新版本描述信息数组，用于向用户展示版本更新内容和确认升级；失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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

try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取新版本描述信息
  onlineUpdater.getNewVersionDescription(versionDigestInfo, descriptionOptions)
    .then((info: Array<update.ComponentDescription>) => {
    console.info(`getNewVersionDescription promise info ${JSON.stringify(info)}`);
  }).catch((getNewVersionDescriptionError: BusinessError) => {
    console.error(`getNewVersionDescription promise error ${JSON.stringify(getNewVersionDescriptionError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getCurrentVersionInfo

getCurrentVersionInfo(callback: AsyncCallback\<CurrentVersionInfo>): void

获取当前版本信息。调用成功后返回当前版本信息对象，包含系统版本号、设备名、版本组件等，帮助用户快速了解设备版本状态，便于升级决策与问题排查。使用callback异步回调。

使用场景：用于在设置界面展示系统版本、对比版本是否为最新、进行版本管理与诊断等场景。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名      | 类型                                       | 必填   | 说明               |
| -------- | ---------------------------------------- | ---- | ---------------- |
| callback | AsyncCallback\<[CurrentVersionInfo](#currentversioninfo)> | 是    | 回调函数，用于接收当前版本信息。回调参数包括： err（错误对象，成功时为null）和currentInfo（当前版本信息对象，包含osVersion、deviceName和versionComponents字段）。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取当前版本信息，通过回调函数接收版本详情
  onlineUpdater.getCurrentVersionInfo((currentVersionInfoError: BusinessError,
    currentVersionInfo: update.CurrentVersionInfo) => {
    if (currentVersionInfoError) {
      console.error(`getCurrentVersionInfo error: ${JSON.stringify(currentVersionInfoError)}`);
      return;
    }
    console.info(`info osVersion = ${currentVersionInfo?.osVersion}`);
    console.info(`info deviceName = ${currentVersionInfo?.deviceName}`);
    console.info(`info displayVersion = ${currentVersionInfo?.versionComponents[0].displayVersion}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getCurrentVersionInfo

getCurrentVersionInfo(): Promise\<CurrentVersionInfo>

获取当前版本信息。调用成功后返回当前版本信息对象，包含系统版本号、设备名、版本组件等，帮助用户快速了解设备版本状态，便于升级决策与问题排查。使用Promise异步回调。

使用场景：用于在设置界面展示系统版本、对比版本是否为最新、进行版本管理与诊断等场景。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**返回值**：

| 类型                                       | 说明                  |
| ---------------------------------------- | ------------------- |
| Promise\<[CurrentVersionInfo](#currentversioninfo)> | Promise对象。成功时resolve返回当前版本信息对象，用于展示系统版本和版本对比；失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取当前版本信息
  onlineUpdater.getCurrentVersionInfo().then((info: update.CurrentVersionInfo) => {
    console.info(`info osVersion = ${info.osVersion}`);
    console.info(`info deviceName = ${info.deviceName}`);
    console.info(`info displayVersion = ${info.versionComponents[0].displayVersion}`);
  }).catch((currentVersionInfoError: BusinessError) => {
    console.error(`getCurrentVersionInfo promise error ${JSON.stringify(currentVersionInfoError)}`);
  });
} catch(error) {
  console.error(`Fail to get updater error: ${error}`);
}
```

### getCurrentVersionDescription

getCurrentVersionDescription(descriptionOptions: DescriptionOptions, callback: AsyncCallback\<Array\<ComponentDescription>>): void

获取当前版本描述信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。获取成功后，返回当前版本描述信息数组，包含版本说明内容，可用于版本信息展示、版本状态确认、版本对比分析等用途。使用callback异步回调。

使用场景：适用于需要向用户展示当前版本详情、确认当前系统版本状态、对比新旧版本差异等场景。典型场景在设备信息界面展示当前版本的更新说明、在版本历史记录界面显示版本变更内容。解决用户无法了解当前版本详情、无法对比新旧版本差异等问题，帮助用户全面了解当前系统状态，辅助版本管理和诊断。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名                | 类型                                       | 必填   | 说明              |
| ------------------ | ---------------------------------------- | ---- | --------------- |
| descriptionOptions | [DescriptionOptions](#descriptionoptions) | 是    | 描述文件选项，用于指定描述文件的格式和语言。详见DescriptionOptions定义。 |
| callback           | AsyncCallback\<Array\<[ComponentDescription](#componentdescription)>> | 是    | 回调函数，用于接收当前版本描述信息。回调参数包括： err(错误对象，成功时为null)和info(当前版本描述信息数组，包含版本说明内容)。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

```ts
// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: "zh-cn" // 中文
};

try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取当前版本描述信息
  onlineUpdater.getCurrentVersionDescription(descriptionOptions, (currentDescriptionError, info) => {
    if (currentDescriptionError) {
      console.error(`getCurrentVersionDescription error: ${JSON.stringify(currentDescriptionError)}`);
      return;
    }
    console.info(`getCurrentVersionDescription info ${JSON.stringify(info)}`);
    console.info(`getCurrentVersionDescription err ${JSON.stringify(currentDescriptionError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getCurrentVersionDescription

getCurrentVersionDescription(descriptionOptions: DescriptionOptions): Promise\<Array\<ComponentDescription>>

获取当前版本描述信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。获取成功后，返回当前版本描述信息数组，包含版本说明内容，可用于版本信息展示、版本状态确认、版本对比分析等用途。使用Promise异步回调。

使用场景：适用于需要向用户展示当前版本详情、确认当前系统版本状态、对比新旧版本差异等场景。典型场景在设备信息界面展示当前版本的更新说明、在版本历史记录界面显示版本变更内容。解决用户无法了解当前版本详情、无法对比新旧版本差异等问题，帮助用户全面了解当前系统状态，辅助版本管理和诊断。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名                | 类型                                       | 必填   | 说明     |
| ------------------ | ---------------------------------------- | ---- | ------ |
| descriptionOptions | [DescriptionOptions](#descriptionoptions) | 是    | 描述文件选项，用于指定描述文件的格式和语言。对象包含format（描述文件格式，可选STANDARD或SIMPLIFIED）和language（语言代码，如'zh-cn'）字段。 |

**返回值**：

| 类型                                       | 说明                   |
| ---------------------------------------- | -------------------- |
| Promise\<Array\<[ComponentDescription](#componentdescription)>> | Promise对象。成功时resolve返回当前版本描述信息数组，用于展示当前版本详情和版本对比；失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: "zh-cn" // 中文
};
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取当前版本描述信息
  onlineUpdater.getCurrentVersionDescription(descriptionOptions).then((info: Array<update.ComponentDescription>) => {
    console.info(`getCurrentVersionDescription promise info ${JSON.stringify(info)}`);
  }).catch((descriptionError: BusinessError) => {
    console.error(`getCurrentVersionDescription promise error ${JSON.stringify(descriptionError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getTaskInfo

getTaskInfo(callback: AsyncCallback\<TaskInfo>): void

获取升级任务信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。获取成功后，返回升级任务信息对象，包含任务是否存在、任务状态、进度等信息。帮助开发者实时掌握升级进度、及时发现异常状态、优化升级策略，提升升级流程的可控性和成功率。使用callback异步回调。

使用场景：适用于实时掌握升级进度、监控任务状态、及时发现异常等场景。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名      | 类型                                    | 必填   | 说明               |
| -------- | ------------------------------------- | ---- | ---------------- |
| callback | AsyncCallback\<[TaskInfo](#taskinfo)> | 是    | 回调函数，用于接收升级任务信息。回调参数包括： err（错误对象，成功时为null）和taskInfo（升级任务信息对象，包含existTask和taskBody字段）。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取升级任务信息，通过回调函数接收任务状态 
  onlineUpdater.getTaskInfo((taskInfoError: BusinessError, taskInfo: update.TaskInfo) => {
    if (taskInfoError) {
      console.error(`getTaskInfo error: ${JSON.stringify(taskInfoError)}`);
      return;
    }
    console.info(`getTaskInfo existTask= ${taskInfo?.existTask}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getTaskInfo

getTaskInfo(): Promise\<TaskInfo>

获取升级任务信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。获取成功后，返回升级任务信息对象，包含任务是否存在、任务状态、进度等信息。帮助开发者实时掌握升级进度、及时发现异常状态、优化升级策略，提升升级流程的可控性和成功率。使用Promise异步回调。

使用场景：适用于实时掌握升级进度、监控任务状态、及时发现异常等场景。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**返回值**：

| 类型                              | 说明                  |
| ------------------------------- | ------------------- |
| Promise\<[TaskInfo](#taskinfo)> | Promise对象。成功时resolve返回升级任务信息对象，用于查询和监控升级任务状态；失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  onlineUpdater.getTaskInfo().then((info: update.TaskInfo) => {
    console.info(`getTaskInfo existTask= ${info.existTask}`);
  }).catch((taskInfoError: BusinessError) => {
    console.error(`getTaskInfo promise error ${JSON.stringify(taskInfoError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### download

download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions, callback: AsyncCallback\<void>): void

下载升级包到设备本地存储。支持进度监听与暂停/恢复控制，帮助用户高效完成升级包获取，节省带宽与时间，提升升级成功率。使用callback异步回调。

使用场景：适用于OTA客户端在线升级、后台自动下载升级包、网络中断后断点续传等场景。

**调用顺序说明**：

- 必须先调用checkNewVersion检查是否有新版本，并获取版本摘要信息。
- 只有当checkNewVersion返回isExistNewVersion为true时，才能调用本方法下载升级包。
- 如果isExistNewVersion为false，表示无新版本，调用本方法会失败。

**相关方法**：

- checkNewVersion()：检查新版本（前置方法）。
- resumeDownload()：恢复下载（暂停后使用）。
- pauseDownload()：暂停下载（下载中使用）。
- upgrade()：安装升级包（下载完成后使用）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名               | 类型                                      | 必填   | 说明                                 |
| ----------------- | --------------------------------------- | ---- | ---------------------------------- |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。|
| downloadOptions   | [DownloadOptions](#downloadoptions)     | 是    | 下载选项，用于控制下载行为。详见DownloadOptions定义。 |
| callback          | AsyncCallback\<void>                    | 是    | 回调函数。当下载成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);


  onlineUpdater.download(versionDigestInfo, downloadOptions, (downloadError: BusinessError) => {
    console.info(`download error ${JSON.stringify(downloadError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### download

download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions): Promise\<void>

下载升级包到设备本地存储。支持进度监听与暂停/恢复控制，帮助用户高效完成升级包获取，节省带宽与时间，提升升级成功率。使用Promise异步回调。

使用场景：适用于OTA客户端在线升级、后台自动下载升级包、网络中断后断点续传等场景。

**调用顺序说明**：

- 必须先调用checkNewVersion检查是否有新版本，并获取版本摘要信息。
- 只有当checkNewVersion返回isExistNewVersion为true时，才能调用本方法下载升级包。
- 如果isExistNewVersion为false，表示无新版本，调用本方法会失败。

**相关方法**：

- checkNewVersion()：检查新版本（前置方法）。
- resumeDownload()：恢复下载（暂停后使用）。
- pauseDownload()：暂停下载（下载中使用）。
- upgrade()：安装升级包（下载完成后使用）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名               | 类型                                      | 必填   | 说明     |
| ----------------- | --------------------------------------- | ---- | ------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。 |
| downloadOptions   | [DownloadOptions](#downloadoptions)     | 是    | 下载选项，用于控制下载行为。详见DownloadOptions定义。 |

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  onlineUpdater.download(versionDigestInfo, downloadOptions).then(() => {
    console.info(`download start`);
  }).catch((downloadError: BusinessError) => {
    console.error(`download error ${JSON.stringify(downloadError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### resumeDownload

resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions, callback: AsyncCallback\<void>): void

恢复已暂停的升级包下载任务，避免重复下载已完成的进度部分。使用callback异步回调。

使用场景：适用于网络中断后断点续传、用户暂停后主动恢复、后台下载任务恢复等场景。

**配对调用说明**：

- 与pauseDownload()成对使用，用于控制下载流程的暂停和恢复 。
- 必须在调用pauseDownload()暂停下载后才能调用此方法恢复下载。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名                   | 类型                                       | 必填   | 说明                                   |
| --------------------- | ---------------------------------------- | ---- | ------------------------------------ |
| versionDigestInfo     | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。 |
| resumeDownloadOptions | [ResumeDownloadOptions](#resumedownloadoptions) | 是    | 恢复下载选项，用于指定恢复下载的网络类型。详见ResumeDownloadOptions定义。 |
| callback              | AsyncCallback\<void>                     | 是    | 回调函数，用于接收恢复下载结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  onlineUpdater.resumeDownload(versionDigestInfo, resumeDownloadOptions,
    (resumeDownloadError: BusinessError) => {
    console.info(`resumeDownload error ${JSON.stringify(resumeDownloadError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### resumeDownload

resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions): Promise\<void>

恢复已暂停的升级包下载任务，避免重复下载已完成的进度部分。使用Promise异步回调。

使用场景：适用于网络中断后断点续传、用户暂停后主动恢复、后台下载任务恢复等场景。

**配对调用说明**：

- 与pauseDownload()成对使用，用于控制下载流程的暂停和恢复 。
- 必须在调用pauseDownload()暂停下载后才能调用此方法恢复下载。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名                   | 类型                                       | 必填   | 说明     |
| --------------------- | ---------------------------------------- | ---- | ------ |
| versionDigestInfo     | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。|
| resumeDownloadOptions | [ResumeDownloadOptions](#resumedownloadoptions) | 是    | 恢复下载选项，用于指定恢复下载的网络类型。详见ResumeDownloadOptions定义。 |

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  onlineUpdater.resumeDownload(versionDigestInfo, resumeDownloadOptions).then(() => {
    console.info(`resumeDownload start`);
  }).catch((resumeDownloadError: BusinessError) => {
    console.error(`resumeDownload error ${JSON.stringify(resumeDownloadError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### pauseDownload

pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions, callback: AsyncCallback\<void>): void

暂停下载新版本。前提条件是仅当当前有正在进行的下载任务时可调用本方法暂停下载，暂停后需调用resumeDownload()恢复下载，恢复完成后才可调用upgrade()安装。使用callback异步回调。

使用场景：适用于用户主动暂停下载、网络环境不佳时暂停下载以节省流量、需要在特定时间段下载等场景。解决用户无法控制下载时机、无法节省网络流量等问题，帮助用户灵活控制下载进度，节省带宽资源，提升用户体验。

**配对调用说明**：

- 与resumeDownload()成对使用，用于控制下载流程的暂停和恢复。暂停下载后可调用resumeDownload()恢复下载，完成暂停和恢复的流程控制。

**状态转换说明**：

- 暂停后可调用resumeDownload()恢复下载。
- 暂停后可通过getTaskInfo()查询当前任务状态。
- 暂停后不能直接调用upgrade()安装，必须先恢复下载完成后再安装。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名                  | 类型                                       | 必填   | 说明                                   |
| -------------------- | ---------------------------------------- | ---- | ------------------------------------ |
| versionDigestInfo    | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。|
| pauseDownloadOptions | [PauseDownloadOptions](#pausedownloadoptions) | 是    | 暂停下载选项，用于控制暂停行为。详见PauseDownloadOptions定义。 |
| callback | AsyncCallback\<void> | 是 | 回调函数，用于接收暂停下载结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 暂停下载升级包，通过回调函数处理暂停结果 
  onlineUpdater.pauseDownload(versionDigestInfo, pauseDownloadOptions,
    (pauseDownloadError: BusinessError) => {
    console.info(`pauseDownload error ${JSON.stringify(pauseDownloadError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### pauseDownload

pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions): Promise\<void>

暂停下载新版本。前提条件是仅当当前有正在进行的下载任务时可调用本方法暂停下载，暂停后需调用resumeDownload()恢复下载，恢复完成后才可调用upgrade()安装。使用Promise异步回调。

使用场景：适用于用户主动暂停下载、网络环境不佳时暂停下载以节省流量、需要在特定时间段下载等场景。解决用户无法控制下载时机、无法节省网络流量等问题，帮助用户灵活控制下载进度，节省带宽资源，提升用户体验。

**配对调用说明**：

- 与resumeDownload()成对使用，用于控制下载流程的暂停和恢复。暂停下载后可调用resumeDownload()恢复下载，完成暂停和恢复的流程控制。

**状态转换说明**：

- 暂停后可调用resumeDownload()恢复下载。
- 暂停后可通过getTaskInfo()查询当前任务状态。
- 暂停后不能直接调用upgrade()安装，必须先恢复下载完成后再安装。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名                  | 类型                                       | 必填   | 说明     |
| -------------------- | ---------------------------------------- | ---- | ------ |
| versionDigestInfo    | [VersionDigestInfo](#versiondigestinfo)  | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。 |
| pauseDownloadOptions | [PauseDownloadOptions](#pausedownloadoptions) | 是    | 暂停下载选项，用于控制暂停行为。详见PauseDownloadOptions定义。 |

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 暂停下载升级包
  onlineUpdater.pauseDownload(versionDigestInfo, pauseDownloadOptions).then(() => {
    console.info(`pauseDownload`);
  }).catch((pauseDownloadError: BusinessError) => {
    console.error(`pauseDownload error ${JSON.stringify(pauseDownloadError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### upgrade

upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions, callback: AsyncCallback\<void>): void

升级新版本，执行安装升级包操作。调用成功后，系统开始安装升级包并准备重启以应用新版本。使用callback异步回调。

使用场景：适用于升级包下载完成，需要安装新版本的场景。解决无法完成系统升级、无法应用新版本等问题，帮助用户完成系统版本更新，获取新功能和性能优化，提升系统稳定性和安全性。

**依赖说明**：
本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。

**调用顺序**：

- 必须先调用checkNewVersion检查是否有新版本，调用download下载升级包并完成下载后，才能调用本方法执行升级安装操作。

**状态转换说明**：

- 应在下载完成后调用此方法安装升级包。
- 安装过程中可通过terminateUpgrade()终止升级。
- 安装完成后设备将重启以应用新版本。

**失败处理**：

当upgrade方法执行失败（状态为UPGRADE_FAIL）时，必须调用clearError清除异常状态后才能重新开始升级流程。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名               | 类型                                      | 必填   | 说明                                   |
| ----------------- | --------------------------------------- | ---- | ------------------------------------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。|
| upgradeOptions    | [UpgradeOptions](#upgradeoptions)       | 是    | 升级选项，用于指定升级操作类型。详见UpgradeOptions定义。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 安装升级包，通过回调函数处理安装结果
  onlineUpdater.upgrade(versionDigestInfo, upgradeOptions, (upgradeError: BusinessError) => {
    console.info(`upgrade error ${JSON.stringify(upgradeError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### upgrade

upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions): Promise\<void>

升级新版本，执行安装升级包操作。调用成功后，系统开始安装升级包并准备重启以应用新版本。使用Promise异步回调。

使用场景：适用于升级包下载完成，需要安装新版本的场景。解决无法完成系统升级、无法应用新版本等问题，帮助用户完成系统版本更新，获取新功能和性能优化，提升系统稳定性和安全性。

**依赖说明**：

本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。

**调用顺序**：

必须先调用checkNewVersion检查是否有新版本，调用download下载升级包并完成下载后，才能调用本方法执行升级安装操作。

**状态转换说明**：

- 应在下载完成后调用此方法安装升级包。
- 安装过程中可通过terminateUpgrade()终止升级。
- 安装完成后设备将重启以应用新版本。

**失败处理**：

当upgrade方法执行失败（状态为UPGRADE_FAIL）时，必须调用clearError清除异常状态后才能重新开始升级流程。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名               | 类型                                      | 必填   | 说明     |
| ----------------- | --------------------------------------- | ---- | ------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。 |
| upgradeOptions    | [UpgradeOptions](#upgradeoptions)       | 是    | 升级选项，用于指定升级操作类型。详见UpgradeOptions定义。 |

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 安装升级包
  onlineUpdater.upgrade(versionDigestInfo, upgradeOptions).then(() => {
    console.info(`upgrade start`);
  }).catch((upgradeError: BusinessError) => {
    console.error(`upgrade error ${JSON.stringify(upgradeError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### clearError

clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions, callback: AsyncCallback\<void>): void

清除异常状态。版本下载或安装失败时，删除已下载的升级包文件，清除错误状态记录。调用成功后，异常状态被清除，升级任务恢复到初始状态，可以重新开始完整的升级流程，从checkNewVersion检查版本步骤开始。使用callback异步回调。

使用场景：适用于升级失败后清除异常、重新开始升级等场景。

**约束条件**：

- 当upgrade方法执行失败（状态为UPGRADE_FAIL）时，必须调用clearError清除异常状态。
- 未调用clearError清除异常状态时，无法重新开始升级流程。
- 清除异常后，可以从checkNewVersion重新开始升级流程。

**相关方法**：

- upgrade()：安装升级包（失败后需调用clearError）。
- checkNewVersion()：重新检查版本（清除异常后调用）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名               | 类型                                      | 必填   | 说明                                   |
| ----------------- | --------------------------------------- | ---- | ------------------------------------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。|
| clearOptions      | [ClearOptions](#clearoptions)           | 是    | 清除选项，用于指定要清除的异常状态类型。详见ClearOptions定义。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 清除异常状态，通过回调函数处理清除结果
  onlineUpdater.clearError(versionDigestInfo, clearOptions, (clearFailError: BusinessError) => {
    console.info(`clearError error ${JSON.stringify(clearFailError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### clearError

clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions): Promise\<void>

清除异常状态。版本下载或安装失败时，删除已下载的升级包文件，清除错误状态记录。调用成功后，异常状态被清除，升级任务恢复到初始状态，可以重新开始完整的升级流程，从checkNewVersion检查版本步骤开始。使用Promise异步回调。

使用场景：适用于升级失败后清除异常、重新开始升级等场景。

**约束关系**：

- 当upgrade方法执行失败（状态为UPGRADE_FAIL）时，必须调用clearError清除异常状态。
- 未调用clearError清除异常状态时，无法重新开始升级流程。
- 清除异常后，可以从checkNewVersion重新开始升级流程。

**相关方法**：

- upgrade()：安装升级包（失败后需调用clearError）。
- checkNewVersion()：重新检查版本（清除异常后调用）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名               | 类型                                      | 必填   | 说明     |
| ----------------- | --------------------------------------- | ---- | ------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo) | 是    | 版本摘要信息，从版本检查结果(checkNewVersion)中获取，用于标识具体版本。详见VersionDigestInfo定义。|
| clearOptions      | [ClearOptions](#clearoptions)           | 是    | 清除选项，用于指定要清除的异常状态类型。详见ClearOptions定义。 |

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

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
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 清除异常状态 
  onlineUpdater.clearError(versionDigestInfo, clearOptions).then(() => {
    console.info(`clearFailError success`);
  }).catch((clearFailError: BusinessError) => {
    console.error(`clearError error ${JSON.stringify(clearFailError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getUpgradePolicy

getUpgradePolicy(callback: AsyncCallback\<UpgradePolicy>): void

获取升级策略信息。获取成功后，返回升级策略信息对象，包含自动下载策略、自动升级策略、升级时间段等配置。使用callback异步回调。

使用场景：适用于需要查询当前系统的升级策略配置，了解自动下载、自动升级的规则和时间段限制，或修改策略前先获取当前配置的场景。

解决无法了解升级策略配置、无法查询自动升级规则等问题，帮助用户掌握系统升级行为，为策略调整提供依据。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名      | 类型                                       | 必填   | 说明              |
| -------- | ---------------------------------------- | ---- | --------------- |
| callback | AsyncCallback\<[UpgradePolicy](#upgradepolicy)> | 是    | 回调函数，用于接收升级策略信息。回调参数包括： err（错误对象，成功时为null）和policy（升级策略信息对象，包含downloadStrategy、autoUpgradeStrategy和autoUpgradePeriods字段）。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取升级策略，通过回调函数接收策略配置
  onlineUpdater.getUpgradePolicy((upgradePolicyError: BusinessError, policy: update.UpgradePolicy) => {
    if (upgradePolicyError) {
      console.error(`getUpgradePolicy error: ${JSON.stringify(upgradePolicyError)}`);
      return;
    }
    console.info(`policy downloadStrategy = ${policy?.downloadStrategy}`);
    console.info(`policy autoUpgradeStrategy = ${policy?.autoUpgradeStrategy}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### getUpgradePolicy

getUpgradePolicy(): Promise\<UpgradePolicy>

获取升级策略信息。获取成功后，返回升级策略信息对象，包含自动下载策略、自动升级策略、升级时间段等配置。使用Promise异步回调。

使用场景：适用于需要查询当前系统的升级策略配置，了解自动下载、自动升级的规则和时间段限制，或修改策略前先获取当前配置的场景。

解决无法了解升级策略配置、无法查询自动升级规则等问题，帮助用户掌握系统升级行为，为策略调整提供依据。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**返回值**：

| 类型                                       | 说明                    |
| ---------------------------------------- | --------------------- |
| Promise\<[UpgradePolicy](#upgradepolicy)> | Promise对象。成功时resolve返回升级策略信息对象，用于查询自动下载、自动升级、升级时间段等策略配置；失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取升级策略
  onlineUpdater.getUpgradePolicy().then((policy: update.UpgradePolicy) => {
    console.info(`policy downloadStrategy = ${policy.downloadStrategy}`);
    console.info(`policy autoUpgradeStrategy = ${policy.autoUpgradeStrategy}`);
  }).catch((upgradePolicyError: BusinessError) => {
    console.error(`getUpgradePolicy promise error ${JSON.stringify(upgradePolicyError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### setUpgradePolicy

setUpgradePolicy(policy: UpgradePolicy, callback: AsyncCallback\<void>): void

设置升级策略，用于控制升级行为。调用成功后，新的升级策略立即生效，系统将根据策略控制自动下载、自动升级及时间段限制。使用callback异步回调。

使用场景：适用于企业设备管理、限制升级时段、控制自动下载等场景。解决无法自定义升级策略、无法控制升级时机等问题，帮助用户灵活配置升级行为，满足企业管理和个性化需求。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名      | 类型                              | 必填   | 说明            |
| -------- | ------------------------------- | ---- | ------------- |
| policy   | [UpgradePolicy](#upgradepolicy) | 是    | 升级策略对象，用于控制升级行为。包含自动下载策略、自动升级策略、升级时间段等配置。详见UpgradePolicy定义。 |
| callback | AsyncCallback<void> | 是 | 回调函数。当设置升级策略成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const upgradePolicy: update.UpgradePolicy = {
  downloadStrategy: false, // 禁止自动下载 
  autoUpgradeStrategy: false, // 禁止自动升级
  autoUpgradePeriods: [{ start: 120, end: 240 }] // 自动升级时间段，用分钟表示
};
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 设置升级策略，通过回调函数处理设置结果 
  onlineUpdater.setUpgradePolicy(upgradePolicy, (upgradePolicyError: BusinessError) => {
    console.info(`setUpgradePolicy result: ${upgradePolicyError}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### setUpgradePolicy

setUpgradePolicy(policy: UpgradePolicy): Promise\<void>

设置升级策略，用于控制升级行为。调用成功后，新的升级策略立即生效，系统将根据策略控制自动下载、自动升级及时间段限制。使用Promise异步回调。

使用场景：适用于企业设备管理、限制升级时段、控制自动下载等场景。解决无法自定义升级策略、无法控制升级时机等问题，帮助用户灵活配置升级行为，满足企业管理和个性化需求。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名    | 类型                              | 必填   | 说明   |
| ------ | ------------------------------- | ---- | ---- |
| policy | [UpgradePolicy](#upgradepolicy) | 是    | 升级策略对象，用于控制升级行为。包含自动下载策略、自动升级策略、升级时间段等配置。详见UpgradePolicy定义。|

**返回值**：

| 类型             | 说明                  |
| -------------- | ------------------- |
| Promise\<void> | Promise对象。成功时resolve表示升级策略设置成功，无返回结果；失败时reject返回错误信息。|

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const upgradePolicy: update.UpgradePolicy = {
  downloadStrategy: false, // 禁止自动下载 
  autoUpgradeStrategy: false, // 禁止自动升级
  autoUpgradePeriods: [{ start: 120, end: 240 }] // 自动升级时间段，用分钟表示
};
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 设置升级策略 
  onlineUpdater.setUpgradePolicy(upgradePolicy).then(() => {
    console.info(`setUpgradePolicy success`);
  }).catch((upgradePolicyError: BusinessError) => {
    console.error(`setUpgradePolicy promise error ${JSON.stringify(upgradePolicyError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### terminateUpgrade

terminateUpgrade(callback: AsyncCallback\<void>): void

终止当前升级任务, 取消正在进行的安装操作。调用成功后，任务状态变更为已取消。使用callback异步回调。

使用场景：适用于用户主动取消升级或紧急停止升级的场景。解决用户无法中止升级、无法紧急停止升级等问题，帮助用户灵活控制升级流程，避免不必要升级或紧急情况下的风险。

**状态转换说明**：

- 仅在下载或安装过程中可以调用此方法终止升级。
- 终止后任务状态变更为已取消。
- 终止后可通过getTaskInfo查询当前任务状态。
- 终止后如需重新升级，建议调用clearError清除异常状态后重新开始。

**相关方法**：

- download()/upgrade()：可被终止的方法。
- getTaskInfo()：查询任务状态。
- clearError()：清除异常状态（终止后如需重新升级）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名      | 类型                   | 必填   | 说明                                     |
| -------- | -------------------- | ---- | -------------------------------------- |
| callback | AsyncCallback\<void> | 是 | 回调函数，用于接收终止升级结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 终止升级任务，通过回调函数处理终止结果
  onlineUpdater.terminateUpgrade((terminateUpgradeError: BusinessError) => {
    console.info(`terminateUpgrade error ${JSON.stringify(terminateUpgradeError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### terminateUpgrade

terminateUpgrade(): Promise\<void>

终止当前升级任务, 取消正在进行的安装操作。调用成功后，任务状态变更为已取消。使用Promise异步回调。

使用场景：适用于用户主动取消升级或紧急停止升级的场景。解决用户无法中止升级、无法紧急停止升级等问题，帮助用户灵活控制升级流程，避免不必要升级或紧急情况下的风险。

**状态转换说明**：

- 仅在下载或安装过程中可以调用此方法终止升级。
- 终止后任务状态变更为已取消。
- 终止后可通过getTaskInfo查询当前任务状态。
- 终止后如需重新升级，建议调用clearError清除异常状态后重新开始。

**相关方法**：

- download()/upgrade()：可被终止的方法。
- getTaskInfo()：查询任务状态。
- clearError()：清除异常状态（终止后如需重新升级）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 终止升级任务
  onlineUpdater.terminateUpgrade().then(() => {
    console.info(`terminateUpgrade success`);
  }).catch((terminateUpgradeError: BusinessError) => {
    console.error(`terminateUpgrade error ${JSON.stringify(terminateUpgradeError)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### on

on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void

注册事件监听，用于实时监控升级状态。注册成功后监听对应类型的升级事件，事件发生时通过回调函数传递事件信息，包括事件ID、任务状态、进度等。

使用场景：适用于实时监控升级进度、跟踪下载状态变化、获取升级结果通知等场景。

**配对调用**：

- 调用on()注册监听后，必须在不再需要监听时调用off()取消监听。
- 未调用off()取消监听会导致内存泄漏，影响系统性能。
- 建议在升级流程结束后或页面销毁时调用off()。

**使用建议**：

- 在调用download、upgrade等长时间操作前注册监听。
- 在操作完成或收到最终事件（如EVENT_DOWNLOAD_SUCCESS、EVENT_UPGRADE_SUCCESS）后取消监听。

**相关方法**：

- off()：取消事件监听（配对方法）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**参数**：

| 参数名               | 类型                                       | 必填   | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |
| eventClassifyInfo | [EventClassifyInfo](#eventclassifyinfo)  | 是    | 事件信息，用于指定要监听的升级事件类型。详见EventClassifyInfo定义。 |
| taskCallback | [UpgradeTaskCallback](#upgradetaskcallback) | 是    | 事件回调，用于处理升级任务事件。回调签名：(eventInfo: EventInfo) => void，其中eventInfo为事件信息对象，包含eventId（事件ID）和taskBody（任务数据）字段。|

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例**：

```ts
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 订阅升级更新事件
  extraInfo: "" // 额外信息，此处为空表示无额外信息
};
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  onlineUpdater.on(eventClassifyInfo, (eventInfo: update.EventInfo) => {
    console.info(`updater on ${JSON.stringify(eventInfo)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

### off

off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void

取消注册事件监听。调用成功后，对应类型的升级事件监听被取消，不再接收该类型的事件通知，避免内存泄漏。

使用场景：适用于升级流程结束、不再需要监听升级事件等场景。

**配对调用说明**：

- 与on()配对使用，用于取消已注册的事件监听。
- 必须在已通过on()注册监听后，才能调用本方法取消监听。
- 建议在升级流程结束后或页面销毁时调用，及时释放资源。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**参数**：

| 参数名               | 类型                                       | 必填   | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |
| eventClassifyInfo | [EventClassifyInfo](#eventclassifyinfo)  | 是    | 事件信息，包含事件类型，用于指定要取消监听的升级事件类型。对象包含eventClassify(事件类型)和extraInfo(额外信息)字段，需根据监听的类型构造。注意事项：通常传入空字符串即可（表示无额外信息）。当需要传递自定义扩展数据或业务标识时，可传入非空字符串。 |
| taskCallback | [UpgradeTaskCallback](#upgradetaskcallback) | 否    | 事件回调。用于处理升级任务事件。回调签名：(eventInfo: EventInfo) => void，其中eventInfo为事件信息对象，包含eventId（事件ID）和taskBody（任务数据）字段。当需要取消特定回调监听时传入此参数，不传入时取消该事件类型的所有监听。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例**：

```ts
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 订阅升级更新事件
  extraInfo: ""
};
try {
  // 创建升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: "com.ohos.ota.updateclient",  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  onlineUpdater.off(eventClassifyInfo, (eventInfo: update.EventInfo) => {
    console.info(`onlineUpdater off ${JSON.stringify(eventInfo)}`);
  });
} catch(error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}
```

## Restorer

提供清除用户数据分区、深度清除用户数据和操作系统分区、同步清除文件密钥等恢复出厂设置功能的工具类。

> **恢复出厂设置流程**：

- 调用getRestorer方法获取Restorer对象。
- 根据需求选择恢复出厂方式：
  1. factoryReset：普通恢复出厂，仅清除用户数据分区。
  2. forceFactoryReset：强制恢复出厂，清除用户数据分区并同步清除文件密钥。
  3. deepFactoryReset：深度恢复出厂，深度清除用户数据分区和操作系统分区。
- 调用相应的恢复出厂方法执行恢复出厂操作，设备将清除数据并恢复到出厂状态。

**设计逻辑**：

三种方式的清除范围和安全级别依次递增，应根据具体场景选择：

- 常规场景使用factoryReset。
- 敏感数据场景使用forceFactoryReset。
- 安全销毁场景使用deepFactoryReset。

### factoryReset

factoryReset(callback: AsyncCallback\<void>): void

清除用户数据分区，删除用户安装的应用、用户文件和个人设置，恢复设备出厂状态。使用callback异步回调。

使用场景：适用于系统恢复出厂、用户选择恢复出厂设置等场景。

**约束和限制**：

- 操作不可逆，将永久删除用户数据，需提前提醒用户备份重要数据。
- 需要系统权限ohos.permission.FACTORY_RESET。
- 操作过程中设备会自动重启，应用需做好状态保存。
- 建议仅在用户明确确认后执行恢复出厂操作。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.FACTORY_RESET

**参数**：

| 参数名      | 类型                   | 必填   | 说明                                     |
| -------- | -------------------- | ---- | -------------------------------------- |
| callback | AsyncCallback\<void> | 是 | 回调函数，用于接收恢复出厂结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  factoryRestorer.factoryReset((factoryResetError) => {
    if (factoryResetError) {
      console.error(`factoryReset error: ${JSON.stringify(factoryResetError)}`);
      return;
    }
    console.info(`factoryReset error ${JSON.stringify(factoryResetError)}`);
  });
} catch(error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```

### factoryReset

factoryReset(): Promise\<void>

清除用户数据分区，删除用户安装的应用、用户文件和个人设置，恢复设备出厂状态。使用Promise异步回调。

使用场景：适用于系统恢复出厂、用户选择恢复出厂设置等场景。

**约束和限制**：

- 操作不可逆，将永久删除用户数据，需提前提醒用户备份重要数据。
- 需要系统权限ohos.permission.FACTORY_RESET。
- 操作过程中设备会自动重启，应用需做好状态保存。
- 建议仅在用户明确确认后执行恢复出厂操作。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.FACTORY_RESET

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  factoryRestorer.factoryReset().then(() => {
    console.info(`factoryReset success`);
  }).catch((resetError: BusinessError) => {
    console.error(`factoryReset error ${JSON.stringify(resetError)}`);
  });
} catch(error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```

### forceFactoryReset<sup>23+</sup>

forceFactoryReset(): Promise\<void>

清除用户数据分区，同步清除文件密钥（用于加密用户数据的密钥），删除用户安装的应用、用户文件，恢复设备出厂状态。调用成功后，系统立即执行强制恢复出厂流程：清除用户数据分区 → 同步清除文件加密密钥 → 清除系统缓存和临时文件 → 设备自动重启恢复到出厂初始状态。使用Promise异步回调。

使用场景：用于需要彻底清除敏感数据、设备交接前清除数据等安全场景。

**原理说明**：

该方法与factoryReset的区别在于同步清除文件密钥。文件密钥用于加密用户数据，即使数据被删除，密钥仍可能残留。forceFactoryReset通过同步清除密钥，确保加密数据无法被恢复，实现更彻底的数据清除，适用于安全销毁场景。

**约束和限制**：

- 操作不可逆，将永久删除所有用户数据和加密密钥，无法恢复。
- 需要特殊系统权限ohos.permission.FORCE_FACTORY_RESET。
- 执行前必须明确提醒用户备份重要数据并确认操作。
- 适用于敏感数据销毁、设备交接等高安全场景。
- 操作过程中设备会立即重启，应用需提前做好状态保存。

**起始版本**： 从API version 23开始支持。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.FORCE_FACTORY_RESET

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  factoryRestorer.forceFactoryReset().then(() => {
    console.info(`forceFactoryReset success`);
  }).catch((forceResetError: BusinessError) => {
    console.error(`forceFactoryReset error ${JSON.stringify(forceResetError)}`);
  });
} catch(error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```

### deepFactoryReset<sup>26+</sup>

deepFactoryReset(factoryResetStrategy: FactoryResetStrategy): Promise\<void>

通过覆盖等方式，深度清除用户数据分区、操作系统分区，彻底销毁数据，恢复设备出厂状态。调用成功后，系统执行深度恢复出厂流程：根据策略确定清除范围 → 对数据分区执行多次覆盖写入 → 销毁操作系统分区关键数据 → 验证数据销毁完整性 → 设备自动重启恢复到出厂初始状态。深度清除通过物理覆盖方式确保数据无法被任何工具恢复。使用Promise异步回调。

使用场景：适用于设备丢失，需要彻底销毁数据的场景。

**原理说明**：

该方法提供最高安全级别的数据清除。与factoryReset（仅清除数据分区）和forceFactoryReset（清除数据分区和密钥）不同，deepFactoryReset通过多次覆盖写入（如多次写入随机数据）物理销毁数据，防止数据恢复工具提取残留数据。清除范围可配置：DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据和操作系统分区。

**约束和限制**：

- 数据销毁不可逆，无法通过任何技术手段恢复，执行前必须获得用户明确授权。
- 需要系统权限ohos.permission.FACTORY_RESET。
- 深度清除耗时较长（可能数小时），必须确保设备电量充足（建议电量>50%）。
- 仅可在Stage模型下使用。
- 适用于设备报废、高安全销毁等极端场景，不建议普通恢复出厂场景使用。
- 执行前必须明确告知用户操作后果并获得确认。
- 建议先调用getDeepFactoryResetInfo查询预计耗时，向用户提示等待时长。

**起始版本**： 从API version 26开始支持。

**模型约束**： 此接口仅可在Stage模型（OpenHarmony应用开发模型，详见[Stage模型开发指导](../../../application-dev/application-models/stage-model-development-overview.md)）下使用。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**：ohos.permission.FACTORY_RESET

**参数**：

| 参数名                | 类型                                       | 必填   | 说明             |
| ------------------ | ---------------------------------------- | ---- | -------------- |
| factoryResetStrategy | [FactoryResetStrategy](#factoryresetstrategy) | 是 | 恢复出厂设置策略，包含scope（重置范围）和strategy（重置策略描述）字段。<br>**前提条件**：<br>- 执行前必须备份重要数据并告知用户操作后果。<br>- 建议先调用getDeepFactoryResetInfo预估耗时。<br>- 确保设备电量充足（建议电量>50%）。<br>- 仅可在Stage模型下使用。<br>scope（重置范围，取值原则：DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据分区和操作系统分区）用于指定恢复出厂的范围。<br>strategy（重置策略描述，取值原则：为重置操作的自定义描述文本，如'quick erase'或'deep erase'，用于标识重置原因或场景）用于记录重置操作信息。|


**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  // 创建恢复出厂设置策略对象
  let factoryResetStrategy: update.FactoryResetStrategy = {
    scope: update.FactoryResetScope.DATA, // 重置范围为用户数据
    strategy: "deepFactoryReset test" // 重置范围描述
  };
  factoryRestorer.deepFactoryReset(factoryResetStrategy).then(() => {
    console.info(`deepFactoryReset success`);
  }).catch((deepResetError: BusinessError) => {
    console.error(`deepFactoryReset error ${JSON.stringify(deepResetError)}`);
  });
} catch(error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```

### getDeepFactoryResetInfo<sup>26+</sup>

getDeepFactoryResetInfo(factoryResetStrategy: FactoryResetStrategy): Promise\<FactoryResetInfo>

获取深度恢复出厂设置信息，用于预估恢复操作耗时。调用此方法后，系统根据清除范围（DATA或DATA_AND_OS）和设备存储容量计算深度清除所需时间，返回包含预计持续时间的FactoryResetInfo对象。使用Promise异步回调。

使用场景：适用于执行深度恢复出厂前向用户提示等待时长、规划操作时间、确保电量充足等场景。

**原理说明**：

该方法通过分析清除范围和存储介质特性计算耗时。深度清除通过多次覆盖写入销毁数据，耗时与清除范围成正比：DATA仅清除用户数据分区耗时较短，DATA_AND_OS清除用户数据和操作系统分区耗时较长。系统根据存储容量、覆盖次数、写入速度等因素计算预计时间。

**约束和限制**：

- 仅可在Stage模型下使用。
- 需要系统权限ohos.permission.FACTORY_RESET。
- 返回的时间为预估值，实际耗时可能因设备状态略有差异。
- 建议在电量低于预估耗时所需电量时不执行深度恢复。
- 必须在执行deepFactoryReset前调用，帮助用户做好时间和电量准备。

**起始版本**： 从API version 26开始支持。

**模型约束**： 此接口仅可在Stage模型下使用。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.FACTORY_RESET

**参数**：

| 参数名                | 类型                                       | 必填   | 说明             |
| ------------------ | ---------------------------------------- | ---- | -------------- |
| factoryResetStrategy  | [FactoryResetStrategy](#factoryresetstrategy)  | 是 | 恢复出厂设置策略，包含scope(重置范围)和strategy(重置策略描述)字段。<br>scope用于指定恢复出厂的范围，取值原则:DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据分区和操作系统分区。<br>strategy用于记录重置操作信息，取值原则：为重置操作的自定义描述文本，用于标识重置原因或场景。 |

**返回值**：

| 类型                              | 说明                  |
| ------------------------------- | ------------------- |
| Promise\<[FactoryResetInfo](#factoryresetinfo)> | Promise对象。成功时resolve返回深度恢复出厂设置信息对象，包含预计耗时等；失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// 创建恢复出厂设置策略对象
  let factoryResetStrategy: update.FactoryResetStrategy = {
    scope: update.FactoryResetScope.DATA, // 重置范围为用户数据 
    strategy: "getDeepFactoryResetInfo test" // 重置范围描述
  };
try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  factoryRestorer.getDeepFactoryResetInfo(factoryResetStrategy).then((deepResetInfo: update.FactoryResetInfo) => {
    console.info(`getDeepFactoryResetInfo success`);
  }).catch((resetInfoError: BusinessError) => {
    console.error(`getDeepFactoryResetInfo promise error ${JSON.stringify(resetInfoError)}`);
  });
} catch(error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}
```

## LocalUpdater

提供校验本地升级包签名和完整性、安装本地升级包、监听本地升级事件等本地固件更新功能的工具类。

**本地升级流程**：

1. 开发者调用getLocalUpdater方法获取LocalUpdater对象。 
2. 用户准备本地升级包文件和对应的证书文件，确保文件已放置在可访问的存储路径。 
3. 开发者调用verifyUpgradePackage方法校验升级包的数字签名、文件完整性和版本兼容性。 
4. 校验通过后，开发者调用applyNewVersion安装升级包，设备将重启以应用新版本。 
5. 开发者调用on方法注册事件监听，实时监控安装进度和状态变化。

**实现机制**：

- 校验机制：验证升级包是否为官方发布且未被篡改，检查签名、完整性和版本兼容性。
- 安装机制：解压并写入升级包内容到系统分区，准备重启应用新版本。
- 安全保证：必须先校验升级包，确保来源可信后方可安装。

### verifyUpgradePackage

verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback\<void>): void

校验升级包的数字签名、文件完整性和版本兼容性，验证升级包是否为官方发布且未被篡改。调用成功且校验通过后，升级包被视为可信，可用于后续安装；若校验失败，将返回错误信息并阻止安装。使用callback异步回调。

使用场景：适用于用户从本地存储设备获取升级包、需要验证升级包来源可信的场景，以及确保升级包完整性、防止恶意升级包攻击等安全场景。

**调用顺序说明：**

 - 必须先调用verifyUpgradePackage校验升级包并校验通过后，才能调用applyNewVersion安装升级包。
 - 未校验直接调用applyNewVersion会导致安装失败，可能造成系统损坏。
 - 校验通过后的升级包可用于后续安装流程。

**相关方法：**

- applyNewVersion()：安装升级包（校验通过后调用）。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名         | 类型                          | 必填   | 说明               |
| ----------- | --------------------------- | ---- | ---------------- |
| upgradeFile | [UpgradeFile](#upgradefile) | 是    | 升级文件，包含文件类型和文件路径，用于指定要校验的本地升级包。详见UpgradeFile定义。 |
| certsFile   | string                      | 是    | 证书文件路径，用于校验升级包签名。支持绝对路径或相对路径。 |
| callback    | AsyncCallback\<void> | 是 | 回调函数，用于接收校验结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

```ts
const upgradeFile: update.UpgradeFile = {
  fileType: update.ComponentType.OTA, // OTA包
  filePath: "/data/local/tmp/updater.zip" // 本地升级包路径，用户需从设备厂商官网或官方渠道下载升级包文件，放置到设备可访问的存储路径，（如/data/local/tmp/updater.zip）
};

// certsFile为证书文件路径，需从设备厂商官网下载并放置到设备可访问路径 
const certsFile = "/path/to/certificate.cert"; // 证书文件路径，从厂商官网下载

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  localUpdater.verifyUpgradePackage(upgradeFile, certsFile, (verifyUpgradePackageError) => {
    if (verifyUpgradePackageError) {
      console.error(`verifyUpgradePackage error: ${JSON.stringify(verifyUpgradePackageError)}`);
      return;
    }
    console.info(`verifyUpgradePackage error ${JSON.stringify(verifyUpgradePackageError)}`);
  });
} catch(error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

### verifyUpgradePackage

verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise\<void>

校验升级包的数字签名、文件完整性和版本兼容性，验证升级包是否为官方发布且未被篡改。调用成功且校验通过后，升级包被视为可信，可用于后续安装；若校验失败，将返回错误信息并阻止安装。使用Promise异步回调。

使用场景：适用于用户从本地存储设备获取升级包、需要验证升级包来源可信的场景，以及确保升级包完整性、防止恶意升级包攻击等安全场景。

**调用顺序说明：**

 - 必须先调用verifyUpgradePackage校验升级包并校验通过后，才能调用applyNewVersion安装升级包。
 - 未校验直接调用applyNewVersion会导致安装失败，可能造成系统损坏。
 - 校验通过后的升级包可用于后续安装流程。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名         | 类型                          | 必填   | 说明     |
| ----------- | --------------------------- | ---- | ------ |
| upgradeFile | [UpgradeFile](#upgradefile) | 是    | 升级文件，包含文件类型和文件路径，用于指定要校验的本地升级包。详见UpgradeFile定义。 |
| certsFile   | string                      | 是    | 证书文件路径，用于校验升级包签名。支持绝对路径或相对路径。 |

**返回值**：

| 类型             | 说明                     |
| -------------- | ---------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const upgradeFile: update.UpgradeFile = {
  fileType: update.ComponentType.OTA, // OTA包
  filePath: "/data/local/tmp/updater.zip" // 本地升级包路径，用户需从设备厂商官网或官方渠道下载升级包文件，放置到设备可访问的存储路径，（如/data/local/tmp/updater.zip）
};

// certsFile为证书文件路径，需从设备厂商官网下载并放置到设备可访问路径 
const certsFile = "/path/to/certificate.cert"; // 证书文件路径，从厂商官网下载

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  localUpdater.verifyUpgradePackage(upgradeFile, certsFile).then(() => {
    console.info(`verifyUpgradePackage success`);
  }).catch((verifyUpgradePackageError: BusinessError) => {
    console.error(`verifyUpgradePackage error ${JSON.stringify(verifyUpgradePackageError)}`);
  });
} catch(error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

### applyNewVersion

applyNewVersion(upgradeFiles: Array\<UpgradeFile>, callback: AsyncCallback\<void>): void

安装升级包。使用callback异步回调。

调用顺序说明：

- 必须先调用verifyUpgradePackage校验升级包并校验通过后，才能调用本方法安装升级包。
- 调用成功后，系统将解压并写入升级包内容到系统分区，准备重启以应用新版本，可通过监听事件跟踪安装进度。
- 通过安装升级包可以完成系统版本更新。

使用场景：适用于从本地存储设备(如SD卡)进行系统升级、完成本地升级流程的场景。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名         | 类型                                 | 必填   | 说明                                      |
| ----------- | ---------------------------------- | ---- | --------------------------------------- |
| upgradeFiles | Array\<[UpgradeFile](#upgradefile)> | 是    | 升级文件数组，用于指定要安装的本地升级包列表。每个元素包含fileType(文件类型)和filePath(文件路径)字段。详见UpgradeFile定义。|
| callback    | AsyncCallback\<void> | 是 | 回调函数，用于接收安装升级包结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

```ts
const upgradeFiles: Array<update.UpgradeFile> = [{
  fileType: update.ComponentType.OTA, // OTA包
  filePath: "/data/local/tmp/updater.zip" // 本地升级包路径，用户需从设备厂商官网或官方渠道下载升级包文件，放置到设备可访问的存储路径，（如/data/local/tmp/updater.zip）
}];

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  localUpdater.applyNewVersion(upgradeFiles, (applyNewVersionError) => {
    if (applyNewVersionError) {
      console.error(`applyNewVersion error: ${JSON.stringify(applyNewVersionError)}`);
      return;
    }
    console.info(`applyNewVersion error ${JSON.stringify(applyNewVersionError)}`);
  });
} catch(error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

### applyNewVersion

applyNewVersion(upgradeFiles: Array\<UpgradeFile>): Promise\<void>

安装升级包。使用Promise异步回调。

调用顺序说明：

- 必须先调用verifyUpgradePackage校验升级包并校验通过后，才能调用本方法安装升级包。
- 调用成功后，系统将解压并写入升级包内容到系统分区，准备重启以应用新版本，可通过监听事件跟踪安装进度。
- 通过安装升级包可以完成系统版本更新。

使用场景：适用于从本地存储设备(如SD卡)进行系统升级、完成本地升级流程的场景。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名         | 类型                                 | 必填   | 说明                                      |
| ----------- | ---------------------------------- | ---- | --------------------------------------- |
| upgradeFiles | Array\<[UpgradeFile](#upgradefile)> | 是    | 升级文件数组，用于指定要安装的本地升级包列表。每个元素包含fileType(文件类型)和filePath(文件路径)字段。详见UpgradeFile定义。|

**返回值**：

| 类型             | 说明                         |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[升级错误码](errorcode-update.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 201      | Permission denied.       |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 401      | Parameter verification failed.    |
| 11500104 | IPC error.               |

**示例**：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

const upgradeFiles: Array<update.UpgradeFile> = [{
  fileType: update.ComponentType.OTA, // OTA包
  filePath: "/data/local/tmp/updater.zip" // 本地升级包路径，用户需从设备厂商官网或官方渠道下载升级包文件，放置到设备可访问的存储路径，（如/data/local/tmp/updater.zip）
}];

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  localUpdater.applyNewVersion(upgradeFiles).then(() => {
    console.info(`applyNewVersion success`);
  }).catch((applyNewVersionError: BusinessError) => {
    console.error(`applyNewVersion error ${JSON.stringify(applyNewVersionError)}`);
  });
} catch(error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

### on

on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void

注册事件监听，用于实时监控升级状态。调用成功后，监听对应类型的升级事件，事件发生时通过回调函数传递事件信息，包括事件ID、任务状态、进度等。解决无法实时了解升级进度、无法及时发现升级异常等问题。通过事件监听可以实时获取升级进度和状态变化，及时发现升级异常并处理，提升用户体验和升级流程的可控性。

使用场景：适用于实时监控升级进度、跟踪下载状态变化、获取升级结果通知等场景。

**配对调用**：

- 调用on()注册监听后，必须在不再需要监听时调用off()取消监听。
- 未调用off()取消监听会导致内存泄漏，影响系统性能。
- 建议在升级流程结束后或页面销毁时调用off()。

**使用建议**：

- 在调用applyNewVersion等长时间操作前注册监听。
- 在操作完成或收到最终事件后取消监听。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名               | 类型                                       | 必填   | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |
| eventClassifyInfo | [EventClassifyInfo](#eventclassifyinfo)  | 是    | 事件信息，用于指定要监听的升级事件类型。详见EventClassifyInfo定义。 |
| taskCallback | [UpgradeTaskCallback](#upgradetaskcallback) | 是    | 事件回调，用于接收升级任务事件通知。回调签名：(eventInfo: EventInfo) => void，其中eventInfo为事件信息对象，包含eventId（事件ID）和taskBody（任务数据）字段。|

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例**：

```ts
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 订阅升级更新事件
  extraInfo: ""
};
// 定义任务更新回调函数，用于处理升级任务事件
let onTaskUpdate: update.UpgradeTaskCallback = (eventInfo: update.EventInfo) => {
  console.info(`on eventInfo id `, eventInfo.eventId);
};

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  localUpdater.on(eventClassifyInfo, onTaskUpdate);
} catch(error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

### off

off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void

取消注册事件监听。调用成功后，不再接收对应类型的升级事件通知，避免内存泄漏。

使用场景：适用于本地升级流程结束、不再需要监听升级事件等场景。

**配对调用说明**：

- 与on()配对使用，用于取消已注册的事件监听。
- 须在已通过on()注册监听后，才能调用本方法取消监听。
- 建议在升级流程结束后或页面销毁时调用，及时释放资源。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

**需要权限**： ohos.permission.UPDATE_SYSTEM

**参数**：

| 参数名               | 类型                                       | 必填   | 说明   |
| ----------------- | ---------------------------------------- | ---- | ---- |
| eventClassifyInfo | [EventClassifyInfo](#eventclassifyinfo)  | 是   | 事件信息对象，用于指定要取消监听的升级事件类型。详见EventClassifyInfo定义。 |
| taskCallback | [UpgradeTaskCallback](#upgradetaskcallback) | 否    | 事件回调，用于取消指定回调监听。回调签名：(eventInfo: EventInfo) => void，其中eventInfo为事件信息对象，包含eventId和taskBody字段。当需要取消特定回调监听时传入此参数，不传入时取消该事件类型的所有监听。 |

**错误码**：

以下的错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID       | 错误信息                                                  |
| -------  | ---------------------------------------------------- |
| 202      | Permission verification failed. A non-system application calls a system API. |

**示例**：

```ts
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 订阅升级更新事件
  extraInfo: ""
};
// 定义任务更新回调函数，用于处理升级任务事件
let onTaskUpdate: update.UpgradeTaskCallback = (eventInfo: update.EventInfo) => {
  console.info(`on eventInfo id `, eventInfo.eventId);
};

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  localUpdater.off(eventClassifyInfo, onTaskUpdate);
} catch(error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}
```

## UpgradeInfo

升级信息。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| upgradeApp   | string                        | 只读:否, 可选:否 | 调用方包名，用于标识调用此升级接口的应用身份。格式为com.xxx.xxx.xxx，由点号分隔的多段组成。长度范围1-255字符，每段长度范围1-64字符，仅支持字母、数字和点号。每段必须以字母开头，不能包含连续点号或以点号开头结尾。超出范围或格式错误时抛出异常。|
| businessType | [BusinessType](#businesstype) | 只读:否, 可选:否 | 升级业务类型。 |

## BusinessType

升级业务类型。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| vendor  | [BusinessVendor](#businessvendor)   | 只读:否, 可选:否 | 供应商类型，用于标识升级包的来源厂商。<br>使用场景：系统根据供应商类型选择对应的升级包管理服务器和验证策略。<br>可选值：PUBLIC(开源厂商，适用于开源版本的升级场景)。<br>建议根据实际升级包来源选择对应类型，开源版本升级时使用PUBLIC。 |
| subType | [BusinessSubType](#businesssubtype) | 只读:否, 可选:否 | 升级类型，用于指定升级的目标对象。<br>使用场景：系统根据升级类型选择相应的升级包和升级流程。<br>可选值：FIRMWARE(固件升级，用于升级系统固件而非应用)。<br>建议：系统固件升级场景使用FIRMWARE，应用升级场景使用其他类型。 |

## CheckResult

版本检查结果。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| ----------------- | --------------------------------- | ------------ | ------ |
| isExistNewVersion | boolean                              | 只读:否, 可选:否 | 是否有新版本。true表示有新版本，false表示没有新版本。|
| newVersionInfo    | [NewVersionInfo](#newversioninfo) | 只读:否, 可选:否 | 新版本数据。 |

## NewVersionInfo

新版本数据。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| ----------------- | ---------------------------------------- | --------- |---- |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo)  | 只读:否, 可选:否 | 版本摘要。 |
| versionComponents | Array\<[VersionComponent](#versioncomponent)> | 只读:否, 可选:否 | 版本组件。 |

## VersionDigestInfo

版本摘要。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| versionDigest | string | 只读:否, 可选:否 | 版本摘要。长度范围1-128字符，从版本检查结果中获取，用于标识具体版本。 |

## VersionComponent

版本组件。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| componentId     | string                              | 只读:否, 可选:否 | 组件标识，用于唯一标识升级包中的组件。从版本检查结果的versionComponents数组中获取，用于后续描述信息查询或组件信息展示等场景。 |
| componentType   | [ComponentType](#componenttype)     | 只读:否, 可选:否 | 组件类型。不同设备类型的支持情况可能不同。OTA升级包在A/B分区设备（指拥有两个系统分区用于无缝升级的设备）和非A/B分区设备上的使用方式有差异：A/B分区设备支持无缝升级（升级过程中设备仍可使用），非A/B分区设备升级时需重启设备。可通过getCurrentVersionInfo接口查询设备版本信息判断设备类型。 |
| upgradeAction   | [UpgradeAction](#upgradeaction)     | 只读:否, 可选:否 | 升级方式。用于指定升级包的应用方式。详见UpgradeAction定义。|
| displayVersion  | string                              | 只读:否, 可选:否 | 显示版本号。    |
| innerVersion    | string                              | 只读:否, 可选:否 | 版本号。      |
| size            | int                              | 只读:否, 可选:否 | 升级包大小，单位为B，取值范围[0, +∞]。超出范围时抛出异常。 |
| effectiveMode   | [EffectiveMode](#effectivemode)     | 只读:否, 可选:否 | 生效模式，用于指定升级生效的方式。详见EffectiveMode定义。 |
| otaMode | [OtaMode<sup>20+</sup>](#otamode20)                 | 只读:否, 可选:是 | 升级模式。详见OtaMode定义。 |

## DescriptionOptions

描述文件选项，用于指定描述文件的格式和语言。对象包含format(描述文件格式，可选STANDARD或SIMPLIFIED)和language(语言代码，如'zh-cn')字段。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| format   | [DescriptionFormat](#descriptionformat) | 只读:否, 可选:否 | 描述文件格式。取值原则：STANDARD适合需要完整描述信息的场景，SIMPLIFIED适合仅需精简描述信息的场景。 |
| language | string                                  | 只读:否, 可选:否 | 描述文件语言，格式如'zh-cn'(中文)、'en-us'(英文)、'ja-jp'(日文)等，长度范围2-10字符，有效字符包括字母（区分大小写）和连字符（-），建议使用小写格式。超出范围或包含无效字符时抛出异常。 |

## ComponentDescription

组件描述文件。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| componentId     | string                              | 只读:否, 可选:否 | 组件标识，用于唯一标识升级包中的组件。<br>使用场景：在获取版本描述信息(getNewVersionDescription)时需要传入componentId以获取对应组件的描述内容;在展示版本详情时可通过componentId区分不同组件。<br>获取方式：从版本检查结果的versionComponents数组中获取对应组件的componentId字段。 |
| descriptionInfo | [DescriptionInfo](#descriptioninfo) | 只读:否, 可选:否 | 描述文件信息。 |

## DescriptionInfo

版本描述文件信息。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| descriptionType | [DescriptionType](#descriptiontype) | 只读:否, 可选:否 | 描述文件类型，用于指定描述信息的表现形式。CONTENT表示直接提供描述文本内容，适用于描述内容较短或需要即时展示的场景；URI表示提供描述内容的链接地址，适用于描述内容较长或需要从外部资源获取的场景。应根据描述内容长度和展示方式选择。 |
| content         | string                              | 只读:否, 可选:否 | 描述文件内容。 |

## CurrentVersionInfo

当前版本信息。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| osVersion         | string                                   | 只读:否, 可选:否 | 系统版本号。 |
| deviceName        | string                                   | 只读:否, 可选:否 | 设备名。   |
| versionComponents | Array\<[VersionComponent](#versioncomponent)> | 只读:否, 可选:否 | 版本组件。  |

## DownloadOptions

下载选项，包含allowNetwork(允许下载的网络类型)和order(升级指令)字段，用于控制下载行为。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| allowNetwork | [NetType](#nettype) | 只读:否, 可选:否 | 网络类型，允许下载的网络类型。设置CELLULAR仅允许数据网络下载，设置WIFI仅允许WIFI下载，设置CELLULAR_AND_WIFI允许两者均可下载。 |
| order        | [Order](#order)     | 只读:否, 可选:否 | 升级指令。用于控制升级操作的执行方式，指定是仅下载、仅安装还是下载并安装升级包。 |

## ResumeDownloadOptions

恢复下载选项，用于指定恢复下载的网络类型。对象包含allowNetwork字段，用于设置允许下载的网络类型。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| allowNetwork | [NetType](#nettype)                    | 只读:否, 可选:否 | 网络类型，允许下载的网络类型。设置CELLULAR仅允许数据网络下载，设置WIFI仅允许WIFI网络下载，设置CELLULAR_AND_WIFI允许两者均可下载。 |

## PauseDownloadOptions

暂停下载选项，用于控制暂停行为。对象包含isAllowAutoResume字段，true表示允许自动恢复，false表示需手动恢复。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| isAllowAutoResume | boolean | 只读:否, 可选:否 | 是否允许自动恢复。<br>true表示允许自动恢复，系统可能自动恢复下载；false表示不允许，需手动调用resumeDownload恢复。 |

## UpgradeOptions

升级选项，包含升级指令等配置，用于指定升级操作类型。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | --------- | -------- |
| order | [Order](#order) | 只读:否, 可选:否 | 升级指令。用于指定升级操作的执行方式。取值原则：DOWNLOAD仅下载升级包，适用于需要先下载后手动安装的场景；INSTALL仅安装已下载的升级包，适用于已下载完成需直接安装的场景；DOWNLOAD_AND_INSTALL下载并安装，适用于完整升级流程；APPLY仅生效，适用于已安装需重启生效的场景；INSTALL_AND_APPLY安装并生效，适用于安装后立即重启生效的场景。应根据当前升级状态和业务需求选择合适的指令。 |

## ClearOptions

清除异常选项，用于指定要清除的异常状态类型。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | -------------- | -------- |
| status | [UpgradeStatus](#upgradestatus) | 只读:否, 可选:否 | 异常状态，用于指定要清除的状态。<br>使用场景：当升级失败(状态为UPGRADE_FAIL)后，系统会保留异常状态阻止重新升级，此时需要调用clearError传入status参数清除异常状态，使系统恢复到初始状态以便重新开始升级流程。<br>常用值：UPGRADE_FAIL(升级失败状态)。注意事项：仅支持清除UPGRADE_FAIL状态。 |

## UpgradePolicy

升级策略，用于控制升级行为。

### 升级策略详细说明

- **downloadStrategy**： 自动下载策略。
- **autoUpgradeStrategy**： 自动升级策略。
- **autoUpgradePeriods**： 自动升级时间段。

需根据实际需求构造对象。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | ------------------- | -------- |
| downloadStrategy    | boolean                        | 只读:否, 可选:否 | 自动下载策略。 <br>true表示可自动下载，false表示不可自动下载。 |
| autoUpgradeStrategy | boolean                        | 只读:否, 可选:否 | 自动升级策略。 <br>true表示可自动升级，false表示不可自动升级。 |
| autoUpgradePeriods  | Array\<[UpgradePeriod](#upgradeperiod)> | 只读:否, 可选:是 | 自动升级时间段，当需要在特定时间段内自动升级时传入此参数(如夜间时段)，此参数为可选参数。不传入此参数时，表示不限制自动升级时间段，可在任意时间自动升级。 |

## UpgradePeriod

升级时间段。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称              | 类型                              | 属性         | 说明   |
| --------------- | ----------------------------------- | ------------------- | -------- |
| start | int | 只读:否, 可选:否 | 开始时间,取值范围[0, 1440],单位为min。表示一天中的分钟数,0表示00:00,1440表示24:00。超出范围时抛出异常。 |
| end   | int | 只读:否, 可选:否 | 结束时间,取值范围[0, 1440],单位为min。表示一天中的分钟数,0表示00:00,1440表示24:00。超出范围时抛出异常。 |

## TaskInfo

任务信息。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| existTask |  boolean                  | 只读:否, 可选:否 | 是否存在升级任务，用于判断当前是否有进行中的升级任务。<br>使用场景：在执行升级操作前查询任务状态，避免重复操作;在升级流程中监控任务状态变化。true表示存在进行中的升级任务(如下载或安装任务)，需要等待任务完成或取消后再执行新任务。false表示当前无任务，可以开始新的升级流程。 |
| taskBody  | [TaskBody](#taskbody) | 只读:否, 可选:否 | 任务数据。   |

## EventInfo

事件信息对象，用于接收升级事件通知时传递的事件详情。包含eventId(事件ID，标识具体事件类型)和taskBody(任务数据，包含任务状态和进度)字段。

使用场景：在注册事件监听(on方法)后，事件发生时回调函数会接收到EventInfo对象，通过解析eventId和taskBody可获知升级任务的实时状态和进度，用于实时监控升级流程。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| eventId  | [EventId](#eventid)   | 只读:否, 可选:否 | 事件ID，用于标识具体的升级事件类型。通过eventId可判断当前发生的具体事件(如EVENT_DOWNLOAD_START表示开始下载、EVENT_UPGRADE_SUCCESS表示升级成功等)，从而采取相应处理。<br>常见事件类型包括下载事件(EVENT_DOWNLOAD_START等)、升级事件(EVENT_UPGRADE_START等)、完成事件(EVENT_UPGRADE_SUCCESS、EVENT_UPGRADE_FAIL)。建议在事件回调中根据eventId执行不同的业务逻辑。 |
| taskBody | [TaskBody](#taskbody) | 只读:否, 可选:否 | 任务数据。 |

## TaskBody

任务数据。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| versionDigestInfo | [VersionDigestInfo](#versiondigestinfo)  | 只读:否, 可选:否 | 版本摘要。 |
| status            | [UpgradeStatus](#upgradestatus)          | 只读:否, 可选:否 | 升级状态。用于标识升级任务的当前执行阶段。包含下载状态（WAITING_DOWNLOAD到DOWNLOAD_FAIL）、安装状态（WAITING_INSTALL到UPDATING）和最终结果（UPGRADE_SUCCESS或UPGRADE_FAIL），用于任务状态监控、进度展示和异常处理等场景。 |
| subStatus         | int                                   | 只读:否, 可选:否 | 子状态，取值范围参考[UpgradeStatus](#upgradestatus)状态码。  |
| progress          | int                                   | 只读:否, 可选:否 | 进度，单位为%，取值范围[0, 100]，超出范围时抛出异常。 |
| installMode       | int                                   | 只读:否, 可选:否 | 安装模式，用于控制升级安装的执行时机。取值范围{0, 1, 2}。0为正常升级，适用于用户主动触发升级的场景；1为夜间升级，适用于设置夜间时段（如22:00-06:00等用户设定的时段）自动升级的场景（避免打扰用户）；2为自动升级，适用于系统自动检测并执行升级的场景。应根据升级策略和用户体验需求选择。超出范围时抛出异常。 |
| errorMessages     | Array\<[ErrorMessage](#errormessage)>    | 只读:否, 可选:否 | 错误信息。 |
| versionComponents | Array\<[VersionComponent](#versioncomponent)> | 只读:否, 可选:否 | 版本组件。 |

## ErrorMessage

错误信息。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| errorCode    | int | 只读:否, 可选:否 | 错误码，用于标识具体的错误类型。通过errorCode可快速定位升级失败的原因(如权限错误201、参数错误401、IPC错误11500104等)，从而采取针对性的处理措施。<br>使用场景：在升级失败事件(EVENT_UPGRADE_FAIL)回调中，通过errorCode判断失败原因，进行相应的错误处理或提示用户。建议结合errorMessage进行详细的错误分析和处理。 |
| errorMessage | string | 只读:否, 可选:否 | 错误描述文本，用于提供错误的详细说明信息。errorMessage提供了错误的具体描述(如'Permission denied'、'Parameter verification failed'等)，帮助开发者理解错误原因和进行调试。<br>使用场景：在错误处理时，可将errorMessage用于日志记录、错误提示展示或错误分析。建议结合errorCode一起使用，errorCode提供错误类型，errorMessage提供详细说明。|

## EventClassifyInfo

事件信息。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| eventClassify | [EventClassify](#eventclassify) | 只读:否, 可选:否 | 事件类型，用于指定要监听的事件分类。可取值：TASK（任务事件）。 |
| extraInfo     | string                          | 只读:否, 可选:是 | 额外信息，用于传递扩展数据。默认值为空字符串，表示无额外信息。当需要传递自定义扩展数据或业务标识时，可传入非空字符串，用于事件监听的精细化匹配或业务扩展场景。 |

## UpgradeFile

升级文件，包含文件类型和文件路径，用于指定要安装的本地升级包。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| fileType | [ComponentType](#componenttype) | 只读:否, 可选:否 | 文件类型，用于指定升级包类型。可选值：OTA（OTA升级包）。 |
| filePath | string                          | 只读:否, 可选:否 | 文件路径，支持绝对路径或相对路径。取值原则：路径长度范围1-255字符，文件必须为有效的升级包文件格式。超出范围时抛出异常。 |

## FactoryResetStrategy

恢复出厂设置策略，包含scope(重置范围)和strategy(重置策略描述)字段。

**起始版本**： 从API version 26开始支持。

**模型约束**： 此接口仅可在Stage模型下使用。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| scope | [FactoryResetScope](#factoryresetscope) | 只读:否, 可选:否 | 重置范围。DATA仅清除用户数据分区；DATA_AND_OS同时清除用户数据分区和操作系统分区，恢复更彻底。 |
| strategy | string                          | 只读:否, 可选:否 | 重置策略，用于记录重置操作的具体策略信息。为重置操作的自定义描述文本，如quick erase表示快速擦除、deep erase表示深度擦除等。使用场景：在执行深度恢复出厂设置时填写此字段，用于标识重置操作的原因（如设备报废、数据销毁）或擦除方式，便于后续审计和追踪。 |

## FactoryResetInfo

恢复出厂设置信息。

**起始版本**： 从API version 26开始支持。

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称       | 类型                            | 属性 | 说明   |
| ------------ | ----------------------------- | -------- | ------ |
| duration | int                          | 只读: 否, 可选: 否 | 恢复出厂设置所需持续时间。单位为min。取值范围[0, +∞]。|

## FactoryResetScope

恢复出厂设置范围。

**起始版本**： 从API version 26开始支持。

**模型约束**：此接口仅可在Stage模型下使用。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称           | 值  | 说明   |
| ------------- | ---- | ---- |
| DATA | 1    | 用户数据。|
| DATA_AND_OS | 2    | 用户数据和操作系统。|

## UpgradeTaskCallback

type UpgradeTaskCallback = (eventInfo: EventInfo) => void

事件回调。

**起始版本**： 从API version 23开始支持。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称        | 类型                    | 必填   | 说明   |
| --------- | ----------------------- | ---- | ---- |
| eventInfo | [EventInfo](#eventinfo) | 是    | 事件信息，包含eventId（事件ID）和taskBody（任务数据）字段。 |

## BusinessVendor

设备厂家。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称    | 值      | 说明   |
| ------ | -------- | ---- |
| PUBLIC | "public" | 开源。表示供应商类型为开源厂商，适用于开源版本的升级场景。 |

## BusinessSubType

升级类型。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称      | 值  | 说明   |
| -------- | ---- | ---- |
| FIRMWARE | 1    | 固件。表示升级类型为固件升级，用于升级系统固件而非应用。 |

## ComponentType

组件类型。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称  | 值  | 说明   |
| ---- | ---- | ---- |
| OTA  | 1    | OTA升级包，用于固件升级的完整升级包文件。 |

## UpgradeAction

升级方式。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称      | 值        | 说明   |
| -------- | ---------- | ---- |
| UPGRADE  | "upgrade"  | 差分包，仅包含与当前版本的差异部分，适用于已安装基础版本的增量升级场景。 |
| RECOVERY | "recovery" | 修复包，用于修复系统异常或恢复系统功能的特殊升级包，适用于系统故障修复场景。 |

## EffectiveMode

生效模式。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称           | 值  | 说明   |
| ------------- | ---- | ---- |
| COLD          | 1    | 冷升级，需重启设备生效，适用于需要完整系统重置或固件升级的场景。  |
| LIVE          | 2    | 热升级，无需重启即可生效，适用于应用层组件升级或需要保持设备运行的场景。 |
| LIVE_AND_COLD | 3    | 融合升级，结合两者特性，适用于同时包含热升级和冷升级组件的场景。 |

## OtaMode<sup>20+</sup>

升级模式。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称           | 值  | 说明   |
| ------------- | ---- | ---- |
| REGULAR_OTA   | 0    | 正常升级，先下载完整升级包到本地，再执行安装升级，适用于大多数常规升级场景。 |
| STREAM_OTA    | 1    | 流式升级，边下载边升级，无需等待完整下载，适用于存储空间受限或需要快速升级的场景。 |
| AB_REGULAR_OTA | 2    | AB正常升级，适用于A/B分区设备。 |
| AB_STREAM_OTA  | 3    | AB流式升级，适用于A/B分区设备。 |

## DescriptionType

描述文件类型。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称     | 值  | 说明   |
| ------- | ---- | ---- |
| CONTENT | 0    | 内容。表示直接提供描述文本内容，适用于描述内容较短或需要即时展示的场景。 |
| URI     | 1    | 链接。表示提供描述内容的链接地址，适用于描述内容较长或需要从外部资源获取的场景。 |

## DescriptionFormat

描述文件格式。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称        | 值  | 说明   |
| ---------- | ---- | ---- |
| STANDARD   | 0    | 标准格式。适合需要完整描述信息的场景。 |
| SIMPLIFIED | 1    | 简易格式。适合仅需精简描述信息的场景。 |

## NetType

网络类型，用于指定下载的网络类型。设置CELLULAR仅允许数据网络下载，设置WIFI仅允许WIFI下载，设置CELLULAR_AND_WIFI允许两者均可下载。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称               | 值  | 说明        |
| ----------------- | ---- | --------- |
| CELLULAR          | 1    | 数据网络。      |
| METERED_WIFI      | 2    | 热点WIFI。    |
| NOT_METERED_WIFI  | 4    | 非热点WIFI。   |
| WIFI              | 6    | WIFI。      |
| CELLULAR_AND_WIFI | 7    | 数据网络和WIFI。 |

## Order

升级指令。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称                  | 值  | 说明    |
| -------------------- | ---- | ----- |
| DOWNLOAD             | 1    | 下载。适合仅下载升级包场景。 |
| INSTALL              | 2    | 安装。适合直接安装已下载的升级包场景。 |
| DOWNLOAD_AND_INSTALL | 3    | 下载并安装。适合下载并安装场景。 |
| APPLY                | 4    | 生效。    |
| INSTALL_AND_APPLY    | 6    | 安装并生效，执行安装后设备将重启以应用新版本。 |

## UpgradeStatus

升级状态。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

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

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

| 名称   | 值        | 说明   |
| ---- | ---------- | ---- |
| TASK | 0x01000000 | 任务事件。 |

## EventId

事件ID。

**系统接口**： 此接口为系统接口。

**系统能力**： SystemCapability.Update.UpdateService

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
