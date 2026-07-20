# getAllowedInstallBundlesSync

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

<a id="getallowedinstallbundlessync"></a>
## getAllowedInstallBundlesSync

```TypeScript
function getAllowedInstallBundlesSync(admin: Want, accountId?: number): Array<string>
```

获取当前/指定用户下的应用程序包安装允许名单。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getAllowedInstallBundlesSync(admin: Want, accountId?: number): Array<string>--><!--Device-bundleManager-function getAllowedInstallBundlesSync(admin: Want, accountId?: number): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 否 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。<br>   - 调用接口时，若传入accountId，表示指定用户。<br> - 调用接口时，若未传入accountId，表示当前用户。*@ohos.account.osAccount** to obtain the account ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回当前用户下的应用程序包安装允许名单。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

