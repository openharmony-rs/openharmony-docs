# CsrAttribute

定义CSR属性表示。

CSR属性字段，当前仅支持字符串类型的属性字段，属性值添加到CSR中编码为utf-8。常见的type为challengePassword。

**起始版本：** 18

<!--Device-cert-interface CsrAttribute--><!--Device-cert-interface CsrAttribute-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## type

```TypeScript
type: string
```

PKCS #9指定的扩展类型。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CsrAttribute-type: string--><!--Device-CsrAttribute-type: string-End-->

**系统能力：** SystemCapability.Security.Cert

## value

```TypeScript
value: string
```

属性值。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CsrAttribute-value: string--><!--Device-CsrAttribute-value: string-End-->

**系统能力：** SystemCapability.Security.Cert

