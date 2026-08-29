# createMediaSourceWithDirectory

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## createMediaSourceWithDirectory

```TypeScript
function createMediaSourceWithDirectory(path: string): Promise< MediaSource | undefined>
```

根据指定目录路径创建一个媒体源对象。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 用于创建媒体源的目录路径信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[MediaSource](arkts-media-media-mediasource-i.md) \| undefined&gt; | Promise对象。成功时返回MediaSource实例，失败时返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5411007](../errorcode-media.md#5411007-无可用资源) | The directory specified by the path parameter does not exist or inaccessible. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function test() {
  media.createMediaSourceWithDirectory("/data/storage/el2/base/media/cache/").then((mediaSource: media.MediaSource | undefined) => {
    if (mediaSource) {
      console.info('Succeeded in creating MediaSource with directory');
    } else {
      console.error('Failed to create MediaSource with directory');
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to create MediaSource with directory, error: ${error}`);
  });
}
```
