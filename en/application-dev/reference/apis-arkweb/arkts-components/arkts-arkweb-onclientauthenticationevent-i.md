# OnClientAuthenticationEvent

Defines the callback information triggered when an SSL client certificate is required, including the host, port, and key type. It is suitable for scenarios where handling client certificate authentication is required, improving authentication process flexibility and security.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler : ClientAuthenticationHandler
```

User operation.

**Type:** [ClientAuthenticationHandler](arkts-arkweb-clientauthenticationhandler-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## host

```TypeScript
host : string
```

Host name of the server that requests a certificate.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## issuers

```TypeScript
issuers : Array<string>
```

Issuer of the certificate that matches the private key.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## keyTypes

```TypeScript
keyTypes : Array<string>
```

Acceptable asymmetric key types.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## port

```TypeScript
port : number
```

Port number for requesting the certificate server. The valid range is 0-65535, and an exception is thrown when the value is out of range.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
