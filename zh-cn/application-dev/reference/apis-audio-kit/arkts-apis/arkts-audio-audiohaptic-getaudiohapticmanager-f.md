# getAudioHapticManager

## 导入模块

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

<a id="getaudiohapticmanager"></a>
## getAudioHapticManager

```TypeScript
function getAudioHapticManager(): AudioHapticManager
```

获取音振管理器。

**起始版本：** 11

<!--Device-audioHaptic-function getAudioHapticManager(): AudioHapticManager--><!--Device-audioHaptic-function getAudioHapticManager(): AudioHapticManager-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AudioHapticManager](arkts-audio-audiohaptic-audiohapticmanager-i.md) | 音振管理器。 |

**示例：**

```TypeScript
let audioHapticManagerInstance: audioHaptic.AudioHapticManager = audioHaptic.getAudioHapticManager();

```

