# GzHeader

传递从zlib例程中获取的Gzip头部信息。

**起始版本：** 12

<!--Device-zlib-interface GzHeader--><!--Device-zlib-interface GzHeader-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## 导入模块

```TypeScript
import { zlib } from '@kit.BasicServicesKit';
```

## comment

```TypeScript
comment?: ArrayBuffer
```

注释。

**类型：** ArrayBuffer

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-comment?: ArrayBuffer--><!--Device-GzHeader-comment?: ArrayBuffer-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## done

```TypeScript
done?: boolean
```

读取gzip标头后为True。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-done?: boolean--><!--Device-GzHeader-done?: boolean-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## extra

```TypeScript
extra?: ArrayBuffer
```

额外字段。

**类型：** ArrayBuffer

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-extra?: ArrayBuffer--><!--Device-GzHeader-extra?: ArrayBuffer-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## extraLen

```TypeScript
extraLen?: number
```

额外字段的长度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-extraLen?: int--><!--Device-GzHeader-extraLen?: int-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## hcrc

```TypeScript
hcrc?: boolean
```

如果存在crc标头，则为True。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-hcrc?: boolean--><!--Device-GzHeader-hcrc?: boolean-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## isText

```TypeScript
isText?: boolean
```

如果压缩数据被认为是文本，则为True。

**类型：** boolean

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-isText?: boolean--><!--Device-GzHeader-isText?: boolean-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## name

```TypeScript
name?: ArrayBuffer
```

文件名。

**类型：** ArrayBuffer

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-name?: ArrayBuffer--><!--Device-GzHeader-name?: ArrayBuffer-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## os

```TypeScript
os?: number
```

操作系统。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-os?: int--><!--Device-GzHeader-os?: int-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## time

```TypeScript
time?: number
```

修改时间。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-time?: long--><!--Device-GzHeader-time?: long-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

## xflags

```TypeScript
xflags?: number
```

额外标志。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GzHeader-xflags?: int--><!--Device-GzHeader-xflags?: int-End-->

**系统能力：** SystemCapability.BundleManager.Zlib

