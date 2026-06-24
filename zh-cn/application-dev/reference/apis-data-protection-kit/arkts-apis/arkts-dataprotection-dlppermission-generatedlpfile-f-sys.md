# generateDLPFile（系统接口）

## generateDLPFile

```TypeScript
function generateDLPFile(plaintextFd: number, ciphertextFd: number, property: DLPProperty): Promise<DLPFile>
```

DLP管理应用调用该接口，将明文文件加密生成DLPFile管理对象，对象仅在授权列表内的用户可以打开，授权又分为完全控制权限和只读权限。使用Promise异步回调。

调用generateDLPFile成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile释放资源。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| plaintextFd | number | 是 | 待加密明文文件的fd。取值范围为[0, 231-1]。超出范围时该数值会被截断。 |
| ciphertextFd | number | 是 | 目标加密文件的fd。取值范围为[0, 231-1]。超出范围时该数值会被截断。 |
| property | DLPProperty | 是 | 授权用户信息：授权用户列表、owner账号、联系人账号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DLPFile&gt; | Promise对象。resolve时返回DLPFile对象表示成功生成DLP文件，reject时抛出错误表示失败。 |

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
| [19100009](../../errorcode-universal.md#19100009-Failed) | Failed to operate the DLP file. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

async function ExampleFunction() {
  let dlpUri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
  let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt';
  let file: number | undefined = undefined;
  let dlp: number | undefined = undefined;
  let dlpFile: dlpPermission.DLPFile | undefined = undefined;

  file = fileIo.openSync(uri).fd;
  dlp = fileIo.openSync(dlpUri).fd;
  let dlpProperty: dlpPermission.DLPProperty = {
    ownerAccount: 'zhangsan',
    ownerAccountType: dlpPermission.AccountType.DOMAIN_ACCOUNT,
    authUserList: [],
    contactAccount: 'zhangsan',
    offlineAccess: true,
    ownerAccountID: 'xxxxxxx',
    everyoneAccessList: []
  };
  dlpFile = await dlpPermission.generateDLPFile(file, dlp, dlpProperty); // 生成DLP文件。

  dlpFile?.closeDLPFile(); // 关闭DLP对象。
  if (file) {
    fileIo.closeSync(file);
  }
  if (dlp) {
    fileIo.closeSync(dlp);
  }
}

ExampleFunction();

```


## generateDLPFile

```TypeScript
function generateDLPFile(plaintextFd: number, ciphertextFd: number, property: DLPProperty, callback: AsyncCallback<DLPFile>): void
```

DLP管理应用调用该接口，将明文文件加密生成权限受控文件，仅在授权列表内的用户可以打开，授权又分为完全控制权限和只读权限。获取DLPFile管理对象，使用callback异步回调。使用完DLPFile对象后，应调用
closeDLPFile释放对象，避免资源泄露。

调用generateDLPFile()成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile()释放资源。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| plaintextFd | number | 是 | 待加密明文文件的fd。取值范围为[0, 231-1]。超出范围时该数值会被截断。 |
| ciphertextFd | number | 是 | 目标加密文件的fd。取值范围为[0, 231-1]。超出范围时该数值会被截断。 |
| property | DLPProperty | 是 | 授权用户信息：授权用户列表、owner账号、联系人账号。 |
| callback | AsyncCallback&lt;DLPFile&gt; | 是 | 回调函数，用于接收生成DLP文件的结果。回调参数包括：err（错误对象，成功时为undefined）和res（DLPFile对象，表示生<br/>成的DLP文件）。 |

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
| [19100009](../../errorcode-universal.md#19100009-Failed) | Failed to operate the DLP file. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

let dlpUri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt';
let file: number | undefined = undefined;
let dlp: number | undefined = undefined;

file = fileIo.openSync(uri).fd;
dlp = fileIo.openSync(dlpUri).fd;
let dlpProperty: dlpPermission.DLPProperty = {
  ownerAccount: 'zhangsan',
  ownerAccountType: dlpPermission.AccountType.DOMAIN_ACCOUNT,
  authUserList: [],
  contactAccount: 'zhangsan',
  offlineAccess: true,
  ownerAccountID: 'xxxxxxx',
  everyoneAccessList: []
};
dlpPermission.generateDLPFile(file, dlp, dlpProperty, (err, res) => { // 生成DLP文件。
  if (err !== undefined) {
    console.error('generateDLPFile error,', err.code, err.message);
  } else {
    console.info('res', JSON.stringify(res));
  }
  fileIo.closeSync(file);
  fileIo.closeSync(dlp);
});

```

