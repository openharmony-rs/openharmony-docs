# removeDisallowedNearLinkProtocols

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## removeDisallowedNearLinkProtocols

```TypeScript
function removeDisallowedNearLinkProtocols(admin: Want, protocols: Array<NearLinkProtocol>, accountId: number): void
```

为指定用户移除禁用的星闪协议名单。移除成功后，指定用户可以重新使用移除列表中的星闪协议进行通信，恢复相应的协议连接能力。使用场景：在企业设备管理场景下，管理员可通过此接口移除之前设置的星闪协议禁用策略，允许用户恢复使用星闪协议进行 设备间通信。适用于需要恢复特定用户星闪通信能力的场景，帮助企业管理员灵活调整用户设备的星闪协议访问权限，满足不同业务场景的通信需求。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function removeDisallowedNearLinkProtocols(admin: Want, protocols: Array<NearLinkProtocol>, accountId: number): void--><!--Device-systemManager-function removeDisallowedNearLinkProtocols(admin: Want, protocols: Array<NearLinkProtocol>, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| protocols | Array&lt;[NearLinkProtocol](arkts-mdm-systemmanager-nearlinkprotocol-e.md)&gt; | 是 | 星闪协议列表。 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。<br/>accountId可以通过 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 需根据实际情况进行替换
let protocols: systemManager.NearLinkProtocol[] = [systemManager.NearLinkProtocol.SSAP,
  systemManager.NearLinkProtocol.DATA_TRANSFER];

// 需根据实际情况进行替换
let accountId: number = 100;
try {
  systemManager.removeDisallowedNearLinkProtocols(wantTemp, protocols, accountId);
  console.info('Succeeded in removing the disabled Starlink protocol list for the specified user.');
} catch (err) {
  console.error(`Failed to remove the disabled Starlink protocol list for the specified user. Code is ${err.code}, message is ${err.message}`);
}
```

