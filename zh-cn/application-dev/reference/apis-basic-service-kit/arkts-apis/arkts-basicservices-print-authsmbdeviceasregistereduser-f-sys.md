# authSmbDeviceAsRegisteredUser（系统接口）

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## authSmbDeviceAsRegisteredUser

```TypeScript
function authSmbDeviceAsRegisteredUser(host: SharedHost, username: string, password: string): Promise<PrinterInformation[]>
```

以注册用户身份对SMB设备进行身份验证，并获取可用打印机。

**起始版本：** 24

**需要权限：** ohos.permission.MANAGE_PRINT_JOB

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-print-function authSmbDeviceAsRegisteredUser(host: SharedHost, username: string, password: string): Promise<PrinterInformation[]>--><!--Device-print-function authSmbDeviceAsRegisteredUser(host: SharedHost, username: string, password: string): Promise<PrinterInformation[]>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | [SharedHost](arkts-basicservices-print-sharedhost-i.md) | 是 | 要进行身份验证的SMB主机。 |
| username | string | 是 | 用于鉴权的用户名。 |
| password | string | 是 | 用于身份验证的密码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PrinterInformation[]> | Promise that resolves with the list of available printers. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | the application does not have permission to call this function. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| 13100012 | SMB account is locked due to multiple failed login attempts. |
| 13100013 | SMB connection failed (network error, host unreachable, or port blocked). |
| 13100014 | Invalid login account or password. |

