# ValidationContext

The validation context of [ValidationCallback](arkts-network-http-validationcallback-t.md)

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## host

```TypeScript
host: string
```

The host of this request.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## ip

```TypeScript
ip: string
```

The real IP which this request connect to.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## pemCerts

```TypeScript
pemCerts: string[]
```

The raw data which in PEM format of certificate.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack

## x509Certs

```TypeScript
x509Certs: X509Cert[]
```

X509 certificate chain.

**Type:** [X509Cert](arkts-network-http-x509cert-t.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetStack
