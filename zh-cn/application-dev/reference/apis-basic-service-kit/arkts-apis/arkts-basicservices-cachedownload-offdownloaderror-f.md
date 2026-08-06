# offDownloadError

## offDownloadError

```TypeScript
function offDownloadError(url: string, callback?: Callback<DownloadError>): void
```

取消订阅预下载的错误事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-cacheDownload-function offDownloadError(url: string, callback?: Callback<DownloadError>): void--><!--Device-cacheDownload-function offDownloadError(url: string, callback?: Callback<DownloadError>): void-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 待注册回调的url，url字符串最大长度为8192字节。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DownloadError&gt; | 否 | 回调函数，返回预下载的错误信息。若不填该参数，表示url下的所有错误回调函数。 |

**示例：**

ArkTS-Dyn示例：

```TypeScript
try {
  const errorCallback = (error: cacheDownload.DownloadError) => {
    console.error(`Error callback from cacheDownload. error code: ${error.errorCode}, error message: ${error.message}`);
  };
  // 订阅预下载的错误事件，当下载错误时执行回调，返回错误信息
  cacheDownload.onDownloadError("https://www.example.com", errorCallback);
  // 取消订阅预下载的错误事件
  cacheDownload.offDownloadError("https://www.example.com", errorCallback);
  // 进行缓存下载，资源若下载成功会被缓存到应用内存或应用沙箱目录的特定文件中。  
  cacheDownload.download("https://www.example.com", {});
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
try {
  const errorCallback = (error: cacheDownload.DownloadError) => {
    console.error(`Error callback from cacheDownload. error code: ${error.errorCode}, error message: ${error.message}`);
  };
  // 订阅预下载的错误事件，当下载错误时执行回调，返回错误信息
  cacheDownload.onDownloadError("https://www.example.com", errorCallback);
  // 取消订阅预下载的错误事件
  cacheDownload.offDownloadError("https://www.example.com", errorCallback);
  // 进行缓存下载，资源若下载成功会被缓存到应用内存或应用沙箱目录的特定文件中。
  cacheDownload.download("https://www.example.com", {});
} catch (err: Error) {
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}
```

