# installForResult

## installForResult

```TypeScript
function installForResult(admin: Want, hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

安装应用

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件 |
| hapFilePaths | Array&lt;string&gt; | 是 | 应用包路径 |
| installParam | InstallParam | 否 | 安装参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 应用安装结果 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9201002](../errorcode-enterpriseDeviceManager.md#9201002-企业应用安装失败) | Failed to install the application. |
| [9201022](../errorcode-enterpriseDeviceManager.md#9201022-系统磁盘空间不足导致应用安装失败) | Failed to install the HAP because of insufficient system disk space. |
| [9201023](../errorcode-enterpriseDeviceManager.md#9201023-企业设备管理禁止安装导致应用安装失败) | Failed to install the HAP because enterprise device management disallows theinstallation. |
| [9201024](../errorcode-enterpriseDeviceManager.md#9201024-hap解析失败导致应用安装失败) | Failed to install the HAP because the HAP fails to be parsed. |
| [9201025](../errorcode-enterpriseDeviceManager.md#9201025-hap签名验证失败导致应用安装失败) | Failed to install the HAP because the HAP signature fails to be verified. |
| [9201026](../errorcode-enterpriseDeviceManager.md#9201026-hap路径无效或文件过大导致应用安装失败) | Failed to install the HAP because the HAP path is invalid orthe HAP is too large. |
| [9201027](../errorcode-enterpriseDeviceManager.md#9201027-hap配置信息不一致导致安装失败) | Failed to install the HAPs because they have different configurationinformation. |
| [9201028](../errorcode-enterpriseDeviceManager.md#9201028-isolationmode配置不支持导致应用安装失败) | Failed to install the HAP because the isolationMode configured is notsupported. |
| [9201029](../errorcode-enterpriseDeviceManager.md#9201029-hap版本过低导致应用安装失败) | Failed to install the HAP since the version of the HAP to install is too early. |
| [9201030](../errorcode-enterpriseDeviceManager.md#9201030-versioncode不大于当前版本导致应用安装失败) | Failed to install the HAP because the VersionCode to be updated is not greaterthan the current VersionCode. |
| [9201031](../errorcode-enterpriseDeviceManager.md#9201031-依赖模块不存在导致应用安装失败) | Installation failed because the dependant module does not exist. |
| [9201032](../errorcode-enterpriseDeviceManager.md#9201032-指定用户id不存在) | The specified user ID is not found. |
| [9201033](../errorcode-enterpriseDeviceManager.md#9201033-overlay检查失败导致应用安装失败) | Failed to install the HAP because the overlay check failed. |
| [9201034](../errorcode-enterpriseDeviceManager.md#9201034-hsp缺少必需权限导致应用安装失败) | Failed to install the HSP due to missing required permissions. |
| [9201035](../errorcode-enterpriseDeviceManager.md#9201035-跨应用共享库安装不被允许导致应用安装失败) | Installation failed because the installation of cross-app shared libraries isnot allowed. |
| [9201036](../errorcode-enterpriseDeviceManager.md#9201036-数据代理uri错误导致应用安装失败) | Failed to install the HAP due to incorrect URI in the data proxy. |
| [9201037](../errorcode-enterpriseDeviceManager.md#9201037-数据代理权限配置错误导致应用安装失败) | Failed to install the HAP due to incorrect permission configuration inthe data proxy. |
| [9201038](../errorcode-enterpriseDeviceManager.md#9201038-代码签名验证失败导致应用安装失败) | Failed to install the HAP due to code signature verification failure. |
| [9201039](../errorcode-enterpriseDeviceManager.md#9201039-企业设备验证失败导致应用安装失败) | Failed to install the HAP due to enterprise device verification failure. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

