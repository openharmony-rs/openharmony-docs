# HiTraceId

此接口为HiTraceId对象接口。用于标识分布式跟踪链中的唯一节点，在需要跨线程、跨进程、跨设备跟踪业务流程的场景中使用，例如电商下单流程、支付流 程、分布式服务调用链等。

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## 导入模块

```TypeScript
```

## chainId

```TypeScript
chainId: bigint
```

跟踪链标识。

**类型：** bigint

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## flags

```TypeScript
flags?: number
```

跟踪标志位，默认值为0。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## parentSpanId

```TypeScript
parentSpanId?: number
```

父分支标识，默认值为0。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## spanId

```TypeScript
spanId?: number
```

分支标识，默认值为0。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiTrace
