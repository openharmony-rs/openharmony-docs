# download

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

<a id="download"></a>
## download

```TypeScript
function download(config: DownloadConfig, callback: AsyncCallback<DownloadTask>): void
```

创建并启动一个下载任务，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [downloadFile(context:](arkts-basicservices-request-downloadfile-f.md#downloadfile-1)

**需要权限：** ohos.permission.INTERNET

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-request-function download(config: DownloadConfig, callback: AsyncCallback<DownloadTask>): void--><!--Device-request-function download(config: DownloadConfig, callback: AsyncCallback<DownloadTask>): void-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | 是 | 下载的配置信息。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;DownloadTask&gt; | 是 | 回调函数。当下载任务成功，err为undefined，data为获取到的DownloadTask对象；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
let downloadTask: request.DownloadTask;
// 需要手动将url替换为真实服务器的HTTP协议地址
request.download({ url: 'https://xxxx/xxxxx.hap', 
filePath: 'xxx/xxxxx.hap'}, (err: BusinessError, data: request.DownloadTask) => {
  if (err) {
    console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  downloadTask = data;
});

```


<a id="download-1"></a>
## download

```TypeScript
function download(config: DownloadConfig): Promise<DownloadTask>
```

创建并启动一个下载任务，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [downloadFile(context:](arkts-basicservices-request-downloadfile-f.md#downloadfile-1)

**需要权限：** ohos.permission.INTERNET

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-request-function download(config: DownloadConfig): Promise<DownloadTask>--><!--Device-request-function download(config: DownloadConfig): Promise<DownloadTask>-End-->

**系统能力：** SystemCapability.MiscServices.Download

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [DownloadConfig](arkts-basicservices-request-downloadconfig-i.md) | 是 | 下载的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DownloadTask&gt; | 使用Promise方式，异步返回下载任务DownloadTask的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The permissions check fails. |

**示例：**

```TypeScript
let downloadTask: request.DownloadTask;
// 需要手动将url替换为真实服务器的HTTP协议地址
request.download({ url: 'https://xxxx/xxxx.hap' }).then((data: request.DownloadTask) => {
  downloadTask = data;
}).catch((err: BusinessError) => {
  console.error(`Failed to request the download. Code: ${err.code}, message: ${err.message}`);
})

```

