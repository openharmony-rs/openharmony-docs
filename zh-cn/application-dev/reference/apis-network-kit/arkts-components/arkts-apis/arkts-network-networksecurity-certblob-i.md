# CertBlob

```TypeScript
export interface CertBlob
```

证书数据。

**起始版本：** 11

<!--Device-networkSecurity-export interface CertBlob--><!--Device-networkSecurity-export interface CertBlob-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## data

```TypeScript
data: string | ArrayBuffer
```

证书内容。

**类型：** string &#124; ArrayBuffer

**起始版本：** 11

<!--Device-CertBlob-data: string | ArrayBuffer--><!--Device-CertBlob-data: string | ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NetStack

## type

```TypeScript
type: CertType
```

证书编码类型。

**类型：** [CertType](arkts-network-networksecurity-certtype-e.md)

**起始版本：** 11

<!--Device-CertBlob-type: CertType--><!--Device-CertBlob-type: CertType-End-->

**系统能力：** SystemCapability.Communication.NetStack
