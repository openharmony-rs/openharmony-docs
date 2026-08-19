# NetFirewallDnsParams(网络防火墙)

防火墙规则DNS信息。 > **说明：**> > 当[addNetFirewallRule](arkts-network-netfirewall-addnetfirewallrule-f.md)的入参rule.type配置为RULE_DNS时，该字段不能为空。

**起始版本：** 15

<!--Device-netFirewall-interface NetFirewallDnsParams--><!--Device-netFirewall-interface NetFirewallDnsParams-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## primaryDns

```TypeScript
primaryDns: string
```

主域名服务器。

**类型：** string

**起始版本：** 15

<!--Device-NetFirewallDnsParams-primaryDns: string--><!--Device-NetFirewallDnsParams-primaryDns: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## standbyDns

```TypeScript
standbyDns?: string
```

备份DNS。

**类型：** string

**起始版本：** 15

<!--Device-NetFirewallDnsParams-standbyDns?: string--><!--Device-NetFirewallDnsParams-standbyDns?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

