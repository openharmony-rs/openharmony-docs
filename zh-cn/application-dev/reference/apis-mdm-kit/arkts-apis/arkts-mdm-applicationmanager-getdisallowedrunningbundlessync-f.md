# getDisallowedRunningBundlesSync

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getDisallowedRunningBundlesSync

```TypeScript
function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array<string>
```

获取当前/指定用户下的应用运行禁止名单。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array<string>--><!--Device-applicationManager-function getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 否 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-2)等接口来获取。<br/>  - 调用接口时，若传入accountId，表示指定用户。<br/> - 调用接口时，若未传入accountId，表示当前用户。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<string> | 返回当前/指定用户下的应用运行禁止名单。<br/>**说明：** API version 20及之前版本，返回值为应用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)列表。从API version 21版本开始，返回值为应用[appId](../../../../quick-start/common-problem-of-application.md#什么是appid)或[appIdentifier](../../../../quick-start/common-problem-of-application.md#什么是appidentifier)列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

