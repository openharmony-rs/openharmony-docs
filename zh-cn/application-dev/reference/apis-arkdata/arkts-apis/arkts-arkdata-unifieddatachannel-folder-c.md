# Folder

文件夹类型数据，是[File](arkts-arkdata-unifieddatachannel-file-c.md)的子类，用于描述文件夹。

**继承/实现关系：** Folder extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## folderUri

```TypeScript
set folderUri(value: string)
```

表示文件夹的uri。

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
    let folder = new unifiedDataChannel.Folder();
    let filePath = pathDir + '/folder';
    folder.folderUri = fileUri.getUriFromPath(filePath);
  }
}
```
