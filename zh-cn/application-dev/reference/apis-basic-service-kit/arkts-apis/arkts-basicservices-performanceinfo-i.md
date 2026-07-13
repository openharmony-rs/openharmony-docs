# PerformanceInfo

预下载的性能信息。

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## connectTime

```TypeScript
readonly connectTime: number
```

从启动到tcp连接完成所需的时间，单位：毫秒（ms）。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## dnsTime

```TypeScript
readonly dnsTime: number
```

从启动到dns解析完成所需的时间，单位：毫秒（ms）。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## firstReceiveTime

```TypeScript
readonly firstReceiveTime: number
```

从启动到接收第一个字节所需的时间，单位：毫秒（ms）。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## firstSendTime

```TypeScript
readonly firstSendTime: number
```

从启动到开始发送第一个字节所需的时间，单位：毫秒（ms）。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## redirectTime

```TypeScript
readonly redirectTime: number
```

从启动到完成所有重定向步骤所需的时间，单位：毫秒（ms）。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## tlsTime

```TypeScript
readonly tlsTime: number
```

从启动到tls连接完成所需的时间，单位：毫秒（ms）。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## totalTime

```TypeScript
readonly totalTime: number
```

从启动到完成请求所需的时间，单位：毫秒（ms）。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

