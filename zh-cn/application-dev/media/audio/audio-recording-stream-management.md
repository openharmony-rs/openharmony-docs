# 查询和监听其他应用录制状态
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zyy0412-->
<!--Designer: @weixin_41398971-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

对于录制音频类的应用，开发者需要关注该应用的音频流的状态以做出相应的操作，比如监听到状态为结束时，及时提示用户录制已结束。

以下各步骤示例为片段代码，可通过示例代码右下方链接获取[完整示例](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS)。

## 读取或监听应用内音频流状态变化

参考[使用AudioCapturer开发音频录制功能(ArkTs)](using-audiocapturer-for-recording.md)或[audio.createAudioCapturer](../../reference/apis-audio-kit/arkts-apis-audio-f.md#audiocreateaudiocapturer8)，先完成AudioCapturer的创建，再通过以下两种方法查看音频流状态的变化。

- 方法1：直接查看AudioCapturer的[属性](../../reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#属性)state：

  <!-- @[view_AudioCapturerState](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->

  ``` TypeScript
  let audioCapturerState: audio.AudioState = audioCapturer.state;
  console.info(`Current state is: ${audioCapturerState }`)
  ```

- 方法2：注册stateChange监听AudioCapturer的状态变化：

  <!-- @[listen_AudioCapturerState](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioCapture.ets) -->
  
  ``` TypeScript
  audioCapturer.on('stateChange', (capturerState: audio.AudioState) => {
    console.info(`State change to: ${capturerState}`)
    // ...
  });
  ```

获取state后可根据[AudioState](../../reference/apis-audio-kit/arkts-apis-audio-e.md#audiostate8)来进行相应的操作，比如显示录制结束的提示等。

## 读取或监听所有录制流的变化

如果部分应用需要查询所有音频流的变化信息，可以通过AudioStreamManager读取或监听所有音频流的变化。

### 判断麦克风是否被占用

录音、语音识别、实时语音通话、短语音消息、直播连麦等业务在启动音频采集前，通常需要先判断麦克风是否被占用。若麦克风已被其他录制流占用，新录音流可能无法正常启动；或者在启动成功后，也可能在运行过程中受系统音频焦点或录音并发策略影响而被中断、进入静音录制状态，进而导致录音文件不完整、语音识别结果缺失等问题。

如果需要判断麦克风是否被占用，可根据业务场景任选以下一种方式：

- 查询当前采集器和输入设备电平：如果需要主动查询当前是否有输入设备正在采集声音，可联合使用[getCurrentAudioCapturerInfoArray](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#getcurrentaudiocapturerinfoarray9)和[getMaxAmplitudeForInputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioVolumeGroupManager.md#getmaxamplitudeforinputdevice12)。先调用`getCurrentAudioCapturerInfoArray`获取当前音频采集器信息，再遍历每个采集器使用的输入设备并调用`getMaxAmplitudeForInputDevice`获取音频流最大电平值，取值范围为[0, 1]。当最大电平值大于0时，说明该设备采集到声音，设备正在录音，可判断麦克风正在被占用。
- 监听录制流变化：如果需要持续感知麦克风占用状态变化，可调用[on('audioCapturerChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#onaudiocapturerchange9)监听音频录制流变化。当回调返回的录制流列表从空变为非空、或出现业务需要关注的麦克风输入录制流时，表示有应用开始录音；当列表中不再存在对应录制流时，表示录音已停止。示例代码可参考[on('audioCapturerChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#onaudiocapturerchange9)。
- 判断指定录制请求是否可启动：如果需要在启动录音前判断指定音源类型的录制请求是否可以启动，可调用[isRecordingAvailable](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#isrecordingavailable20)，传入业务要使用的[AudioCapturerInfo](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiocapturerinfo8)。返回`true`表示当前音源类型的录制可以启动，返回`false`表示当前录制请求可能因被占用或焦点策略等原因启动失败。示例代码可参考[isRecordingAvailable](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#isrecordingavailable20)。

> **说明：**
>
> - `isRecordingAvailable`用于判断传入音源类型的录制是否可以启动成功，不用于返回当前正在录制的应用或录制流详情。需要查看录制流详情时，使用`getCurrentAudioCapturerInfoArray`；需要持续感知录制流变化时，使用`on('audioCapturerChange')`。
> - `SourceType`表示录制流的音源类型。除`SOURCE_TYPE_MIC`外，语音识别`SOURCE_TYPE_VOICE_RECOGNITION`、语音通话`SOURCE_TYPE_VOICE_COMMUNICATION`、短语音`SOURCE_TYPE_VOICE_MESSAGE`、录像`SOURCE_TYPE_CAMCORDER`、纯净录音`SOURCE_TYPE_UNPROCESSED`等录制场景也可能使用麦克风输入。如果当前业务创建录制流时仅使用`SOURCE_TYPE_MIC`，可只过滤`SOURCE_TYPE_MIC`；如果业务需要把上述场景也作为麦克风占用处理，应按业务范围同时过滤对应音源类型。
> - `getMaxAmplitudeForInputDevice`用于获取指定输入设备音频流的最大电平值。需先通过`getCurrentAudioCapturerInfoArray`获取音频采集器正在使用的输入设备信息，再调用该接口查询对应设备的最大电平值。
> - `getCurrentAudioCapturerInfoArray`和`on('audioCapturerChange')`返回的音频采集器信息可能包含系统内部音频录制流，如语音唤醒、蜂窝通话等。开发者可通过返回结果中[AudioCapturerChangeInfo](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiocapturerchangeinfo9)的[capturerInfo](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiocapturerchangeinfo9)属性获取[AudioCapturerInfo](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiocapturerinfo8)，再结合其[source](../../reference/apis-audio-kit/arkts-apis-audio-i.md#audiocapturerinfo8)属性和业务场景，判断该录制流是否属于当前业务需要识别的麦克风占用场景。

<!--Del-->
> **说明：**
> 
> 对于标记为系统接口（system api）的音频流变化信息需要系统级别应用才可查看，若应用不是系统应用，将无法获取准确信息。
<!--DelEnd-->

如下为音频流管理调用关系图：

![Invoking relationship of recording stream management](figures/invoking-relationship-recording-stream-mgmt.png)

在进行应用开发的过程中，开发者需要先调用[getStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioManager.md#getstreammanager9)创建AudioStreamManager实例，进而通过该实例管理音频流。

详细API含义可参考[AudioStreamManager](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md)。

## 开发步骤及注意事项

1. 创建AudioStreamManager实例。

   <!-- @[get_StreamManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioStreamManager.ets) -->

   ``` TypeScript
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   let audioManager = audio.getAudioManager();
   let audioStreamManager = audioManager.getStreamManager();
   ```

2. 使用[on('audioCapturerChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#onaudiocapturerchange9)监听音频录制流变化事件。如果应用需要在音频录制流状态变化、设备变化时获取通知，可以订阅该事件。

   <!-- @[audioStreamManager_on](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioStreamManager.ets) -->
   
   ``` TypeScript
   audioStreamManager.on('audioCapturerChange', (audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) =>  {
     // ...
     for (let i = 0; i < audioCapturerChangeInfoArray.length; i++) {
       console.info(`## CapChange on is called for element ${i} ##`);
       console.info(`StreamId for ${i} is: ${audioCapturerChangeInfoArray[i].streamId}`);
       console.info(`Source for ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.source}`);
       console.info(`Flag  ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.capturerFlags}`);
   
       // ...
   
       let devDescriptor: audio.AudioDeviceDescriptors = audioCapturerChangeInfoArray[i].deviceDescriptors;
       for (let j = 0; j < audioCapturerChangeInfoArray[i].deviceDescriptors.length; j++) {
         console.info(`Id: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].id}`);
         console.info(`Type: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].deviceType}`);
         console.info(`Role: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].deviceRole}`);
         console.info(`Name: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].name}`);
         console.info(`Address: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].address}`);
         console.info(`SampleRates: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].sampleRates[0]}`);
         console.info(`ChannelCounts ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].channelCounts[0]}`);
         console.info(`ChannelMask: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].channelMasks}`);
       }
     }
     // ...
   });
   ```

3. （可选）使用[off('audioCapturerChange')](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#offaudiocapturerchange9)取消监听音频录制流变化。

   <!-- @[cancel_ListenAudioStreamManager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioStreamManager.ets) -->

   ``` TypeScript
   audioStreamManager.off('audioCapturerChange');
   console.info('CapturerChange Off is called');
   ```

4. （可选）使用[getCurrentAudioCapturerInfoArray](../../reference/apis-audio-kit/arkts-apis-audio-AudioStreamManager.md#getcurrentaudiocapturerinfoarray9)获取当前音频录制流的信息。该接口可获取音频录制流唯一ID、音频采集器信息以及音频录制设备信息。

   > **说明：**
   > 
   > 对所有音频流状态进行监听的应用需要[声明权限](../../security/AccessToken/declare-permissions.md)ohos.permission.USE_BLUETOOTH，否则无法获得实际的设备名称和设备地址信息，查询到的设备名称和设备地址（蓝牙设备的相关属性）将为空字符串。
   > 从API version 20开始，通常在音频录制启动前调用[isRecordingAvailable](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/arkts-apis-audio-audiostreammanager#isrecordingavailable20)，判断当前传入的音频采集器信息中音源类型的录制是否可以启动成功。

   <!-- @[get_CurrentAudioCapturerInfoArray](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/AudioCaptureSampleJS/entry/src/main/ets/pages/AudioStreamManager.ets) -->   
   
   ``` TypeScript
   async function getCurrentAudioCapturerInfoArray(updateCallback?:
     (msg: string, isError: boolean) => void): Promise<void>{
     // ...
   
     await audioStreamManager.getCurrentAudioCapturerInfoArray()
       .then((audioCapturerChangeInfoArray: audio.AudioCapturerChangeInfoArray) => {
         console.info('getCurrentAudioCapturerInfoArray Get Promise Called');
         // ...
         if (audioCapturerChangeInfoArray != null) {
           for (let i = 0; i < audioCapturerChangeInfoArray.length; i++) {
             console.info(`StreamId for ${i} is: ${audioCapturerChangeInfoArray[i].streamId}`);
             console.info(`Source for ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.source}`);
             console.info(`Flag  ${i} is: ${audioCapturerChangeInfoArray[i].capturerInfo.capturerFlags}`);
   
             // ...
   
             for (let j = 0; j < audioCapturerChangeInfoArray[i].deviceDescriptors.length; j++) {
               console.info(`Id: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].id}`);
               console.info(`Type: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].deviceType}`);
               console.info(`Role: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].deviceRole}`);
               console.info(`Name: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].name}`);
               console.info(`Address: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].address}`);
               console.info(`SampleRates: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].sampleRates[0]}`);
               console.info(`ChannelCounts ${i} : ${audioCapturerChangeInfoArray[i]
                 .deviceDescriptors[j].channelCounts[0]}`);
               console.info(`ChannelMask: ${i} : ${audioCapturerChangeInfoArray[i].deviceDescriptors[j].channelMasks}`);
             }
           }
         }
         // ...
       }).catch((err: BusinessError) => {
         console.error(`Invoke getCurrentAudioCapturerInfoArray failed, code is ${err.code}, message is ${err.message}`);
         // ...
       });
     // ...
   }
   ```
