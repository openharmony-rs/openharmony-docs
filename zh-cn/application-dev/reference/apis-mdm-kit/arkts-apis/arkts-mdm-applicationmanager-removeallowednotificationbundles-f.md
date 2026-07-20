# removeAllowedNotificationBundles

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

<a id="removeallowednotificationbundles"></a>
## removeAllowedNotificationBundles

```TypeScript
function removeAllowedNotificationBundles(admin: Want, bundleNames: Array<string>, accountId: number): void
```

从允许发送通知的应用名单中移除应用。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function removeAllowedNotificationBundles(admin: Want, bundleNames: Array<string>, accountId: number): void--><!--Device-applicationManager-function removeAllowedNotificationBundles(admin: Want, bundleNames: Array<string>, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleNames | Array&lt;string&gt; | 是 | 应用包名数组，指定需要移除的应用。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br> accountId可以通过@ohos.account.osAccount中的[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid-1)等接口来获取。 |

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

let bundleNames: Array<string> = ['com.example.notificationapp'];

try {
  applicationManager.removeAllowedNotificationBundles(wantTemp, bundleNames, 100);
  console.info('Succeeded in removing allowed notification bundles.');
} catch (err) {
  console.error(`Failed to remove allowed notification bundles. Code is ${err.code}, message is ${err.message}`);
}

```

