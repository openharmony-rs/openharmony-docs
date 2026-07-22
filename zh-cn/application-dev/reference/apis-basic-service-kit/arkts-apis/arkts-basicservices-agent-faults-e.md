# Faults

定义任务失败的原因。
> **说明：**  
>  
> API version 12及以下版本，只支持串行的尝试连接域名相关ip，且不支持单个ip的连接时间控制，如果DNS返回的首个ip是阻塞的，可能会导致握手超时，进而引发TIMEOUT错误。

**起始版本：** 10

<!--Device-agent-enum Faults--><!--Device-agent-enum Faults-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## OTHERS

```TypeScript
OTHERS = 0xFF
```

表示其他故障。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-OTHERS = 0xFF--><!--Device-Faults-OTHERS = 0xFF-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## DISCONNECTED

```TypeScript
DISCONNECTED = 0x00
```

表示网络断开连接。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-DISCONNECTED = 0x00--><!--Device-Faults-DISCONNECTED = 0x00-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## TIMEOUT

```TypeScript
TIMEOUT = 0x10
```

表示任务超时。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-TIMEOUT = 0x10--><!--Device-Faults-TIMEOUT = 0x10-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## PROTOCOL

```TypeScript
PROTOCOL = 0x20
```

表示协议错误，例如：服务器内部错误（500）、无法处理的数据区间（416）等。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-PROTOCOL = 0x20--><!--Device-Faults-PROTOCOL = 0x20-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## PARAM

```TypeScript
PARAM = 0x30
```

表示参数错误，例如：url格式错误等。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-PARAM = 0x30--><!--Device-Faults-PARAM = 0x30-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## FSIO

```TypeScript
FSIO = 0x40
```

表示文件系统io错误，例如：打开/查找/读取/写入/关闭。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-FSIO = 0x40--><!--Device-Faults-FSIO = 0x40-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## DNS

```TypeScript
DNS = 0x50
```

表示DNS解析错误。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-DNS = 0x50--><!--Device-Faults-DNS = 0x50-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## TCP

```TypeScript
TCP = 0x60
```

表示TCP连接错误。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-TCP = 0x60--><!--Device-Faults-TCP = 0x60-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## SSL

```TypeScript
SSL = 0x70
```

表示SSL连接错误，例如：证书错误、证书校验失败错误等。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-SSL = 0x70--><!--Device-Faults-SSL = 0x70-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## REDIRECT

```TypeScript
REDIRECT = 0x80
```

表示重定向错误。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Faults-REDIRECT = 0x80--><!--Device-Faults-REDIRECT = 0x80-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## LOW_SPEED

```TypeScript
LOW_SPEED = 0x90
```

表示任务速度过低。

**起始版本：** 20

<!--Device-Faults-LOW_SPEED = 0x90--><!--Device-Faults-LOW_SPEED = 0x90-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

