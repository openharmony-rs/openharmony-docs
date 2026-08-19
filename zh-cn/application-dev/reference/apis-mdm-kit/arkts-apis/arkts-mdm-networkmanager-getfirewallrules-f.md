# getFirewallRules

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## getFirewallRules

```TypeScript
function getFirewallRules(admin: Want): Array<FirewallRule>
```

查询设备防火墙过滤规则。适用于企业网络安全审计场景，例如检查当前防火墙策略配置、审计网络访问控制规则、验证防火墙规则是否正确执行、排查网络访问问题，帮助企业审核和验证网络安全策略，确保网络访问控制符合安全要求。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function getFirewallRules(admin: Want): Array<FirewallRule>--><!--Device-networkManager-function getFirewallRules(admin: Want): Array<FirewallRule>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[FirewallRule](arkts-mdm-networkmanager-firewallrule-i.md)&gt; | 返回当前设备配置的防火墙过滤规则列表，当方法调用错误时会抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let firewallRule: Array<networkManager.FirewallRule>;
try {
  firewallRule = networkManager.getFirewallRules(wantTemp);
  console.info('Succeeded in getting firewall rules');
} catch (err) {
  console.error(`Failed to get firewall rules. Code: ${err.code}, message: ${err.message}`);
}
```

