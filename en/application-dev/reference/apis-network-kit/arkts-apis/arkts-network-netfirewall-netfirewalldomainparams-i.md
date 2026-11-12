# NetFirewallDomainParams

```TypeScript
interface NetFirewallDomainParams
```

Defines domain name parameters of a firewall rule. Currently, Chinese domain names are not supported.

**Since:** 15

<!--Device-netFirewall-interface NetFirewallDomainParams--><!--Device-netFirewall-interface NetFirewallDomainParams-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## domain

```TypeScript
domain: string
```

When **isWildcard** is **false**, a complete domain is required, for example, "www.example.com"; when **isWildcard** is **true**, wildcard rules are supported. For details about the format, see the description below. When **isWildcard** is **true**, **domain** supports the wildcard character *"*"*, which can appear at the beginning, the end, or both the beginning and the end of a domain name, indicating that it matches any character of any length (including zero). The following wildcard formats are supported:  
- `"*.xxx.xxx"`: prefix wildcard, matching xxx.xxx and all its subdomains. For example, "*.example.com" can  
match "example.com", "www.example.com", and "a.b.example.com". (Supported since API version 21)  
- `"*xx.xxx.xxx"`: prefix wildcard, matching domain names ending with "xx.xxx.xxx". For example,  
"*a.example.com" can match "a.example.com" and "www.a.example.com". (Supported since API version 26.0.1)  
- `"xxx.xxx.xxx.*"`: suffix wildcard, matching domain names starting with "xxx.xxx.xxx.". For example,  
"www.example.*" can match "www.example.com" and "www.example.cn". (Supported since API version 26.0.1)  
- `"xxx.xxx.xxx.xx*"`: suffix wildcard, matching domain names starting with "xxx.xxx.xxx.xx". For example,  
"www.example.co*" can match "www.example.com" and "www.example.com.cn". (Supported since API version 26.0.1).

**Type:** string

**Since:** 15

<!--Device-NetFirewallDomainParams-domain: string--><!--Device-NetFirewallDomainParams-domain: string-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## isWildcard

```TypeScript
isWildcard: boolean
```

Whether to contain wildcards. The value **true** means to contain wildcards; and the value **false** means the opposite.

**Type:** boolean

**Since:** 15

<!--Device-NetFirewallDomainParams-isWildcard: boolean--><!--Device-NetFirewallDomainParams-isWildcard: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
