# TimeoutOptions

Task timeout configuration.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-cacheDownload-interface TimeoutOptions--><!--Device-cacheDownload-interface TimeoutOptions-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## httpTotalTimeout

```TypeScript
httpTotalTimeout?: int
```

Complete HTTP request-response cycle timeout, in seconds. The default value is 60. The minimum value is 1. The value should be an integer.

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeoutOptions-httpTotalTimeout?: int--><!--Device-TimeoutOptions-httpTotalTimeout?: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## networkCheckTimeout

```TypeScript
networkCheckTimeout?: int
```

Network availability check timeout, in seconds. The default value is 20. The minimum value is 0. The maximum value is 20. When set to 0, no check will be performed. The value should be an integer.

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeoutOptions-networkCheckTimeout?: int--><!--Device-TimeoutOptions-networkCheckTimeout?: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

