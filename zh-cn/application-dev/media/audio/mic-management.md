# 管理麦克风静音状态
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

因为在录制过程中需要使用麦克风录制相关音频数据，所以建议开发者在调用录制接口前查询麦克风状态，并在录制过程中监听麦克风的状态变化，避免影响录制效果。

在音频录制过程中，用户可以将麦克风静音，此时录音过程正常进行，录制生成的数据文件的大小随录制时长递增，但写入文件的数据均为0，即无声数据（空白数据）。

录音不支持音量调节。

## 开发步骤及注意事项

以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS)。

在AudioVolumeGroupManager中提供了管理麦克风状态的方法，接口的详细说明请参考音量API文档[AudioVolumeGroupManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioVolumeGroupManager.md)。

1. 创建audioVolumeGroupManager对象。

   <!-- @[create_AudioVolumeGroupManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/MacManager.ets) --> 
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   
   let audioVolumeGroupManager: audio.AudioVolumeGroupManager;
   // 创建audioVolumeGroupManager对象。
   async function loadVolumeGroupManager(updateCallback?: (msg: string, isError: boolean) => void): Promise<void> {
     const groupid = audio.DEFAULT_VOLUME_GROUP_ID;
     audioVolumeGroupManager = await audio.getAudioManager().getVolumeManager().getVolumeGroupManager(groupid);
     console.info('audioVolumeGroupManager create success.');
     // ...
   }
   ```

2. 调用[on('micStateChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioVolumeGroupManager.md#onmicstatechange9)监听麦克风状态变化，当麦克风静音状态发生变化时将通知应用。

   目前此订阅接口在单进程多AudioManager实例的使用场景下，仅最后一个实例的订阅生效，其他实例的订阅会被覆盖（即使最后一个实例没有进行订阅），因此推荐使用单一AudioManager实例进行开发。

   <!-- @[mac_on](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/MacManager.ets) --> 

   ``` TypeScript
   // 监听麦克风状态变化。
   async function on() {
     audioVolumeGroupManager.on('micStateChange', (micStateChange: audio.MicStateChangeEvent) => {
       console.info(`Current microphone status is: ${micStateChange.mute} `);
     });
   }
   ```

3. 调用[isMicrophoneMute](../../reference/apis-audio-kit/arkts-apis-audio-AudioVolumeGroupManager.md#ismicrophonemute9)查询麦克风当前静音状态，返回true为静音，false为非静音。

   <!-- @[is_MicrophoneMute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/MacManager.ets) -->

   ``` TypeScript
   // 查询麦克风是否静音。
   async function isMicrophoneMute(updateCallback?: (msg: string, isError: boolean) => void): Promise<void> {
     await audioVolumeGroupManager.isMicrophoneMute().then((value: boolean) => {
       console.info(`isMicrophoneMute is: ${value}.`);
       // ...
     });
   }
   ```

   <!--Del-->
4. **（仅对系统应用开放）** 根据查询结果的实际情况，调用[setMicMute](../../reference/apis-audio-kit/js-apis-audio-sys.md#setmicmute11)设置麦克风静音状态，入参输入true为静音，false为非静音。

   ``` TypeScript
   // 设置麦克风静音，入参为true。
   async function setMicrophoneMuteTrue() {
     await audioVolumeGroupManager.setMicMute(true).then(() => {
       console.info('setMicrophoneMute to mute.');
     });
   }

   // 取消麦克风静音，入参为false。
   async function setMicrophoneMuteFalse() {
     await audioVolumeGroupManager.setMicMute(false).then(() => {
       console.info('setMicrophoneMute to not mute.');
     });
   }
   ```

## 完整示例

参考以下示例，完成从设置麦克风静音到取消麦克风静音的过程。

``` TypeScript
import { audio } from '@kit.AudioKit';

let audioVolumeGroupManager: audio.AudioVolumeGroupManager;

async function loadVolumeGroupManager() {
  const groupid = audio.DEFAULT_VOLUME_GROUP_ID;
  audioVolumeGroupManager = await audio.getAudioManager().getVolumeManager().getVolumeGroupManager(groupid);
  console.info('audioVolumeGroupManager------create-------success.');
}

// 监听麦克风状态变化。
async function on() {
  await loadVolumeGroupManager();
  audioVolumeGroupManager.on('micStateChange', (micStateChange) => {
    console.info(`Current microphone status is: ${micStateChange.mute} `);
  });
}

// 查询麦克风是否静音。
async function isMicrophoneMute() {
  await audioVolumeGroupManager.isMicrophoneMute().then((value) => {
    console.info(`isMicrophoneMute is: ${value}.`);
  });
}

// 设置麦克风静音。
async function setMicrophoneMuteTrue() {
  await loadVolumeGroupManager();
  await audioVolumeGroupManager.setMicMute(true).then(() => {
    console.info('setMicrophoneMute to mute.');
  });
}

// 取消麦克风静音。
async function setMicrophoneMuteFalse() {
  await loadVolumeGroupManager();
  await audioVolumeGroupManager.setMicMute(false).then(() => {
    console.info('setMicrophoneMute to not mute.');
  });
}

async function test(){
  await on();
  await isMicrophoneMute();
  await setMicrophoneMuteTrue();
  await isMicrophoneMute();
  await setMicrophoneMuteFalse();
  await isMicrophoneMute();
  await setMicrophoneMuteTrue();
  await isMicrophoneMute();
}
```
   <!--DelEnd--> 