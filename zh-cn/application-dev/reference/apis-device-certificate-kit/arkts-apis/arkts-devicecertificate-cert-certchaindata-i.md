# CertChainData

证书链数据，在证书链校验时，作为入参传入。

**起始版本：** 9

<!--Device-cert-interface CertChainData--><!--Device-cert-interface CertChainData-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## count

```TypeScript
count: number
```

传入的数据中，包含的证书数量。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainData-count: int--><!--Device-CertChainData-count: int-End-->

**系统能力：** SystemCapability.Security.Cert

## data

```TypeScript
data: Uint8Array
```

证书数据。

**类型：** Uint8Array

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainData-data: Uint8Array--><!--Device-CertChainData-data: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## encodingFormat

```TypeScript
encodingFormat: EncodingFormat
```

编码格式。

**类型：** EncodingFormat

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CertChainData-encodingFormat: EncodingFormat--><!--Device-CertChainData-encodingFormat: EncodingFormat-End-->

**系统能力：** SystemCapability.Security.Cert

