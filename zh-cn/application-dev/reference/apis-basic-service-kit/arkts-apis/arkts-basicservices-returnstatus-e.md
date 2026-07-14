# ReturnStatus

压缩/解压缩函数的返回代码。

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.Zlib

## OK

```TypeScript
OK = 0
```

函数调用成功。该接口支持在原子化服务中使用。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## STREAM_END

```TypeScript
STREAM_END = 1
```

函数调用成功，表示已处理了整个数据。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## NEED_DICT

```TypeScript
NEED_DICT = 2
```

函数调用成功，表示需要预设字典才能继续解压缩。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## ERRNO

```TypeScript
ERRNO = -1
```

函数调用失败，表示文件操作错误。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## STREAM_ERROR

```TypeScript
STREAM_ERROR = -2
```

函数调用失败，表示压缩或解压缩流错误。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## DATA_ERROR

```TypeScript
DATA_ERROR = -3
```

函数调用失败，表示输入数据不正确。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## MEM_ERROR

```TypeScript
MEM_ERROR = -4
```

函数调用失败，表示内存分配失败。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## BUF_ERROR

```TypeScript
BUF_ERROR = -5
```

函数调用失败，表示输入缓冲区不正确。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

