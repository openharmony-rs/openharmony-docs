# MicStateChangeEvent

麦克风状态变化时，应用接收到的事件。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## mute

```TypeScript
mute: boolean
```

系统麦克风是否为静音状态。true表示静音，false表示非静音。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Device

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioVolumeGroupManager.mute(audio.AudioVolumeType.MEDIA, true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to mute the stream. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the stream is muted.');
});
```

```TypeScript
audioVolumeGroupManager.mute(audio.AudioVolumeType.MEDIA, true).then(() => {
  console.info('Promise returned to indicate that the stream is muted.');
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.mute(audio.AudioVolumeType.MEDIA, true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to mute the stream. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in muting the stream.');
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioManager.mute(audio.AudioVolumeType.MEDIA, true).then(() => {
  console.info('Succeeded in muting the stream.');
}).catch((err: BusinessError) => {
  console.error(`Failed to mute the stream. Code: ${err.code}, message: ${err.message}`);
});
```
