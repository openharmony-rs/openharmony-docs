# PerformanceInfo

预下载的性能信息。

**起始版本：** 23

<!--Device-cacheDownload-interface PerformanceInfo--><!--Device-cacheDownload-interface PerformanceInfo-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## connectTime

```TypeScript
readonly connectTime: double
```

从启动到tcp连接完成所需的时间，单位：毫秒（ms）。

**类型：** double

**起始版本：** 23

<!--Device-PerformanceInfo-readonly connectTime: double--><!--Device-PerformanceInfo-readonly connectTime: double-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## dnsTime

```TypeScript
readonly dnsTime: double
```

从启动到dns解析完成所需的时间，单位：毫秒（ms）。

**类型：** double

**起始版本：** 23

<!--Device-PerformanceInfo-readonly dnsTime: double--><!--Device-PerformanceInfo-readonly dnsTime: double-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## firstReceiveTime

```TypeScript
readonly firstReceiveTime: double
```

从启动到接收第一个字节所需的时间，单位：毫秒（ms）。

**类型：** double

**起始版本：** 23

<!--Device-PerformanceInfo-readonly firstReceiveTime: double--><!--Device-PerformanceInfo-readonly firstReceiveTime: double-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## firstSendTime

```TypeScript
readonly firstSendTime: double
```

从启动到开始发送第一个字节所需的时间，单位：毫秒（ms）。

**类型：** double

**起始版本：** 23

<!--Device-PerformanceInfo-readonly firstSendTime: double--><!--Device-PerformanceInfo-readonly firstSendTime: double-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## redirectTime

```TypeScript
readonly redirectTime: double
```

从启动到完成所有重定向步骤所需的时间，单位：毫秒（ms）。

**类型：** double

**起始版本：** 23

<!--Device-PerformanceInfo-readonly redirectTime: double--><!--Device-PerformanceInfo-readonly redirectTime: double-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## tlsTime

```TypeScript
readonly tlsTime: double
```

从启动到tls连接完成所需的时间，单位：毫秒（ms）。

**类型：** double

**起始版本：** 23

<!--Device-PerformanceInfo-readonly tlsTime: double--><!--Device-PerformanceInfo-readonly tlsTime: double-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## totalTime

```TypeScript
readonly totalTime: double
```

从启动到完成请求所需的时间，单位：毫秒（ms）。

**类型：** double

**起始版本：** 23

<!--Device-PerformanceInfo-readonly totalTime: double--><!--Device-PerformanceInfo-readonly totalTime: double-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

