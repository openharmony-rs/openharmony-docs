# ClientCert

```TypeScript
export interface ClientCert
```

Defines the client certificate type.

**Since:** 11

<!--Device-http-export interface ClientCert--><!--Device-http-export interface ClientCert-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## certPath

```TypeScript
certPath: string
```

Path of the certificate file.

**Type:** string

**Since:** 11

<!--Device-ClientCert-certPath: string--><!--Device-ClientCert-certPath: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## certType

```TypeScript
certType?: CertType
```

Certificate type. The default value is **PEM**.

**Type:** [CertType](arkts-network-http-certtype-e.md)

**Since:** 11

<!--Device-ClientCert-certType?: CertType--><!--Device-ClientCert-certType?: CertType-End-->

**System capability:** SystemCapability.Communication.NetStack

## keyPassword

```TypeScript
keyPassword?: string
```

Password of the certificate key file. The default value is an empty string.

**Type:** string

**Since:** 11

<!--Device-ClientCert-keyPassword?: string--><!--Device-ClientCert-keyPassword?: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## keyPath

```TypeScript
keyPath: string
```

Path of the certificate key file.

**Type:** string

**Since:** 11

<!--Device-ClientCert-keyPath: string--><!--Device-ClientCert-keyPath: string-End-->

**System capability:** SystemCapability.Communication.NetStack
