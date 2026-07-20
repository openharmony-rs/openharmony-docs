# LocalUpdater（系统接口）

提供校验本地升级包签名和完整性、安装本地升级包、监听本地升级事件等本地固件更新功能的工具类。

使用场景：离线环境系统升级、网络不稳定场景升级、自主可控升级流程。

**收益说明**：

解决无法联网自动升级的问题，适合离线环境或网络不稳定场景，无需依赖升级包管理服务器，降低升级成本，自主可控升级时间，确保系统完整性。

**实现机制**：

- 校验机制：验证升级包是否为官方发布且未被篡改，检查签名、完整性和版本兼容性。  
- 安装机制：解压并写入升级包内容到系统分区，准备重启应用新版本。  
- 安全保证：必须先校验升级包，确保来源可信后方可安装。

**起始版本：** 9

<!--Device-update-export interface LocalUpdater--><!--Device-update-export interface LocalUpdater-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

<a id="applynewversion"></a>
## applyNewVersion

```TypeScript
applyNewVersion(upgradeFiles: Array<UpgradeFile>, callback: AsyncCallback<void>): void
```

安装升级包。升级过程中设备会重启，应用需做好状态保存。使用callback异步回调。

**原理说明**：

该方法执行本地升级包安装流程：读取升级包文件 → 解压升级包内容 → 验证包完整性（校验签名和版本兼容性，依赖verifyUpgradePackage的校验结果） → 写入系统分区（覆盖或更新系统文件） → 更新版本标识 →准备重启环境 → 设备重启应用新版本。安装过程中维护任务状态，可通过on方法监听安装进度和状态变化。安装成功后，设备重启并加载新版本系统，升级完成。

调用顺序说明：

- 必须先调用verifyUpgradePackage校验升级包并校验通过后，才能调用本方法安装升级包。  
- 未校验直接调用本方法可能导致安装失败或系统损坏，必须先调用verifyUpgradePackage校验升级包。  
- 调用成功后，系统将解压并写入升级包内容到系统分区，准备重启以应用新版本，开发者可通过监听事件跟踪安装进度。  
- 通过安装升级包可以完成系统版本更新。

使用场景：从本地存储设备(如SD卡)进行系统升级、完成本地升级流程。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-LocalUpdater-applyNewVersion(upgradeFiles: Array<UpgradeFile>, callback: AsyncCallback<void>): void--><!--Device-LocalUpdater-applyNewVersion(upgradeFiles: Array<UpgradeFile>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeFiles | Array&lt;UpgradeFile&gt; | 是 | 升级文件数组，用于指定要安装的本地升级包列表。必须先调用verifyUpgradePackage校验升级包并校验通过后才能使用此参数安装。每个元素包含fileType(文件类型)和filePath(文件路径)字段，filePath长度范围[1，255]，单位：字符。超出范围时抛出异常，由开发者提供升级包文件路径。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收安装升级包结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

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

<a id="applynewversion-1"></a>
## applyNewVersion

```TypeScript
applyNewVersion(upgradeFiles: Array<UpgradeFile>): Promise<void>
```

安装升级包。升级过程中设备会重启，应用需做好状态保存。使用Promise异步回调。

**原理说明**：

该方法执行本地升级包安装流程：读取升级包文件 → 解压升级包内容 → 验证包完整性（校验签名和版本兼容性，依赖verifyUpgradePackage的校验结果） → 写入系统分区（覆盖或更新系统文件） → 更新版本标识 →准备重启环境 → 设备重启应用新版本。安装过程中维护任务状态，可通过on方法监听安装进度和状态变化。安装成功后，设备重启并加载新版本系统，升级完成。

调用顺序说明：

- 必须先调用verifyUpgradePackage校验升级包并校验通过后，才能调用本方法安装升级包。  
- 未校验直接调用本方法可能导致安装失败或系统损坏，必须先调用verifyUpgradePackage校验升级包。  
- 调用成功后，系统将解压并写入升级包内容到系统分区，准备重启以应用新版本，可通过监听事件跟踪安装进度。  
- 通过安装升级包可以完成系统版本更新。

使用场景：从本地存储设备(如SD卡)进行系统升级、完成本地升级流程。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-LocalUpdater-applyNewVersion(upgradeFiles: Array<UpgradeFile>): Promise<void>--><!--Device-LocalUpdater-applyNewVersion(upgradeFiles: Array<UpgradeFile>): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeFiles | Array&lt;UpgradeFile&gt; | 是 | 升级文件数组，用于指定要安装的本地升级包列表。必须先调用verifyUpgradePackage校验升级包并校验通过后才能使用此参数安装。每个元素包含fileType(文件类型)和filePath(文件路径)字段，filePath长度范围[1，255], 单位：字符。超出范围时抛出异常，由开发者提供升级包文件路径。 |

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

<a id="off"></a>
## off

```TypeScript
off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void
```

取消注册事件监听。调用成功后，不再接收对应类型的升级事件通知，避免内存泄漏。

使用场景：本地升级流程结束、不再需要监听升级事件。

**原理说明**：

该方法执行事件监听取消流程：验证eventClassifyInfo参数（确认事件类型）→ 从升级服务的事件监听列表中移除对应的回调函数（若传入taskCallback则移除特定回调，否则移除该事件类型的所有监听）→ 释放监听占用的系统资源 → 断开事件传递通道。取消监听后，升级服务不再向该应用发送该类型的事件通知，应用进程不再接收相关事件回调，释放监听占用的内存和IPC通道资源。

**配对调用说明**：

- 与on()配对使用，用于取消已注册的事件监听。  
- 须在已通过on()注册监听后，才能调用本方法取消监听。  
- 建议在升级流程结束后或页面销毁时调用，及时释放资源。

**起始版本：** 9

<!--Device-LocalUpdater-off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void--><!--Device-LocalUpdater-off(eventClassifyInfo: EventClassifyInfo, taskCallback?: UpgradeTaskCallback): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | 是 | 事件信息对象（EventClassifyInfo），用于指定要取消监听的升级事件类型。必须先通过on方法注册监听后才能使用此参数取消监听。 |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | 否 | 事件回调，用于取消指定回调监听。回调签名：(eventInfo: EventInfo) => void，其中eventInfo为事件信息对象，包含eventId和taskBody字段。当需要取消特定回调监听时传入此参数；不传入此参数时默认为undefined，表示取消该事件类型的所有监听。 |

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

<a id="on"></a>
## on

```TypeScript
on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void
```

注册事件监听，用于实时监控升级状态。调用成功后，监听对应类型的升级事件，事件发生时通过回调函数传递事件信息，包括事件ID、任务状态、进度等。通过事件监听可以实时获取升级进度和状态变化，及时发现升级异常并处理，提升用户体验和升级流程的可控性。

使用场景：OTA升级客户端显示升级进度条和百分比、设备管理系统批量设备升级状态监控、后台自动升级任务进度跟踪。

**原理说明**：

该方法通过系统事件机制注册本地升级事件监听：构造eventClassifyInfo指定事件类型（如TASK）→ 将回调函数注册到本地升级服务的事件监听列表 → 本地升级服务在安装状态变化时触发事件（如安装开始、安装进度更新、安装成功等）→ 事件通过IPC通道传递到应用进程 → 调用注册的回调函数传递EventInfo对象。事件监听采用异步回调机制，不影响本地升级流程执行，建议在升级流程结束后调用off取消监听避免内存泄漏。

**配对调用**：

- 调用on()注册监听后，必须在不再需要监听时调用off()取消监听。  
- 未调用off()取消监听会导致内存泄漏，影响系统性能。  
- 建议在升级流程结束后或页面销毁时调用off()。

**使用建议**：

- 在调用applyNewVersion等长时间操作前注册监听。  
- 在操作完成或收到最终事件后取消监听。

**起始版本：** 9

<!--Device-LocalUpdater-on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void--><!--Device-LocalUpdater-on(eventClassifyInfo: EventClassifyInfo, taskCallback: UpgradeTaskCallback): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| eventClassifyInfo | [EventClassifyInfo](arkts-basicservices-update-eventclassifyinfo-i-sys.md) | 是 | 事件信息对象(EventClassifyInfo)，用于指定要注册监听的升级事件类型。 |
| taskCallback | [UpgradeTaskCallback](arkts-basicservices-update-upgradetaskcallback-t-sys.md) | 是 | 事件回调，用于接收升级任务事件通知。回调签名：(eventInfo: EventInfo) => void，其中eventInfo为事件信息对象，包含eventId（事件ID）和taskBody（任务数据）字段。 |

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

<a id="verifyupgradepackage"></a>
## verifyUpgradePackage

```TypeScript
verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback<void>): void
```

校验升级包的数字签名、文件完整性和版本兼容性，验证升级包是否为官方发布且未被篡改。调用成功且校验通过后，升级包被视为可信，可用于后续安装；若校验失败，将返回错误信息并阻止安装。使用callback异步回调。

使用场景：用户从本地存储设备获取升级包、需要验证来源可信，以及确保完整性、防止恶意包攻击。

**原理说明**：

该方法执行升级包安全校验流程：读取升级包文件和证书文件 → 使用证书验证升级包的数字签名（验证签名算法、签名值、证书有效性）→ 计算升级包的哈希值并与包内哈希校验值比对验证文件完整性 → 检查升级包版本号与当前系统版本兼容性→ 返回校验结果。数字签名验证确保升级包来源可信（由官方签名），完整性验证确保升级包未被篡改，版本兼容性验证确保升级包适用于当前设备。校验通过后升级包标记为可信状态，方可用于后续安装流程。

**调用顺序说明**：

- 升级包必须从设备厂商官网或官方渠道下载，确保来源可信。使用非官方渠道下载的升级包可能存在安全风险。  
- 必须先调用verifyUpgradePackage校验升级包并校验通过后，才能调用applyNewVersion安装升级包。  
- 未校验直接调用applyNewVersion会导致安装失败，可能造成系统损坏。  
- 校验通过后的升级包可用于后续安装流程。

**相关方法**：

- applyNewVersion()：安装升级包（校验通过后调用）。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-LocalUpdater-verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback<void>): void--><!--Device-LocalUpdater-verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeFile | [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | 是 | 升级文件（UpgradeFile），包含文件类型和文件路径，用于指定要校验的本地升级包。 |
| certsFile | string | 是 | 证书文件路径，用于校验升级包签名。证书文件必须从设备厂商官网下载，确保来源可信。支持绝对路径或相对路径，路径长度范围[1，255]，单位：字符。仅支持字母、数字、下划线、连字符、点号和斜杠等路径合法字符。超出长度范围或包含无效字符时抛出异常。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收校验结果。回调参数包括： err(错误对象，成功时为null，失败时为错误对象)。 |

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

<a id="verifyupgradepackage-1"></a>
## verifyUpgradePackage

```TypeScript
verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise<void>
```

校验升级包的数字签名、文件完整性和版本兼容性，验证升级包是否为官方发布且未被篡改。调用成功且校验通过后，升级包被视为可信，可用于后续安装；若校验失败，将返回错误信息并阻止安装。使用Promise异步回调。

使用场景：用户从本地存储设备获取升级包、需要验证来源可信，以及确保完整性、防止恶意包攻击。

**原理说明**：

该方法执行升级包安全校验流程：读取升级包文件和证书文件 → 使用证书验证升级包的数字签名（验证签名算法、签名值、证书有效性）→ 计算升级包的哈希值并与包内哈希校验值比对验证文件完整性 → 检查升级包版本号与当前系统版本兼容性→ 返回校验结果。数字签名验证确保升级包来源可信（由官方签名），完整性验证确保升级包未被篡改，版本兼容性验证确保升级包适用于当前设备。校验通过后升级包标记为可信状态，方可用于后续安装流程。

**调用顺序说明**：

- 升级包必须从设备厂商官网或官方渠道下载，确保来源可信。使用非官方渠道下载的升级包可能存在安全风险。  
- 必须先调用verifyUpgradePackage校验升级包并校验通过后，才能调用applyNewVersion安装升级包。  
- 未校验直接调用applyNewVersion会导致安装失败，可能造成系统损坏。  
- 校验通过后的升级包可用于后续安装流程。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_SYSTEM

<!--Device-LocalUpdater-verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise<void>--><!--Device-LocalUpdater-verifyUpgradePackage(upgradeFile: UpgradeFile, certsFile: string): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| upgradeFile | [UpgradeFile](arkts-basicservices-update-upgradefile-i-sys.md) | 是 | 升级文件（UpgradeFile），包含文件类型和文件路径，用于指定要校验的本地升级包。 |
| certsFile | string | 是 | 证书文件路径，用于校验升级包签名。证书文件必须从设备厂商官网下载，确保来源可信。支持绝对路径或相对路径，路径长度范围[1，255]，单位：字符。仅支持字母、数字、下划线、连字符、点号和斜杠等路径合法字符。超出长度范围或包含无效字符时抛出异常。 |

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

