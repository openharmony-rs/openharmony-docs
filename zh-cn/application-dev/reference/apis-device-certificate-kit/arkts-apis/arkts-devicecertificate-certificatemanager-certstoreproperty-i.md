# CertStoreProperty

表示获取证书存储位置的参数集合，包括证书的类型及证书的位置。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-certificateManager-export interface CertStoreProperty--><!--Device-certificateManager-export interface CertStoreProperty-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certAlg

```TypeScript
certAlg?: CertAlgorithm
```

表示证书算法类型。仅当certType为CA\_CERT\_SYSTEM时有效，默认值为INTERNATIONAL。 海外设备不支持SM算法。

**类型：** CertAlgorithm

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-CertStoreProperty-certAlg?: CertAlgorithm--><!--Device-CertStoreProperty-certAlg?: CertAlgorithm-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certScope

```TypeScript
certScope?: CertScope
```

表示证书的存储位置。当证书类型为CA\_CERT\_USER时，此项为必选项。

**类型：** CertScope

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-CertStoreProperty-certScope?: CertScope--><!--Device-CertStoreProperty-certScope?: CertScope-End-->

**系统能力：** SystemCapability.Security.CertificateManager

## certType

```TypeScript
certType: CertType
```

表示证书的类型。

**类型：** CertType

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-CertStoreProperty-certType: CertType--><!--Device-CertStoreProperty-certType: CertType-End-->

**系统能力：** SystemCapability.Security.CertificateManager

