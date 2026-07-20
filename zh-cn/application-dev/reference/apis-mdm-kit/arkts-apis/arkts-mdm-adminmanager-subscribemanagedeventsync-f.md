# subscribeManagedEventSync

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

<a id="subscribemanagedeventsync"></a>
## subscribeManagedEventSync

```TypeScript
function subscribeManagedEventSync(admin: Want, managedEvents: Array<ManagedEvent>): void
```

订阅系统管理事件。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_SUBSCRIBE_MANAGED_EVENT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function subscribeManagedEventSync(admin: Want, managedEvents: Array<ManagedEvent>): void--><!--Device-adminManager-function subscribeManagedEventSync(admin: Want, managedEvents: Array<ManagedEvent>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| managedEvents | Array&lt;ManagedEvent&gt; | 是 | 订阅事件数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device.<br>**适用版本：** 26.0.0+ |
| [9200008](../errorcode-enterpriseDeviceManager.md#9200008-系统订阅事件无效) | The specified system event is invalid. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let events: Array<adminManager.ManagedEvent> = [adminManager.ManagedEvent.MANAGED_EVENT_BUNDLE_ADDED, adminManager.ManagedEvent.MANAGED_EVENT_BUNDLE_REMOVED];

try {
  adminManager.subscribeManagedEventSync(wantTemp, events);
  console.info('Succeeded in subscribing managed event.');
} catch (err) {
  console.error(`Failed to subscribe managed event. Code: ${err.code}, message: ${err.message}`);
}

```

