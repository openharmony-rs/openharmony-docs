# createSystemSoundPlayer

## createSystemSoundPlayer

```TypeScript
function createSystemSoundPlayer(): Promise<SystemSoundPlayer | null>
```

创建系统音效播放器对象。使用Promise异步回调。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.SystemSound.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SystemSoundPlayer \| null&gt; | 成功返回系统音效播放器对象，失败返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../../apis-media-kit/errorcode-media.md#5400101-内存分配失败) | No memory. Return by promise. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let systemSoundPlayer: systemSoundManager.SystemSoundPlayer | null = null;

systemSoundManager.createSystemSoundPlayer().then((systemSoundPlayerInstance) => {
  console.info('Succeeded in creating the system sound player.');
  systemSoundPlayer = systemSoundPlayerInstance;
}).catch((err: BusinessError) => {
  console.error(`Failed to create the system sound player. Code: ${err.code}, message: ${err.message}`);
});

```

