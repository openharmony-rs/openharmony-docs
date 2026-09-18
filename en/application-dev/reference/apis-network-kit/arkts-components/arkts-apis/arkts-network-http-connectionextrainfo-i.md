# ConnectionExtraInfo

Defines the detailed information about the HTTP request interaction.

**Since:** 24

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## cipherSuite

```TypeScript
cipherSuite?: CipherSuite
```

Cipher suite used in the request. It is returned only when the TLS protocol is used.

**Type:** [CipherSuite](arkts-network-http-ciphersuite-t.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## isCacheHit

```TypeScript
isCacheHit: boolean
```

Whether the local cache is hit in the request process. **true**: yes; **false**: no.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## isProxyConnection

```TypeScript
isProxyConnection: boolean
```

Whether to use a proxy in the request process. **true**: yes; **false**: no.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## isReusedConnection

```TypeScript
isReusedConnection: boolean
```

Whether to reuse the connection in the request process. **true**: yes; **false**: no.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## localAddress

```TypeScript
localAddress: string
```

IP address of the client in the request process.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## localPort

```TypeScript
localPort: number
```

Port number of the client in the request process. The value ranges from 1 to 65535.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## networkProtocolName

```TypeScript
networkProtocolName: string
```

HTTP version used in the [request](arkts-network-http-httprequest-i.md#request), for example, 'HTTP /1.0', 'HTTP/1.1', 'HTTP/2', 'HTTP/2 over TLS', 'HTTP/3', or 'Unknown/Non-HTTP'.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## redirectCount

```TypeScript
redirectCount: number
```

Number of redirections in the request process.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## remoteAddress

```TypeScript
remoteAddress: string
```

IP address of the server in the request process.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## remotePort

```TypeScript
remotePort: number
```

Port number of the server in the request process. The value ranges from 1 to 65535.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## tlsVersion

```TypeScript
tlsVersion?: TlsVersion
```

TLS version used in the request. It is returned only when the TLS protocol is used.

**Type:** [TlsVersion](arkts-network-http-tlsversion-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack
