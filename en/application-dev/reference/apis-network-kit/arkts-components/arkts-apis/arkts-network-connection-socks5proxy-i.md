# Socks5Proxy

```TypeScript
export interface Socks5Proxy
```

Socks5 Proxy Configuration Information.

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

DNS resolution strategy. Determines whether the client or the proxy server resolves the domain name.

**Type:** [Socks5DnsStrategy](arkts-network-connection-socks5dnsstrategy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-dnsStrategy?: Socks5DnsStrategy--><!--Device-Socks5Proxy-dnsStrategy?: Socks5DnsStrategy-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## exclusionList

```TypeScript
exclusionList?: Array<string>
```

Exclusion list for proxy servers.

**Type:** Array&lt;string&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-exclusionList?: Array<string>--><!--Device-Socks5Proxy-exclusionList?: Array<string>-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## host

```TypeScript
host: string
```

Proxy server host name.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-host: string--><!--Device-Socks5Proxy-host: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## password

```TypeScript
password?: string
```

Proxy password.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-password?: string--><!--Device-Socks5Proxy-password?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## port

```TypeScript
port: number
```

Host port.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-port: int--><!--Device-Socks5Proxy-port: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Core

## username

```TypeScript
username?: string
```

Proxy username.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Socks5Proxy-username?: string--><!--Device-Socks5Proxy-username?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Core
