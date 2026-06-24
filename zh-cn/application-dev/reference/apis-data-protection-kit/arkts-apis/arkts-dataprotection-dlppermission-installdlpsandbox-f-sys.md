# installDLPSandbox（系统接口）

## installDLPSandbox

```TypeScript
function installDLPSandbox(bundleName: string, access: DLPFileAccess, userId: number, uri: string): Promise<DLPSandboxInfo>
```

安装一个应用的DLP沙箱。DLP沙箱为受保护的DLP文件创建独立的运行环境，与原应用进程隔离，确保数据在授权范围内安全流转。沙箱应用继承原应用的功能但仅能访问授权的DLP文件。使用Promise异步回调。

调用installDLPSandbox成功后必须在使用完毕后调用uninstallDLPSandbox卸载沙箱。

DLP文件管理应用打开受保护文件前，需要先为目标应用安装DLP沙箱。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。最小7字节，最大128字节。超出范围时抛出错误码19100001。 |
| access | DLPFileAccess | 是 | DLP文件授权类型。设置不同的授权类型将决定用户对DLP文件的访问权限范围。超出范围时抛出错误码19100001。 |
| userId | number | 是 | 当前的用户ID，通过账号子系统获取的系统账号ID，默认主用户ID：100。传入无效值时抛出错误码19100001。 |
| uri | string | 是 | DLP文件的URI。不超过4095字节。超出范围时抛出错误码19100001。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DLPSandboxInfo&gt; | Promise对象。安装沙箱应用，返回应用沙箱信息。 |

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
  console.info('dlpSandboxInfo: ', JSON.stringify(dlpSandboxInfo));
}).catch((error: BusinessError)=> {
  console.error(error.message);
}); // 安装DLP沙箱。

```


## installDLPSandbox

```TypeScript
function installDLPSandbox(bundleName: string, access: DLPFileAccess, userId: number, uri: string, callback: AsyncCallback<DLPSandboxInfo>): void
```

安装一个应用的DLP沙箱。使用callback异步回调。调用成功后，系统为应用创建DLP沙箱环境并返回沙箱信息。

调用installDLPSandbox成功后必须在使用完毕后调用uninstallDLPSandbox卸载沙箱。

DLP文件管理应用打开受保护文件前，需要先为目标应用安装DLP沙箱。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。最小7字节，最大128字节。超出范围时抛出错误码19100001。 |
| access | DLPFileAccess | 是 | DLP文件授权类型。设置不同的授权类型将决定用户对DLP文件的访问权限范围。超出范围时抛出错误码19100001。 |
| userId | number | 是 | 当前的用户ID，通过账号子系统获取的系统账号ID，默认主用户ID：100。超出范围时抛出错误码19100001。 |
| uri | string | 是 | DLP文件的URI。不超过4095字节。 超出范围时抛出错误码19100001。 |
| callback | AsyncCallback&lt;DLPSandboxInfo&gt; | 是 | 回调函数，用于接收应用沙箱信息。回调参数包括：err（错误对象，成功时为undefined）和res（<br/>DLPSandboxInfo对象，包含应用沙箱信息）。 |

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
dlpPermission.installDLPSandbox('com.ohos.note', dlpPermission.DLPFileAccess.READ_ONLY, 100, uri, (err, res) => {
  if (err !== undefined) {
    console.error('installDLPSandbox error,', err.code, err.message);
  } else {
    console.info('res', JSON.stringify(res));
  }
}); // 安装DLP沙箱。

```

