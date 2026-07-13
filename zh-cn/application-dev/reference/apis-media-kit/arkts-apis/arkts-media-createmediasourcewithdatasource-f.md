# createMediaSourceWithDataSource

## createMediaSourceWithDataSource

```TypeScript
function createMediaSourceWithDataSource(dataSrc: AVDataSrcDescriptor): MediaSource | undefined
```

通过自定义数据源创建媒体源。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dataSrc | AVDataSrcDescriptor | 是 | 流式媒体资源描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MediaSource | 返回MediaSource，用于媒体资源设置。 |

**示例：**

```TypeScript
import { common } from '@kit.AbilityKit';
import { fileIo as fs, ReadOptions } from '@kit.CoreFileKit';

let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let fileDescriptor = await context.resourceManager.getRawFd('xxx.mp4');
let file = fs.openSync("xxx.mp4");
let dataSrc: media.AVDataSrcDescriptor = {
  fileSize: fileDescriptor.length,
  callback: (buf: ArrayBuffer, length: number, pos?: number) => {
    let readLen = 0;
    if (pos) {
      let option: ReadOptions = {
        offset: pos,
        length: length,
      };
      readLen = fs.readSync(file.fd, buf, option);
    }
    return readLen > 0 ? readLen : -1;
  }
}
let mediaSource : media.MediaSource | undefined =  media.createMediaSourceWithDataSource(dataSrc);

```

