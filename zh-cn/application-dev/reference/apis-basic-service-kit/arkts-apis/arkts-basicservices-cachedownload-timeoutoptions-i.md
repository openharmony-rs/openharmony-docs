# TimeoutOptions

Task timeout configuration.

**起始版本：** 26.0.0

<!--Device-cacheDownload-interface TimeoutOptions--><!--Device-cacheDownload-interface TimeoutOptions-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## httpTotalTimeout

```TypeScript
httpTotalTimeout?: number
```

Complete HTTP request-response cycle timeout, in seconds.The default value is 60.The minimum value is 1.The value should be an integer.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeoutOptions-httpTotalTimeout?: int--><!--Device-TimeoutOptions-httpTotalTimeout?: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## networkCheckTimeout

```TypeScript
networkCheckTimeout?: number
```

Network availability check timeout, in seconds.The default value is 20.The minimum value is 0.The maximum value is 20.When set to 0, no check will be performed.The value should be an integer.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeoutOptions-networkCheckTimeout?: int--><!--Device-TimeoutOptions-networkCheckTimeout?: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

