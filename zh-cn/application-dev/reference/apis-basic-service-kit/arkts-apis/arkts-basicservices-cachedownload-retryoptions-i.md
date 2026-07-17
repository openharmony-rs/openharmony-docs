# RetryOptions

Task retry configuration.

**起始版本：** 26.0.0

<!--Device-cacheDownload-interface RetryOptions--><!--Device-cacheDownload-interface RetryOptions-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## maxRetryCount

```TypeScript
maxRetryCount?: number
```

Maximum number of retry attempts.The default value is 1.The minimum value is 0.The maximum value is 10.When set to 0, no retries will be performed.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RetryOptions-maxRetryCount?: int--><!--Device-RetryOptions-maxRetryCount?: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

