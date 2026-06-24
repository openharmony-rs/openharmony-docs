# openDLPFile（系统接口）

## openDLPFile

```TypeScript
function openDLPFile(ciphertextFd: number, appId: string): Promise<DLPFile>
```

DLP管理应用调用该接口，打开DLP文件。调用成功后返回DLPFile管理对象，可用于管理DLP文件的权限和进行相关操作。使用Promise异步回调。

调用openDLPFile()成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile释放资源。

DLP管理应用或授权应用需要访问受保护的DLP文件内容时，先打开文件获取管理对象。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ciphertextFd | number | 是 | 加密文件的fd。 |
| appId | string | 是 | 调用方身份。最小8字节，最大1024字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DLPFile&gt; | Promise对象。resolve时返回DLPFile对象表示成功打开DLP文件，reject时抛出错误表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Nonsystem) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100002](../../errorcode-universal.md#19100002-Credential) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../../errorcode-universal.md#19100003-Credential) | Credential task time out. |
| [19100004](../../errorcode-universal.md#19100004-Credential) | Credential service error. |
| [19100005](../../errorcode-universal.md#19100005-Credential) | Credential authentication server error. |
| [19100008](../../errorcode-universal.md#19100008-The) | The file is not a DLP file. |
| [19100009](../../errorcode-universal.md#19100009-Failed) | Failed to operate the DLP file. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |
| [19100018](../../errorcode-universal.md#19100018-The) | The application is not authorized. |
| [19100019](../../errorcode-universal.md#19100019-The) | The DLP file has expired. |
| [19100020](../../errorcode-universal.md#19100020-No) | No network connection. |

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
  appId = data.signatureInfo.appId; // appId通过应用包信息获取

  file = fileIo.openSync(uri).fd; // file通过文件打开获取fd
  dlpFile = await dlpPermission.openDLPFile(file, appId); // 打开DLP文件。

  if (file) {
    fileIo.closeSync(file);
  }
}

ExampleFunction();

```


## openDLPFile

```TypeScript
function openDLPFile(ciphertextFd: number, appId: string, callback: AsyncCallback<DLPFile>): void
```

DLP管理应用调用该接口，打开DLP文件。使用callback异步回调。调用成功后返回DLPFile管理对象，可用于管理DLP文件的权限和进行相关操作。使用完DLPFile对象后，应调用closeDLPFile释放对象，避免资
源泄露。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ciphertextFd | number | 是 | 加密文件的fd。 |
| appId | string | 是 | 调用方身份。最小8字节，最大1024字节。超出范围时返回错误码19100001。 |
| callback | AsyncCallback&lt;DLPFile&gt; | 是 | 回调函数。用于接收打开DLP文件的结果。回调参数包括：err（错误对象，成功时为undefined）和res（DLPFile对象，表示打<br/>开的DLP文件）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Nonsystem) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100002](../../errorcode-universal.md#19100002-Credential) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../../errorcode-universal.md#19100003-Credential) | Credential task time out. |
| [19100004](../../errorcode-universal.md#19100004-Credential) | Credential service error. |
| [19100005](../../errorcode-universal.md#19100005-Credential) | Credential authentication server error. |
| [19100008](../../errorcode-universal.md#19100008-The) | The file is not a DLP file. |
| [19100009](../../errorcode-universal.md#19100009-Failed) | Failed to operate the DLP file. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |
| [19100018](../../errorcode-universal.md#19100018-The) | The application is not authorized. |
| [19100019](../../errorcode-universal.md#19100019-The) | The DLP file has expired. |
| [19100020](../../errorcode-universal.md#19100020-No) | No network connection. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';
import { bundleManager } from '@kit.AbilityKit';

let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
let file: number | undefined = undefined;
let bundleFlags = bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_SIGNATURE_INFO;
let appId = '';
let bundleName = 'com.ohos.note';
let userId = 100;

let data = bundleManager.getBundleInfoSync(bundleName, bundleFlags, userId);
appId = data.signatureInfo.appId; // appId通过应用包信息获取

file = fileIo.openSync(uri).fd; // file通过文件打开获取fd
dlpPermission.openDLPFile(file, appId, (err, res) => { // 打开DLP文件。
  if (err !== undefined) {
    console.error('openDLPFile error,', err.code, err.message);
  } else {
    console.info('res', JSON.stringify(res));
  }
  if (file) {
    fileIo.closeSync(file);
  }
});

```

