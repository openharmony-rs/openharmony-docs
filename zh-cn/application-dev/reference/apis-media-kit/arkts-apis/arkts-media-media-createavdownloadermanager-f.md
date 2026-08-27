# createAVDownloaderManager

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createAVDownloaderManager

```TypeScript
function createAVDownloaderManager(): Promise<AVDownloaderManager>
```

创建一个离线下载任务管理器实例。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVDownloaderManager](arkts-media-media-avdownloadermanager-i.md)&gt; | Promise对象。返回离线下载任务管理器实例。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  media.createAVDownloaderManager().then((downloaderManager: media.AVDownloaderManager) => {
    console.info('Succeeded in creating AVDownloaderManager');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create AVDownloaderManager, error: ${error}`);
  });
}
```
