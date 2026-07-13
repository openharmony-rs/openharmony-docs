# HuksReturnResult

调用接口返回的result。

**起始版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## certChains

```TypeScript
certChains?: Array<string>
```

表示证书链数据。默认为undefined。

**类型：** Array<string>

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## outData

```TypeScript
outData?: Uint8Array
```

表示
[initSession](arkts-universalkeystore-initsession-f.md#initsession-1)
操作之后获取到的challenge信息。默认为undefined。

**类型：** Uint8Array

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## properties

```TypeScript
properties?: Array<HuksParam>
```

表示
[initSession](arkts-universalkeystore-initsession-f.md#initsession-1)
操作之后获取到的challenge信息。默认为undefined。

**类型：** Array<HuksParam>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## sharedSecret

```TypeScript
sharedSecret?: Uint8Array
```

定义共享密钥。

**类型：** Uint8Array

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

