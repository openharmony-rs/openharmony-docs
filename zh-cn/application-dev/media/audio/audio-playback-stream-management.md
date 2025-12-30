# 音频播放流管理
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

对于播放音频类的应用，开发者需要关注该应用的音频流的状态以做出相应的操作，比如监听到状态为播放中/暂停时，及时改变播放按钮的UI显示。

以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS)。

## 读取或监听应用内音频流状态变化

参考[使用AudioRenderer开发音频播放功能](using-audiorenderer-for-playback.md)或[audio.createAudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-f.md#audiocreateaudiorenderer8)，完成AudioRenderer的创建，然后可以通过以下两种方式查看音频流状态的变化：

- 方法1：直接查看AudioRenderer的[state](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#属性)：

  <!-- @[check_renderstate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
  
  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  // ...
      let audioRendererState: audio.AudioState = audioRenderer.state;
      console.info(`Current state is: ${audioRendererState }`);
  ```

- 方法2：注册stateChange监听AudioRenderer的状态变化：

  <!-- @[regist_listeningrendererchange](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
  
  ``` TypeScript
  import { audio } from '@kit.AudioKit';
  // ...
      audioRenderer.on('stateChange', (rendererState: audio.AudioState) => {
        console.info(`State change to: ${rendererState}`);
        // ...
      });
  ```

获取state后可对照[AudioState](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiostate8)来进行相应的操作，比如更改暂停播放按钮的显示等。

## 读取或监听所有音频流的变化

如果部分应用需要查询获取所有音频流的变化信息，可以通过AudioStreamManager读取或监听所有音频流的变化。

<!--Del-->
> **说明：**
> 
> 对于标记为系统接口（system api）的音频流变化信息需要系统级别应用才可查看，若应用不是系统应用，将无法获取准确信息。
<!--DelEnd-->

如下为音频流管理调用关系图：

![Audio stream management invoking relationship](figures/audio-stream-mgmt-invoking-relationship.png)

在进行应用开发的过程中，开发者需要先调用[getStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getstreammanager9)创建AudioStreamManager实例，进而通过该实例管理音频流。

详细API含义可参考[AudioStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md)。

## 开发步骤及注意事项

1. 创建AudioStreamManager实例。

   <!-- @[create_streammanager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
   let audioManager = audio.getAudioManager();
   // ...
   let audioStreamManager = audioManager.getStreamManager();
   ```

2. 使用[on('audioRendererChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#onaudiorendererchange9)监听音频播放流的变化。如果音频流监听应用需要在音频播放流状态变化、设备变化时获取通知，可以订阅该事件。

   <!-- @[regist_renderchangechallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
     audioStreamManager.on('audioRendererChange',  (audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
       for (let i = 0; i < audioRendererChangeInfoArray.length; i++) {
         let audioRendererChangeInfo = audioRendererChangeInfoArray[i];
         console.info(`## RendererChange on is called for ${i} ##`);
         console.info(`StreamId for ${i} is: ${audioRendererChangeInfo.streamId}`);
         console.info(`Content ${i} is: ${audioRendererChangeInfo.rendererInfo.content}`);
         console.info(`Stream ${i} is: ${audioRendererChangeInfo.rendererInfo.usage}`);
         console.info(`Flag ${i} is: ${audioRendererChangeInfo.rendererInfo.rendererFlags}`);
         // ...
         for (let j = 0;j < audioRendererChangeInfo.deviceDescriptors.length; j++) {
           console.info(`Id: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].id}`);
           console.info(`Type: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].deviceType}`);
           console.info(`Role: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].deviceRole}`);
           console.info(`Name: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].name}`);
           console.info(`Address: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].address}`);
           console.info(`SampleRates: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].sampleRates[0]}`);
           console.info(`ChannelCount ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].channelCounts[0]}`);
           console.info(`ChannelMask: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].channelMasks}`);
         }
       }
     });
   ```

3. （可选）使用[off('audioRendererChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#offaudiorendererchange9)取消监听音频播放流变化。

   <!-- @[unregist_renderchangechallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
 
   ``` TypeScript
   audioStreamManager.off('audioRendererChange');
   console.info('RendererChange Off is called ');
   ```

4. （可选）使用[getCurrentAudioRendererInfoArray](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#getcurrentaudiorendererinfoarray9)获取所有音频播放流的信息。该接口可获取音频播放流唯一ID、音频渲染器信息以及音频播放设备信息。

   > **说明：**
   >
   > 对所有音频流状态进行监听的应用需要[声明权限](../../security/AccessToken/declare-permissions.md)ohos.permission.USE_BLUETOOTH，否则无法获得实际的设备名称和设备地址信息，查询到的设备名称和设备地址（蓝牙设备的相关属性）将为空字符串。

   <!-- @[get_allstreaminfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioRendererSampleJS/entry/src/main/ets/pages/renderer.ets) -->
   
   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   // ...
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
   async function getCurrentAudioRendererInfoArray(): Promise<void> {
     await audioStreamManager.getCurrentAudioRendererInfoArray()
       .then((audioRendererChangeInfoArray: audio.AudioRendererChangeInfoArray) => {
         console.info(`getCurrentAudioRendererInfoArray  Get Promise is called `);
         // ...
         if (audioRendererChangeInfoArray != null) {
           for (let i = 0; i < audioRendererChangeInfoArray.length; i++) {
             let audioRendererChangeInfo = audioRendererChangeInfoArray[i];
             console.info(`StreamId for ${i} is: ${audioRendererChangeInfo.streamId}`);
             console.info(`Content ${i} is: ${audioRendererChangeInfo.rendererInfo.content}`);
             console.info(`Stream ${i} is: ${audioRendererChangeInfo.rendererInfo.usage}`);
             console.info(`Flag ${i} is: ${audioRendererChangeInfo.rendererInfo.rendererFlags}`);
             // ...
             for (let j = 0;j < audioRendererChangeInfo.deviceDescriptors.length; j++) {
               console.info(`Id: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].id}`);
               console.info(`Type: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].deviceType}`);
               console.info(`Role: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].deviceRole}`);
               console.info(`Name: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].name}`);
               console.info(`Address: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].address}`);
               console.info(`SampleRates: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].sampleRates[0]}`);
               console.info(`ChannelCount ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].channelCounts[0]}`);
               console.info(`ChannelMask: ${i} : ${audioRendererChangeInfo.deviceDescriptors[j].channelMasks}`);
             }
           }
         }
       }).catch((err: BusinessError ) => {
         console.error(`Invoke getCurrentAudioRendererInfoArray failed, code is ${err.code}, message is ${err.message}`);
         // ...
       });
   }
   ```