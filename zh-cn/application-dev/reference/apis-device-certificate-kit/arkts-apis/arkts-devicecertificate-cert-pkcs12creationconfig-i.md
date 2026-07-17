# Pkcs12CreationConfig

表示创建P12的配置。

**起始版本：** 21

<!--Device-cert-interface Pkcs12CreationConfig--><!--Device-cert-interface Pkcs12CreationConfig-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## certEncParams

```TypeScript
certEncParams?: PbesParams
```

表示证书加密的算法参数。

**类型：** PbesParams

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12CreationConfig-certEncParams?: PbesParams--><!--Device-Pkcs12CreationConfig-certEncParams?: PbesParams-End-->

**系统能力：** SystemCapability.Security.Cert

## encryptCert

```TypeScript
encryptCert?: boolean
```

表示是否加密证书。默认为true。true为加密，false为不加密。

**类型：** boolean

**默认值：** true

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12CreationConfig-encryptCert?: boolean--><!--Device-Pkcs12CreationConfig-encryptCert?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## keyEncParams

```TypeScript
keyEncParams?: PbesParams
```

表示私钥加密的算法参数。

**类型：** PbesParams

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12CreationConfig-keyEncParams?: PbesParams--><!--Device-Pkcs12CreationConfig-keyEncParams?: PbesParams-End-->

**系统能力：** SystemCapability.Security.Cert

## macDigestAlgorithm

```TypeScript
macDigestAlgorithm?: Pkcs12MacDigestAlgorithm
```

表示P12的MAC摘要算法。默认为SHA256。

**类型：** Pkcs12MacDigestAlgorithm

**默认值：** Pkcs12MacDigestAlgorithm.SHA256

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12CreationConfig-macDigestAlgorithm?: Pkcs12MacDigestAlgorithm--><!--Device-Pkcs12CreationConfig-macDigestAlgorithm?: Pkcs12MacDigestAlgorithm-End-->

**系统能力：** SystemCapability.Security.Cert

## macIterations

```TypeScript
macIterations?: number
```

表示P12的MAC的迭代次数。默认为2048。取值应为正整数。

**类型：** number

**默认值：** 2048

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12CreationConfig-macIterations?: int--><!--Device-Pkcs12CreationConfig-macIterations?: int-End-->

**系统能力：** SystemCapability.Security.Cert

## macSaltLen

```TypeScript
macSaltLen?: number
```

表示P12的MAC的盐值长度。最小值为8，默认为16。取值应为≥8的整数。

**类型：** number

**默认值：** 16

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12CreationConfig-macSaltLen?: int--><!--Device-Pkcs12CreationConfig-macSaltLen?: int-End-->

**系统能力：** SystemCapability.Security.Cert

## password

```TypeScript
password: string
```

表示P12的密码。最小长度为4。

**类型：** string

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12CreationConfig-password: string--><!--Device-Pkcs12CreationConfig-password: string-End-->

**系统能力：** SystemCapability.Security.Cert

