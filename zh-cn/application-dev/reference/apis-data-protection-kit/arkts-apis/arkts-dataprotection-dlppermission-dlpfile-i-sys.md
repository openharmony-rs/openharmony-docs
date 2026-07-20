# DLPFile（系统接口）

管理DLPFile的实例，表示一个DLP文件对象，需要通过[generateDLPFile](arkts-dataprotection-dlppermission-generatedlpfile-f-sys.md#generatedlpfile-1)/[openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md#opendlpfile-1)获取DLPFile的实例。DLPFile对象代表一个已打开的DLP文件句柄，封装了对DLP文件的所有操作接口。对象在使用完毕后必须调用[closeDLPFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#closedlpfile-1)方法释放资源，避免文件句柄泄漏。DLPFile对象在跨进程传递时，需要进行授权。

**起始版本：** 10

<!--Device-dlpPermission-export interface DLPFile--><!--Device-dlpPermission-export interface DLPFile-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

<a id="adddlplinkfile"></a>
## addDLPLinkFile

```TypeScript
addDLPLinkFile(linkFileName: string): Promise<void>
```

在FUSE文件系统(Filesystem in Userspace)添加link文件。FUSE是一种用户空间文件系统框架，允许在用户空间实现自定义文件系统逻辑。link文件是FUSE中映射到DLP密文的虚拟文件，对该文件的读写操作会同步到实际DLP文件。使用Promise异步回调。

在调用addDLPLinkFile后需要调用[deleteDLPLinkFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#deletedlplinkfile-1)移除DLP link文件。

DLP应用需要通过标准文件接口访问加密文件内容时，先添加link文件将DLP文件映射为虚拟明文文件，应用可像操作普通文件一样读写该link文件。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-addDLPLinkFile(linkFileName: string): Promise<void>--><!--Device-DLPFile-addDLPLinkFile(linkFileName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| linkFileName | string | 是 | 用于FUSE文件系统的link文件名。不超过255字节。超出范围时抛出错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;
  
  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。

  dlpFile?.closeDLPFile(); // 关闭DLP对象。
  if (file) {
    fileIo.closeSync(file);
  }
}

ExampleFunction();

```

<a id="adddlplinkfile-1"></a>
## addDLPLinkFile

```TypeScript
addDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void
```

在FUSE文件系统添加link文件。使用callback异步回调。调用成功后，在FUSE文件系统中创建一个映射到DLP文件密文的虚拟文件。

在调用addDLPLinkFile后需要调用[deleteDLPLinkFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#deletedlplinkfile-1)移除DLP link文件。

DLP应用需要通过标准文件接口访问加密文件内容时使用此接口。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-addDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void--><!--Device-DLPFile-addDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| linkFileName | string | 是 | 用于FUSE文件系统的link文件名。不超过255字节。超出范围时抛出错误码401。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收添加link文件的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;
  
  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  dlpFile.addDLPLinkFile('test.txt.dlp.link', async (err, res) => {
    if (err !== undefined) {
      console.error('addDLPLinkFile error,', err.code, err.message);
    } else {
      console.info('res', JSON.stringify(res));
    }
    await dlpFile?.closeDLPFile(); // 关闭DLP对象。
    fileIo.closeSync(file);
  }); // 添加link文件。
}

ExampleFunction();

```

<a id="closedlpfile"></a>
## closeDLPFile

```TypeScript
closeDLPFile(): Promise<void>
```

关闭DLPFile，释放对象。使用Promise异步回调。

调用[openDLPFile](arkts-dataprotection-dlppermission-opendlpfile-f-sys.md#opendlpfile-1)成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile()释放资源。

文件所有者决定关闭DLP文件时使用此接口。

> **说明：**  
>  
> dlpFile不再使用，应该关闭释放内存，且对象不应继续使用。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-closeDLPFile(): Promise<void>--><!--Device-DLPFile-closeDLPFile(): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。

  dlpFile?.closeDLPFile(); // 关闭DLP对象。
  if (file) {
    fileIo.closeSync(file);
  }
}

ExampleFunction();

```

<a id="closedlpfile-1"></a>
## closeDLPFile

```TypeScript
closeDLPFile(callback: AsyncCallback<void>): void
```

关闭DLPFile，释放对象，使用callback异步回调。

调用openDLPFile()成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile()释放资源。

文件所有者决定关闭DLP文件时使用此接口。

> **说明：**  
>  
> dlpFile不再使用，应该关闭释放内存，且对象不应继续使用。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-closeDLPFile(callback: AsyncCallback<void>): void--><!--Device-DLPFile-closeDLPFile(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收关闭DLPFile的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  dlpFile.closeDLPFile((err, res) => { // 关闭DLP文件。
    if (err !== undefined) {
      console.error('closeDLPFile error,', err.code, err.message);
    } else {
      console.info('res', JSON.stringify(res));
    }
    fileIo.closeSync(file);
  });
}

ExampleFunction();

```

<a id="deletedlplinkfile"></a>
## deleteDLPLinkFile

```TypeScript
deleteDLPLinkFile(linkFileName: string): Promise<void>
```

删除FUSE文件系统中创建的link文件。使用Promise异步回调。调用成功后，从FUSE文件系统中移除指定的link文件。

在调用deleteDLPLinkFile前需要调用[addDLPLinkFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#adddlplinkfile-1)添加DLP link文件。

DLP文件访问结束后清理link文件映射时使用此接口。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-deleteDLPLinkFile(linkFileName: string): Promise<void>--><!--Device-DLPFile-deleteDLPLinkFile(linkFileName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| linkFileName | string | 是 | 用于FUSE文件系统的link文件名。不超过255字节。超出范围时抛出错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。
  await dlpFile.deleteDLPLinkFile('test.txt.dlp.link'); // 删除link文件。
  
  await dlpFile?.closeDLPFile(); // 关闭DLP对象。
  if (file) {
    fileIo.closeSync(file);
  }
}

ExampleFunction();

```

<a id="deletedlplinkfile-1"></a>
## deleteDLPLinkFile

```TypeScript
deleteDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void
```

删除FUSE文件系统中创建的link文件，使用callback异步回调。调用成功后，从FUSE文件系统中移除指定的link文件。

在调用deleteDLPLinkFile前需要调用[addDLPLinkFile](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#adddlplinkfile-1)添加DLP link文件。

DLP文件访问结束后清理link文件映射时使用此接口。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-deleteDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void--><!--Device-DLPFile-deleteDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| linkFileName | string | 是 | 用于FUSE文件系统的link文件名。不超过255字节。超出范围时抛出错误码401。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收删除link文件的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。
  dlpFile.deleteDLPLinkFile('test.txt.dlp.link', async (err, res) => { // 删除link文件。
    if (err !== undefined) {
      console.error('deleteDLPLinkFile error,', err.code, err.message);
    } else {
      console.info('res', JSON.stringify(res));
    }
    await dlpFile?.closeDLPFile(); // 关闭DLP对象。
    fileIo.closeSync(file);
  });
}

ExampleFunction();

```

<a id="recoverdlpfile"></a>
## recoverDLPFile

```TypeScript
recoverDLPFile(plaintextFd: number): Promise<void>
```

移除DLP文件的权限控制，恢复成明文文件。使用Promise异步回调。

文件所有者决定取消文件的DLP保护时使用此接口，将其转换为普通文件以便自由分享。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-recoverDLPFile(plaintextFd: number): Promise<void>--><!--Device-DLPFile-recoverDLPFile(plaintextFd: number): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| plaintextFd | number | 是 | 目标明文文件的fd。取值范围为[0, 2<sup>31</sup>-1]。当fd小于0时，打印错误日志，函数停止运行；当fd大于2<sup>31</sup   >-1时，fd的值被截断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-加解密出错) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-加解密超时) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-凭据服务错误) | Credential service error. |
| [19100005](../errorcode-dlp.md#19100005-凭据认证服务器错误) | Credential authentication server error. |
| [19100008](../errorcode-dlp.md#19100008-非dlp文件) | The file is not a DLP file. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100010](../errorcode-dlp.md#19100010-只读dlp文件) | The DLP file is read only. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let destFile: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  destFile = fileIo.openSync('destUri').fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.recoverDLPFile(destFile); // 还原DLP文件。
  dlpFile?.closeDLPFile(); // 关闭DLP对象。
  if (file) {
    fileIo.closeSync(file);
  }
  if (destFile) {
    fileIo.closeSync(destFile);
  }
}

ExampleFunction();

```

<a id="recoverdlpfile-1"></a>
## recoverDLPFile

```TypeScript
recoverDLPFile(plaintextFd: number, callback: AsyncCallback<void>): void
```

移除DLP文件的权限控制，恢复成明文文件，使用callback异步回调。

文件所有者决定取消文件的DLP保护时使用此接口。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-recoverDLPFile(plaintextFd: number, callback: AsyncCallback<void>): void--><!--Device-DLPFile-recoverDLPFile(plaintextFd: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| plaintextFd | number | 是 | 目标明文文件的fd。取值范围为[0, 2<sup>31</sup>-1]。当fd小于0时，打印错误日志，函数停止运行；当fd大于2<sup>31</sup   >-1时，fd的值被截断。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收恢复明文文件的结果。回调参数包括：err（错误对象，成功时为undefined）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100002](../errorcode-dlp.md#19100002-加解密出错) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../errorcode-dlp.md#19100003-加解密超时) | Credential task time out. |
| [19100004](../errorcode-dlp.md#19100004-凭据服务错误) | Credential service error. |
| [19100005](../errorcode-dlp.md#19100005-凭据认证服务器错误) | Credential authentication server error. |
| [19100008](../errorcode-dlp.md#19100008-非dlp文件) | The file is not a DLP file. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100010](../errorcode-dlp.md#19100010-只读dlp文件) | The DLP file is read only. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let destFile: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  destFile = fileIo.openSync('destUri').fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  dlpFile.recoverDLPFile(destFile, async (err, res) => { // 还原DLP文件。
    if (err !== undefined) {
      console.error('recoverDLPFile error,', err.code, err.message);
    } else {
      console.info('res', JSON.stringify(res));
    }
    await dlpFile?.closeDLPFile(); // 关闭DLP对象。
    fileIo.closeSync(file);
    fileIo.closeSync(destFile);
  });
}

ExampleFunction();

```

<a id="replacedlplinkfile"></a>
## replaceDLPLinkFile

```TypeScript
replaceDLPLinkFile(linkFileName: string): Promise<void>
```

替换link文件。使用Promise异步回调。调用成功后，使用新的link文件名替换当前link文件。

需要切换访问不同的DLP文件时，通过替换link文件实现文件映射的切换。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-replaceDLPLinkFile(linkFileName: string): Promise<void>--><!--Device-DLPFile-replaceDLPLinkFile(linkFileName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| linkFileName | string | 是 | 用于FUSE文件系统的link文件名。不超过255字节。超出范围时抛出错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。
  await dlpFile.stopFuseLink(); // 暂停link读写。
  await dlpFile.replaceDLPLinkFile('test_new.txt.dlp.link'); // 替换link文件。
  await dlpFile.resumeFuseLink(); // 恢复link读写。
  
  await dlpFile?.closeDLPFile(); // 关闭DLP对象。
  if (file) {
    fileIo.closeSync(file);
  }
}

ExampleFunction();

```

<a id="replacedlplinkfile-1"></a>
## replaceDLPLinkFile

```TypeScript
replaceDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void
```

替换link文件，使用callback异步回调。调用成功后，使用新的link文件名替换当前link文件。

需要切换访问不同的DLP文件时替换link文件。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-replaceDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void--><!--Device-DLPFile-replaceDLPLinkFile(linkFileName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| linkFileName | string | 是 | 用于FUSE文件系统的link文件名。不超过255字节。超出范围时抛出错误码401。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收替换link文件的结果。回调参数包括：err（错误对象，成功时为undefined）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。
  await dlpFile.stopFuseLink(); // 暂停link读写。
  dlpFile.replaceDLPLinkFile('test_new.txt.dlp.link', async (err, res) => { // 替换link文件。
    if (err !== undefined) {
      console.error('replaceDLPLinkFile error,', err.code, err.message);
    } else {
      console.info('res', JSON.stringify(res));
      await dlpFile?.resumeFuseLink(); // 恢复link读写。
    }
    await dlpFile?.closeDLPFile(); // 关闭DLP对象。
    fileIo.closeSync(file);
  });
}

ExampleFunction();

```

<a id="resumefuselink"></a>
## resumeFuseLink

```TypeScript
resumeFuseLink(): Promise<void>
```

恢复FUSE关联读写。使用Promise异步回调。调用成功后，恢复对link文件的读写操作。

必须在调用[stopFuseLink](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#stopfuselink-1)暂停读写后才能调用此方法恢复读写功能。

link文件替换完成后，需要恢复读写关联以继续正常的文件访问。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-resumeFuseLink(): Promise<void>--><!--Device-DLPFile-resumeFuseLink(): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。
  await dlpFile.stopFuseLink(); // 暂停link读写。
  await dlpFile.resumeFuseLink(); // 恢复link读写。
  
  dlpFile?.closeDLPFile(); // 关闭DLP对象。
  if (file) {
    fileIo.closeSync(file);
  }
}

ExampleFunction();

```

<a id="resumefuselink-1"></a>
## resumeFuseLink

```TypeScript
resumeFuseLink(callback: AsyncCallback<void>): void
```

恢复FUSE关联读写，使用callback异步回调。调用成功后，恢复对link文件的读写操作。

必须在调用[stopFuseLink](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#stopfuselink-1)暂停读写后才能调用此方法恢复读写功能。

link文件替换完成后需要恢复读写关联。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-resumeFuseLink(callback: AsyncCallback<void>): void--><!--Device-DLPFile-resumeFuseLink(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收恢复FUSE关联的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。
  await dlpFile.stopFuseLink(); // 暂停link读写。
  dlpFile.resumeFuseLink(async (err, res) => {
    if (err !== undefined) {
      console.error('resumeFuseLink error,', err.code, err.message);
    } else {
      console.info('res', JSON.stringify(res));
    }
    await dlpFile?.closeDLPFile(); // 关闭DLP对象。
    fileIo.closeSync(file);
  }); // 恢复link读写。
}

ExampleFunction();

```

<a id="stopfuselink"></a>
## stopFuseLink

```TypeScript
stopFuseLink(): Promise<void>
```

停止FUSE关联读写。使用Promise异步回调。调用成功后，暂停对link文件的读写操作。

调用stopFuseLink暂停FUSE关联读写后，必须调用[resumeFuseLink](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#resumefuselink-1)恢复读写功能。

在删除link文件前，需要先停止关联读写以确保文件操作安全。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-stopFuseLink(): Promise<void>--><!--Device-DLPFile-stopFuseLink(): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId) // 打开DLP文件。
  dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。
  dlpFile.stopFuseLink(); // 暂停link读写。
  dlpFile?.closeDLPFile(); // 关闭DLP对象。
  if (file) {
    fileIo.closeSync(file);
  }
}

ExampleFunction();

```

<a id="stopfuselink-1"></a>
## stopFuseLink

```TypeScript
stopFuseLink(callback: AsyncCallback<void>): void
```

停止FUSE关联读写。使用callback异步回调。调用成功后，暂停对link文件的读写操作。

调用stopFuseLink暂停FUSE关联读写后，必须调用[resumeFuseLink](arkts-dataprotection-dlppermission-dlpfile-i-sys.md#resumefuselink-1)恢复读写功能。

删除link文件前需要暂停读写关联。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-DLPFile-stopFuseLink(callback: AsyncCallback<void>): void--><!--Device-DLPFile-stopFuseLink(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收停止FUSE关联的结果。回调参数包括：err（错误对象，成功时为undefined）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

async function ExampleFunction() {
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let file: number | undefined = undefined;
  let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
  let appId = '';
  let bundleName = 'com.ohos.note';
  let userId = 100;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
  appId = data.signatureInfo.appId;

  file = fileIo.openSync(uri).fd;
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。
  await dlpFile.addDLPLinkFile('test.txt.dlp.link'); // 添加link文件。
  dlpFile.stopFuseLink(async (err, res) => {
    if (err !== undefined) {
      console.error('stopFuseLink error,', err.code, err.message);
    } else {
      console.info('res', JSON.stringify(res));
    }
    await dlpFile?.closeDLPFile(); // 关闭DLP对象。
    fileIo.closeSync(file);
  }); // 暂停link读写。
}

ExampleFunction();

```

## dlpProperty

```TypeScript
dlpProperty: DLPProperty
```

表示DLP文件授权相关信息。

**类型：** DLPProperty

**起始版本：** 10

<!--Device-DLPFile-dlpProperty: DLPProperty--><!--Device-DLPFile-dlpProperty: DLPProperty-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

