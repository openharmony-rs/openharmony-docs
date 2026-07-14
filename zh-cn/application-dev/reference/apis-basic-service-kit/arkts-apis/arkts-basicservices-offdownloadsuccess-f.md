# offDownloadSuccess

## offDownloadSuccess

```TypeScript
function offDownloadSuccess(url: string, callback?: Callback<void>): void
```

取消订阅预下载的完成事件。使用callback异步回调。

**起始版本：** 23

**系统能力：** SystemCapability.Request.FileTransferAgent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 待注册回调的url，url字符串的最大长度为8192字节。 |
| callback | Callback&lt;void&gt; | 否 | 回调函数。若不填该参数，表示url下的所有完成回调函数。 |

**示例：**

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';

try {
  const successCallback = () => {
    console.info("Succeeded in getting callback from cacheDownload");
  };
  // 订阅预下载的完成事件，当下载完成时执行回调
  cacheDownload.onDownloadSuccess("https://www.example.com", successCallback);
  // 取消订阅预下载的完成事件
  cacheDownload.offDownloadSuccess("https://www.example.com", successCallback);
  // 进行缓存下载，资源若下载成功会被缓存到应用内存或应用沙箱目录的特定文件中。  
  cacheDownload.download("https://www.example.com", {});
} catch (err) {
  console.error(`Failed to download the resource. err code: ${err.code}, err message: ${err.message}`);
}

```

