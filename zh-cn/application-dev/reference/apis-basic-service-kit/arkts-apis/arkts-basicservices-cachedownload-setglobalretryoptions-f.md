# setGlobalRetryOptions

## setGlobalRetryOptions

```TypeScript
function setGlobalRetryOptions(options?: RetryOptions): void
```

Sets retry options for all tasks. Used when task-specific retry configuration is not configured.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cacheDownload-function setGlobalRetryOptions(options?: RetryOptions): void--><!--Device-cacheDownload-function setGlobalRetryOptions(options?: RetryOptions): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RetryOptions](arkts-basicservices-cachedownload-retryoptions-i.md) | 否 | Task retry configurations. &lt;br&gt;Default value: Refer to the default value of RetryOptions. |

## 示例

ArkTS-Dyn示例：

```TypeScript
try {
  // 设置全局的任务最大重试次数
  cacheDownload.setGlobalRetryOptions({
    maxRetryCount: 1
  });
  cacheDownload.download("https://www.example.com", {});
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
try {
  // 设置全局的任务最大重试次数
  cacheDownload.setGlobalRetryOptions({
    maxRetryCount: 1
  });
  cacheDownload.download("https://www.example.com", {});
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}
```

