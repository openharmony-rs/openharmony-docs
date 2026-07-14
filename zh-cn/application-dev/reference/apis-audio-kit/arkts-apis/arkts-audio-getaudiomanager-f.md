# getAudioManager

## getAudioManager

```TypeScript
function getAudioManager(): AudioManager
```

获取音频管理器。

**起始版本：** 7

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AudioManager | 音频管理器对象。 |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

let audioManager = audio.getAudioManager();

```

