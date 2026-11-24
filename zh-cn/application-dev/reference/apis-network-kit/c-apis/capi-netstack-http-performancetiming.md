# Http_PerformanceTiming

```c
typedef struct Http_PerformanceTiming {...} Http_PerformanceTiming
```

## 概述

HTTP响应时间信息，会在[Http_Response](capi-netstack-http-response.md)中收集。

<!--Device-struct Http_PerformanceTiming {...}--><!--Device-struct Http_PerformanceTiming {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| double dnsTiming | 从request请求到DNS解析完成的耗时，包含域名解析，TCP连接等流程耗时。<br><!--Device-double dnsTiming--><!--Device-double dnsTiming-End--> |
| double tcpTiming | 从request请求到TCP连接完成的耗时。<br><!--Device-double tcpTiming--><!--Device-double tcpTiming-End--> |
| double tlsTiming | 从request请求到TLS连接完成的耗时。<br><!--Device-double tlsTiming--><!--Device-double tlsTiming-End--> |
| double firstSendTiming | 从request请求到开始发送第一个字节的耗时。<br><!--Device-double firstSendTiming--><!--Device-double firstSendTiming-End--> |
| double firstReceiveTiming | 从request请求到接收到第一个字节的耗时。<br><!--Device-double firstReceiveTiming--><!--Device-double firstReceiveTiming-End--> |
| double totalFinishTiming | 从request请求到完成请求的耗时。<br><!--Device-double totalFinishTiming--><!--Device-double totalFinishTiming-End--> |
| double redirectTiming | 从request请求到完成所有重定向步骤的耗时。<br><!--Device-double redirectTiming--><!--Device-double redirectTiming-End--> |


