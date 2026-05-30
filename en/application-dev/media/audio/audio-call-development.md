# Developing Audio Call
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

During an audio call, audio output (playing the peer voice) and audio input (recording the local voice) are carried out simultaneously. You can use the AudioRenderer to implement audio output and the AudioCapturer to implement audio input.

Before starting or stopping using the audio call service, the application needs to check the [audio scene](audio-call-overview.md#audio-scene) and [ringer mode](audio-call-overview.md#ringer-mode) to adopt proper audio management and prompt strategies.

The sample code below demonstrates the basic process of using the AudioRenderer and AudioCapturer to implement the audio call service, without the process of call data transmission. In actual development, the peer call data transmitted over the network needs to be decoded and played, and the sample code uses the process of reading an audio file instead; the local call data needs to be encoded and packed and then sent to the peer over the network, and the sample code uses the process of writing an audio file instead.

The examples in each of the following steps are code snippets. You can click the link at the bottom right of the sample code to obtain the [complete sample codes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/VoipCallSampleJS).

## Using AudioRenderer to Play the Peer Voice

This process is similar to the process of [using AudioRenderer to develop audio playback (ArkTs)](using-audiorenderer-for-playback.md). The key differences lie in the **audioRendererInfo** parameter and audio data source. In the **audioRendererInfo** parameter used for audio streams, **usage** must be set to **STREAM_USAGE_VOICE_COMMUNICATION**.

<!-- @[all_VoIPDemoForAudioRenderer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/VoipCallSampleJS/entry/src/main/ets/pages/VoIpDemoForAudioRenderer.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit'; // Import the audio module.
import { BusinessError } from '@kit.BasicServicesKit'; // Import BusinessError.
import { fileIo as fs } from '@kit.CoreFileKit'; // Import the file operation module.
import { common } from '@kit.AbilityKit'; // Import UIAbilityContext.

// The process is similar to the process of using AudioRenderer to develop audio playback. The key differences lie in the audioRendererInfo parameter and audio data source.
const TAG = 'VoIPDemoForAudioRenderer';

class Options {
  public offset?: number;
  public length?: number;
}

let bufferSize: number = 0;
let audioRenderer: audio.AudioRenderer | undefined = undefined;
let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // Sampling rate.
  channels: audio.AudioChannel.CHANNEL_2, // Channel.
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // Sampling format.
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // Encoding format.
};
let audioRendererInfo: audio.AudioRendererInfo = {
  // Set the parameters related to the call scenario.
  usage: audio.StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION, // Audio stream usage type: VoIP call.
  rendererFlags: 0 // AudioRenderer flag. The default value is 0.
};
let audioRendererOptions: audio.AudioRendererOptions = {
  streamInfo: audioStreamInfo,
  rendererInfo: audioRendererInfo
};
let file: fs.File;
let writeDataCallback: audio.AudioRendererWriteDataCallback;
// ...
async function initArguments(context: common.UIAbilityContext) {
  let path = context.cacheDir;
  // This is just an example. Replace the file with the PCM file to be played by the application.
  let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
  file = fs.openSync(filePath, fs.OpenMode.READ_ONLY);
  writeDataCallback = (buffer: ArrayBuffer) => {
    let options: Options = {
      offset: bufferSize,
      length: buffer.byteLength
    };

    try {
      let bufferLength = fs.readSync(file.fd, buffer, options);
      bufferSize += buffer.byteLength;
      // If the data passed in the current callback is less than one frame, the blank areas must be filled with silent data to avoid playback noise.
      if (bufferLength < buffer.byteLength) {
        let view = new DataView(buffer);
        for (let i = bufferLength; i < buffer.byteLength; i++) {
          // For blank areas, silent data should be used. When using the SAMPLE_FORMAT_U8 audio sampling format, 0x7F represents silent data. For other sampling formats, 0 is used as silent data.
          view.setUint8(i, 0);
        }
      }
      // This function does not return a callback result in API version 11, but does so in API version 12 and later versions.
      // If you do not want to play a certain buffer, return audio.AudioDataCallbackResult.INVALID.
      return audio.AudioDataCallbackResult.VALID;
    } catch (error) {
      console.error('Error reading file:', error);

      if (globalLogUpdate) {
        globalLogUpdate(`Error reading file: ${error}`, true);
      }
      // This function does not return a callback result in API version 11, but does so in API version 12 and later versions.
      return audio.AudioDataCallbackResult.INVALID;
    }
  };
}

// Create an instance and set the events to listen for.
async function init() {
  audio.createAudioRenderer(audioRendererOptions, (err, renderer) => { // Create an AudioRenderer instance.
    if (!err) {
      console.info(`${TAG}: creating AudioRenderer success`);
      // ...
      audioRenderer = renderer;
      if (audioRenderer !== undefined) {
        audioRenderer.on('writeData', writeDataCallback);
      }
    } else {
      console.info(`${TAG}: creating AudioRenderer failed, error: ${err.message}`);
      // ...
    }
  });
}

// Start audio rendering.
async function start() {
  if (audioRenderer !== undefined) {
    let stateGroup = [audio.AudioState.STATE_PREPARED, audio.AudioState.STATE_PAUSED, audio.AudioState.STATE_STOPPED];
    if (stateGroup.indexOf(audioRenderer.state.valueOf()) === -1) { // Rendering can be started only when the AudioRenderer is in the prepared, paused, or stopped state.
      console.error(TAG + 'start failed');
      // ...
      return;
    }
    // Start rendering.
    audioRenderer.start((err: BusinessError) => {
      if (err) {
        console.error('Renderer start failed.');
        // ...
      } else {
        console.info('Renderer start success.');
        // ...
      }
    });
  }
}

// Pause the rendering.
async function pause() {
  if (audioRenderer !== undefined) {
    // Rendering can be paused only when the AudioRenderer is in the running state.
    if (audioRenderer.state.valueOf() !== audio.AudioState.STATE_RUNNING) {
      console.info('Renderer is not running');
      // ...
      return;
    }
    // Pause the rendering.
    audioRenderer.pause((err: BusinessError) => {
      if (err) {
        console.error('Renderer pause failed.');
        // ...
      } else {
        console.info('Renderer pause success.');
        // ...
      }
    });
  }
}

// Stop rendering.
async function stop() {
  if (audioRenderer !== undefined) {
    // Rendering can be stopped only when the AudioRenderer is in the running or paused state.
    if (audioRenderer.state.valueOf() !== audio.AudioState.STATE_RUNNING &&
      audioRenderer.state.valueOf() !== audio.AudioState.STATE_PAUSED) {
      console.info('Renderer is not running or paused.');
      // ...
      return;
    }
    // Stop rendering.
    audioRenderer.stop((err: BusinessError) => {
      if (err) {
        console.error('Renderer stop failed.');
        // ...
      } else {
        fs.close(file);
        console.info('Renderer stop success.');
        // ...
      }
    });
  }
}

// Release the instance.
async function release() {
  if (audioRenderer !== undefined) {
    // The AudioRenderer can be released only when it is not in the released state.
    if (audioRenderer.state.valueOf() === audio.AudioState.STATE_RELEASED) {
      console.info('Renderer already released');
      // ...
      return;
    }
    // Release the resources.
    audioRenderer.release((err: BusinessError) => {
      if (err) {
        console.error('Renderer release failed.');
        // ...
      } else {
        console.info('Renderer release success.');
        // ...
      }
    });
  }
}
```

## Using AudioCapturer to Record the Local Voice

This process is similar to the process of [using AudioCapturer to develop audio recording (ArkTs)](using-audiocapturer-for-recording.md). The key differences lie in the **audioCapturerInfo** parameter and audio data stream direction. In the **audioCapturerInfo** parameter used for audio streams, **source** must be set to **SOURCE_TYPE_VOICE_COMMUNICATION**.

You must request the ohos.permission.MICROPHONE permission for all recording tasks. For details, see [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).

<!-- @[all_VoIPDemoForAudioCapturer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Audio/VoipCallSampleJS/entry/src/main/ets/pages/VoIpDemoForAudioCapturer.ets) -->

``` TypeScript
import { audio } from '@kit.AudioKit'; // Import the audio module.
import { BusinessError } from '@kit.BasicServicesKit'; // Import BusinessError.
import { fileIo as fs } from '@kit.CoreFileKit'; // Import the file operation module.
import { common, abilityAccessCtrl, PermissionRequestResult } from '@kit.AbilityKit'; // Import UIAbilityContext.
// The process is similar to the process of using AudioCapturer to develop audio recording. The key differences lie in the audioCapturerInfo parameter and audio data stream direction.
const TAG = 'VoIPDemoForAudioCapturer';

class Options {
  public offset?: number;
  public length?: number;
}

let bufferSize: number = 0;
let audioCapturer: audio.AudioCapturer | undefined = undefined;
let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // Sampling rate.
  channels: audio.AudioChannel.CHANNEL_2, // Channel.
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // Sampling format.
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // Encoding format.
};
let audioCapturerInfo: audio.AudioCapturerInfo = {
  // Set the parameters related to the call scenario.
  source: audio.SourceType.SOURCE_TYPE_VOICE_COMMUNICATION, // Audio source type: voice communication.
  capturerFlags: 0 // AudioCapturer flag. The default value is 0.
};
let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};
let file: fs.File;
let readDataCallback: Callback<ArrayBuffer>;

// ...

async function initArguments(context: common.UIAbilityContext) {
  let path = context.cacheDir;
  let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
  file = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
  console.info(`File opened: ${filePath}`);

  readDataCallback = (buffer: ArrayBuffer) => {
    let options: Options = {
      offset: bufferSize,
      length: buffer.byteLength
    }
    fs.writeSync(file.fd, buffer, options);
    bufferSize += buffer.byteLength;
  }
}

// Create an instance and set the events to listen for.
async function init() {
  audio.createAudioCapturer(audioCapturerOptions, (err, capturer) => { // Create an AudioCapturer instance.
    if (err) {
      console.error(`Invoke createAudioCapturer failed, code is ${err.code}, message is ${err.message}`);
      // ...
      return;
    }
    console.info(`${TAG}: create AudioCapturer success`);
    // ...
    audioCapturer = capturer;
    if (audioCapturer !== undefined) {
      audioCapturer.on('readData', readDataCallback);
    }
  });
}

// Start audio recording.
async function start() {
  if (audioCapturer !== undefined) {
    let stateGroup = [audio.AudioState.STATE_PREPARED, audio.AudioState.STATE_PAUSED, audio.AudioState.STATE_STOPPED];
    if (stateGroup.indexOf(audioCapturer.state.valueOf()) === -1) {
      // Recording can be started only when the AudioCapturer is in the STATE_PREPARED, STATE_PAUSED, or STATE_STOPPED state.
      console.error(`${TAG}: start failed`);
      // ...
      return;
    }

    // Start recording.
    audioCapturer.start((err: BusinessError) => {
      if (err) {
        console.error('Capturer start failed.');
        // ...
      } else {
        console.info('Capturer start success.');
        // ...
      }
    });
  }
}

// Stop recording.
async function stop() {
  if (audioCapturer !== undefined) {
    // The AudioCapturer can be stopped only when it is in the STATE_RUNNING or STATE_PAUSED state.
    if (audioCapturer.state.valueOf() !== audio.AudioState.STATE_RUNNING &&
      audioCapturer.state.valueOf() !== audio.AudioState.STATE_PAUSED) {
      console.info('Capturer is not running or paused');
      // ...
      return;
    }

    // Stop recording.
    audioCapturer.stop((err: BusinessError) => {
      if (err) {
        console.error('Capturer stop failed.');
        // ...
      } else {
        fs.close(file);
        console.info('Capturer stop success.');
        // ...
      }
    });
  }
}

// Release the instance.
async function release() {
  if (audioCapturer !== undefined) {
    // The AudioCapturer can be released only when it is not in the STATE_RELEASED or STATE_NEW state.
    if (audioCapturer.state.valueOf() === audio.AudioState.STATE_RELEASED ||
      audioCapturer.state.valueOf() === audio.AudioState.STATE_NEW) {
      console.info('Capturer already released');
      // ...
      return;
    }

    // Release the resources.
    audioCapturer.release((err: BusinessError) => {
      if (err) {
        console.error('Capturer release failed.');
        // ...
      } else {
        console.info('Capturer release success.');
        // ...
      }
    });
  }
}
```
