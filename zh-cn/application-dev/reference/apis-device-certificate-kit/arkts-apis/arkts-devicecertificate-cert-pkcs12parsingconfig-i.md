# Pkcs12ParsingConfig

表示解析P12的配置。

**起始版本：** 18

<!--Device-cert-interface Pkcs12ParsingConfig--><!--Device-cert-interface Pkcs12ParsingConfig-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## needsCert

```TypeScript
needsCert?: boolean
```

表示是否获取证书。默认为true。true为获取，false为不获取。

**类型：** boolean

**默认值：** true

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12ParsingConfig-needsCert?: boolean--><!--Device-Pkcs12ParsingConfig-needsCert?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## needsOtherCerts

```TypeScript
needsOtherCerts?: boolean
```

表示是否获取其他证书。默认为false。true为获取，false为不获取。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12ParsingConfig-needsOtherCerts?: boolean--><!--Device-Pkcs12ParsingConfig-needsOtherCerts?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## needsPrivateKey

```TypeScript
needsPrivateKey?: boolean
```

表示是否获取私钥。默认为true。

true为获取，返回PKCS8编码的私钥数据；false为不获取。

**类型：** boolean

**默认值：** true

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12ParsingConfig-needsPrivateKey?: boolean--><!--Device-Pkcs12ParsingConfig-needsPrivateKey?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## password

```TypeScript
password: string
```

密码。

**类型：** string

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12ParsingConfig-password: string--><!--Device-Pkcs12ParsingConfig-password: string-End-->

**系统能力：** SystemCapability.Security.Cert

## privateKeyFormat

```TypeScript
privateKeyFormat?: EncodingBaseFormat
```

表示获取私钥的格式，当前支持PEM和DER格式。参数缺省时，默认为PEM格式。

> **说明：**  
>  
> 当needsPrivateKey值为true时，该参数生效。

**类型：** EncodingBaseFormat

**默认值：** EncodingBaseFormat.PEM

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-Pkcs12ParsingConfig-privateKeyFormat?: EncodingBaseFormat--><!--Device-Pkcs12ParsingConfig-privateKeyFormat?: EncodingBaseFormat-End-->

**系统能力：** SystemCapability.Security.Cert

