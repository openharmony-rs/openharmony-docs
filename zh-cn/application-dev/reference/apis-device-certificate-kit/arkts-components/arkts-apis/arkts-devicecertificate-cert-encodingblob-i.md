# EncodingBlob

```TypeScript
interface EncodingBlob
```

表示一个编码后的二进制数据块。

**起始版本：** 9

<!--Device-cert-interface EncodingBlob--><!--Device-cert-interface EncodingBlob-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## data

```TypeScript
data: Uint8Array
```

编码数据。

**类型：** Uint8Array

**起始版本：** 9

**原子化服务API（仅ArkTS-Dyn）：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-EncodingBlob-data: Uint8Array--><!--Device-EncodingBlob-data: Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## encodingFormat

```TypeScript
encodingFormat: EncodingFormat
```

编码格式。

**类型：** [EncodingFormat](arkts-devicecertificate-cert-encodingformat-e.md)

**起始版本：** 9

**原子化服务API（仅ArkTS-Dyn）：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-EncodingBlob-encodingFormat: EncodingFormat--><!--Device-EncodingBlob-encodingFormat: EncodingFormat-End-->

**系统能力：** SystemCapability.Security.Cert
