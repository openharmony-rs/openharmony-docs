# FileVersion

端云文件版本管理类。支持对端云文件的历史版本进行管理，提供获取文件历史版本信息列表的能力，通过历史版本信息，可将历史版本下载到本地；并提供历史版本文件替换当前本地文件的能力，针对版本冲突，提供查询冲突标志，解除冲突标志的能力。

**起始版本：** 20

<!--Device-cloudSync-class FileVersion--><!--Device-cloudSync-class FileVersion-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

<a id="clearfileconflict"></a>
## clearFileConflict

```TypeScript
clearFileConflict(uri: string): Promise<void>
```

清除本地文件版本冲突标志。如果产生冲突，本地解决冲突后需要调用此方法来清除冲突标记，后续才可以触发自动同步机制，和云上保持一致。使用Promise异步回调。

**起始版本：** 20

<!--Device-FileVersion-clearFileConflict(uri: string): Promise<void>--><!--Device-FileVersion-clearFileConflict(uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待清除冲突标志的文件URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

let isConflict = false;
fileVersion.isFileConflict(uri).then((isConflictRet: boolean) => {
  isConflict = isConflictRet;
  console.info("current file is conflict: " + isConflictRet);
}).catch((err: BusinessError) => {
  console.error(`get current file conflict flag failed with error message: ${err.message}, error code: ${err.code}`);
});
fileVersion.clearFileConflict(uri).then(() => {
  console.info("clean file conflict flag success");
}).catch((err: BusinessError) => {
  console.error("clean file conflict flag failed with error message: " + err.message + ", error code: " + err.code);
});

```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

A constructor used to create a FileVersion object.

**起始版本：** 20

<!--Device-FileVersion-constructor()--><!--Device-FileVersion-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
let fileVersion = new cloudSync.FileVersion();

```

<a id="downloadhistoryversion"></a>
## downloadHistoryVersion

```TypeScript
downloadHistoryVersion(uri: string, versionId: string, callback: Callback<VersionDownloadProgress>): Promise<string>
```

根据版本号获取指定文件的某一版本的文件内容。用户通过版本号指定云上某一版本，将其下载到本地临时存储路径，临时文件由应用自行决定是否替换原始文件，也可以选择保留或直接删除。callback返回文件下载进度，Promise返回历史版本临时文件的URI。

**起始版本：** 20

<!--Device-FileVersion-downloadHistoryVersion(uri: string, versionId: string, callback: Callback<VersionDownloadProgress>): Promise<string>--><!--Device-FileVersion-downloadHistoryVersion(uri: string, versionId: string, callback: Callback<VersionDownloadProgress>): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 文件的URI。 |
| versionId | string | 是 | 文件某一版本的版本号，格式以接口[gethistoryversionlist](arkts-corefile-cloudsync-fileversion-c.md#gethistoryversionlist-1)返回为准。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;VersionDownloadProgress&gt; | 是 | 回调函数，返回下载进度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回历史版本临时存储文件的URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400002 | Network unavailable. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

<a id="gethistoryversionlist"></a>
## getHistoryVersionList

```TypeScript
getHistoryVersionList(uri: string, versionNumLimit: number): Promise<Array<HistoryVersion>>
```

获取历史版本列表，返回内容按修改时间排序，修改时间越早，位置越靠后。使用Promise异步回调。

当云上版本数量小于传入的长度限制时，按照实际版本数量返回历史版本列表。

当云上版本数量大于等于传入的长度限制时，则返回最新的versionNumLimit个版本。

**起始版本：** 20

<!--Device-FileVersion-getHistoryVersionList(uri: string, versionNumLimit: int): Promise<Array<HistoryVersion>>--><!--Device-FileVersion-getHistoryVersionList(uri: string, versionNumLimit: int): Promise<Array<HistoryVersion>>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 文件的URI。 |
| versionNumLimit | number | 是 | 历史版本列表长度限制，取值范围[0, 100000]（单位：个）。当输入值大于100000时，按照最大值返回列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;HistoryVersion&gt;&gt; | Promise对象，返回历史版本列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400002 | Network unavailable. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
let limit = 10;

fileVersion.getHistoryVersionList(uri, limit).then((versionList: Array<cloudSync.HistoryVersion>) => {
  for(let i = 0, len = versionList.length; i < len; i++) {
    console.info("get history versionId: " + versionList[i].versionId);
  }
}).catch((err: BusinessError) => {
  console.error("get history version failed with error message: " + err.message + ", error code: " + err.code);
});

```

<a id="isfileconflict"></a>
## isFileConflict

```TypeScript
isFileConflict(uri: string): Promise<boolean>
```

获取本地文件版本冲突标志。使用Promise异步回调。此方法只有应用在配置手动解冲突后才会生效，否则默认自动解冲突，返回值为false，由同步流程自动完成解冲突；

当应用配置手动解冲突后，调用此方法会返回当前文件是否与云侧文件产生冲突，并且由应用提示用户对冲突进行处理，在冲突解决前不会再自动同步上云。当处理完冲突后，需要调用[clearFileConflict](arkts-corefile-cloudsync-fileversion-c.md#clearfileconflict-1)方法来清除冲突标志，后续才会继续触发同步，与云端保持一致。

**起始版本：** 20

<!--Device-FileVersion-isFileConflict(uri: string): Promise<boolean>--><!--Device-FileVersion-isFileConflict(uri: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 文件的URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回本地文件和云端文件的冲突标志，true表示冲突，false表示不冲突。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

fileVersion.isFileConflict(uri).then((isConflict: boolean) => {
  console.info("current file is conflict: " + isConflict);
}).catch((err: BusinessError) => {
  console.error("get current file conflict flag failed with error message: " + err.message + ", error code: " + err.code);
});

```

<a id="replacefilewithhistoryversion"></a>
## replaceFileWithHistoryVersion

```TypeScript
replaceFileWithHistoryVersion(originalUri: string, versionUri: string): Promise<void>
```

提供使用历史版本文件替换本地文件的能力。在替换前，需要调用[downloadHistoryVersion](arkts-corefile-cloudsync-fileversion-c.md#downloadhistoryversion-1)方法对选择的历史版本进行下载并拿到versionUri；直接调用此接口或者versionUri非法会产生异常；替换完成后会删除临时存储文件。使用Promise异步回调。

**起始版本：** 20

<!--Device-FileVersion-replaceFileWithHistoryVersion(originalUri: string, versionUri: string): Promise<void>--><!--Device-FileVersion-replaceFileWithHistoryVersion(originalUri: string, versionUri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| originalUri | string | 是 | 本地文件的URI。 |
| versionUri | string | 是 | 历史版本文件的URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900010 | Try again. |
| 13900012 | Permission denied by the file system. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 14000002 | Invalid URI. Possible causes: 1.originalUri invalid; 2.versionUri invalid. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 22400007 | The version file specified to replace the original file does not exist. |

**示例：**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';
import { BusinessError } from '@kit.BasicServicesKit';

let fileVersion = new cloudSync.FileVersion();

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
let versionId = '123456'; // 以 getHistoryVersionList 方法返回的格式为准，此处仅作为 demo 示例。

let callback = (data: cloudSync.VersionDownloadProgress) => {
  if (data.state == cloudSync.State.RUNNING) {
    console.info("download progress: " + data.progress);
  } else if (data.state == cloudSync.State.FAILED) {
    console.info("download failed errType: " + data.errType);
  } else if (data.state == cloudSync.State.COMPLETED) {
    console.info("download version file success");
  }
};

let versionUri = "";
fileVersion.downloadHistoryVersion(uri, versionId, callback).then((fileUri: string) => {
  versionUri = fileUri;
  console.info("success to begin download, downloadFileUri: " + fileUri);
}).catch((err: BusinessError) => {
  console.error(`download history version file failed with error message: ${err.message}, error code: ${err.code}`);
});
fileVersion.replaceFileWithHistoryVersion(uri, versionUri).then(() => {
  console.info("replace file with history version success.");
}).catch((err: BusinessError) => {
  console.error("replace file with history version failed with error message: " + err.message + ", error code: " + err.code);
});

```

