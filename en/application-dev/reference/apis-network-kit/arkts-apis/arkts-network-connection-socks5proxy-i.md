# Socks5Proxy

```TypeScript
export interface Socks5Proxy
```

Defines the SOCKS5 proxy configuration.

**Since:** 26.0.0

<!--Device-connection-export interface Socks5Proxy--><!--Device-connection-export interface Socks5Proxy-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## dnsStrategy

```TypeScript
dnsStrategy?: Socks5DnsStrategy
```

Whether the system or the proxy server performs DNS resolution.

Note: If this parameter is not specified, the proxy server performs DNS resolution if the host name has the **socks5h://** prefix, and the system performs DNS resolution otherwise.

**Type:** [Socks5DnsStrategy](arkts-network-connection-socks5dnsstrategy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-dnsStrategy?: Socks5DnsStrategy--><!--Device-Socks5Proxy-dnsStrategy?: Socks5DnsStrategy-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## exclusionList

```TypeScript
exclusionList?: Array<string>
```

List of the names of hosts that do not use a proxy. Host names can be domain names, IP addresses, or wildcards. The detailed matching rules are as follows:

- Domain name matching:

  - Exact match: The host name of the proxy server exactly matches any host name in the list.  
  - Partial match: The host name of the proxy server contains any host name in the list.

For example, if **"example.com"** is set in the host name list, "example.com", "www.example.com", and"example.com:80" will be matched, but "www.myexample.com" and "myexample.com.org" will not be matched.

- IP address matching: The host name of the proxy server exactly matches any IP address in the list.  
- Both the domain name and IP address are added to the list for matching.  
- A single asterisk (*) is the only valid wildcard. If the list contains only wildcards, the wildcards match all  
host names; that is, the HTTP proxy is disabled. A wildcard can only be added independently. It cannot be added to the list together with other domain names or IP addresses. Otherwise, the wildcard does not take effect.  
- Host names are case insensitive.  
6. Protocol prefixes such as http, https, socks5, and socks5h are not considered during host name matching.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-exclusionList?: Array<string>--><!--Device-Socks5Proxy-exclusionList?: Array<string>-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## host

```TypeScript
host: string
```

Host name of the proxy server.

Note: If this parameter is set to an empty string, no SOCKS5 proxy is configured.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-host: string--><!--Device-Socks5Proxy-host: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## password

```TypeScript
password?: string
```

Password of the user who uses the proxy.

Note: The setting takes effect only when the username parameter is set.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-password?: string--><!--Device-Socks5Proxy-password?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## port

```TypeScript
port: number
```

Host port. Value range: [0, 65535]

Note: If the parameter value is not within the preceding range, no SOCKS5 proxy is configured.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-port: int--><!--Device-Socks5Proxy-port: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## username

```TypeScript
username?: string
```

Name of the user who uses the proxy.

Note: This parameter takes effect only when the password parameter is set.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-username?: string--><!--Device-Socks5Proxy-username?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
