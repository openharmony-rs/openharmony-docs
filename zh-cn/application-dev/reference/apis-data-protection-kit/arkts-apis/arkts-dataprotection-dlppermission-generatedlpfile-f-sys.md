# generateDLPFile（系统接口）

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

<a id="generatedlpfile"></a>
## generateDLPFile

```TypeScript
function generateDLPFile(plaintextFd: number, ciphertextFd: number, property: DLPProperty): Promise<DLPFile>
```

DLP管理应用调用该接口，将明文文件加密生成DLPFile管理对象，对象仅在授权列表内的用户可以打开，授权又分为完全控制权限和只读权限。使用Promise异步回调。

调用generateDLPFile成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile释放资源。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-dlpPermission-function generateDLPFile(plaintextFd: number, ciphertextFd: number, property: DLPProperty): Promise<DLPFile>--><!--Device-dlpPermission-function generateDLPFile(plaintextFd: number, ciphertextFd: number, property: DLPProperty): Promise<DLPFile>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| plaintextFd | number | 是 | 待加密明文文件的fd。取值范围为[0, 2<sup>31</sup>-1]。当fd小于0时，打印错误日志，函数停止运行；当fd大于2<sup>31</sup>-1时，fd的值被截断。 |
| ciphertextFd | number | 是 | 目标加密文件的fd。取值范围为[0, 2<sup>31</sup>-1]。当fd小于0时，打印错误日志，函数停止运行；当fd大于2<sup>31</sup>-1时，fd的值被截断。 |
| property | [DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i-sys.md) | 是 | 授权用户信息：授权用户列表、owner账号、联系人账号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DLPFile&gt; | Promise对象。resolve时返回DLPFile对象表示成功生成DLP文件，reject时抛出错误表示失败。 |

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
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

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


<a id="generatedlpfile-1"></a>
## generateDLPFile

```TypeScript
function generateDLPFile(plaintextFd: number, ciphertextFd: number, property: DLPProperty, callback: AsyncCallback<DLPFile>): void
```

DLP管理应用调用该接口，将明文文件加密生成权限受控文件，仅在授权列表内的用户可以打开，授权又分为完全控制权限和只读权限。获取DLPFile管理对象，使用callback异步回调。使用完DLPFile对象后，应调用closeDLPFile释放对象，避免资源泄露。

调用generateDLPFile()成功后返回DLPFile对象，必须在使用完毕后调用closeDLPFile()释放资源。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-dlpPermission-function generateDLPFile(plaintextFd: number, ciphertextFd: number, property: DLPProperty, callback: AsyncCallback<DLPFile>): void--><!--Device-dlpPermission-function generateDLPFile(plaintextFd: number, ciphertextFd: number, property: DLPProperty, callback: AsyncCallback<DLPFile>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| plaintextFd | number | 是 | 待加密明文文件的fd。取值范围为[0, 2<sup>31</sup>-1]。当fd小于0时，打印错误日志，函数停止运行；当fd大于2<sup>31</sup>-1时，fd的值被截断。 |
| ciphertextFd | number | 是 | 目标加密文件的fd。取值范围为[0, 2<sup>31</sup>-1]。当fd小于0时，打印错误日志，函数停止运行；当fd大于2<sup>31</sup>-1时，fd的值被截断。 |
| property | [DLPProperty](arkts-dataprotection-dlppermission-dlpproperty-i-sys.md) | 是 | 授权用户信息：授权用户列表、owner账号、联系人账号。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DLPFile&gt; | 是 | 回调函数。当生成DLP文件成功，err为undefined，data为获取到的DLP文件信息；否则为错误对象。 |

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
| [19100009](../errorcode-dlp.md#19100009-操作dlp文件失败) | Failed to operate the DLP file. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

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

