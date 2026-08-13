# addAllowedNotificationBundles

## addAllowedNotificationBundles

```TypeScript
function addAllowedNotificationBundles(admin: Want, bundleNames: Array<string>, accountId: number): void
```

添加允许发送通知的应用名单。设置通知允许名单后，不在此名单内的应用无法发送通知。 > **说明：** > > 1.如果Kiosk模式与通知允许名单策略同时设置，那么设置Kiosk模式的应用与通知允许名单中的应用都可以发送通知。 > 2.当已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy)设置了禁用设备通知能力时，再通 > 过本接口设置通知允许名单，会抛出错误码9200010。 > 3.通知允许名单对系统服务不生效，系统服务始终可以发送通知。系统应用受通知允许名单管控。 > 4.支持跨用户设置，设置后跨用户立即生效。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addAllowedNotificationBundles(admin: Want, bundleNames: Array<string>, accountId: number): void--><!--Device-applicationManager-function addAllowedNotificationBundles(admin: Want, bundleNames: Array<string>, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| bundleNames | Array&lt;string&gt; | 是 | 应用包名数组，指定允许发送通知的应用。最多支持200个应用。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。 &lt;br&gt;accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId)等接口来获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-策略冲突) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

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
  applicationManager.addAllowedNotificationBundles(wantTemp, bundleNames, 100);
  console.info('Succeeded in adding allowed notification bundles.');
} catch (err) {
  console.error(`Failed to add allowed notification bundles. Code is ${err.code}, message is ${err.message}`);
}
```

