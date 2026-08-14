# removeFirewallRule

## removeFirewallRule

```TypeScript
function removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void
```

移除设备防火墙过滤规则。适用于企业网络安全策略调整场景，例如取消某些网络访问限制、调整防火墙策略、清理过时或无效的规则，帮助企业灵活调整网络安全策略，确保网络访问控制策略与实际需求保持一致。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md#LogType)。 移除规则后如果不存在[Action](arkts-mdm-networkmanager-action-e.md#Action)为ALLOW规则后，会将[addFirewallRule](arkts-mdm-networkmanager-addfirewallrule-f.md#addFirewallRule)添 加的默认DENY规则清空。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void--><!--Device-networkManager-function removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| firewallRule | [FirewallRule](arkts-mdm-networkmanager-firewallrule-i.md) | 否 | 移除防火墙过滤规则。值为空时，清空所有的防火墙规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let firewallRule: networkManager.FirewallRule = {
  // 需根据实际情况进行替换
  "srcAddr": "192.168.1.1-192.168.22.66",
  "destAddr": "10.1.1.1",
  "srcPort": "8080",
  "destPort": "8080",
  "appUid": "9696",
  "direction": networkManager.Direction.OUTPUT,
  "action": networkManager.Action.DENY,
  "protocol": networkManager.Protocol.UDP,
  "family": 1,
  "logType": networkManager.LogType.NFLOG
};

// 移除指定的规则
try {
  networkManager.removeFirewallRule(wantTemp, firewallRule);
  console.info('Succeeded in removing firewall rule.');
} catch (err) {
  console.error(`Failed to remove firewall rule. Code: ${err.code}, message: ${err.message}`);
}

// 清空IP协议版本为IPv4的所有规则
try {
  networkManager.removeFirewallRule(wantTemp);
  console.info('Succeeded in removing all firewall rule.');
} catch (err) {
  console.error(`Failed to remove all firewall rule. Code: ${err.code}, message: ${err.message}`);
}
```

