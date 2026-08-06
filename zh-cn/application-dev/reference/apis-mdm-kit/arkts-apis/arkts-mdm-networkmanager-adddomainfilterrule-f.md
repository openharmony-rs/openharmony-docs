# addDomainFilterRule

## addDomainFilterRule

```TypeScript
function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void
```

为设备添加域名过滤规则。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 > **说明：** > > - 添加[Action]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_为ALLOW规则后会自动添加默认DENY规则，不在ALLOW规则之内的域名解析数据包将被丢弃或拦截。 > > - 添加的规则在设备重启后会被清空。 > > - 为避免DNS缓存导致拦截规则失效，建议系统启动后立即配置域名过滤规则。若已因DNS缓存导致拦截失效，重启系统可清除缓存，恢复拦截功能。 > > - 规则匹配顺序：先匹配本接口添加的域名过滤规则，再匹配IP防火墙规则（由[addFirewallRule]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_添加）；在域名规则或IP规则中，均按 > [Action]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_为ALLOW、DENY、REJECT的顺序进行匹配。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void--><!--Device-networkManager-function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| domainFilterRule | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 域名过滤规则对象，包含域名、应用UID、IP协议版本等配置项。 |

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
let domainFilterRule: networkManager.DomainFilterRule = {
  // 需根据实际情况进行替换
  "domainName": "www.example.com",
  "appUid": "9696",
  "action": networkManager.Action.DENY,
  "family": 1,
  "logType": networkManager.LogType.NFLOG
};

try {
  networkManager.addDomainFilterRule(wantTemp, domainFilterRule);
  console.info('Succeeded in adding domain filter rules');
} catch (err) {
  console.error(`Failed to add domain filter rules. Code: ${err.code}, message: ${err.message}`);
}
```

