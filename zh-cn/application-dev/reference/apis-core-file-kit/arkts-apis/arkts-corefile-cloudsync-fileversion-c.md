# FileVersion

�����ļ��汾�����ࡣ֧�ֶԶ����ļ�����ʷ�汾���й������ṩ��ȡ�ļ���ʷ�汾��Ϣ�б���������ͨ����ʷ�汾��Ϣ���ɽ���ʷ�汾���ص����أ����ṩ��ʷ�汾�ļ��滻��ǰ�����ļ�����������԰汾��ͻ���ṩ��ѯ��ͻ��־�������ͻ��־��������

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## clearFileConflict

```TypeScript
clearFileConflict(uri: string): Promise<void>
```

��������ļ��汾��ͻ��־�����������ͻ�����ؽ����ͻ����Ҫ���ô˷����������ͻ��ǣ������ſ��Դ����Զ�ͬ�����ƣ������ϱ���һ�¡�ʹ��Promise�첽�ص���

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ͻ��־���ļ�URI�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied by the file system. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid URI. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

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

## constructor

```TypeScript
constructor()
```

A constructor used to create a FileVersion object.

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
let fileVersion = new cloudSync.FileVersion();

```

## downloadHistoryVersion

```TypeScript
downloadHistoryVersion(uri: string, versionId: string, callback: Callback<VersionDownloadProgress>): Promise<string>
```

���ݰ汾�Ż�ȡָ���ļ���ĳһ�汾���ļ����ݡ��û�ͨ���汾��ָ������ĳһ�汾���������ص�������ʱ�洢·������ʱ�ļ���Ӧ�����о����Ƿ��滻ԭʼ�ļ���Ҳ����ѡ������ֱ��ɾ����callback�����ļ����ؽ��ȣ�Promise������ʷ
�汾��ʱ�ļ���URI��

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �ļ���URI�� |
| versionId | string | 是 | �ļ�ĳһ�汾�İ汾�ţ���ʽ�Խӿ�<br/>[gethistoryversionlist](arkts-corefile-cloudsync-fileversion-c.md#getHistoryVersionList-1)����Ϊ׼�� |
| callback | Callback&lt;VersionDownloadProgress&gt; | 是 | �ص��������������ؽ��ȡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise���󣬷�����ʷ�汾��ʱ�洢�ļ���URI�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied by the file system. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid URI. |
| [22400002](../../errorcode-universal.md#22400002-Network) | Network unavailable. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

## getHistoryVersionList

```TypeScript
getHistoryVersionList(uri: string, versionNumLimit: number): Promise<Array<HistoryVersion>>
```

��ȡ��ʷ�汾�б����������ݰ��޸�ʱ�������޸�ʱ��Խ�磬λ��Խ����ʹ��Promise�첽�ص���

�����ϰ汾����С�ڴ���ĳ�������ʱ������ʵ�ʰ汾����������ʷ�汾�б���

�����ϰ汾�������ڵ��ڴ���ĳ�������ʱ���򷵻����µ�versionNumLimit���汾��

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �ļ���URI�� |
| versionNumLimit | number | 是 | ��ʷ�汾�б��������ƣ�ȡֵ��Χ[0, 100000]����λ��������������ֵ����100000ʱ���������ֵ�����б��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;HistoryVersion&gt;&gt; | Promise���󣬷�����ʷ�汾�б��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied by the file system. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid URI. |
| [22400002](../../errorcode-universal.md#22400002-Network) | Network unavailable. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

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

## isFileConflict

```TypeScript
isFileConflict(uri: string): Promise<boolean>
```

��ȡ�����ļ��汾��ͻ��־��ʹ��Promise�첽�ص����˷���ֻ��Ӧ���������ֶ����ͻ��Ż���Ч������Ĭ���Զ����ͻ������ֵΪfalse����ͬ�������Զ���ɽ��ͻ��

��Ӧ�������ֶ����ͻ�󣬵��ô˷����᷵�ص�ǰ�ļ��Ƿ����Ʋ��ļ�������ͻ��������Ӧ����ʾ�û��Գ�ͻ���д������ڳ�ͻ���ǰ�������Զ�ͬ�����ơ����������ͻ����Ҫ����
[clearFileConflict](arkts-corefile-cloudsync-fileversion-c.md#clearFileConflict-1)�����������ͻ��־�������Ż��������ͬ�������ƶ˱���һ�¡�

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �ļ���URI�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󣬷��ر����ļ����ƶ��ļ��ĳ�ͻ��־��true��ʾ��ͻ��false��ʾ����ͻ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied by the file system. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid URI. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

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

## replaceFileWithHistoryVersion

```TypeScript
replaceFileWithHistoryVersion(originalUri: string, versionUri: string): Promise<void>
```

�ṩʹ����ʷ�汾�ļ��滻�����ļ������������滻ǰ����Ҫ����[downloadHistoryVersion](arkts-corefile-cloudsync-fileversion-c.md#downloadHistoryVersion-1)������ѡ�����ʷ
�汾�������ز��õ�versionUri��ֱ�ӵ��ô˽ӿڻ���versionUri�Ƿ�������쳣���滻��ɺ��ɾ����ʱ�洢�ļ���ʹ��Promise�첽�ص���

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| originalUri | string | 是 | �����ļ���URI�� |
| versionUri | string | 是 | ��ʷ�汾�ļ���URI�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error. |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor. |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again. |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied by the file system. |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid URI. Possible causes: 1.originalUri invalid; 2.versionUri invalid. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| [22400007](../../errorcode-universal.md#22400007-The) | The version file specified to replace the original file does not exist. |

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

