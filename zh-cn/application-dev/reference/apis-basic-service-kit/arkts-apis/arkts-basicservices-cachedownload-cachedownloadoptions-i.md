# CacheDownloadOptions

缓存下载的配置选项。包括HTTP选项、传输选项和任务选项。

**起始版本：** 18

<!--Device-cacheDownload-interface CacheDownloadOptions--><!--Device-cacheDownload-interface CacheDownloadOptions-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';
```

## caPath

```TypeScript
caPath?: string
```

CA证书路径。目前仅支持.pem格式证书，默认使用系统预设的CA证书。

**类型：** string

**起始版本：** 21

<!--Device-CacheDownloadOptions-caPath?: string--><!--Device-CacheDownloadOptions-caPath?: string-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## cacheStrategy

```TypeScript
cacheStrategy?: CacheStrategy
```

使用缓存刷新策略FORCE或LAZY，默认使用FORCE。

**类型：** CacheStrategy

**起始版本：** 23

<!--Device-CacheDownloadOptions-cacheStrategy?: CacheStrategy--><!--Device-CacheDownloadOptions-cacheStrategy?: CacheStrategy-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## headers

```TypeScript
headers?: Record<string, string>
```

缓存下载任务在HTTP传输时使用的请求头。默认值为空。

**类型：** Record&lt;string, string&gt;

**起始版本：** 18

<!--Device-CacheDownloadOptions-headers?: Record<string, string>--><!--Device-CacheDownloadOptions-headers?: Record<string, string>-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## retry

```TypeScript
retry?: RetryOptions
```

Task retry configuration.

**类型：** RetryOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CacheDownloadOptions-retry?: RetryOptions--><!--Device-CacheDownloadOptions-retry?: RetryOptions-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## sslType

```TypeScript
sslType?: SslType
```

使用安全通信协议TLS或TLCP，默认使用TLS。当前TLS和TLCP均不支持双向认证。

**类型：** SslType

**起始版本：** 21

<!--Device-CacheDownloadOptions-sslType?: SslType--><!--Device-CacheDownloadOptions-sslType?: SslType-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## timeout

```TypeScript
timeout?: TimeoutOptions
```

Task timeout configuration.

**类型：** TimeoutOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CacheDownloadOptions-timeout?: TimeoutOptions--><!--Device-CacheDownloadOptions-timeout?: TimeoutOptions-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

