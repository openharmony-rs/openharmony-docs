# PlaybackStrategy

播放器首选播放设置。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## enableCameraPostprocessing

```TypeScript
enableCameraPostprocessing?: boolean
```

表示是否在视频播放时启用相机后处理，用于在播放视频内容时应用图像增强。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.Core

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
async function test(){
  let avPlayer = await media.createAVPlayer();
  // 此处仅为示意，实际开发中需要在stateChange事件成功触发至initialized状态后才能调用。
  avPlayer.enableCameraPostprocessing();
}
```
