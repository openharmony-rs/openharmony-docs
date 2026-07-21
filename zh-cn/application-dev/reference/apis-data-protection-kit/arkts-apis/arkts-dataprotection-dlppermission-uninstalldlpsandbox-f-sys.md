# uninstallDLPSandbox（系统接口）

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

<a id="uninstalldlpsandbox"></a>
## uninstallDLPSandbox

```TypeScript
function uninstallDLPSandbox(bundleName: string, userId: number, appIndex: number): Promise<void>
```

卸载一个应用的DLP沙箱。使用Promise异步回调。调用成功后，系统销毁指定的DLP沙箱环境并释放相关资源。

需要清理对应的沙箱环境时使用此接口。

必须在调用[installDLPSandbox](arkts-dataprotection-dlppermission-installdlpsandbox-f-sys.md#installdlpsandbox-1)安装沙箱后才能调用此方法卸载。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-dlpPermission-function uninstallDLPSandbox(bundleName: string, userId: number, appIndex: number): Promise<void>--><!--Device-dlpPermission-function uninstallDLPSandbox(bundleName: string, userId: number, appIndex: number): Promise<void>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。最小7字节，最大128字节。超出范围时抛出错误码401。 |
| userId | number | 是 | 当前的用户ID，通过账号子系统获取的系统账号ID，默认主用户ID：100。<br>取值范围为[0, 2<sup>31</sup>-1]，超出范围将被截断。当传入参数值小于0时，输出错误日志。 |
| appIndex | number | 是 | DLP沙箱号，即installDLPSandbox接口调用成功后的返回值，用于标识已安装的DLP沙箱。取值范围为[1000, 1100]，超出范围时输出错误日志。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

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


<a id="uninstalldlpsandbox-1"></a>
## uninstallDLPSandbox

```TypeScript
function uninstallDLPSandbox(bundleName: string, userId: number, appIndex: number, callback: AsyncCallback<void>): void
```

卸载一个应用的DLP沙箱。使用callback异步回调。调用成功后，系统销毁指定的DLP沙箱环境并释放相关资源。

需要清理沙箱环境时使用此接口。

必须在调用[installDLPSandbox](arkts-dataprotection-dlppermission-installdlpsandbox-f-sys.md#installdlpsandbox-1)安装沙箱后才能调用此方法卸载。

**起始版本：** 10

**需要权限：** ohos.permission.ACCESS_DLP_FILE

<!--Device-dlpPermission-function uninstallDLPSandbox(bundleName: string, userId: number, appIndex: number, callback: AsyncCallback<void>): void--><!--Device-dlpPermission-function uninstallDLPSandbox(bundleName: string, userId: number, appIndex: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。最小7字节，最大128字节。超出范围时抛出错误码401。 |
| userId | number | 是 | 当前的用户ID，通过账号子系统获取的系统账号ID，默认主用户ID：100。取值范围为[0, 2<sup>31</sup>-1]，超出范围将被截断。 |
| appIndex | number | 是 | DLP沙箱号，即installDLPSandbox接口调用成功后的返回值，用于标识已安装的DLP沙箱。取值范围为[1000, 1100]，超出范围时输出错误日志。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当卸载DLP沙箱成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

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

