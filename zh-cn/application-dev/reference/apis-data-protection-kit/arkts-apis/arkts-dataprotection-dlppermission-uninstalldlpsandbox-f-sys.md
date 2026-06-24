# uninstallDLPSandbox（系统接口）

## uninstallDLPSandbox

```TypeScript
function uninstallDLPSandbox(bundleName: string, userId: number, appIndex: number): Promise<void>
```

卸载一个应用的DLP沙箱。使用Promise异步回调。调用成功后，系统销毁指定的DLP沙箱环境并释放相关资源。

需要清理对应的沙箱环境时使用此接口。

必须在调用installDLPSandbox安装沙箱后才能调用此方法卸载。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。最小7字节，最大128字节。超出范围时抛出错误码19100001。 |
| userId | number | 是 | 当前的用户ID，通过账号子系统获取的系统账号ID，默认主用户ID：100。超出范围时抛出错误码19100001。 |
| appIndex | number | 是 | DLP沙箱号，即installDLPSandbox接口调用成功后的返回值，用于标识已安装的DLP沙箱。超出范围时抛出错误码19100001。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Nonsystem) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
dlpPermission.installDLPSandbox('com.ohos.note', dlpPermission.DLPFileAccess.READ_ONLY, 100,
  uri).then(async (dlpSandboxInfo: dlpPermission.DLPSandboxInfo) => {
  console.info('dlpSandboxInfo：', JSON.stringify(dlpSandboxInfo));
  await dlpPermission.uninstallDLPSandbox('com.ohos.note', 100, dlpSandboxInfo.appIndex); // 卸载DLP沙箱。
}).catch((error: BusinessError)=> {
  console.error(error.message);
}); // 安装后卸载DLP沙箱。

```


## uninstallDLPSandbox

```TypeScript
function uninstallDLPSandbox(bundleName: string, userId: number, appIndex: number, callback: AsyncCallback<void>): void
```

卸载一个应用的DLP沙箱。使用callback异步回调。调用成功后，系统销毁指定的DLP沙箱环境并释放相关资源。

需要清理沙箱环境时使用此接口。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。最小7字节，最大128字节。超出范围时抛出错误码19100001。 |
| userId | number | 是 | 当前的用户ID，通过账号子系统获取的系统账号ID，默认主用户ID：100。超出范围时抛出错误码19100001。 |
| appIndex | number | 是 | DLP沙箱号，即installDLPSandbox接口调用成功后的返回值，用于标识已安装的DLP沙箱。取值范围为[1000, 1100]。超出范围时抛出错误码<br/>19100001。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，用于接收卸载结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Nonsystem) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br/>2. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

let uri = 'file://docs/storage/Users/currentUser/Desktop/test.txt.dlp';
dlpPermission.installDLPSandbox('com.ohos.note', dlpPermission.DLPFileAccess.READ_ONLY, 100,
  uri).then((dlpSandboxInfo: dlpPermission.DLPSandboxInfo) => {
  console.info('dlpSandboxInfo：', JSON.stringify(dlpSandboxInfo));
  dlpPermission.uninstallDLPSandbox('com.ohos.note', 100, dlpSandboxInfo.appIndex, (err, res) => {
    if (err !== undefined) {
      console.error('uninstallDLPSandbox error,', err.code, err.message);
    } else {
      console.info('res', JSON.stringify(res));
    }
  }); // 卸载DLP沙箱。
}).catch((error: BusinessError)=> {
  console.error(error.message);
}); // 安装后卸载DLP沙箱。

```

