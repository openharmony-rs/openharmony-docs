# ClientCert

Defines the client certificate type.

**Since:** 11

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

**System capability:** SystemCapability.Communication.NetStack

## certType

```TypeScript
certType?: CertType
```

Certificate type. The default value is **PEM**.

**Type:** [CertType](arkts-network-http-certtype-e.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## keyPassword

```TypeScript
keyPassword?: string
```

Password of the certificate key file. The default value is an empty string.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## keyPath

```TypeScript
keyPath: string
```

Path of the certificate key file.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack
