# Updater（系统接口）

提供系统在线更新功能的工具类。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## checkNewVersion

```TypeScript
checkNewVersion(callback: AsyncCallback<CheckResult>): void
```

检查新版本信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;CheckResult&gt; | 是 | 回调函数，返回搜包结果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## checkNewVersion

```TypeScript
checkNewVersion(): Promise<CheckResult>
```

检查新版本信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CheckResult&gt; | Promise对象，返回搜包结果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## clearError

```TypeScript
clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions, callback: AsyncCallback<void>): void
```

清除异常状态，版本下载、安装异常时，清理升级包文件及升级状态。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| clearOptions | ClearOptions | 是 | 清除选项。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当清除异常成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## clearError

```TypeScript
clearError(versionDigestInfo: VersionDigestInfo, clearOptions: ClearOptions): Promise<void>
```

清除异常状态，版本下载、安装异常时，清理升级包文件及升级状态。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| clearOptions | ClearOptions | 是 | 清除选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## download

```TypeScript
download(
      versionDigestInfo: VersionDigestInfo,
      downloadOptions: DownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

下载新版本。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| downloadOptions | DownloadOptions | 是 | 下载选项。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当下载成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## download

```TypeScript
download(versionDigestInfo: VersionDigestInfo, downloadOptions: DownloadOptions): Promise<void>
```

下载新版本。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| downloadOptions | DownloadOptions | 是 | 下载选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getCurrentVersionDescription

```TypeScript
getCurrentVersionDescription(
      descriptionOptions: DescriptionOptions,
      callback: AsyncCallback<Array<ComponentDescription>>
    ): void
```

获取当前版本描述信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptionOptions | DescriptionOptions | 是 | 描述文件选项。 |
| callback | AsyncCallback&lt;Array&lt;ComponentDescription&gt;&gt; | 是 | 回调函数，返回当前版本描述信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getCurrentVersionDescription

```TypeScript
getCurrentVersionDescription(descriptionOptions: DescriptionOptions): Promise<Array<ComponentDescription>>
```

获取当前版本描述信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptionOptions | DescriptionOptions | 是 | 描述文件选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ComponentDescription&gt;&gt; | Promise对象，返回当前版本描述信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getCurrentVersionInfo

```TypeScript
getCurrentVersionInfo(callback: AsyncCallback<CurrentVersionInfo>): void
```

获取当前版本信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;CurrentVersionInfo&gt; | 是 | 回调函数，返回当前版本信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getCurrentVersionInfo

```TypeScript
getCurrentVersionInfo(): Promise<CurrentVersionInfo>
```

获取当前版本信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CurrentVersionInfo&gt; | Promise对象，返回当前版本信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getNewVersionDescription

```TypeScript
getNewVersionDescription(
      versionDigestInfo: VersionDigestInfo,
      descriptionOptions: DescriptionOptions,
      callback: AsyncCallback<Array<ComponentDescription>>
    ): void
```

获取新版本描述信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| descriptionOptions | DescriptionOptions | 是 | 描述文件选项。 |
| callback | AsyncCallback&lt;Array&lt;ComponentDescription&gt;&gt; | 是 | 回调函数，返回新版本描述信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getNewVersionDescription

```TypeScript
getNewVersionDescription(
      versionDigestInfo: VersionDigestInfo,
      descriptionOptions: DescriptionOptions
    ): Promise<Array<ComponentDescription>>
```

获取新版本描述信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| descriptionOptions | DescriptionOptions | 是 | 描述文件选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ComponentDescription&gt;&gt; | Promise对象，返回新版本描述信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getNewVersionInfo

```TypeScript
getNewVersionInfo(callback: AsyncCallback<NewVersionInfo>): void
```

获取新版本信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;NewVersionInfo&gt; | 是 | 回调函数，返回新版本信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getNewVersionInfo

```TypeScript
getNewVersionInfo(): Promise<NewVersionInfo>
```

获取新版本信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NewVersionInfo&gt; | Promise对象，返回新版本信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getTaskInfo

```TypeScript
getTaskInfo(callback: AsyncCallback<TaskInfo>): void
```

获取升级任务信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;TaskInfo&gt; | 是 | 回调函数，返回升级任务信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getTaskInfo

```TypeScript
getTaskInfo(): Promise<TaskInfo>
```

获取升级任务信息。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;TaskInfo&gt; | Promise对象，返回任务信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getUpgradePolicy

```TypeScript
getUpgradePolicy(callback: AsyncCallback<UpgradePolicy>): void
```

获取升级策略信息。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;UpgradePolicy&gt; | 是 | 回调函数，返回升级策略信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## getUpgradePolicy

```TypeScript
getUpgradePolicy(): Promise<UpgradePolicy>
```

获取升级策略。通过promise方式作为异步方法。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;UpgradePolicy&gt; | Promise对象，返回升级策略信息对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## off

```TypeScript
off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void
```

取消注册事件监听。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventClassifyInfo | EventClassifyInfo | 是 | 事件信息。 |
| taskCallback | UpgradeTaskCallback | 否 | 事件回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
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

## on

```TypeScript
on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void
```

注册事件监听。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventClassifyInfo | EventClassifyInfo | 是 | 事件信息。 |
| taskCallback | UpgradeTaskCallback | 是 | 事件回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
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

## pauseDownload

```TypeScript
pauseDownload(
      versionDigestInfo: VersionDigestInfo,
      pauseDownloadOptions: PauseDownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

暂停下载新版本。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| pauseDownloadOptions | PauseDownloadOptions | 是 | 暂停下载选项。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当暂停下载成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## pauseDownload

```TypeScript
pauseDownload(versionDigestInfo: VersionDigestInfo, pauseDownloadOptions: PauseDownloadOptions): Promise<void>
```

暂停下载新版本。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| pauseDownloadOptions | PauseDownloadOptions | 是 | 暂停下载选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## resumeDownload

```TypeScript
resumeDownload(
      versionDigestInfo: VersionDigestInfo,
      resumeDownloadOptions: ResumeDownloadOptions,
      callback: AsyncCallback<void>
    ): void
```

恢复下载新版本。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| resumeDownloadOptions | ResumeDownloadOptions | 是 | 恢复下载选项。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当恢复下载成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## resumeDownload

```TypeScript
resumeDownload(versionDigestInfo: VersionDigestInfo, resumeDownloadOptions: ResumeDownloadOptions): Promise<void>
```

恢复下载新版本。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| resumeDownloadOptions | ResumeDownloadOptions | 是 | 恢复下载选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## setUpgradePolicy

```TypeScript
setUpgradePolicy(policy: UpgradePolicy, callback: AsyncCallback<void>): void
```

设置升级策略。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | UpgradePolicy | 是 | 升级策略。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置升级策略成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## setUpgradePolicy

```TypeScript
setUpgradePolicy(policy: UpgradePolicy): Promise<void>
```

设置升级策略。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| policy | UpgradePolicy | 是 | 升级策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## terminateUpgrade

```TypeScript
terminateUpgrade(callback: AsyncCallback<void>): void
```

终止升级。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当终止升级执行成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## terminateUpgrade

```TypeScript
terminateUpgrade(): Promise<void>
```

终止升级。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## upgrade

```TypeScript
upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions, callback: AsyncCallback<void>): void
```

升级新版本。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| upgradeOptions | UpgradeOptions | 是 | 更新选项。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当升级执行成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

## upgrade

```TypeScript
upgrade(versionDigestInfo: VersionDigestInfo, upgradeOptions: UpgradeOptions): Promise<void>
```

升级新版本。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| versionDigestInfo | VersionDigestInfo | 是 | 版本摘要信息。 |
| upgradeOptions | UpgradeOptions | 是 | 更新选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter verification failed. |
| [11500104](../../errorcode-universal.md#11500104-IPC) | IPC error. |

**示例：**

```TypeScript
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

