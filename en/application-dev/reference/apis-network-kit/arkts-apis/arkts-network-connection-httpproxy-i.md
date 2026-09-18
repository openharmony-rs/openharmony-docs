# HttpProxy

Represents the HTTP proxy configuration.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## exclusionList

```TypeScript
exclusionList: Array<string>
```

List of the names of hosts that do not use a proxy. Host names can be domain names, IP addresses, or wildcards. The detailed matching rules are as follows:

- Domain name matching:  
- Exact match: The host name of the proxy server exactly matches any host name in the list.  
- Partial match: The host name of the proxy server contains any host name in the list.

For example, if **ample.com** is set in the host name list, **ample.com**, **www.ample.com**, and **ample.com:80** are matched, and **www.example.com** and **ample.com.org** are not matched.

- IP address matching: The host name of the proxy server exactly matches any IP address in the list.  
- Both the domain name and IP address are added to the list for matching.  
- A single asterisk (*) is the only valid wildcard. If the list contains only wildcards, the wildcards match all  
host names; that is, the HTTP proxy is disabled. A wildcard can only be added independently. It cannot be added to the list together with other domain names or IP addresses. Otherwise, the wildcard does not take effect.  
- Host names are case insensitive.  
- Protocol prefixes such as **http** and **https** are ignored during matching.

**Type:** Array&lt;string&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## host

```TypeScript
host: string
```

Host name of the proxy server.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## password

```TypeScript
password?: string
```

Password of the user who uses the proxy.

Note: The setting takes effect only when the username parameter is set.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Communication.NetManager.Core

## port

```TypeScript
port: number
```

Host port. The value range is [0, 65535].

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## username

```TypeScript
username?: string
```

Name of the user who uses the proxy.

Note: This parameter takes effect only when the password parameter is set.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Communication.NetManager.Core
