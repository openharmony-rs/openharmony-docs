# HiTraceFlag

跟踪标志组合类型枚举。用于控制分布式跟踪的行为模式，例如在需要跟踪异步调用的业务流程中使用INCLUDE\_ASYNC标志，在不需要详细分支信息的简单业务 流程中使用DONOT\_CREATE\_SPAN标志，在需要调试埋点信息的场景中使用TP\_INFO标志。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-hiTraceChain-enum HiTraceFlag--><!--Device-hiTraceChain-enum HiTraceFlag-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DEFAULT

```TypeScript
DEFAULT = 0
```

默认标志。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceFlag-DEFAULT = 0--><!--Device-HiTraceFlag-DEFAULT = 0-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## INCLUDE_ASYNC

```TypeScript
INCLUDE_ASYNC = 1
```

异步调用标志。 设置该标志，同时跟踪同步和异步调用；默认只跟踪同步调用。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceFlag-INCLUDE_ASYNC = 1--><!--Device-HiTraceFlag-INCLUDE_ASYNC = 1-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DONOT_CREATE_SPAN

```TypeScript
DONOT_CREATE_SPAN = 1 << 1
```

无分支标志。 设置该标志，不创建分支信息；默认创建分支信息。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceFlag-DONOT_CREATE_SPAN = 1 << 1--><!--Device-HiTraceFlag-DONOT_CREATE_SPAN = 1 << 1-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## TP_INFO

```TypeScript
TP_INFO = 1 << 2
```

埋点标志。 设置该标志后，调用[tracepoint()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口时会打印埋点信息hilog；默认不打印埋点信息hilog日志。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceFlag-TP_INFO = 1 << 2--><!--Device-HiTraceFlag-TP_INFO = 1 << 2-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## NO_BE_INFO

```TypeScript
NO_BE_INFO = 1 << 3
```

无开始结束信息标志。 调试场景下设置该标志，调用开始跟踪接口[begin()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和结束跟踪接口[end()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_时， 分别会打印开始、结束跟踪信息hilo日志；默认不打印开始、结束跟踪信息hilog日志。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceFlag-NO_BE_INFO = 1 << 3--><!--Device-HiTraceFlag-NO_BE_INFO = 1 << 3-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## DISABLE_LOG

```TypeScript
DISABLE_LOG = 1 << 4
```

日志关联标志。 设置该标志，不会在hilog日志中附加HiTraceId信息；默认会在hilog日志中附加HiTraceId信息。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceFlag-DISABLE_LOG = 1 << 4--><!--Device-HiTraceFlag-DISABLE_LOG = 1 << 4-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## FAILURE_TRIGGER

```TypeScript
FAILURE_TRIGGER = 1 << 5
```

故障触发标志。预置标志，暂未启用。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceFlag-FAILURE_TRIGGER = 1 << 5--><!--Device-HiTraceFlag-FAILURE_TRIGGER = 1 << 5-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

## D2D_TP_INFO

```TypeScript
D2D_TP_INFO = 1 << 6
```

设备间埋点标志，为TP\_INFO的子集，用于调试场景。 已设置TP\_INFO时，D2D\_TP\_INFO不生效；未设置TP\_INFO时，D2D\_TP\_INFO生效，调用信息埋点接口 [tracepoint()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_仅在mode参数为DEVICE时打印埋点信息hilog日志。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-HiTraceFlag-D2D_TP_INFO = 1 << 6--><!--Device-HiTraceFlag-D2D_TP_INFO = 1 << 6-End-->

**系统能力：** SystemCapability.HiviewDFX.HiTrace

