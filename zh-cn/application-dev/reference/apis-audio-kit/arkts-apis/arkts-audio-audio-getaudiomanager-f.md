# getAudioManager

## getAudioManager

```TypeScript
function getAudioManager(): AudioManager
```

获取音频管理器。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-audio-function getAudioManager(): AudioManager--><!--Device-audio-function getAudioManager(): AudioManager-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 音频管理器对象。 |

**示例：**

```TypeScript
import { audio } from '@kit.AudioKit';

let audioManager = audio.getAudioManager();
```

