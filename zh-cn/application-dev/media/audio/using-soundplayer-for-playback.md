# 使用SoundPlayer开发系统音效播放功能
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @huyue57-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

从API版本23开始，支持系统音效播放。

SoundPlayer提供系统音效播放功能，适用于拍照或录像提示音，比如在开始拍照、开始录像或结束录像时播放提示音。

## 支持的音效类型

支持的音效类型SystemSoundType信息如下表所示。可通过`systemSoundManager.SystemSoundType.PHOTO_SHUTTER`等具体类型，作为load、play或unload方法的入参。

| 播放音效类型 | 值 | 说明 | 
| -------- | -------- | -------- |
| PHOTO_SHUTTER | 0 | 拍照音效。 | 
| VIDEO_RECORDING_BEGIN | 1 | 视频录制开始音效。 | 
| VIDEO_RECORDING_END | 2 | 视频录制结束音效。 |

## 开发步骤

以下各步骤示例为片段代码，可通过点击示例代码右下方的链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/SystemSoundPlayer)。

1. 在调用SystemSoundPlayer的接口前，需要先通过createSystemSoundPlayer创建实例。

   <!-- @[sound_player_create](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/SystemSoundPlayer/entry/src/main/ets/pages/SoundPlayer.ets) -->
   
   ``` TypeScript
   import { systemSoundManager } from '@kit.AudioKit';
   // ...
   
   // SystemSoundPlayer对象。
   let systemSoundPlayer: systemSoundManager.SystemSoundPlayer | null = null;
   
   // ...
     systemSoundManager.createSystemSoundPlayer().then((systemSoundPlayerInstance) => {
       console.info('Succeeded in creating the system sound player.');
       systemSoundPlayer = systemSoundPlayerInstance;
     }).catch((err: BusinessError) => {
       console.error(`Failed to create the system sound player. Code: ${err.code}, message: ${err.message}`);
     });
   ```

2. 调用load接口，加载指定类型音效资源。

   <!-- @[sound_player_load](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/SystemSoundPlayer/entry/src/main/ets/pages/SoundPlayer.ets) -->
   
   ``` TypeScript
   import { systemSoundManager } from '@kit.AudioKit';
   // ...
   
   // 音效类型。
   let systemSoundType: systemSoundManager.SystemSoundType = systemSoundManager.SystemSoundType.PHOTO_SHUTTER;
   
   // ...
     systemSoundPlayer?.load(systemSoundType).then(() => {
       console.info('Succeeded in calling the load method.');
     }).catch((err: BusinessError) => {
       console.error(`Failed to call the load method. Code: ${err.code}, message: ${err.message}`);
     });
   ```

3. 调用play接口，播放已加载的音效资源。

   <!-- @[sound_player_play](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/SystemSoundPlayer/entry/src/main/ets/pages/SoundPlayer.ets) -->
   
   ``` TypeScript
   import { systemSoundManager } from '@kit.AudioKit';
   // ...
   
   // 音效类型。
   let systemSoundType: systemSoundManager.SystemSoundType = systemSoundManager.SystemSoundType.PHOTO_SHUTTER;
   
   // ...
     systemSoundPlayer?.play(systemSoundType).then(() => {
       console.info('Succeeded in calling the play method.');
     }).catch((err: BusinessError) => {
       console.error(`Failed to call the play method. Code: ${err.code}, message: ${err.message}`);
     });
   ```

4. 调用unload接口，卸载之前已加载的音效资源。

   <!-- @[sound_player_unload](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/SystemSoundPlayer/entry/src/main/ets/pages/SoundPlayer.ets) -->
   
   ``` TypeScript
   import { systemSoundManager } from '@kit.AudioKit';
   // ...
   
   // 音效类型。
   let systemSoundType: systemSoundManager.SystemSoundType = systemSoundManager.SystemSoundType.PHOTO_SHUTTER;
   
   // ...
     systemSoundPlayer?.unload(systemSoundType).then(() => {
       console.info('Succeeded in calling the unload method.');
     }).catch((err: BusinessError) => {
       console.error(`Failed to call the unload method. Code: ${err.code}, message: ${err.message}`);
     });
   ```

5. 调用release接口，释放系统音效播放器。

   <!-- @[sound_player_release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/SystemSoundPlayer/entry/src/main/ets/pages/SoundPlayer.ets) -->
   
   ``` TypeScript
   systemSoundPlayer?.release().then(() => {
     console.info('Succeeded in calling the release method.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to call the release method. Code: ${err.code}, message: ${err.message}`);
   });
   ```