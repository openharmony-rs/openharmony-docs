# installForResult

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## installForResult

```TypeScript
function installForResult(admin: Want, hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>
```

安装指定路径下的应用包，并返回安装结果。使用Promise异步回调。 此接口只能安装分发类型为enterprise_mdm（MDM应用）和enterprise_normal（普通企业应用）类型的应用，可以通过 [getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md)接口查询应用自身的 BundleInfo，其中BundleInfo.appInfo.appDistributionType为应用的分发类型。 > **说明：** > > 该接口比较耗时，当调用此接口后，后续如果在应用主线程调用其他同步接口时需要等待该接口异步返回。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function installForResult(admin: Want, hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>--><!--Device-bundleManager-function installForResult(admin: Want, hapFilePaths: Array<string>, installParam?: InstallParam): Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| hapFilePaths | Array&lt;string&gt; | 是 | 待安装应用包路径数组。应用包路径为应用沙箱路径(应用沙箱路径和真实路径的对应关系可参见： [应用沙箱路径和真实物理路径的对应关系](../../../file-management/app-sandbox-directory.md#应用沙箱路径和真实物理路径的对应关系))等应用有权限访问的路径。 |
| installParam | InstallParam | 否 | 应用包安装参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。当应用程序包安装失败时，抛出错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9201036](../errorcode-enterpriseDeviceManager.md#9201036-数据代理uri错误导致应用安装失败) | Failed to install the HAP due to incorrect URI in the data proxy. |
| [9201037](../errorcode-enterpriseDeviceManager.md#9201037-数据代理权限配置错误导致应用安装失败) | Failed to install the HAP due to incorrect permission configuration in the data proxy. |
| [9201038](../errorcode-enterpriseDeviceManager.md#9201038-代码签名验证失败导致应用安装失败) | Failed to install the HAP due to code signature verification failure. |
| [9201039](../errorcode-enterpriseDeviceManager.md#9201039-企业设备验证失败导致应用安装失败) | Failed to install the HAP due to enterprise device verification failure. |
| [9201032](../errorcode-enterpriseDeviceManager.md#9201032-指定用户id不存在) | The specified user ID is not found. |
| [9201033](../errorcode-enterpriseDeviceManager.md#9201033-overlay检查失败导致应用安装失败) | Failed to install the HAP because the overlay check failed. |
| [9201002](../errorcode-enterpriseDeviceManager.md#9201002-企业应用安装失败) | Failed to install the application. |
| [9201034](../errorcode-enterpriseDeviceManager.md#9201034-hsp缺少必需权限导致应用安装失败) | Failed to install the HSP due to missing required permissions. |
| [9201035](../errorcode-enterpriseDeviceManager.md#9201035-跨应用共享库安装不被允许导致应用安装失败) | Installation failed because the installation of cross-app shared libraries is not allowed. |
| [9201028](../errorcode-enterpriseDeviceManager.md#9201028-isolationmode配置不支持导致应用安装失败) | Failed to install the HAP because the isolationMode configured is not supported. |
| [9201029](../errorcode-enterpriseDeviceManager.md#9201029-hap版本过低导致应用安装失败) | Failed to install the HAP since the version of the HAP to install is too early. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9201030](../errorcode-enterpriseDeviceManager.md#9201030-versioncode不大于当前版本导致应用安装失败) | Failed to install the HAP because the VersionCode to be updated is not greater than the current VersionCode. |
| [9201031](../errorcode-enterpriseDeviceManager.md#9201031-依赖模块不存在导致应用安装失败) | Installation failed because the dependent module does not exist. |
| [9201024](../errorcode-enterpriseDeviceManager.md#9201024-hap解析失败导致应用安装失败) | Failed to install the HAP because the HAP fails to be parsed. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9201025](../errorcode-enterpriseDeviceManager.md#9201025-hap签名验证失败导致应用安装失败) | Failed to install the HAP because the HAP signature fails to be verified. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9201026](../errorcode-enterpriseDeviceManager.md#9201026-hap路径无效或文件过大导致应用安装失败) | Failed to install the HAP because the HAP path is invalid or the HAP is too large. |
| [9201027](../errorcode-enterpriseDeviceManager.md#9201027-hap配置信息不一致导致安装失败) | Failed to install the HAPs because they have different configuration information. |
| [9201022](../errorcode-enterpriseDeviceManager.md#9201022-系统磁盘空间不足导致应用安装失败) | Failed to install the HAP because of insufficient system disk space. |
| [9201023](../errorcode-enterpriseDeviceManager.md#9201023-企业设备管理禁止安装导致应用安装失败) | Failed to install the HAP because enterprise device management disallows the installation. |

