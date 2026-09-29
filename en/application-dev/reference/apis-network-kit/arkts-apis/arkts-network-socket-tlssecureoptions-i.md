# TLSSecureOptions

```TypeScript
export interface TLSSecureOptions
```

TLS security options. When **cert** (local certificate) and **key** (private key) are not empty, the two-way authentication mode is enabled. If **cert** or **key** is empty, one-way authentication is enabled.

**Since:** 9

<!--Device-socket-export interface TLSSecureOptions--><!--Device-socket-export interface TLSSecureOptions-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## ca

```TypeScript
ca?: string | Array<string>
```

CA certificate of the server, which is used to authenticate the digital certificate of the server. The default value is the preset CA certificate&lt;sup&gt;12+&lt;/sup&gt;. A maximum of 1000 certificates can be set.

**Type:** string &#124; Array&lt;string&gt;

**Since:** 9

<!--Device-TLSSecureOptions-ca?: string | Array<string>--><!--Device-TLSSecureOptions-ca?: string | Array<string>-End-->

**System capability:** SystemCapability.Communication.NetStack

## cert

```TypeScript
cert?: string | Array<string>
```

Digital certificate of the local client. An array can be passed since API version 24. A maximum of 1000 certificates can be set.

**Type:** string &#124; Array&lt;string&gt;

**Since:** 9

<!--Device-TLSSecureOptions-cert?: string | Array<string>--><!--Device-TLSSecureOptions-cert?: string | Array<string>-End-->

**System capability:** SystemCapability.Communication.NetStack

## cipherSuite

```TypeScript
cipherSuite?: string
```

Cipher suite used during communication. The default value is **""**.

**Type:** string

**Since:** 9

<!--Device-TLSSecureOptions-cipherSuite?: string--><!--Device-TLSSecureOptions-cipherSuite?: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## isBidirectionalAuthentication

```TypeScript
isBidirectionalAuthentication?: boolean
```

Two-way authentication. The default value is **false**. The value **true** means to enable two-way authentication, and the value **false** means the opposite.

**Type:** boolean

**Since:** 12

<!--Device-TLSSecureOptions-isBidirectionalAuthentication?: boolean--><!--Device-TLSSecureOptions-isBidirectionalAuthentication?: boolean-End-->

**System capability:** SystemCapability.Communication.NetStack

## key

```TypeScript
key?: string
```

Private key of the local digital certificate.

**Type:** string

**Since:** 9

<!--Device-TLSSecureOptions-key?: string--><!--Device-TLSSecureOptions-key?: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## password

```TypeScript
password?: string
```

Password for reading the private key.

**Type:** string

**Since:** 9

<!--Device-TLSSecureOptions-password?: string--><!--Device-TLSSecureOptions-password?: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## protocols

```TypeScript
protocols?: Protocol | Array<Protocol>
```

TLS protocol version. The default value is **TLSv1.2**.

**Type:** [Protocol](arkts-network-socket-protocol-e.md) &#124; Array&lt;[Protocol](arkts-network-socket-protocol-e.md)&gt;

**Since:** 9

<!--Device-TLSSecureOptions-protocols?: Protocol | Array<Protocol>--><!--Device-TLSSecureOptions-protocols?: Protocol | Array<Protocol>-End-->

**System capability:** SystemCapability.Communication.NetStack

## signatureAlgorithms

```TypeScript
signatureAlgorithms?: string
```

Signing algorithm used during communication. The default value is **""**.

**Type:** string

**Since:** 9

<!--Device-TLSSecureOptions-signatureAlgorithms?: string--><!--Device-TLSSecureOptions-signatureAlgorithms?: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## useRemoteCipherPrefer

```TypeScript
useRemoteCipherPrefer?: boolean
```

Whether to use the remote cipher suite preferentially. The value **true** means to use the remote cipher suite preferentially, and the value **false** means the opposite.

**Type:** boolean

**Since:** 9

<!--Device-TLSSecureOptions-useRemoteCipherPrefer?: boolean--><!--Device-TLSSecureOptions-useRemoteCipherPrefer?: boolean-End-->

**System capability:** SystemCapability.Communication.NetStack
