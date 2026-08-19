# TlsConfig

TLS加密版本及套件配置。

**起始版本：** 23

<!--Device-http-export interface TlsConfig--><!--Device-http-export interface TlsConfig-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## cipherSuites

```TypeScript
cipherSuites?: CipherSuite[]
```

声明加密套件类型的数组。如果没有设置，默认携带全部支持的加密套件类型，加密套件类型参考[TlsV13SpecificCipherSuite](arkts-network-http-tlsv13specificciphersuite-t.md)、 [TlsV12SpecificCipherSuite](arkts-network-http-tlsv12specificciphersuite-t.md)、 [TlsV10SpecificCipherSuite](arkts-network-http-tlsv10specificciphersuite-t.md)。

**类型：** [CipherSuite](arkts-network-http-ciphersuite-t.md)[]

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TlsConfig-cipherSuites?: CipherSuite[]--><!--Device-TlsConfig-cipherSuites?: CipherSuite[]-End-->

**系统能力：** SystemCapability.Communication.NetStack

## tlsVersionMax

```TypeScript
tlsVersionMax: TlsVersion
```

TLS最高版本号。

**类型：** [TlsVersion](arkts-network-http-tlsversion-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TlsConfig-tlsVersionMax: TlsVersion--><!--Device-TlsConfig-tlsVersionMax: TlsVersion-End-->

**系统能力：** SystemCapability.Communication.NetStack

## tlsVersionMin

```TypeScript
tlsVersionMin: TlsVersion
```

TLS最低版本号。

**类型：** [TlsVersion](arkts-network-http-tlsversion-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TlsConfig-tlsVersionMin: TlsVersion--><!--Device-TlsConfig-tlsVersionMin: TlsVersion-End-->

**系统能力：** SystemCapability.Communication.NetStack

