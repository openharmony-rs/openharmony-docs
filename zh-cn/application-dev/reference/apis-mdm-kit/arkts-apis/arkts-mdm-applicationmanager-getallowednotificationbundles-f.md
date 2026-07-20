# getAllowedNotificationBundles

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

<a id="getallowednotificationbundles"></a>
## getAllowedNotificationBundles

```TypeScript
function getAllowedNotificationBundles(admin: Want | null, accountId: number): Array<string>
```

获取允许发送通知的应用名单。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getAllowedNotificationBundles(admin: Want | null, accountId: number): Array<string>--><!--Device-applicationManager-function getAllowedNotificationBundles(admin: Want | null, accountId: number): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br>accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回允许发送通知的应用包名数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<string> = applicationManager.getAllowedNotificationBundles(wantTemp, 100);
  console.info(`Succeeded in getting allowed notification bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed notification bundles. Code is ${err.code}, message is ${err.message}`);
}

```

