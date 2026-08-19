# NetFirewallDomainParams(网络防火墙)

防火墙规则域名参数，目前不支持中文域名。

**起始版本：** 15

<!--Device-netFirewall-interface NetFirewallDomainParams--><!--Device-netFirewall-interface NetFirewallDomainParams-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## domain

```TypeScript
domain: string
```

当isWildcard为false时，需要确定的完整域， 例如"www.example.cn"。

**类型：** string

**起始版本：** 15

<!--Device-NetFirewallDomainParams-domain: string--><!--Device-NetFirewallDomainParams-domain: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## isWildcard

```TypeScript
isWildcard: boolean
```

是否包含通配符。true表示包含，false表示不包含。

**类型：** boolean

**起始版本：** 15

<!--Device-NetFirewallDomainParams-isWildcard: boolean--><!--Device-NetFirewallDomainParams-isWildcard: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

