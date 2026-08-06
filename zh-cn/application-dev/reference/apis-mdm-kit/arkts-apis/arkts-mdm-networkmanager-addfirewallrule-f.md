# addFirewallRule

## addFirewallRule

```TypeScript
function addFirewallRule(admin: Want, firewallRule: FirewallRule): void
```

为设备添加防火墙过滤规则。适用于企业网络安全管控场景，例如限制特定IP地址的网络访问、防止恶意网络攻击、控制应用程序的网络通信、实现网络访问的允许名单或禁用名单管理，帮助企业精细化控制 网络访问，防止网络攻击和数据泄露。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 > **说明：** > > - 添加了[Action]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_为ALLOW规则后，将会默认添加DENY规则，不在ALLOW规则之内的网络数据包将会被丢弃或拦截。 > > - 设备重启，将会清空防火墙过滤规则。 > > - 规则匹配顺序：先匹配域名过滤规则（由[addDomainFilterRule]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_添加），再匹配本接口添加的IP防火墙规则；在域名规则或IP规 > 则中，均按[Action]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_为ALLOW、DENY、REJECT的顺序进行匹配。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function addFirewallRule(admin: Want, firewallRule: FirewallRule): void--><!--Device-networkManager-function addFirewallRule(admin: Want, firewallRule: FirewallRule): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| firewallRule | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 添加防火墙过滤规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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

try {
  networkManager.addFirewallRule(wantTemp, firewallRule);
  console.info('Succeeded in adding firewall rule.');
} catch (err) {
  console.error(`Failed to add firewall rule. Code: ${err.code}, message: ${err.message}`);
}
```

