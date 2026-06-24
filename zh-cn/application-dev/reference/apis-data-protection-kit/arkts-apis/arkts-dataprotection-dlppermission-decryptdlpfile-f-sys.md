# decryptDlpFile（系统接口）

## decryptDlpFile

```TypeScript
function decryptDlpFile(dlpFd: number, plaintextFd: number): Promise<void>
```

将DLP文件解密生成明文文件，仅支持企业账号调用。使用Promise异步回调。

该接口用于将DLP加密文件解密为明文文件，适用于拥有者权限用户导出或迁移文件。

> **说明：**
>
> 该接口仅支持企业账号调用，需要企业自行搭建企业账号服务器配套使用。由企业服务器管控账号是否有权限解密DLP文件。

**起始版本：** 21

**需要权限：** ohos.permission.ENTERPRISE_ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dlpFd | number | 是 | 待解密DLP文件的fd。取值范围为[0, 231-1]。当fd小于0时，函数抛出错误码19100001；当fd大于231-1时，<br/>fd的值被截断。 |
| plaintextFd | number | 是 | 目标解密文件的fd。取值范围为[0, 231-1]。当fd小于0时，函数抛出错误码19100001；当fd大于231-<br/>1时，fd的值被截断。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Nonsystem) | Non-system applications use system APIs.&lt;br&gt;**适用版本：** 20 - 20 |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100002](../../errorcode-universal.md#19100002-Credential) | Credential service busy due to too many tasks or duplicate tasks. |
| [19100003](../../errorcode-universal.md#19100003-Credential) | Credential task time out. |
| [19100004](../../errorcode-universal.md#19100004-Credential) | Credential service error. |
| [19100005](../../errorcode-universal.md#19100005-Credential) | Credential authentication server error. |
| [19100008](../../errorcode-universal.md#19100008-The) | The file is not a DLP file. |
| [19100009](../../errorcode-universal.md#19100009-Failed) | Failed to operate the DLP file. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |
| [19100013](../../errorcode-universal.md#19100013-The) | The user does not have the permission. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { fileIo } from '@kit.CoreFileKit';

let plaintextFd: number | undefined = undefined;
let dlpFd: number | undefined = undefined;
let plainFilePath: string = "file://docs/storage/Users/currentUser/Documents/test.txt";
let dlpFilePath: string = "file://docs/storage/Users/currentUser/Documents/test.txt.dlp";
plaintextFd = fileIo.openSync(plainFilePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE).fd; // 打开目标明文文件。
dlpFd = fileIo.openSync(dlpFilePath, fileIo.OpenMode.READ_ONLY).fd; // 打开待解密DLP文件。
dlpPermission.decryptDlpFile(dlpFd, plaintextFd).then((res) => {
  console.info('Successfully decrypt DLP file.');
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
}).finally(()=>{
  if (dlpFd) {
    fileIo.closeSync(dlpFd);
  }
  if (plaintextFd) {
    fileIo.closeSync(plaintextFd);
  }
});

```

