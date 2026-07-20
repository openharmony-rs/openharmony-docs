# getInstallationAllowedAppDistributionTypes

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

<a id="getinstallationallowedappdistributiontypes"></a>
## getInstallationAllowedAppDistributionTypes

```TypeScript
function getInstallationAllowedAppDistributionTypes(admin: Want): Array<AppDistributionType>
```

获取可安装的应用程序签名证书的分发类型。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getInstallationAllowedAppDistributionTypes(admin: Want): Array<AppDistributionType>--><!--Device-bundleManager-function getInstallationAllowedAppDistributionTypes(admin: Want): Array<AppDistributionType>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;AppDistributionType&gt; | 应用程序签名证书的分发类型数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

