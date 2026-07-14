# ZStream

处理所有用于压缩和解压缩所需的信息。

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.Zlib

## adler

```TypeScript
adler?: number
```

未压缩数据的Adler-32或CRC-32值。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## availableIn

```TypeScript
availableIn?: number
```

nextIn可用的字节数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## availableOut

```TypeScript
availableOut?: number
```

nextOut的剩余可用字节数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## dataType

```TypeScript
dataType?: number
```

关于数据类型的最佳猜测：deflate的二进制或文本，或inflate的解码状态。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## nextIn

```TypeScript
nextIn?: ArrayBuffer
```

需要压缩的输入字节。

**类型：** ArrayBuffer

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## nextOut

```TypeScript
nextOut?: ArrayBuffer
```

压缩后的输出字节。

**类型：** ArrayBuffer

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## totalIn

```TypeScript
totalIn?: number
```

到目前为止读取的输入字节总数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## totalOut

```TypeScript
totalOut?: number
```

到目前为止输出字节总数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

