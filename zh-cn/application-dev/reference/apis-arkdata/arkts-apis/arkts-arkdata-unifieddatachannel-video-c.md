# Video

视频类型数据，是[File](arkts-arkdata-unifieddatachannel-file-c.md)的子类，用于描述视频文件。

**继承/实现关系：** Video extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## videoUri

```TypeScript
set videoUri(value: string)
```

本地视频数据uri或网络视频uri，本地视频数据uri可通过[getUriFromPath](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md)函数获取。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**示例**

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
import { fileUri } from '@kit.CoreFileKit';
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let context = this.context;
    let pathDir = context.filesDir;
    let video = new unifiedDataChannel.Video();
    let filePath = pathDir + '/test.mp4';
    video.videoUri = fileUri.getUriFromPath(filePath);
  }
}
```
