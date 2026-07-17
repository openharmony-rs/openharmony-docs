# LocalUpdater（系统接口）

提供本地固件更新功能的工具类。

**起始版本：** 9

<!--Device-update-export interface LocalUpdater--><!--Device-update-export interface LocalUpdater-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## applyNewVersion

```TypeScript
applyNewVersion(upgradeFiles: Array<UpgradeFile>, callback: AsyncCallback<void>): void
```

安装升级包。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-LocalUpdater-applyNewVersion(upgradeFiles: Array<UpgradeFile>, callback: AsyncCallback<void>): void--><!--Device-LocalUpdater-applyNewVersion(upgradeFiles: Array<UpgradeFile>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeFiles | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<UpgradeFile> | 是 | 升级文件。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当安装升级包执行成功时，err为undefined，否则为错误对象。 |

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

const upgradeFiles: Array<update.UpgradeFile> = [{
  fileType: update.ComponentType.OTA, // OTA包
  filePath: '/data/local/tmp/updater.zip' // 本地升级包路径，用户需从设备厂商官网或官方渠道下载升级包文件，放置到设备可访问的存储路径，（如/data/local/tmp/updater.zip）
}];

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  // 安装新版本
  localUpdater.applyNewVersion(upgradeFiles, (applyNewVersionError: BusinessError) => {
    if (applyNewVersionError) {
      console.error(`applyNewVersion error, code:${applyNewVersionError.code}, message:${applyNewVersionError.message}.`);
      return;
    }
    console.info(`applyNewVersion success`);
  });
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}

```

## applyNewVersion

```TypeScript
applyNewVersion(upgradeFiles: Array<UpgradeFile>): Promise<void>
```

安装升级包。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-LocalUpdater-applyNewVersion(upgradeFiles: Array<UpgradeFile>): Promise<void>--><!--Device-LocalUpdater-applyNewVersion(upgradeFiles: Array<UpgradeFile>): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeFiles | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<UpgradeFile> | 是 | 升级文件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

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

const upgradeFiles: Array<update.UpgradeFile> = [{
  fileType: update.ComponentType.OTA, // OTA包
  filePath: '/data/local/tmp/updater.zip' // 本地升级包路径，用户需从设备厂商官网或官方渠道下载升级包文件，放置到设备可访问的存储路径，（如/data/local/tmp/updater.zip）
}];

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  // 安装新版本
  localUpdater.applyNewVersion(upgradeFiles).then(() => {
    console.info(`applyNewVersion success`);
  }).catch((applyNewVersionError: BusinessError) => {
    console.error(`applyNewVersion error, code:${applyNewVersionError.code}, message:${applyNewVersionError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}

```

## off

```TypeScript
off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void
```

取消注册事件监听。使用callback异步回调。

**起始版本：** 9

<!--Device-LocalUpdater-off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void--><!--Device-LocalUpdater-off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | 是 | 事件信息。 |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | 否 | 事件回调。 |

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
// 定义任务更新回调函数，用于处理升级任务事件
let onTaskUpdate: update.UpgradeTaskCallback = (eventInfo: update.EventInfo) => {
  console.info(`on eventInfo id `, eventInfo.eventId);
};

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  // 取消本地升级事件监听
  localUpdater.off(eventClassifyInfo, onTaskUpdate);
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}

```

## on

```TypeScript
on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void
```

注册事件监听。使用callback异步回调。

**起始版本：** 9

<!--Device-LocalUpdater-on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void--><!--Device-LocalUpdater-on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | 是 | 事件信息。 |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | 是 | 事件回调。 |

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
// 定义任务更新回调函数，用于处理升级任务事件
let onTaskUpdate: update.UpgradeTaskCallback = (eventInfo: update.EventInfo) => {
  console.info(`on eventInfo id `, eventInfo.eventId);
};

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  // 注册本地升级事件监听
  localUpdater.on(eventClassifyInfo, onTaskUpdate);
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}

```

## verifyUpgradePackage

```TypeScript
verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback<void>): void
```

校验升级包。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-LocalUpdater-verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback<void>): void--><!--Device-LocalUpdater-verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeFile | [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | 是 | 升级文件。 |
| certsFile | string | 是 | 证书文件路径。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当校验成功时，err为undefined，否则为错误对象。 |

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

const upgradeFile: update.UpgradeFile = {
  fileType: update.ComponentType.OTA, // OTA包
  filePath: '/data/local/tmp/updater.zip' // 本地升级包路径，用户需从设备厂商官网或官方渠道下载升级包文件，放置到设备可访问的存储路径，（如/data/local/tmp/updater.zip）
};
// certsFile为证书文件路径，需从设备厂商官网下载并放置到设备可访问路径 
const certsFile = '/path/to/certificate.cert'; // 证书文件路径，从厂商官网下载

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  // 验证升级包
  localUpdater.verifyUpgradePackage(upgradeFile, certsFile, (verifyUpgradePackageError: BusinessError) => {
    if (verifyUpgradePackageError) {
      console.error(`verifyUpgradePackage error, code:${verifyUpgradePackageError.code}, message:${verifyUpgradePackageError.message}.`);
      return;
    }
    console.info(`verifyUpgradePackage success`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Fail to get localUpdater. Code: ${err.code}, message: ${err.message}.`);
}

```

## verifyUpgradePackage

```TypeScript
verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise<void>
```

校验升级包。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-LocalUpdater-verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise<void>--><!--Device-LocalUpdater-verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeFile | [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | 是 | 升级文件。 |
| certsFile | string | 是 | 证书文件路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

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

const upgradeFile: update.UpgradeFile = {
  fileType: update.ComponentType.OTA, // OTA包
  filePath: '/data/local/tmp/updater.zip' // 本地升级包路径，用户需从设备厂商官网或官方渠道下载升级包文件，放置到设备可访问的存储路径，（如/data/local/tmp/updater.zip）
};

// certsFile为证书文件路径，需从设备厂商官网下载并放置到设备可访问路径 
const certsFile = '/path/to/certificate.cert'; // 证书文件路径，从厂商官网下载

try {
  // 获取本地升级对象
  let localUpdater = update.getLocalUpdater();
  // 验证升级包
  localUpdater.verifyUpgradePackage(upgradeFile, certsFile).then(() => {
    console.info(`verifyUpgradePackage success`);
  }).catch((verifyUpgradePackageError: BusinessError) => {
    console.error(`verifyUpgradePackage error, code:${verifyUpgradePackageError.code}, message:${verifyUpgradePackageError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get localUpdater error: ${error}`);
}

```

