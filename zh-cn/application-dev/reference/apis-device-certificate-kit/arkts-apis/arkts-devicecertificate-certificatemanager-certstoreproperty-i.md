# CertStoreProperty

表示获取证书存储位置的参数集合，包括证书的类型及证书的位置。

**起始版本：** 18

<!--Device-certificateManager-export interface CertStoreProperty--><!--Device-certificateManager-export interface CertStoreProperty-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## certAlg

```TypeScript
certAlg?: CertAlgorithm
```

表示证书算法类型。仅当certType为CA_CERT_SYSTEM时有效，默认值为INTERNATIONAL。海外设备不支持SM算法。

**类型：** CertAlgorithm

**起始版本：** 20

<!--Device-CertStoreProperty-certAlg?: CertAlgorithm--><!--Device-CertStoreProperty-certAlg?: CertAlgorithm-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certScope

```TypeScript
certScope?: CertScope
```

表示证书的存储位置。当证书类型为CA_CERT_USER时，此项为必选项。

**类型：** CertScope

**起始版本：** 18

<!--Device-CertStoreProperty-certScope?: CertScope--><!--Device-CertStoreProperty-certScope?: CertScope-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certType

```TypeScript
certType: CertType
```

表示证书的类型。

**类型：** CertType

**起始版本：** 18

<!--Device-CertStoreProperty-certType: CertType--><!--Device-CertStoreProperty-certType: CertType-End-->

**系统能力：** SystemCapability.Security.CertificateManager

