# ClientAuthenticationHandler

```TypeScript
declare class ClientAuthenticationHandler
```

ClientAuthenticationHandler is a class in the **Web** component that handles SSL client certificate authentication requests. When a server requests a client certificate for TLS mutual authentication, this handler is provided to the app through the `onClientAuthenticationRequest` event callback, allowing the app to select appropriate certificate credentials for response. For sample code, see [onClientAuthenticationRequest](arkts-arkweb-web-comp-attribute.md#onclientauthenticationrequest).

**Since:** 9

<!--Device-unnamed-declare class ClientAuthenticationHandler--><!--Device-unnamed-declare class ClientAuthenticationHandler-End-->

**System capability:** SystemCapability.Web.Webview.Core

## cancel

```TypeScript
cancel(): void
```

Cancel this certificate request.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClientAuthenticationHandler-cancel(): void--><!--Device-ClientAuthenticationHandler-cancel(): void-End-->

**System capability:** SystemCapability.Web.Webview.Core

<a id="confirm1"></a>

## confirm

```TypeScript
confirm(priKeyFile: string, certChainFile: string): void
```

Uses the specified private key and client certificate chain.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClientAuthenticationHandler-confirm(priKeyFile: string, certChainFile: string): void--><!--Device-ClientAuthenticationHandler-confirm(priKeyFile: string, certChainFile: string): void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| priKeyFile | string | Yes | Full path for storing the private key file. |
| certChainFile | string | Yes | Full path for storing the certificate chain file. |

<a id="confirm2"></a>

## confirm

```TypeScript
confirm(authUri: string): void
```

Instructs the **Web** component to use the specified credentials (obtained from the certificate management module).

> **NOTE:** 
> 
> - The authUri parameter must be obtained through the system certificate manager and requires the ohos.permission.ACCESS_CERT_MANAGER permission to be configured.

| Signing Algorithm | Key Length |  
| ------- | ------ |  
| SSL_SIGN_RSA_PKCS1_SHA256 | 1024 (supported since API version 18), 2048, 3072, and 4096 |
| SSL_SIGN_RSA_PKCS1_SHA384 | 1024 (supported since API version 18), 2048, 3072, and 4096 |
| SSL_SIGN_RSA_PKCS1_SHA512 | 1024 (supported since API version 18), 2048, 3072, and 4096 |
| SSL_SIGN_RSA_PSS_SHA256 | 1024 (supported since API version 18), 2048, 3072, and 4096 |
| SSL_SIGN_RSA_PSS_SHA384 | 1024 (supported since API version 18), 2048, 3072, and 4096 |
| SSL_SIGN_RSA_PSS_SHA512 | 1024 (supported since API version 18), 2048, 3072, and 4096 |
| SSL_SIGN_ECDSA_SECP256R1_SHA256 | 256 |
| SSL_SIGN_ECDSA_SECP384R1_SHA384 | 384 |
| SSL_SIGN_ECDSA_SECP521R1_SHA512 | 521 |

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClientAuthenticationHandler-confirm(authUri: string): void--><!--Device-ClientAuthenticationHandler-confirm(authUri: string): void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authUri | string | Yes | Key value of the credentials. |

<a id="confirm3"></a>

## confirm

```TypeScript
confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void
```

Instructs the **Web** component to use the specified credential and credential type obtained from the certificate management module.

**Since:** 22

<!--Device-ClientAuthenticationHandler-confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void--><!--Device-ClientAuthenticationHandler-confirm(identity: string, credentialTypeOrCertChainFile: CredentialType | string): void-End-->

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| identity | string | Yes | Unique ID of a credential. |
| credentialTypeOrCertChainFile | [CredentialType](arkts-arkweb-web-comp-credentialtype-e.md) &#124; string | Yes | Credential type when the type is CredentialType, or certificate chain file path when the type is string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

## constructor

```TypeScript
constructor()
```

Constructs a **ClientAuthenticationHandler**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClientAuthenticationHandler-constructor()--><!--Device-ClientAuthenticationHandler-constructor()-End-->

**System capability:** SystemCapability.Web.Webview.Core

## ignore

```TypeScript
ignore(): void
```

Ignores this request.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ClientAuthenticationHandler-ignore(): void--><!--Device-ClientAuthenticationHandler-ignore(): void-End-->

**System capability:** SystemCapability.Web.Webview.Core
