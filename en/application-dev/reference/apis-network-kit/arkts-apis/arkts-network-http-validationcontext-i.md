# ValidationContext

```TypeScript
export interface ValidationContext
```

Certificate context information used when verifying the identity of the remote server, which is passed in as a parameter of [ValidationCallback](arkts-network-http-validationcallback-t.md).

**Since:** 26.0.0

<!--Device-http-export interface ValidationContext--><!--Device-http-export interface ValidationContext-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## host

```TypeScript
host: string
```

Target host name of this request.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ValidationContext-host: string--><!--Device-ValidationContext-host: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## ip

```TypeScript
ip: string
```

IP address actually connected for this request.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ValidationContext-ip: string--><!--Device-ValidationContext-ip: string-End-->

**System capability:** SystemCapability.Communication.NetStack

## pemCerts

```TypeScript
pemCerts: string[]
```

Raw certificate data in PEM format.

**Type:** string[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ValidationContext-pemCerts: string[]--><!--Device-ValidationContext-pemCerts: string[]-End-->

**System capability:** SystemCapability.Communication.NetStack

## x509Certs

```TypeScript
x509Certs: X509Cert[]
```

X.509 certificate chain.

**Type:** [X509Cert](arkts-network-http-x509cert-t.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ValidationContext-x509Certs: X509Cert[]--><!--Device-ValidationContext-x509Certs: X509Cert[]-End-->

**System capability:** SystemCapability.Communication.NetStack
