# HiTraceId

此接口为HiTraceId对象接口。用于标识分布式跟踪链中的唯一节点，在需要跨线程、跨进程、跨设备跟踪业务流程的场景中使用，例如电商下单流程、支付流 程、分布式服务调用链等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hiTraceChain-interface HiTraceId--><!--Device-hiTraceChain-interface HiTraceId-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## chainId

```TypeScript
chainId: bigint
```

跟踪链标识。

**类型：** bigint

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HiTraceId-chainId: bigint--><!--Device-HiTraceId-chainId: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## flags

```TypeScript
flags?: int
```

跟踪标志位，默认值为0。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HiTraceId-flags?: int--><!--Device-HiTraceId-flags?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## parentSpanId

```TypeScript
parentSpanId?: int
```

父分支标识，默认值为0。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HiTraceId-parentSpanId?: int--><!--Device-HiTraceId-parentSpanId?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## spanId

```TypeScript
spanId?: int
```

分支标识，默认值为0。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HiTraceId-spanId?: int--><!--Device-HiTraceId-spanId?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

