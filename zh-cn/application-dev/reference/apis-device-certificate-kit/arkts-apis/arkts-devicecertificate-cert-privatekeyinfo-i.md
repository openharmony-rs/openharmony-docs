# PrivateKeyInfo

表示私钥信息。

**起始版本：** 18

<!--Device-cert-interface PrivateKeyInfo--><!--Device-cert-interface PrivateKeyInfo-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## key

```TypeScript
key: string | Uint8Array
```

未加密或加密的私钥，支持PEM或DER格式。

**类型：** string \| Uint8Array

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PrivateKeyInfo-key: string | Uint8Array--><!--Device-PrivateKeyInfo-key: string | Uint8Array-End-->

**系统能力：** SystemCapability.Security.Cert

## password

```TypeScript
password?: string
```

私钥的密码，如果私钥是加密的。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PrivateKeyInfo-password?: string--><!--Device-PrivateKeyInfo-password?: string-End-->

**系统能力：** SystemCapability.Security.Cert

