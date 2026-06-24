# installForResult

## installForResult

```TypeScript
function installForResult(admin: Want, hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

��װӦ��

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ��� |
| hapFilePaths | Array&lt;string&gt; | 是 | Ӧ�ð�·�� |
| installParam | InstallParam | 否 | ��װ���� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Ӧ�ð�װ��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9201002](../../errorcode-universal.md#9201002-Failed) | Failed to install the application. |
| [9201022](../../errorcode-universal.md#9201022-Failed) | Failed to install the HAP because of insufficient system disk space. |
| [9201023](../../errorcode-universal.md#9201023-Failed) | Failed to install the HAP because enterprise device management disallows the<br/>installation. |
| [9201024](../../errorcode-universal.md#9201024-Failed) | Failed to install the HAP because the HAP fails to be parsed. |
| [9201025](../../errorcode-universal.md#9201025-Failed) | Failed to install the HAP because the HAP signature fails to be verified. |
| [9201026](../../errorcode-universal.md#9201026-Failed) | Failed to install the HAP because the HAP path is invalid or<br/>the HAP is too large. |
| [9201027](../../errorcode-universal.md#9201027-Failed) | Failed to install the HAPs because they have different configuration<br/>information. |
| [9201028](../../errorcode-universal.md#9201028-Failed) | Failed to install the HAP because the isolationMode configured is not<br/>supported. |
| [9201029](../../errorcode-universal.md#9201029-Failed) | Failed to install the HAP since the version of the HAP to install is too early. |
| [9201030](../../errorcode-universal.md#9201030-Failed) | Failed to install the HAP because the VersionCode to be updated is not greater<br/>than the current VersionCode. |
| [9201031](../../errorcode-universal.md#9201031-Installation) | Installation failed because the dependant module does not exist. |
| [9201032](../../errorcode-universal.md#9201032-The) | The specified user ID is not found. |
| [9201033](../../errorcode-universal.md#9201033-Failed) | Failed to install the HAP because the overlay check failed. |
| [9201034](../../errorcode-universal.md#9201034-Failed) | Failed to install the HSP due to missing required permissions. |
| [9201035](../../errorcode-universal.md#9201035-Installation) | Installation failed because the installation of cross-app shared libraries is<br/>not allowed. |
| [9201036](../../errorcode-universal.md#9201036-Failed) | Failed to install the HAP due to incorrect URI in the data proxy. |
| [9201037](../../errorcode-universal.md#9201037-Failed) | Failed to install the HAP due to incorrect permission configuration in<br/>the data proxy. |
| [9201038](../../errorcode-universal.md#9201038-Failed) | Failed to install the HAP due to code signature verification failure. |
| [9201039](../../errorcode-universal.md#9201039-Failed) | Failed to install the HAP due to enterprise device verification failure. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

