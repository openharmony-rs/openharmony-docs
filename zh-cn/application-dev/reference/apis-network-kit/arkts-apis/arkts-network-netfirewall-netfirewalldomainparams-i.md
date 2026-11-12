# NetFirewallDomainParams

```TypeScript
interface NetFirewallDomainParams
```

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

当isWildcard为false时，需要确定的完整域名，例如"www.example.com"；当isWildcard为true时，支持通配符规则，具体格式见下文说明。当isWildcard为true时，domain支持使用通配符"*"，"*"可出现在域名的首部、尾部或首尾同时出现，表示匹配任意长度（包括零）的任意字符。支持以下通配符格式：  
- `"*.xxx.xxx"`：前缀通配，匹配xxx.xxx及其所有子域名。例如"*.example.com"可匹配"example.com"、"www.example.com"、"a.b.example.com"。（从API版本21开始支持）  
- `"*xx.xxx.xxx"`：前缀通配，匹配以"xx.xxx.xxx"结尾的域名。例如"*a.example.com"可匹配"a.example.com"、"www.a.example.com"。（从API版本26.0.1开始支持）  
- `"xxx.xxx.xxx.*"`：后缀通配，匹配以"xxx.xxx.xxx."开头的域名。例如"www.example.*"可匹配"www.example.com"、"www.example.cn"。（从API版本26.0.1开始支持）  
- `"xxx.xxx.xxx.xx*"`：后缀通配，匹配以"xxx.xxx.xxx.xx"开头的域名。例如"www.example.co*"可匹配"www.example.com"、"www.example.com.cn"。（从API版本26.0.1开始支持）。

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
