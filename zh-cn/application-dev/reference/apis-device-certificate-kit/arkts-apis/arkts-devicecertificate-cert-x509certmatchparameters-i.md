# X509CertMatchParameters

用于匹配证书的过滤参数。如果参数中任一项都未指定，则匹配所有证书。

**起始版本：** 11

<!--Device-cert-interface X509CertMatchParameters--><!--Device-cert-interface X509CertMatchParameters-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## authorityKeyIdentifier

```TypeScript
authorityKeyIdentifier?: Uint8Array
```

指定证书颁发机构密钥。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-authorityKeyIdentifier?: Uint8Array--><!--Device-X509CertMatchParameters-authorityKeyIdentifier?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## certPolicy

```TypeScript
certPolicy?: Array<string>
```

指定证书策略。

**类型：** Array<string>

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-certPolicy?: Array<string>--><!--Device-X509CertMatchParameters-certPolicy?: Array<string>-End-->

**系统能力：** SystemCapability.Security.Cert

## extendedKeyUsage

```TypeScript
extendedKeyUsage?: Array<string>
```

指定扩展密钥用途。

**类型：** Array<string>

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-extendedKeyUsage?: Array<string>--><!--Device-X509CertMatchParameters-extendedKeyUsage?: Array<string>-End-->

**系统能力：** SystemCapability.Security.Cert

## issuer

```TypeScript
issuer?: Uint8Array
```

指定证书颁发者，为DER编码格式。

**类型：** Uint8Array

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-issuer?: Uint8Array--><!--Device-X509CertMatchParameters-issuer?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## keyUsage

```TypeScript
keyUsage?: Array<boolean>
```

指定是否需要匹配密钥用途。true为需要，false为不需要。

**类型：** Array<boolean>

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-keyUsage?: Array<boolean>--><!--Device-X509CertMatchParameters-keyUsage?: Array<boolean>-End-->

**系统能力：** SystemCapability.Security.Cert

## matchAllSubjectAltNames

```TypeScript
matchAllSubjectAltNames?: boolean
```

指定是否需要匹配证书主体名称。true为需要，false为不需要。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-matchAllSubjectAltNames?: boolean--><!--Device-X509CertMatchParameters-matchAllSubjectAltNames?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## minPathLenConstraint

```TypeScript
minPathLenConstraint?: number
```

指定证书CA路径长度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-minPathLenConstraint?: int--><!--Device-X509CertMatchParameters-minPathLenConstraint?: int-End-->

**系统能力：** SystemCapability.Security.Cert

## nameConstraints

```TypeScript
nameConstraints?: Uint8Array
```

指定证书的使用者名称。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-nameConstraints?: Uint8Array--><!--Device-X509CertMatchParameters-nameConstraints?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## privateKey

```TypeScript
privateKey?: string | Uint8Array
```

指定证书私钥，string表示PEM格式私钥，Uint8Array表示DER格式私钥。

**类型：** string | Uint8Array

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-privateKey?: string | Uint8Array--><!--Device-X509CertMatchParameters-privateKey?: string | Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## privateKeyValid

```TypeScript
privateKeyValid?: string
```

指定证书私钥有效期。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-privateKeyValid?: string--><!--Device-X509CertMatchParameters-privateKeyValid?: string-End-->

**系统能力：** SystemCapability.Security.Cert

## publicKey

```TypeScript
publicKey?: DataBlob
```

指定证书公钥，DER编码格式。

**类型：** DataBlob

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-publicKey?: DataBlob--><!--Device-X509CertMatchParameters-publicKey?: DataBlob-End-->

**系统能力：** SystemCapability.Security.Cert

## publicKeyAlgID

```TypeScript
publicKeyAlgID?: string
```

指定证书公钥的算法。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-publicKeyAlgID?: string--><!--Device-X509CertMatchParameters-publicKeyAlgID?: string-End-->

**系统能力：** SystemCapability.Security.Cert

## serialNumber

```TypeScript
serialNumber?: bigint
```

指定证书的序列号。

**类型：** bigint

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-serialNumber?: bigint--><!--Device-X509CertMatchParameters-serialNumber?: bigint-End-->

**系统能力：** SystemCapability.Security.Cert

## subject

```TypeScript
subject?: Uint8Array
```

指定证书主体名称，DER编码格式。

**类型：** Uint8Array

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-subject?: Uint8Array--><!--Device-X509CertMatchParameters-subject?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## subjectAlternativeNames

```TypeScript
subjectAlternativeNames?: Array<GeneralName>
```

指定证书主体名称。

**类型：** Array<GeneralName>

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-subjectAlternativeNames?: Array<GeneralName>--><!--Device-X509CertMatchParameters-subjectAlternativeNames?: Array<GeneralName>-End-->

**系统能力：** SystemCapability.Security.Cert

## subjectKeyIdentifier

```TypeScript
subjectKeyIdentifier?: Uint8Array
```

指定证书公钥。

**类型：** Uint8Array

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-subjectKeyIdentifier?: Uint8Array--><!--Device-X509CertMatchParameters-subjectKeyIdentifier?: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## validDate

```TypeScript
validDate?: string
```

指定证书有效期。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-validDate?: string--><!--Device-X509CertMatchParameters-validDate?: string-End-->

**系统能力：** SystemCapability.Security.Cert

## x509Cert

```TypeScript
x509Cert?: X509Cert
```

指定具体的证书对象。

**类型：** X509Cert

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-X509CertMatchParameters-x509Cert?: X509Cert--><!--Device-X509CertMatchParameters-x509Cert?: X509Cert-End-->

**系统能力：** SystemCapability.Security.Cert

