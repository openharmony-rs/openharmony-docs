# setGlobalTimeoutOptions

## setGlobalTimeoutOptions

```TypeScript
function setGlobalTimeoutOptions(options?: TimeoutOptions): void
```

Sets timeout configuration for all tasks.
Used when task-specific timeout configuration is not configured.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TimeoutOptions | 否 | Task timeout configuration.<br>Default value: Refer to the default value of TimeoutOptions. |

**示例：**

```TypeScript
try {
  // 设置全局任务超时配置
  cacheDownload.setGlobalTimeoutOptions({
    networkCheckTimeout: 20,
    httpTotalTimeout: 60,
  })
  cacheDownload.download("https://www.example.com", {});
} catch (err) {
  console.error(`Failed to download the resource. err code: ${err?.code}, err message: ${err?.message}`);
}

```

