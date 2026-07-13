# HuksSessionHandle

HUKS handle结构体。

**起始版本：** 9

**系统能力：** SystemCapability.Security.Huks.Core

## challenge

```TypeScript
challenge?: Uint8Array
```

表示
[initSession](arkts-universalkeystore-initsession-f.md#initsession-1)
操作之后获取到的challenge信息。默认为undefined。

**类型：** Uint8Array

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

## handle

```TypeScript
handle: number
```

表示无符号整数类型的handle值。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Huks.Core

