# Updater（系统接口）

提供在线检查新版本、下载升级包、安装升级包、管理升级策略、获取版本信息等系统在线更新功能的工具类。

使用场景：设备厂商OTA升级客户端应用、在线系统升级、自动版本检查和升级管理。

**收益说明**：

支持用户及时获取系统更新，提升升级效率和用户体验，降低用户操作成本，支持自动版本检查、后台下载、断点续传等功能。

**实现机制**：

- 版本检查：向升级包管理服务器查询新版本信息。  
- 下载管理：支持网络类型选择、暂停/恢复下载、断点续传。  
- 安装机制：升级包下载完成后解压并写入系统分区，准备重启应用。  
- 状态管理：维护升级任务状态，支持查询任务信息、清除异常状态、终止升级。

**起始版本：** 9

<!--Device-update-export interface Updater--><!--Device-update-export interface Updater-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## checkNewVersion

```TypeScript
checkNewVersion(callback: AsyncCallback<CheckResult>): void
```

检查新版本信息，返回是否有新版本、新版本号、版本摘要信息等。

调用成功后返回版本检查结果对象，可用于判断是否需要升级，为后续下载、升级等操作提供版本标识。使用callback异步回调。

本方法是在线升级流程的起始方法，返回的版本摘要信息是后续方法的必要参数。

调用本方法后，后续可调用以下方法：getNewVersionInfo（获取新版本详细信息）、download（下载升级包）、upgrade（安装升级包）。

这些后续方法均需传入本方法返回的versionDigestInfo参数，且仅当isExistNewVersion为true时可调用。

当isExistNewVersion为false时表示已是最新版本，无需执行后续升级操作。

使用场景：需要快速检查是否有新版本并获取版本摘要。支持用户及时了解系统更新状态，为升级决策提供依据。

**原理说明**：

该方法向设备厂商部署的升级包管理服务器发起版本检查请求，携带设备当前版本信息、设备型号等参数。服务器根据请求参数查询是否有适配该设备的更新版本，返回版本检查结果对象（CheckResult），包含isExistNewVersion标志位、newVersionInfo结构体（版本摘要、版本号等）。

检查流程包括：开发者构造请求参数 → 系统发起HTTP请求 → 服务器查询版本信息 → 系统解析响应 → 系统返回结果。

**约束和限制**：

- 本方法依赖设备厂商部署的升级包管理服务器，需确保服务器正常部署且可访问。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-checkNewVersion(callback: AsyncCallback<CheckResult>): void--><!--Device-Updater-checkNewVersion(callback: AsyncCallback<CheckResult>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;CheckResult&gt; | 是 | 回调函数，用于接收版本检查结果。回调参数包括err（错误对象，成功时为null）和checkResult（版本检查结果对象）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 检查新版本，通过回调函数获取检查结果
  onlineUpdater.checkNewVersion((checkNewVersionError: BusinessError,  
    checkResult: update.CheckResult) => {
      // 错误处理
      if (checkNewVersionError) {
        console.error(`checkNewVersion error, code:${checkNewVersionError.code}, message:${checkNewVersionError.message}.`);
        return;
      }
      console.info(`checkNewVersion isExistNewVersion  ${checkResult?.isExistNewVersion}`);
    });
} catch (error) {
  let errInfo: BusinessError = error as BusinessError;
  console.error(`Failed to get updater. Code: ${errInfo.code}, message: ${errInfo.message}.`);
}

```

## checkNewVersion

```TypeScript
checkNewVersion(): Promise<CheckResult>
```

检查新版本信息，返回是否有新版本、新版本号、版本摘要信息等。

调用成功后返回版本检查结果对象，可用于判断是否需要升级，为后续下载、升级等操作提供版本标识。使用Promise异步回调。

本方法是在线升级流程的起始方法，返回的版本摘要信息是后续方法的必要参数。

调用本方法后，后续可调用以下方法：getNewVersionInfo（获取新版本详细信息）、download（下载升级包）、upgrade（安装升级包）。

这些后续方法均需传入本方法返回的versionDigestInfo参数，且仅当isExistNewVersion为true时可调用。

当isExistNewVersion为false时表示已是最新版本，无需执行后续升级操作。

使用场景：需要快速检查是否有新版本并获取版本摘要。帮助用户及时了解系统更新状态，为升级决策提供依据。

**原理说明**：

本方法提供在线升级功能，依赖设备厂商部署的升级包管理服务器。该方法向设备厂商部署的升级包管理服务器发起版本检查请求，携带设备当前版本信息、设备型号等参数。服务器根据请求参数查询是否有适配该设备的更新版本，返回版本检查结果对象（CheckResult），包含isExistNewVersion标志位、newVersionInfo结构体（版本摘要、版本号等）。

检查流程包括：构造请求参数 → 发起HTTP请求 → 服务器查询 → 解析响应 → 返回结果。

**约束和限制**：

- 本方法依赖设备厂商部署的升级包管理服务器，需确保服务器正常部署且可访问。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-checkNewVersion(): Promise<CheckResult>--><!--Device-Updater-checkNewVersion(): Promise<CheckResult>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CheckResult&gt; | Promise对象。成功时resolve返回版本检查结果对象，失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 检查新版本
  onlineUpdater.checkNewVersion().then((result: update.CheckResult) => {
    console.info(`checkNewVersion isExistNewVersion: ${result.isExistNewVersion}`);
    // 版本摘要信息
    console.info(`checkNewVersion versionDigestInfo: ${result.newVersionInfo.versionDigestInfo.versionDigest}`);
    }).catch((checkNewVersionError: BusinessError) => {
      console.error(`checkNewVersion promise error, code:${checkNewVersionError.code}, message:${checkNewVersionError.message}.`);
    });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Fail to checkNewVersion. Code: ${err.code}, message: ${err.message}.`);
}

```

## clearError

```TypeScript
clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions, callback: AsyncCallback<void>): void
```

清除异常状态。版本下载或安装失败时，删除已下载的升级包文件，清除错误状态记录。调用成功后，异常状态被清除，升级任务恢复到初始状态，可以重新开始完整的升级流程，从checkNewVersion检查版本步骤开始。使用callback异步回调。

使用场景：升级失败后清除异常、重新开始升级。

**原理说明**：

该方法执行异常状态清除流程：验证clearOptions参数（确认status为UPGRADE_FAIL）→ 删除本地存储的升级包文件（释放存储空间）→ 清除系统服务中的错误状态记录 → 重置任务状态为初始状态 → 清除错误信息缓存。清除完成后，升级服务恢复到可用状态，可以重新调用checkNewVersion开始新的升级流程。仅支持清除UPGRADE_FAIL状态，其他状态调用会返回错误。

**约束条件**：

- 当upgrade方法执行失败（状态为UPGRADE_FAIL）时，必须调用clearError清除异常状态。  
- 未调用clearError清除异常状态时，无法重新开始升级流程。  
- 清除异常后，可以从checkNewVersion重新开始升级流程。

**相关方法**：

- upgrade()：安装升级包（失败后需调用clearError）。  
- checkNewVersion()：重新检查版本（清除异常后调用）。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions, callback: AsyncCallback<void>): void--><!--Device-Updater-clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| clearOptions | [ClearOptions](arkts-basicservices-update-clearoptions-i-sys.md) | 是 | 清除选项（ClearOptions），用于指定要清除的异常状态类型。status字段仅支持UPGRADE_FAIL状态，当upgrade方法执行失败(状态为UPGRADE_FAIL)后，系统会保留异常状态阻止重新升级，此时需要传入UPGRADE_FAIL清除异常状态，使系统恢复到初始状态以便重新开始升级流程。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收清除异常状态结果。回调参数包括err（错误对象，成功时为null，失败时为错误对象）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 清除选项
const clearOptions: update.ClearOptions = {
  status: update.UpgradeStatus.UPGRADE_FAIL,
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 清除异常状态，通过回调函数处理清除结果
  onlineUpdater.clearError(versionDigestInfo, clearOptions, (clearFailError: BusinessError) => {
    if (clearFailError) {
      // 清除失败
      console.error(`clearError execute error. code:${clearFailError.code}, message:${clearFailError.message}.`);
    } else {
      // 清除成功
      console.info(`clearError execute success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## clearError

```TypeScript
clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions): Promise<void>
```

清除异常状态。版本下载或安装失败时，删除已下载的升级包文件，清除错误状态记录。调用成功后，异常状态被清除，升级任务恢复到初始状态，可以重新开始完整的升级流程，从checkNewVersion检查版本步骤开始。使用Promise异步回调。

使用场景：升级失败后清除异常、重新开始升级。

**原理说明**：

该方法执行异常状态清除流程：验证clearOptions参数（确认status为UPGRADE_FAIL）→ 删除本地存储的升级包文件（释放存储空间）→ 清除系统服务中的错误状态记录 → 重置任务状态为初始状态 → 清除错误信息缓存。清除完成后，升级服务恢复到可用状态，可以重新调用checkNewVersion开始新的升级流程。仅支持清除UPGRADE_FAIL状态，其他状态调用会返回错误。

**约束关系**：

- 当upgrade方法执行失败（状态为UPGRADE_FAIL）时，必须调用clearError清除异常状态。  
- 未调用clearError清除异常状态时，无法重新开始升级流程。  
- 清除异常后，可以从checkNewVersion重新开始升级流程。

**相关方法**：

- upgrade()：安装升级包（失败后需调用clearError）。  
- checkNewVersion()：重新检查版本（清除异常后调用）。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions): Promise<void>--><!--Device-Updater-clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| clearOptions | [ClearOptions](arkts-basicservices-update-clearoptions-i-sys.md) | 是 | 清除选项（ClearOptions），用于指定要清除的异常状态类型。status字段仅支持UPGRADE_FAIL状态，当upgrade方法执行失败(状态为UPGRADE_FAIL)后，系统会保留异常状态阻止重新升级，此时需要传入UPGRADE_FAIL清除异常状态，使系统恢复到初始状态以便重新开始升级流程。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 清除选项
const clearOptions: update.ClearOptions = {
  status: update.UpgradeStatus.UPGRADE_FAIL,
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 清除异常状态 
  onlineUpdater.clearError(versionDigestInfo, clearOptions).then(() => {
    console.info(`clearError execute success`);
  }).catch((clearFailError: BusinessError) => {
    console.error(`clearError execute error. code:${clearFailError.code}, message:${clearFailError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## download

```TypeScript
download(
      versionDigestInfo: VersionDigestInfo,
      downloadOptions: DownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

下载升级包到设备本地存储。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。支持进度监听与暂停/恢复控制，帮助用户高效完成升级包获取，节省带宽与时间，提升升级成功率。使用callback异步回调。

使用场景：OTA客户端在线升级、后台自动下载升级包、网络中断后断点续传。

**原理说明**：

该方法从升级包管理服务器下载升级包到设备本地存储。

支持断点续传机制：记录已下载的字节位置和网络连接状态，中断后可从断点继续下载。暂停下载时保存当前进度状态（已下载大小、文件路径等），恢复下载时读取进度状态继续接收。

**调用顺序说明**：

- 必须先调用checkNewVersion检查是否有新版本，并获取版本摘要信息。  
- 必须先调用checkNewVersion检查新版本，且仅当isExistNewVersion为true时可调用本方法下载升级包。  
- 如果isExistNewVersion为false，表示无新版本，调用本方法会返回“已是最新版本”。

**相关方法**：

- checkNewVersion()：检查新版本（前置方法）。  
- resumeDownload()：恢复下载（暂停后调用）。  
- pauseDownload()：暂停下载（下载中调用）。  
- upgrade()：安装升级包（下载完成后调用）。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-download(      versionDigestInfo: VersionDigestInfo,      downloadOptions: DownloadOptions,      callback: AsyncCallback<void>    ): void--><!--Device-Updater-download(      versionDigestInfo: VersionDigestInfo,      downloadOptions: DownloadOptions,      callback: AsyncCallback<void>    ): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| downloadOptions | [DownloadOptions](arkts-basicservices-update-downloadoptions-i-sys.md) | 是 | 下载选项（DownloadOptions），用于控制下载行为。allowNetwork字段设置允许下载的网络类型，建议根据升级包大小和网络环境选择：升级包大小超过100MB建议使用WIFI避免流量消耗和提升下载速度；移动场景或无WIFI环境可使用CELLULAR；不确定网络环境建议使用CELLULAR_AND_WIFI。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收下载结果。回调参数包括err（错误对象，成功时为null，失败时为错误对象）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 下载选项
const downloadOptions: update.DownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // 允许数据网络下载
  order: update.Order.DOWNLOAD // 下载
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 下载升级包
  onlineUpdater.download(versionDigestInfo, downloadOptions, (downloadError: BusinessError) => {
    if (downloadError) {
      // 下载失败
      console.error(`download error. code:${downloadError.code}, message:${downloadError.message}.`);
    } else {
      // 下载成功
      console.info(`download success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## download

```TypeScript
download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions): Promise<void>
```

下载升级包到设备本地存储。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。支持进度监听与暂停/恢复控制，

帮助用户高效完成升级包获取，节省带宽与时间，提升升级成功率。使用Promise异步回调。

使用场景：OTA客户端在线升级、后台自动下载升级包、网络中断后断点续传。

**原理说明**：

该方法从升级包管理服务器下载升级包到设备本地存储。

支持断点续传机制：记录已下载的字节位置和网络连接状态，中断后可从断点继续下载。暂停下载时保存当前进度状态（已下载大小、文件路径等），恢复下载时读取进度状态继续接收。

**调用顺序说明**：

- 必须先调用checkNewVersion检查是否有新版本，并获取版本摘要信息。  
- 只有当checkNewVersion返回isExistNewVersion为true时，才能调用本方法下载升级包。  
- 如果isExistNewVersion为false，表示无新版本，调用本方法会返回"已是最新版本"。

**相关方法**：

- checkNewVersion()：检查新版本（前置方法）。  
- resumeDownload()：恢复下载（暂停后调用）。  
- pauseDownload()：暂停下载（下载中调用）。  
- upgrade()：安装升级包（download方法下载完成后调用）。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions): Promise<void>--><!--Device-Updater-download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| downloadOptions | [DownloadOptions](arkts-basicservices-update-downloadoptions-i-sys.md) | 是 | 下载选项（DownloadOptions），用于控制下载行为。allowNetwork字段设置允许下载的网络类型，建议根据升级包大小和网络环境选择：升级包大小超过100MB建议使用WIFI避免流量消耗和提升下载速度；移动场景或无WIFI环境可使用CELLULAR；不确定网络环境建议使用CELLULAR_AND_WIFI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，表示下载任务启动成功；失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 下载选项
const downloadOptions: update.DownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // 允许数据网络下载
  order: update.Order.DOWNLOAD // 下载
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 下载升级包
  onlineUpdater.download(versionDigestInfo, downloadOptions).then(() => {
    console.info(`download start`);
  }).catch((downloadError: BusinessError) => {
    console.error(`download error. code:${downloadError.code}, message:${downloadError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getCurrentVersionDescription

```TypeScript
getCurrentVersionDescription(
      descriptionOptions: DescriptionOptions,
      callback: AsyncCallback<Array<ComponentDescription>>
    ): void
```

获取当前版本描述信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。获取成功后，返回当前版本描述信息数组，包含版本说明内容，可用于版本信息展示、版本状态确认、版本对比分析等用途。使用callback异步回调。

使用场景：需要向用户展示当前版本详情、确认当前系统版本状态、对比新旧版本差异。如设备信息界面展示更新说明、版本历史记录界面显示变更内容。若需获取技术性版本信息（如版本号、设备名等），请使用getCurrentVersionInfo方法。

**原理说明**：

该方法从升级包管理服务器获取当前版本各组件的描述信息。

描述信息包含各组件的功能说明、版本特性等内容，支持CONTENT（文本形式）和URI（链接形式）两种返回方式。

**相关方法**：

- getCurrentVersionInfo()：获取当前版本信息(版本号、设备名等)，可独立调用。  
- getCurrentVersionDescription()：获取当前版本描述信息，适合向用户展示。  
- 两者可配合使用：先通过getCurrentVersionInfo获取基础信息，再通过本方法获取详细描述进行展示。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getCurrentVersionDescription(      descriptionOptions: DescriptionOptions,      callback: AsyncCallback<Array<ComponentDescription>>    ): void--><!--Device-Updater-getCurrentVersionDescription(      descriptionOptions: DescriptionOptions,      callback: AsyncCallback<Array<ComponentDescription>>    ): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptionOptions | [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | 是 | 描述文件选项（DescriptionOptions），用于指定描述文件的格式和语言。format字段设置描述格式(STANDARD标准格式或SIMPLIFIED简易格式)。language字段设置语言类型，格式如'zh-cn'(中文)、'en-us'(英文)、'ja-jp'(日文)等，长度范围[2，10]，单位：字符。有效字符包括字母（区分大小写）和连字符（-），建议使用小写格式。超出范围或包含无效字符时抛出异常。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;ComponentDescription&gt;&gt; | 是 | 回调函数，用于接收当前版本描述信息。回调参数包括： err(错误对象，成功时为null)和info(当前版本描述信息数组，包含版本说明内容)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: 'zh-cn' // 中文
};

try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取当前版本描述信息
  onlineUpdater.getCurrentVersionDescription(descriptionOptions, (currentDescriptionError, info) => {
    if (currentDescriptionError) {
      console.error(`getCurrentVersionDescription error, code:${currentDescriptionError.code}, message:${currentDescriptionError.message}.`);
      return;
    }
    console.info(`getCurrentVersionDescription info ${JSON.stringify(info)}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getCurrentVersionDescription

```TypeScript
getCurrentVersionDescription(descriptionOptions: DescriptionOptions): Promise<Array<ComponentDescription>>
```

获取当前版本描述信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。获取成功后，返回当前版本描述信息数组，包含版本说明内容，可用于版本信息展示、版本状态确认、版本对比分析等用途。使用Promise异步回调。

使用场景：需要向用户展示当前版本详情、确认当前系统版本状态、对比新旧版本差异。如设备信息界面展示更新说明、版本历史记录界面显示变更内容。若需获取技术性版本信息（如版本号、设备名等），请使用getCurrentVersionInfo方法。

**原理说明**：

该方法从升级包管理服务器获取当前版本各组件的描述信息。获取流程包括：读取当前版本标识 → 向服务器发起描述信息请求（携带descriptionOptions参数指定格式和语言）→ 服务器根据版本标识查询描述内容 → 解析描述数据（转换为目标格式和语言）→ 返回描述信息数组。描述信息包含各组件的功能说明、版本特性等内容，支持CONTENT（文本形式）和URI（链接形式）两种返回方式。

**相关方法**：

- getCurrentVersionInfo()：获取当前版本信息(版本号、设备名等)，可独立调用。  
- getCurrentVersionDescription()：获取当前版本描述信息，适合向用户展示。  
- 两者可配合使用：先通过getCurrentVersionInfo获取基础信息，再通过本方法获取详细描述进行展示。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getCurrentVersionDescription(descriptionOptions: DescriptionOptions): Promise<Array<ComponentDescription>>--><!--Device-Updater-getCurrentVersionDescription(descriptionOptions: DescriptionOptions): Promise<Array<ComponentDescription>>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptionOptions | [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | 是 | 描述文件选项（DescriptionOptions），用于指定描述文件的格式和语言。format字段设置描述格式(STANDARD标准格式或SIMPLIFIED简易格式)。language字段设置语言类型，格式如'zh-cn'(中文)、'en-us'(英文)、'ja-jp'(日文)等，长度范围[2，10]，单位：字符。有效字符包括字母（区分大小写）和连字符（-），建议使用小写格式。超出范围或包含无效字符时抛出异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ComponentDescription&gt;&gt; | Promise对象。成功时resolve返回当前版本描述信息数组，用于展示当前版本详情和版本对比；失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: 'zh-cn' // 中文
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取当前版本描述信息
  onlineUpdater.getCurrentVersionDescription(descriptionOptions).then((info: Array<update.ComponentDescription>) => {
    console.info(`getCurrentVersionDescription promise info ${JSON.stringify(info)}`);
  }).catch((descriptionError: BusinessError) => {
    console.error(`getCurrentVersionDescription error, code:${descriptionError.code}, message:${descriptionError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getCurrentVersionInfo

```TypeScript
getCurrentVersionInfo(callback: AsyncCallback<CurrentVersionInfo>): void
```

获取当前版本信息。调用成功后返回当前版本信息对象，包含系统版本号、设备名、版本组件等，帮助用户快速了解设备版本状态，便于升级决策与问题排查。使用callback异步回调。

使用场景：用于在设置界面展示系统版本、对比版本是否为最新、进行版本管理与诊断。若需向用户展示当前版本的可读说明内容，建议使用getCurrentVersionDescription方法。

**原理说明**：

该方法从设备本地系统文件和配置中读取当前版本信息，包括osVersion（系统版本号，从系统版本配置文件读取）、deviceName（设备名称，从设备属性配置读取）和versionComponents（各组件版本信息数组，从系统分区元数据读取）。信息来源于设备本地，不依赖网络连接，调用后直接返回本地缓存的版本数据。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getCurrentVersionInfo(callback: AsyncCallback<CurrentVersionInfo>): void--><!--Device-Updater-getCurrentVersionInfo(callback: AsyncCallback<CurrentVersionInfo>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;CurrentVersionInfo&gt; | 是 | 回调函数，用于接收当前版本信息（CurrentVersionInfo）。回调参数包括： err（错误对象，成功时为null）和currentInfo（当前版本信息对象，包含osVersion、deviceName和versionComponents字段）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取当前版本信息，通过回调函数接收版本详情
  onlineUpdater.getCurrentVersionInfo((currentVersionInfoError: BusinessError,
    currentVersionInfo: update.CurrentVersionInfo) => {
    if (currentVersionInfoError) {
      console.error(`getCurrentVersionInfo error, code:${currentVersionInfoError.code}, message:${currentVersionInfoError.message}.`);
      return;
    }
    console.info(`info osVersion = ${currentVersionInfo?.osVersion}`);
    console.info(`info deviceName = ${currentVersionInfo?.deviceName}`);
    console.info(`info displayVersion = ${currentVersionInfo?.versionComponents[0].displayVersion}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getCurrentVersionInfo

```TypeScript
getCurrentVersionInfo(): Promise<CurrentVersionInfo>
```

获取当前版本信息。调用成功后返回当前版本信息对象，包含系统版本号、设备名、版本组件等，帮助用户快速了解设备版本状态，便于升级决策与问题排查。使用Promise异步回调。

使用场景：用于在设置界面展示系统版本、对比版本是否为最新、进行版本管理与诊断。若需向用户展示当前版本的可读说明内容，建议使用getCurrentVersionDescription方法。

**原理说明**：

该方法从设备本地系统文件和配置中读取当前版本信息，包括osVersion（系统版本号，从系统版本配置文件读取）、deviceName（设备名称，从设备属性配置读取）和versionComponents（各组件版本信息数组，从系统分区元数据读取）。信息来源于设备本地，不依赖网络连接，调用后直接返回本地缓存的版本数据。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getCurrentVersionInfo(): Promise<CurrentVersionInfo>--><!--Device-Updater-getCurrentVersionInfo(): Promise<CurrentVersionInfo>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CurrentVersionInfo&gt; | Promise对象。成功时resolve返回当前版本信息对象，用于展示系统版本和版本对比；失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取当前版本信息
  onlineUpdater.getCurrentVersionInfo().then((info: update.CurrentVersionInfo) => {
    console.info(`info osVersion = ${info.osVersion}`);
    console.info(`info deviceName = ${info.deviceName}`);
    console.info(`info displayVersion = ${info.versionComponents[0].displayVersion}`);
  }).catch((currentVersionInfoError: BusinessError) => {
    console.error(`getCurrentVersionInfo error, code:${currentVersionInfoError.code}, message:${currentVersionInfoError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get updater error: ${error}`);
}

```

## getNewVersionDescription

```TypeScript
getNewVersionDescription(
      versionDigestInfo: VersionDigestInfo,
      descriptionOptions: DescriptionOptions,
      callback: AsyncCallback<Array<ComponentDescription>>
    ): void
```

获取新版本描述信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。调用成功后，返回新版本描述信息数组，包含各组件的版本说明内容。使用callback异步回调。

使用场景：向用户展示版本更新内容、确认是否升级。帮助用户了解新版本的功能改进和修复内容，辅助用户做出升级决策。

**原理说明**：

该方法基于checkNewVersion返回的版本摘要信息，向升级包管理服务器查询各组件的版本描述内容。描述信息包含各组件的功能改进说明、修复内容、版本特性等。服务器返回描述信息数组，每个元素对应一个组件的描述内容（ComponentDescription）。根据descriptionOptions参数指定的格式（STANDARD标准格式或SIMPLIFIED简易格式）和语言（如zh-cn中文），服务器返回相应格式和语言的描述文本。描述内容可以是文本形式（DescriptionType.CONTENT）或链接形式（DescriptionType.URI），用于向用户展示版本更新内容。

**调用说明**：

- 需先调用checkNewVersion检查是否有新版本，并获取版本摘要信息。  
- versionDigestInfo参数从checkNewVersion返回结果中获取，须先调用checkNewVersion。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getNewVersionDescription(      versionDigestInfo: VersionDigestInfo,      descriptionOptions: DescriptionOptions,      callback: AsyncCallback<Array<ComponentDescription>>    ): void--><!--Device-Updater-getNewVersionDescription(      versionDigestInfo: VersionDigestInfo,      descriptionOptions: DescriptionOptions,      callback: AsyncCallback<Array<ComponentDescription>>    ): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息对象，包含版本标识（versionDigest字段）。必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取。版本摘要作为服务器生成的版本唯一标识，用于后续的版本查询、下载和升级操作。仅当isExistNewVersion为true时该参数有效。 |
| descriptionOptions | [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | 是 | 描述文件选项（DescriptionOptions），用于指定描述文件的格式和语言。format字段设置描述格式(STANDARD标准格式或SIMPLIFIED简易格式)。language字段设置语言类型，格式如'zh-cn'(中文)、'en-us'(英文)、'ja-jp'(日文)等，长度范围[2，10]，单位：字符。有效字符包括字母（区分大小写）和连字符（-），建议使用小写格式。超出范围或包含无效字符时抛出异常。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;ComponentDescription&gt;&gt; | 是 | 回调函数，用于接收新版本描述信息。回调参数包括： err（错误对象，成功时为null）和descriptionInfo（新版本描述信息数组，包含各组件的版本说明内容）。调用前须先调用checkNewVersion检查新版本，且仅当isExistNewVersion为true时descriptionInfo有效；若为false，则descriptionInfo为null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 从checkNewVersion结果中获取版本摘要信息
};

// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: 'zh-cn' // 中文
};

try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取新版本描述信息
  onlineUpdater.getNewVersionDescription(versionDigestInfo, descriptionOptions, (descriptionError, descriptionInfo) => {
    if (descriptionError) {
      console.error(`getNewVersionDescription error, code:${descriptionError.code}, message:${descriptionError.message}.`);
      return;
    }
    console.info(`getNewVersionDescription info ${JSON.stringify(descriptionInfo)}`);
  });
} catch (error) {
  console.error(`Fail to get updater error: ${error}`);
}

```

## getNewVersionDescription

```TypeScript
getNewVersionDescription(
      versionDigestInfo: VersionDigestInfo,
      descriptionOptions: DescriptionOptions
    ): Promise<Array<ComponentDescription>>
```

获取新版本描述信息（ComponentDescription）。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。调用成功后，返回新版本描述信息数组，包含各组件的版本说明内容。使用Promise异步回调。

使用场景：向用户展示版本更新内容、确认是否升级。帮助用户了解新版本的功能改进和修复内容，辅助用户做出升级决策。

**原理说明**：

该方法基于checkNewVersion返回的版本摘要信息，向升级包管理服务器查询各组件的版本描述内容。描述信息包含各组件的功能改进说明、修复内容、版本特性等。服务器返回描述信息数组，每个元素对应一个组件的描述内容（ComponentDescription）。根据descriptionOptions参数指定的格式（STANDARD标准格式或SIMPLIFIED简易格式）和语言（如zh-cn中文），服务器返回相应格式和语言的描述文本。描述内容可以是文本形式（DescriptionType.CONTENT）或链接形式（DescriptionType.URI），用于向用户展示版本更新内容。

**调用说明**：

- 需先调用checkNewVersion检查是否有新版本，并获取版本摘要信息。  
- versionDigestInfo参数从checkNewVersion返回结果中获取。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getNewVersionDescription(      versionDigestInfo: VersionDigestInfo,      descriptionOptions: DescriptionOptions    ): Promise<Array<ComponentDescription>>--><!--Device-Updater-getNewVersionDescription(      versionDigestInfo: VersionDigestInfo,      descriptionOptions: DescriptionOptions    ): Promise<Array<ComponentDescription>>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| descriptionOptions | [DescriptionOptions](arkts-basicservices-update-descriptionoptions-i-sys.md) | 是 | 描述文件选项（DescriptionOptions），用于指定描述文件的格式和语言。format字段设置描述格式(STANDARD标准格式或SIMPLIFIED简易格式)。language字段设置语言类型，格式如'zh-cn'(中文)、'en-us'(英文)、'ja-jp'(日文)等，长度范围[2，10]，单位：字符。有效字符包括字母（区分大小写）和连字符（-），建议使用小写格式。超出范围或包含无效字符时抛出异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ComponentDescription&gt;&gt; | Promise对象。成功时resolve返回新版本描述信息数组，用于向用户展示版本更新内容和确认升级；失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 描述文件选项
const descriptionOptions: update.DescriptionOptions = {
  format: update.DescriptionFormat.STANDARD, // 标准格式
  language: 'zh-cn' // 中文
};

try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取新版本描述信息
  onlineUpdater.getNewVersionDescription(versionDigestInfo, descriptionOptions)
    .then((info: Array<update.ComponentDescription>) => {
    console.info(`getNewVersionDescription promise info ${JSON.stringify(info)}`);
  }).catch((descriptionError: BusinessError) => {
    console.error(`getNewVersionDescription promise error, code:${descriptionError.code}, message:${descriptionError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getNewVersionInfo

```TypeScript
getNewVersionInfo(callback: AsyncCallback<NewVersionInfo>): void
```

获取新版本信息，向升级包管理服务器查询新版本的详细信息，包括版本号、版本摘要、版本组件等。调用成功后，返回新版本信息对象，包含版本摘要和完整的版本组件列表，可用于向用户展示完整版本信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。使用callback异步回调。

使用场景：需要获取新版本技术性信息（如版本号、升级包大小、组件详情）用于版本管理、诊断或技术分析。帮助开发者全面了解新版本技术细节。

若需向用户展示可读的版本说明内容，建议使用getNewVersionDescription方法。

**原理说明**：

该方法基于checkNewVersion返回的版本摘要信息，向升级包管理服务器查询新版本的完整详情。服务器返回NewVersionInfo对象，包含versionDigestInfo（版本摘要，用于后续下载和升级操作的版本标识）和versionComponents数组（各组件的版本号、大小、类型等详细信息）。必须在checkNewVersion返回isExistNewVersion为true后调用，否则返回空数据。

**调用顺序**：

- 必须先调用checkNewVersion检查是否有新版本。  
- 仅当checkNewVersion返回isExistNewVersion为true时可调用。

**相关方法**：

- checkNewVersion()：检查是否有新版本（前置方法）。  
- getNewVersionInfo()：获取新版本技术信息(版本号、组件详情)，适合版本管理和诊断场景。  
- getNewVersionDescription()：获取新版本描述文本(版本说明内容)，适合向用户展示更新内容的场景。  
- download()：下载升级包（后续方法）。

**约束和限制**：

- 本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。  
- 必须先调用checkNewVersion检查是否有新版本，且仅当isExistNewVersion为true时调用。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getNewVersionInfo(callback: AsyncCallback<NewVersionInfo>): void--><!--Device-Updater-getNewVersionInfo(callback: AsyncCallback<NewVersionInfo>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;NewVersionInfo&gt; | 是 | 回调函数，用于接收新版本信息（NewVersionInfo）。回调参数包括：err（错误对象，成功时为null）和newInfo（新版本信息对象）。调用前须先调用checkNewVersion检查新版本，且仅当isExistNewVersion为true时newInfo有效；若为false，则newInfo为null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取新版本信息，通过回调函数接收版本详情
  onlineUpdater.getNewVersionInfo((getNewVersionInfoError: BusinessError, newInfo: update.NewVersionInfo) => {
    if (getNewVersionInfoError) {
      console.error(`getNewVersionInfo error, code:${getNewVersionInfoError.code}, message:${getNewVersionInfoError.message}.`);
      return;
    }
    console.info(`info displayVersion = ${newInfo?.versionComponents[0].displayVersion}`);
    console.info(`info innerVersion = ${newInfo?.versionComponents[0].innerVersion}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getNewVersionInfo

```TypeScript
getNewVersionInfo(): Promise<NewVersionInfo>
```

获取新版本信息，向升级包管理服务器查询新版本的详细信息，包括版本号、版本摘要、版本组件等。调用成功后，返回新版本信息对象，包含版本摘要和完整的版本组件列表，可用于向用户展示完整版本信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。使用Promise异步回调。

使用场景：需要获取新版本技术性信息（如版本号、升级包大小、组件详情）用于版本管理、诊断或技术分析。帮助开发者全面了解新版本技术细节。

若需向用户展示可读的版本说明内容，建议使用getNewVersionDescription方法。

**原理说明**：

该方法基于checkNewVersion返回的版本摘要信息，向升级包管理服务器查询新版本的完整详情。服务器返回NewVersionInfo对象，包含versionDigestInfo（版本摘要，用于后续下载和升级操作的版本标识）和versionComponents数组（各组件的版本号、大小、类型等详细信息）。必须在checkNewVersion返回isExistNewVersion为true后调用，否则返回空数据。

**调用顺序**：

- 必须先调用checkNewVersion检查是否有新版本。  
- 只有当checkNewVersion返回isExistNewVersion为true时，才能调用此方法获取新版本详细信息。

**相关方法**：

- checkNewVersion()：检查是否有新版本（前置方法）。  
- getNewVersionInfo()：获取新版本技术信息(版本号、组件详情)，适合版本管理和诊断场景。  
- getNewVersionDescription()：获取新版本描述文本(版本说明内容)，适合向用户展示更新内容的场景。  
- download()：下载升级包（后续方法）。

**约束和限制**：

- 本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。  
- 必须先调用checkNewVersion检查是否有新版本，且仅当isExistNewVersion为true时调用。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getNewVersionInfo(): Promise<NewVersionInfo>--><!--Device-Updater-getNewVersionInfo(): Promise<NewVersionInfo>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NewVersionInfo&gt; | Promise对象。成功时resolve返回新版本详细信息对象，用于向用户展示完整版本信息；失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取新版本信息
  onlineUpdater.getNewVersionInfo().then((info: update.NewVersionInfo) => {
    console.info(`info displayVersion = ${info.versionComponents[0].displayVersion}`);
    console.info(`info innerVersion = ${info.versionComponents[0].innerVersion}`);
  }).catch((getNewVersionInfoError: BusinessError) => {
    console.error(`getNewVersionInfo promise error, code:${getNewVersionInfoError.code}, message:${getNewVersionInfoError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getTaskInfo

```TypeScript
getTaskInfo(callback: AsyncCallback<TaskInfo>): void
```

获取升级任务信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。获取成功后，返回升级任务信息对象，包含任务是否存在、任务状态、进度等信息。帮助开发者实时掌握升级进度、及时发现异常状态、优化升级策略，提升升级流程的可控性和成功率。使用callback异步回调。

使用场景：实时掌握升级进度、监控任务状态、及时发现异常。

**原理说明**：

该方法从系统升级服务查询当前升级任务的状态信息。系统维护一个升级任务状态记录，包含existTask（是否存在任务）、taskBody（任务详情，包括版本摘要、当前状态、进度百分比、安装模式等）。任务状态在下载、安装过程中实时更新，通过该方法可查询最新状态。状态信息存储在系统服务进程的内存中，每次调用从服务进程实时查询返回。

**相关方法**：

- download()：下载升级包(可在下载过程中调用getTaskInfo查询下载进度和状态)。  
- upgrade()：安装升级包(可在安装过程中调用getTaskInfo查询安装进度和状态)。  
- pauseDownload()：暂停下载(暂停后可调用getTaskInfo查询暂停状态)。  
- terminateUpgrade()：终止升级(终止后可调用getTaskInfo查询任务取消状态)。

**调用时机**：

- 推荐在调用download或upgrade开始升级任务后，按需调用getTaskInfo查询任务进度。  
- 在升级流程中可通过事件监听(on方法)实时获取进度，或通过getTaskInfo主动查询当前状态。  
- 在异常或中断场景下可调用getTaskInfo确认任务状态后决定后续操作。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getTaskInfo(callback: AsyncCallback<TaskInfo>): void--><!--Device-Updater-getTaskInfo(callback: AsyncCallback<TaskInfo>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;TaskInfo&gt; | 是 | 回调函数，用于接收升级任务信息（TaskInfo）。回调参数包括： err（错误对象，成功时为null）和taskInfo（升级任务信息对象，包含existTask和taskBody字段）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);

  // 获取升级任务信息，通过回调函数接收任务状态 
  onlineUpdater.getTaskInfo((taskInfoError: BusinessError, taskInfo: update.TaskInfo) => {
    if (taskInfoError) {
      console.error(`getTaskInfo error, code:${taskInfoError.code}, message:${taskInfoError.message}.`);
      return;
    }
    console.info(`getTaskInfo existTask= ${taskInfo?.existTask}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getTaskInfo

```TypeScript
getTaskInfo(): Promise<TaskInfo>
```

获取升级任务信息。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。获取成功后，返回升级任务信息对象，包含任务是否存在、任务状态、进度等信息。帮助开发者实时掌握升级进度、及时发现异常状态、优化升级策略，提升升级流程的可控性和成功率。使用Promise异步回调。

使用场景：实时掌握升级进度、监控任务状态、及时发现异常。

**原理说明**：

该方法从系统升级服务查询当前升级任务的状态信息。系统维护一个升级任务状态记录，包含existTask（是否存在任务）、taskBody（任务详情，包括版本摘要、当前状态、进度百分比、安装模式等）。任务状态在下载、安装过程中实时更新，通过该方法可查询最新状态。状态信息存储在系统服务进程的内存中，每次调用从服务进程实时查询返回。

**相关方法**：

- download()：下载升级包(可在下载过程中调用getTaskInfo查询下载进度和状态)。  
- upgrade()：安装升级包(可在安装过程中调用getTaskInfo查询安装进度和状态)。  
- pauseDownload()：暂停下载(暂停后可调用getTaskInfo查询暂停状态)。  
- terminateUpgrade()：终止升级(终止后可调用getTaskInfo查询任务取消状态)。

**调用时机**：

- 推荐在调用download或upgrade开始升级任务后，定期调用getTaskInfo查询任务进度。  
- 在升级流程中可通过事件监听(on方法)实时获取进度，或通过getTaskInfo主动查询当前状态。  
- 在异常或中断场景下可调用getTaskInfo确认任务状态后决定后续操作。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getTaskInfo(): Promise<TaskInfo>--><!--Device-Updater-getTaskInfo(): Promise<TaskInfo>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;TaskInfo&gt; | Promise对象。成功时resolve返回升级任务信息对象，用于查询和监控升级任务状态；失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取升级任务信息
  onlineUpdater.getTaskInfo().then((info: update.TaskInfo) => {
    console.info(`getTaskInfo existTask= ${info.existTask}`);
  }).catch((taskInfoError: BusinessError) => {
    // 处理获取任务信息失败的情况
    console.error(`Failed to get task info. code:${taskInfoError.code}, message:${taskInfoError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getUpgradePolicy

```TypeScript
getUpgradePolicy(callback: AsyncCallback<UpgradePolicy>): void
```

获取升级策略信息。获取成功后，返回升级策略信息对象，包含自动下载策略、自动升级策略、升级时间段等配置。使用callback异步回调。

使用场景：设备管理系统查看当前升级策略配置、OTA升级客户端启动前检查策略配置、企业设备管理平台展示升级规则。

**原理说明**：

该方法从系统升级服务查询升级策略配置信息。策略配置存储在系统配置文件中，包括downloadStrategy（自动下载开关）、autoUpgradeStrategy（自动升级开关）和autoUpgradePeriods（升级时间段列表）。调用该方法时，系统服务读取配置文件，解析策略参数并封装成UpgradePolicy对象返回。策略配置由setUpgradePolicy方法设置，系统维护策略的持久化存储，重启后策略仍然有效。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getUpgradePolicy(callback: AsyncCallback<UpgradePolicy>): void--><!--Device-Updater-getUpgradePolicy(callback: AsyncCallback<UpgradePolicy>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;UpgradePolicy&gt; | 是 | 回调函数，用于接收升级策略信息（UpgradePolicy）。回调参数包括： err（错误对象，成功时为null）和policy（升级策略信息对象，包含downloadStrategy、autoUpgradeStrategy和autoUpgradePeriods字段）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取升级策略，通过回调函数接收策略配置
  onlineUpdater.getUpgradePolicy((upgradePolicyError: BusinessError, policy: update.UpgradePolicy) => {
    if (upgradePolicyError) {
      console.error(`getUpgradePolicy error. code:${upgradePolicyError.code}, message:${upgradePolicyError.message}.`);
      return;
    }
    console.info(`policy downloadStrategy = ${policy?.downloadStrategy}`);
    console.info(`policy autoUpgradeStrategy = ${policy?.autoUpgradeStrategy}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## getUpgradePolicy

```TypeScript
getUpgradePolicy(): Promise<UpgradePolicy>
```

获取升级策略信息。获取成功后，返回升级策略信息对象，包含自动下载策略、自动升级策略、升级时间段等配置。使用Promise异步回调。

使用场景：设备管理系统查看当前升级策略配置、OTA升级客户端启动前检查策略配置、企业设备管理平台展示升级规则。

**原理说明**：

该方法从系统升级服务查询升级策略配置信息。策略配置存储在系统配置文件中，包括downloadStrategy（自动下载开关）、autoUpgradeStrategy（自动升级开关）和autoUpgradePeriods（升级时间段列表）。调用该方法时，系统服务读取配置文件，解析策略参数并封装成UpgradePolicy对象返回。策略配置由setUpgradePolicy方法设置，系统维护策略的持久化存储，重启后策略仍然有效。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-getUpgradePolicy(): Promise<UpgradePolicy>--><!--Device-Updater-getUpgradePolicy(): Promise<UpgradePolicy>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UpgradePolicy&gt; | Promise对象。成功时resolve返回升级策略信息对象，用于查询自动下载、自动升级、升级时间段等策略配置；失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 获取升级策略
  onlineUpdater.getUpgradePolicy().then((policy: update.UpgradePolicy) => {
    console.info(`policy downloadStrategy = ${policy.downloadStrategy}`);
    console.info(`policy autoUpgradeStrategy = ${policy.autoUpgradeStrategy}`);
  }).catch((upgradePolicyError: BusinessError) => {
    console.error(`getUpgradePolicy error. code:${upgradePolicyError.code}, message:${upgradePolicyError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## off

```TypeScript
off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void
```

取消注册事件监听。调用成功后，对应类型的升级事件监听被取消，不再接收该类型的事件通知，避免内存泄漏。

使用场景：升级流程结束、不再需要监听升级事件。必须先通过on()注册监听后才能使用此参数取消监听。

**原理说明**：

该方法执行事件监听取消流程：验证eventClassifyInfo参数（确认事件类型）→ 从升级服务的事件监听列表中移除对应的回调函数（若传入taskCallback则移除特定回调，否则移除该事件类型的所有监听）→ 释放监听占用的系统资源 → 断开事件传递通道。取消监听后，升级服务不再向该应用发送该类型的事件通知，应用进程不再接收相关事件回调，释放监听占用的内存和IPC通道资源。

**配对调用说明**：

- 与on()配对使用，用于取消已注册的事件监听。  
- 必须在已通过on()注册监听后，才能调用本方法取消监听。  
- 建议在升级流程结束后或页面销毁时调用，及时释放资源。

**起始版本：** 9

<!--Device-Updater-off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void--><!--Device-Updater-off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | 是 | 事件信息对象(EventClassifyInfo)，用于指定要取消监听的升级事件类型。前置条件:必须先通过on方法注册监听，注册后系统维护事件监听列表并持续接收对应类型的本地升级事件通知。使用此参数取消监听后，系统从事件监听列表中移除对应监听记录，释放监听占用的内存和IPC通道资源，应用不再接收该类型的事件通知。 |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | 否 | 事件回调。用于处理升级任务事件。回调签名：(eventInfo: EventInfo) => void，其中eventInfo为事件信息对象，包含eventId（事件ID）和taskBody（任务数据）字段。当需要取消特定回调监听时传入此参数，不传入时取消该事件类型的所有监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 任务事件类型
  extraInfo: ''
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 取消事件监听
  onlineUpdater.off(eventClassifyInfo, (eventInfo: update.EventInfo) => {
    console.info(`onlineUpdater off ${JSON.stringify(eventInfo)}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## on

```TypeScript
on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void
```

注册事件监听，用于实时监控升级状态。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。注册成功后监听对应类型的升级事件，事件发生时通过回调函数传递事件信息，包括事件ID、任务状态、进度等。

使用场景：OTA升级客户端显示升级进度条和百分比、设备管理系统批量设备升级状态监控、后台自动升级任务进度跟踪。

**原理说明**：

该方法通过系统事件机制注册升级事件监听：构造eventClassifyInfo指定事件类型（如TASK）→ 将回调函数注册到升级服务的事件监听列表 → 升级服务在状态变化时触发事件（如下载开始、下载进度更新、升级成功等）→ 事件通过IPC通道传递到应用进程 → 调用注册的回调函数传递EventInfo对象。事件监听采用异步回调机制，不影响升级流程执行，建议在升级流程结束后调用off取消监听避免内存泄漏。

**配对调用**：

- 调用on()注册监听后，必须在不再需要监听时调用off()取消监听。  
- 未调用off()取消监听会导致内存泄漏，影响系统性能。  
- 建议在升级流程结束后或页面销毁时调用off()。

**使用建议**：

- 在调用download、upgrade等长时间操作前注册监听。  
- 在操作完成或收到最终事件（如EVENT_DOWNLOAD_SUCCESS、EVENT_UPGRADE_SUCCESS）后取消监听。

**相关方法**：

- off()：取消事件监听（配对方法）。

**起始版本：** 9

<!--Device-Updater-on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void--><!--Device-Updater-on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | 是 | 事件信息对象(EventClassifyInfo)，用于指定要注册监听的升级事件类型。系统根据eventClassifyInfo参数注册对应类型的升级事件监听，事件发生时通过taskCallback回调函数传递事件信息。 |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | 是 | 事件回调（UpgradeTaskCallback），用于处理升级任务事件。回调签名：(eventInfo: EventInfo) =>void，其中eventInfo为事件信息对象，包含eventId（事件ID）和taskBody（任务数据）字段。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
const eventClassifyInfo: update.EventClassifyInfo = {
  eventClassify: update.EventClassify.TASK, // 任务事件类型
  extraInfo: '' // 额外信息，此处为空表示无额外信息
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 注册事件监听，实时监控升级状态
  onlineUpdater.on(eventClassifyInfo, (eventInfo: update.EventInfo) => {
    console.info(`updater on ${JSON.stringify(eventInfo)}`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## pauseDownload

```TypeScript
pauseDownload(
      versionDigestInfo: VersionDigestInfo,
      pauseDownloadOptions: PauseDownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

暂停下载新版本。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。仅当当前有正在进行的下载任务时可调用本方法暂停下载，暂停后需调用resumeDownload()恢复下载，恢复完成后才可调用upgrade()安装。使用callback异步回调。

使用场景：用户主动暂停下载、网络环境不佳时暂停以节省流量、需要在特定时间段（如22:00-06:00夜间时段或工作日的08:00-18:00工作时间）下载时暂停。

**原理说明**：

该方法执行下载暂停流程：中断当前网络连接 → 保存进度状态（已下载字节位置、文件路径、网络类型、版本摘要信息）→ 标记任务状态为DOWNLOAD_PAUSED → 释放部分网络资源。暂停时系统将进度状态写入持久化存储，确保设备重启或应用退出后仍可恢复。根据isAllowAutoResume参数，系统可能自动恢复或等待手动调用resumeDownload。

**配对调用说明**：

- 与resumeDownload()成对使用，用于控制下载流程的暂停和恢复。暂停下载后可调用resumeDownload()恢复下载，完成暂停和恢复的流程控制。

**状态转换说明**：

- 暂停后可调用resumeDownload()恢复下载。  
- 暂停后可通过getTaskInfo()查询当前任务状态。  
- 暂停后不能直接调用upgrade()安装，必须先恢复下载并完成后再安装。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-pauseDownload(      versionDigestInfo: VersionDigestInfo,      pauseDownloadOptions: PauseDownloadOptions,      callback: AsyncCallback<void>    ): void--><!--Device-Updater-pauseDownload(      versionDigestInfo: VersionDigestInfo,      pauseDownloadOptions: PauseDownloadOptions,      callback: AsyncCallback<void>    ): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| pauseDownloadOptions | [PauseDownloadOptions](arkts-basicservices-update-pausedownloadoptions-i-sys.md) | 是 | 暂停下载选项（PauseDownloadOptions），用于控制暂停行为。如果没有正在进行的下载任务，使用此参数将导致暂停操作失败或参数无效。isAllowAutoResume字段设置是否允许自动恢复，建议：网络不稳定场景建议设置true启用自动恢复，提升下载成功率；需要精确控制下载时机或避免在特定网络环境下恢复的场景建议设置false，通过手动调用resumeDownload控制恢复时机。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收暂停下载结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 暂停下载选项
const pauseDownloadOptions: update.PauseDownloadOptions = {
  isAllowAutoResume: true // 允许自动恢复下载
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 暂停下载升级包
  onlineUpdater.pauseDownload(versionDigestInfo, pauseDownloadOptions,
    (pauseDownloadError: BusinessError) => {
    if (pauseDownloadError) {
      console.error(`pauseDownload error. code:${pauseDownloadError.code}, message:${pauseDownloadError.message}.`);
    } else {
      console.info(`pauseDownload success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## pauseDownload

```TypeScript
pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions): Promise<void>
```

暂停下载新版本。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。仅当当前有正在进行的下载任务时可调用本方法暂停下载，暂停后需调用resumeDownload()恢复下载，恢复完成后才可调用upgrade()安装。使用Promise异步回调。

使用场景：用户主动暂停下载、网络环境不佳时暂停以节省流量、需要在特定时间段下载。

**原理说明**：

该方法执行下载暂停流程：中断当前网络连接 → 保存进度状态（已下载字节位置、文件路径、网络类型、版本摘要信息）→ 标记任务状态为DOWNLOAD_PAUSED → 释放部分网络资源。暂停时系统将进度状态写入持久化存储，确保设备重启或应用退出后仍可恢复。根据isAllowAutoResume参数，系统可能自动恢复或等待手动调用resumeDownload。

**配对调用说明**：

- 与resumeDownload()成对使用，用于控制下载流程的暂停和恢复。暂停下载后可调用resumeDownload()恢复下载，完成暂停和恢复的流程控制。

**状态转换说明**：

- 暂停后可调用resumeDownload()恢复下载。  
- 暂停后可通过getTaskInfo()查询当前任务状态。  
- 暂停后不能直接调用upgrade()安装，必须先恢复下载完成后再安装。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions): Promise<void>--><!--Device-Updater-pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| pauseDownloadOptions | [PauseDownloadOptions](arkts-basicservices-update-pausedownloadoptions-i-sys.md) | 是 | 暂停下载选项（PauseDownloadOptions），用于控制暂停行为。仅当有正在进行的下载任务时才生效。如果没有正在进行的下载任务，使用此参数将导致暂停操作失败或参数无效。isAllowAutoResume字段设置是否允许自动恢复，建议：网络不稳定场景建议设置true启用自动恢复，提升下载成功率；需要精确控制下载时机或避免在特定网络环境下恢复的场景建议设置false，通过手动调用resumeDownload控制恢复时机。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 暂停下载选项
const pauseDownloadOptions: update.PauseDownloadOptions = {
  isAllowAutoResume: true // 允许自动恢复下载
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 暂停下载升级包
  onlineUpdater.pauseDownload(versionDigestInfo, pauseDownloadOptions).then(() => {
    console.info(`pauseDownload`);
  }).catch((pauseDownloadError: BusinessError) => {
    console.error(`pauseDownload error. code:${pauseDownloadError.code}, message:${pauseDownloadError.message}.`);
    
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## resumeDownload

```TypeScript
resumeDownload(
      versionDigestInfo: VersionDigestInfo,
      resumeDownloadOptions: ResumeDownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

恢复已暂停的升级包下载任务，避免重复下载已完成的进度部分。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。使用callback异步回调。

使用场景：网络中断后断点续传、用户暂停后主动恢复、后台下载任务恢复。

**原理说明**：

该方法从暂停点恢复下载流程：读取暂停时保存的进度状态（已下载字节位置、文件路径、网络连接信息）→ 根据resumeDownloadOptions选择网络类型 → 向服务器发起断点续传请求（携带已下载位置信息）→ 服务器返回剩余数据 → 从断点位置继续写入本地文件 → 实时更新进度。恢复下载时系统会验证已下载部分的完整性，确保数据一致性后再继续接收新数据。

**配对调用说明**：

- 与pauseDownload()成对使用，用于控制下载流程的暂停和恢复。  
- 必须在调用pauseDownload()暂停下载后才能调用此方法恢复下载。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-resumeDownload(      versionDigestInfo: VersionDigestInfo,      resumeDownloadOptions: ResumeDownloadOptions,      callback: AsyncCallback<void>    ): void--><!--Device-Updater-resumeDownload(      versionDigestInfo: VersionDigestInfo,      resumeDownloadOptions: ResumeDownloadOptions,      callback: AsyncCallback<void>    ): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| resumeDownloadOptions | [ResumeDownloadOptions](arkts-basicservices-update-resumedownloadoptions-i-sys.md) | 是 | 恢复下载选项（ResumeDownloadOptions），用于指定恢复下载的网络类型。仅当已调用pauseDownload暂停下载后才生效。如果未调用pauseDownload暂停下载，使用此参数将导致恢复下载失败或参数无效。allowNetwork字段设置允许恢复下载的网络类型，建议根据升级包大小和网络环境选择：升级包大小超过100MB建议使用WIFI避免流量消耗和提升下载速度；移动场景或无WIFI环境可使用CELLULAR；不确定网络环境建议使用CELLULAR_AND_WIFI。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收恢复下载结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 恢复下载选项
const resumeDownloadOptions: update.ResumeDownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // 允许数据网络下载
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 恢复下载升级包
  onlineUpdater.resumeDownload(versionDigestInfo, resumeDownloadOptions,
    (resumeDownloadError: BusinessError) => {
    if (resumeDownloadError) {
      console.error(`resumeDownload error. code:${resumeDownloadError.code}, message:${resumeDownloadError.message}.`);
    } else {
      console.info(`resumeDownload success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## resumeDownload

```TypeScript
resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions): Promise<void>
```

恢复已暂停的升级包下载任务，避免重复下载已完成的进度部分。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。使用Promise异步回调。

使用场景：网络中断后断点续传、用户暂停后主动恢复、后台下载任务恢复。

**原理说明**：

该方法从暂停点恢复下载流程：读取暂停时保存的进度状态（已下载字节位置、文件路径、网络连接信息）→ 根据resumeDownloadOptions选择网络类型 → 向服务器发起断点续传请求（携带已下载位置信息）→ 服务器返回剩余数据 → 从断点位置继续写入本地文件 → 实时更新进度。恢复下载时系统会验证已下载部分的完整性，确保数据一致性后再继续接收新数据。

**配对调用说明**：

- 与pauseDownload()成对使用，用于控制下载流程的暂停和恢复。  
- 必须在调用pauseDownload()暂停下载后才能调用此方法恢复下载。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions): Promise<void>--><!--Device-Updater-resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| resumeDownloadOptions | [ResumeDownloadOptions](arkts-basicservices-update-resumedownloadoptions-i-sys.md) | 是 | 恢复下载选项（ResumeDownloadOptions），用于指定恢复下载的网络类型。仅当已调用pauseDownload暂停下载后才生效。如果未调用pauseDownload暂停下载，使用此参数将导致恢复下载失败或参数无效。allowNetwork字段设置允许恢复下载的网络类型，建议根据升级包大小和网络环境选择：升级包大小超过100MB建议使用WIFI避免流量消耗和提升下载速度；移动场景或无WIFI环境可使用CELLULAR；不确定网络环境建议使用CELLULAR_AND_WIFI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 恢复下载选项
const resumeDownloadOptions: update.ResumeDownloadOptions = {
  allowNetwork: update.NetType.CELLULAR, // 允许数据网络下载
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 恢复下载升级包
  onlineUpdater.resumeDownload(versionDigestInfo, resumeDownloadOptions).then(() => {
    console.info(`resumeDownload start`);
  }).catch((resumeDownloadError: BusinessError) => {
    console.error(`resumeDownload error. code:${resumeDownloadError.code}, message:${resumeDownloadError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## setUpgradePolicy

```TypeScript
setUpgradePolicy(policy: UpgradePolicy, callback: AsyncCallback<void>): void
```

设置升级策略，用于控制升级行为。调用成功后，新的升级策略立即生效，系统将根据策略控制自动下载、自动升级及时间段限制。使用callback异步回调。

使用场景：企业设备管理、限制升级时段、控制自动下载。帮助用户灵活配置升级行为，满足企业管理和个性化需求。

**原理说明**：

该方法将升级策略写入系统配置文件并更新升级服务的运行参数。

设置流程包括：验证策略参数有效性 → 将策略数据写入系统配置文件持久化存储 → 更新升级服务的策略缓存 → 通知升级服务应用新策略。策略立即生效，系统会根据downloadStrategy控制是否自动下载升级包，根据autoUpgradeStrategy控制是否自动安装，根据autoUpgradePeriods限制升级时间段。策略持久化保存，设备重启后策略仍然有效。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-setUpgradePolicy(policy: UpgradePolicy, callback: AsyncCallback<void>): void--><!--Device-Updater-setUpgradePolicy(policy: UpgradePolicy, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md) | 是 | 升级策略对象（UpgradePolicy），用于控制升级行为。包含downloadStrategy(自动下载策略)、autoUpgradeStrategy(自动升级策略)和autoUpgradePeriods(自动升级时间段)三个字段。downloadStrategy字段设置是否允许自动下载，true表示可自动下载(适用于希望系统自动检测并下载新版本的场景)，false表示不可自动下载(适用于需要用户手动确认下载的场景)。autoUpgradeStrategy字段设置是否允许自动升级，true表示可自动升级(适用于希望系统自动完成升级流程的场景)，false表示不可自动升级(适用于需要用户手动确认升级的场景)。autoUpgradePeriods字段设置自动升级时间段(可选)，当需要在特定时间段内自动升级时传入此参数，如夜间时段；不传入时默认为空数组[]，表示不限制自动升级时间段。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收设置升级策略结果。回调参数包括err（错误对象，成功时为null，失败时为错误对象）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const upgradePolicy: update.UpgradePolicy = {
  downloadStrategy: false, // 禁止自动下载 
  autoUpgradeStrategy: false, // 禁止自动升级
  autoUpgradePeriods: [{ start: 120, end: 240 }] // 自动升级时间段，用分钟表示
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 设置升级策略，通过回调函数处理设置结果 
  onlineUpdater.setUpgradePolicy(upgradePolicy, (setUpgradePolicyError: BusinessError) => {
    if (setUpgradePolicyError) {
      console.error(`setUpgradePolicy error, code:${setUpgradePolicyError.code}, message:${setUpgradePolicyError.message}.`);
    } else {
      console.info(`setUpgradePolicy success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## setUpgradePolicy

```TypeScript
setUpgradePolicy(policy: UpgradePolicy): Promise<void>
```

设置升级策略，用于控制升级行为。调用成功后，新的升级策略立即生效，系统将根据策略控制自动下载、自动升级及时间段限制。使用Promise异步回调。

使用场景：企业设备管理、限制升级时段、控制自动下载。帮助用户灵活配置升级行为，满足企业管理和个性化需求。

**原理说明**：

该方法将升级策略写入系统配置文件并更新升级服务的运行参数。

设置流程包括：验证策略参数有效性 → 将策略数据写入系统配置文件持久化存储 → 更新升级服务的策略缓存 → 通知升级服务应用新策略。策略立即生效，系统会根据downloadStrategy控制是否自动下载升级包，根据autoUpgradeStrategy控制是否自动安装，根据autoUpgradePeriods限制升级时间段。策略持久化保存，设备重启后策略仍然有效。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-setUpgradePolicy(policy: UpgradePolicy): Promise<void>--><!--Device-Updater-setUpgradePolicy(policy: UpgradePolicy): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | [UpgradePolicy](arkts-basicservices-update-upgradepolicy-i-sys.md) | 是 | 升级策略对象（UpgradePolicy），用于控制升级行为。包含downloadStrategy(自动下载策略)、autoUpgradeStrategy(自动升级策略)和autoUpgradePeriods(自动升级时间段)三个字段。downloadStrategy字段设置是否允许自动下载，true表示可自动下载(适用于希望系统自动检测并下载新版本的场景)，false表示不可自动下载(适用于需要用户手动确认下载的场景)。autoUpgradeStrategy字段设置是否允许自动升级，true表示可自动升级(适用于希望系统自动完成升级流程的场景)，false表示不可自动升级(适用于需要用户手动确认升级的场景)。autoUpgradePeriods字段设置自动升级时间段(可选)，当需要在特定时间段内自动升级时传入此参数，如夜间时段；不传入时默认为空数组[]，表示不限制自动升级时间段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，表示升级策略设置成功；失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const upgradePolicy: update.UpgradePolicy = {
  downloadStrategy: false, // 禁止自动下载 
  autoUpgradeStrategy: false, // 禁止自动升级
  autoUpgradePeriods: [{ start: 120, end: 240 }] // 自动升级时间段，用分钟表示
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 设置升级策略 
  onlineUpdater.setUpgradePolicy(upgradePolicy).then(() => {
    console.info(`setUpgradePolicy success`);
  }).catch((setUpgradePolicyError: BusinessError) => {
    console.error(`setUpgradePolicy promise error, code:${setUpgradePolicyError.code}, message:${setUpgradePolicyError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## terminateUpgrade

```TypeScript
terminateUpgrade(callback: AsyncCallback<void>): void
```

终止当前升级任务，取消正在进行的安装操作。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。调用成功后，任务状态变更为已取消。使用callback异步回调。

使用场景：用户主动取消升级或紧急停止升级。帮助用户灵活控制升级流程，避免用户不需要的升级或在紧急情况下停止升级。

**原理说明**：

该方法执行升级终止流程：检测当前任务状态（仅下载或安装中可终止）→ 向升级服务发送终止指令 → 中断当前操作（停止下载或停止安装写入）→ 变更任务状态为已取消 → 清理临时资源（释放网络连接、清理临时文件）→ 通知升级服务更新状态。终止后系统保留已下载的部分数据，建议调用clearError清除异常状态后再重新开始升级流程。

**状态转换说明**：

- 仅在下载或安装过程中可以调用此方法终止升级。  
- 终止后任务状态变更为已取消。  
- 终止后可通过getTaskInfo查询当前任务状态。  
- 终止后如需重新升级，建议调用clearError清除异常状态后重新开始。

**相关方法**：

- download()/upgrade()：可被终止的方法。  
- getTaskInfo()：查询任务状态。  
- clearError()：清除异常状态（终止后如需重新升级）。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-terminateUpgrade(callback: AsyncCallback<void>): void--><!--Device-Updater-terminateUpgrade(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收终止升级结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 终止升级任务，通过回调函数处理终止结果
  onlineUpdater.terminateUpgrade((terminateUpgradeError: BusinessError) => {
    if (terminateUpgradeError) {
      console.error(`terminateUpgrade error, code:${terminateUpgradeError.code}, message:${terminateUpgradeError.message}.`);
    } else {
      console.info(`terminateUpgrade success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## terminateUpgrade

```TypeScript
terminateUpgrade(): Promise<void>
```

终止当前升级任务，取消正在进行的安装操作。本方法为在线升级功能，依赖设备厂商部署的升级包管理服务器。调用成功后，任务状态变更为已取消。使用Promise异步回调。

使用场景：用户主动取消升级或紧急停止升级。帮助用户灵活控制升级流程，避免用户不需要的升级或在紧急情况下停止升级。

**原理说明**：

该方法执行升级终止流程：检测当前任务状态（仅下载或安装中可终止）→ 向升级服务发送终止指令 → 中断当前操作（停止下载或停止安装写入）→ 变更任务状态为已取消 → 清理临时资源（释放网络连接、清理临时文件）→ 通知升级服务更新状态。终止后系统保留已下载的部分数据，建议调用clearError清除异常状态后再重新开始升级流程。

**状态转换说明**：

- 仅在下载或安装过程中可以调用此方法终止升级。  
- 终止后任务状态变更为已取消。  
- 终止后可通过getTaskInfo查询当前任务状态。  
- 终止后如需重新升级，建议调用clearError清除异常状态后重新开始。

**相关方法**：

- download()/upgrade()：可被终止的方法。  
- getTaskInfo()：查询任务状态。  
- clearError()：清除异常状态（终止后如需重新升级）。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-terminateUpgrade(): Promise<void>--><!--Device-Updater-terminateUpgrade(): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 终止升级任务
  onlineUpdater.terminateUpgrade().then(() => {
    console.info(`terminateUpgrade success`);
  }).catch((terminateUpgradeError: BusinessError) => {
    console.error(`terminateUpgrade error, code:${terminateUpgradeError.code}, message:${terminateUpgradeError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## upgrade

```TypeScript
upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions, callback: AsyncCallback<void>): void
```

升级新版本，执行安装升级包操作。调用成功后，系统开始安装升级包并准备重启以应用新版本。使用callback异步回调。

使用场景：升级包下载完成，需要安装新版本。帮助用户完成系统版本更新，获取新功能和性能优化。

**原理说明**：

该方法执行升级包的安装操作，将已下载的升级包应用到系统。安装流程包括：验证升级包完整性 → 解压升级包文件 → 写入系统分区（覆盖或更新系统文件）→ 更新版本标识 → 准备重启。根据upgradeOptions.order参数选择升级操作类型：DOWNLOAD仅下载升级包（不执行安装）、INSTALL仅安装已下载的升级包（不自动重启）、DOWNLOAD_AND_INSTALL下载并安装升级包（完整流程）、APPLY仅生效已安装的升级包（重启应用新版本）、INSTALL_AND_APPLY安装并立即重启生效。

**依赖说明**：

本方法为在线升级流程的安装阶段，实际安装操作为本地操作（安装已下载的升级包），不需要网络连接。但该方法通常在download方法下载完成后调用，整个在线升级流程依赖设备厂商部署的升级包管理服务器。

**调用顺序**：

- 必须先调用checkNewVersion检查是否有新版本，调用download下载升级包并完成下载后，才能调用本方法执行升级安装操作。

**状态转换说明**：

- 应在下载完成后调用此方法安装升级包。  
- 安装过程中可通过terminateUpgrade()终止升级。  
- 安装完成后设备将重启以应用新版本。

**失败处理**：

当upgrade方法执行失败（状态为UPGRADE_FAIL）时，必须调用clearError清除异常状态后才能重新开始升级流程。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions, callback: AsyncCallback<void>): void--><!--Device-Updater-upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| upgradeOptions | [UpgradeOptions](arkts-basicservices-update-upgradeoptions-i-sys.md) | 是 | 升级选项（UpgradeOptions），用于指定升级操作类型。order字段设置升级指令，应根据当前升级状态和业务需求选择：DOWNLOAD仅下载升级包，适用于需要先下载后手动安装的场景；INSTALL仅安装已下载的升级包，适用于已下载完成需直接安装的场景；DOWNLOAD_AND_INSTALL下载并安装，适用于完整升级流程；APPLY仅生效，适用于已安装需重启生效的场景；INSTALL_AND_APPLY安装并生效，适用于安装后立即重启生效的场景。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收升级安装结果。回调参数包括err（错误对象，成功时为null，失败时为错误对象）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 安装选项
const upgradeOptions: update.UpgradeOptions = {
  order: update.Order.INSTALL // 安装指令
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 安装升级包
  onlineUpdater.upgrade(versionDigestInfo, upgradeOptions, (upgradeError: BusinessError) => {
    if (upgradeError) {
      console.error(`upgrade error. code:${upgradeError.code}, message:${upgradeError.message}.`);
    } else {
      console.info(`upgrade success`);
    };
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

## upgrade

```TypeScript
upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions): Promise<void>
```

升级新版本，执行安装升级包操作。调用成功后，系统开始安装升级包并准备重启以应用新版本。使用Promise异步回调。

使用场景：升级包下载完成，需要安装新版本。帮助用户完成系统版本更新，获取新功能和性能优化。

**原理说明**：

该方法执行升级包的安装操作，将已下载的升级包应用到系统。安装流程包括：验证升级包完整性 → 解压升级包文件 → 写入系统分区（覆盖或更新系统文件）→ 更新版本标识 → 准备重启。根据upgradeOptions.order参数选择升级操作类型：DOWNLOAD仅下载升级包（不执行安装）、INSTALL仅安装已下载的升级包（不自动重启）、DOWNLOAD_AND_INSTALL下载并安装升级包（完整流程）、APPLY仅生效已安装的升级包（重启应用新版本）、INSTALL_AND_APPLY安装并立即重启生效。

**依赖说明**：

本方法为在线升级流程的安装阶段，实际安装操作为本地操作（安装已下载的升级包），不需要网络连接。但该方法通常在download方法下载完成后调用，整个在线升级流程依赖设备厂商部署的升级包管理服务器。

**调用顺序**：

必须先调用checkNewVersion检查是否有新版本，调用download下载升级包并完成下载后，才能调用本方法执行升级安装操作。

**状态转换说明**：

- 应在下载完成后调用此方法安装升级包。  
- 安装过程中可通过terminateUpgrade()终止升级。  
- 安装完成后设备将重启以应用新版本。

**失败处理**：

当upgrade方法执行失败（状态为UPGRADE_FAIL）时，必须调用clearError清除异常状态后才能重新开始升级流程。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-Updater-upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions): Promise<void>--><!--Device-Updater-upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | [VersionDigestInfo](arkts-basicservices-update-versiondigestinfo-i-sys.md) | 是 | 版本摘要信息（VersionDigestInfo），必须先调用checkNewVersion检查新版本并确认isExistNewVersion为true后才能使用此参数。参数从checkNewVersion返回结果的newVersionInfo字段中获取，用于标识具体版本。仅当isExistNewVersion为true时该参数有效。 |
| upgradeOptions | [UpgradeOptions](arkts-basicservices-update-upgradeoptions-i-sys.md) | 是 | 升级选项（UpgradeOptions），用于指定升级操作类型。order字段设置升级指令，应根据当前升级状态和业务需求选择：DOWNLOAD仅下载升级包，适用于需要先下载后手动安装的场景；INSTALL仅安装已下载的升级包，适用于已下载完成需直接安装的场景；DOWNLOAD_AND_INSTALL下载并安装，适用于完整升级流程；APPLY仅生效，适用于已安装需重启生效的场景；INSTALL_AND_APPLY安装并生效，适用于安装后立即重启生效的场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter verification failed. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 版本摘要信息（需先调用checkNewVersion检查新版本并确认isExistNewVersion为true，
// 从返回结果的newVersionInfo.versionDigestInfo字段获取）
const versionDigestInfo: update.VersionDigestInfo = {
  versionDigest: 'versionDigest' // 实际值需通过checkNewVersion接口获取
};

// 安装选项
const upgradeOptions: update.UpgradeOptions = {
  order: update.Order.INSTALL // 安装指令
};
try {
  // 定义升级信息对象
  const upgradeInfo: update.UpgradeInfo = {
    upgradeApp: 'com.ohos.ota.updateclient',  // 调用方包名
    businessType: {
      vendor: update.BusinessVendor.PUBLIC, // 供应商类型
      subType: update.BusinessSubType.FIRMWARE // 升级类型为固件
    }
  };
  // 获取在线升级对象
  let onlineUpdater = update.getOnlineUpdater(upgradeInfo);
  // 安装升级包
  onlineUpdater.upgrade(versionDigestInfo, upgradeOptions).then(() => {
    console.info(`upgrade start`);
  }).catch((upgradeError: BusinessError) => {
    console.error(`upgrade error. code:${upgradeError.code}, message:${upgradeError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get onlineUpdater error: ${error}`);
}

```

