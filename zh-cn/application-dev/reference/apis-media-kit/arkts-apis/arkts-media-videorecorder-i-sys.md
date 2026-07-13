# VideoRecorder（系统接口）

The maintenance of this interface has been stopped since version api 9. Please use AVRecorder.
Manages and record video. Before calling an VideoRecorder method, you must use createVideoRecorder()
to create an VideoRecorder instance.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

## getInputSurface

```TypeScript
getInputSurface(callback: AsyncCallback<string>): void
```

get input surface.it must be called between prepare completed and start.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;string&gt; | 是 | Callback used to return the input surface id in string. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
let surfaceID: string; // 传递给外界的surfaceID。
videoRecorder.getInputSurface((err: BusinessError, surfaceId: string) => {
  if (err == null) {
    console.info('getInputSurface success');
    surfaceID = surfaceId;
  } else {
    console.error('getInputSurface failed and error is ' + err.message);
  }
});

```

## getInputSurface

```TypeScript
getInputSurface(): Promise<string>
```

get input surface. it must be called between prepare completed and start.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | A Promise instance used to return the input surface id in string. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
let surfaceID: string; // 传递给外界的surfaceID。
videoRecorder.getInputSurface().then((surfaceId: string) => {
  console.info('getInputSurface success');
  surfaceID = surfaceId;
}).catch((err: BusinessError) => {
  console.error('getInputSurface failed and catch error is ' + err.message);
});

```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Listens for video recording error events.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | Type of the video recording error event to listen for. |
| callback | ErrorCallback | 是 | Callback used to listen for the video recording error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied.<br>**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 当获取videoRecordState接口出错时通过此订阅事件上报。
videoRecorder.on('error', (error: BusinessError) => { // 设置'error'事件回调。
  console.error(`audio error called, error: ${error}`);
})

```

## pause

```TypeScript
pause(callback: AsyncCallback<void>): void
```

Pauses video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | A callback instance used to return when pause completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.pause((err: BusinessError) => {
  if (err == null) {
    console.info('pause videorecorder success');
  } else {
    console.error('pause videorecorder failed and error is ' + err.message);
  }
});

```

## pause

```TypeScript
pause(): Promise<void>
```

Pauses video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when pause completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.pause().then(() => {
  console.info('pause videorecorder success');
}).catch((err: BusinessError) => {
  console.error('pause videorecorder failed and catch error is ' + err.message);
});

```

## prepare

```TypeScript
prepare(config: VideoRecorderConfig, callback: AsyncCallback<void>): void
```

Prepares for recording.

**起始版本：** 9

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | VideoRecorderConfig | 是 | Recording parameters. |
| callback | AsyncCallback&lt;void&gt; | 是 | A callback instance used to return when prepare completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by callback. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 配置参数以实际硬件设备支持的范围为准。
let videoProfile: media.VideoRecorderProfile = {
  audioBitrate : 48000,
  audioChannels : 2,
  audioCodec : media.CodecMimeType.AUDIO_AAC,
  audioSampleRate : 48000,
  fileFormat : media.ContainerFormatType.CFT_MPEG_4,
  videoBitrate : 2000000,
  videoCodec : media.CodecMimeType.VIDEO_AVC,
  videoFrameWidth : 640,
  videoFrameHeight : 480,
  videoFrameRate : 30
}

let videoConfig: media.VideoRecorderConfig = {
  audioSourceType : media.AudioSourceType.AUDIO_SOURCE_TYPE_MIC,
  videoSourceType : media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
  profile : videoProfile,
  url : 'fd://xx', // 文件需先由调用者创建，并给予适当的权限。
  rotation : 0,
  location : { latitude : 30, longitude : 130 }
}

// asyncallback.
videoRecorder.prepare(videoConfig, (err: BusinessError) => {
  if (err == null) {
    console.info('prepare success');
  } else {
    console.error('prepare failed and error is ' + err.message);
  }
})

```

## prepare

```TypeScript
prepare(config: VideoRecorderConfig): Promise<void>
```

Prepares for recording.

**起始版本：** 9

**需要权限：** ohos.permission.MICROPHONE

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | VideoRecorderConfig | 是 | Recording parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when prepare completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Return by promise. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3.Parameter verification failed. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 配置参数以实际硬件设备支持的范围为准。
let videoProfile: media.VideoRecorderProfile = {
  audioBitrate : 48000,
  audioChannels : 2,
  audioCodec : media.CodecMimeType.AUDIO_AAC,
  audioSampleRate : 48000,
  fileFormat : media.ContainerFormatType.CFT_MPEG_4,
  videoBitrate : 2000000,
  videoCodec : media.CodecMimeType.VIDEO_AVC,
  videoFrameWidth : 640,
  videoFrameHeight : 480,
  videoFrameRate : 30
}

let videoConfig: media.VideoRecorderConfig = {
  audioSourceType : media.AudioSourceType.AUDIO_SOURCE_TYPE_MIC,
  videoSourceType : media.VideoSourceType.VIDEO_SOURCE_TYPE_SURFACE_YUV,
  profile : videoProfile,
  url : 'fd://xx', // 文件需先由调用者创建，并给予适当的权限。
  rotation : 0,
  location : { latitude : 30, longitude : 130 }
}

// promise.
videoRecorder.prepare(videoConfig).then(() => {
  console.info('prepare success');
}).catch((err: BusinessError) => {
  console.error('prepare failed and catch error is ' + err.message);
});

```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases resources used for video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | A callback instance used to return when release completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.release((err: BusinessError) => {
  if (err == null) {
    console.info('release videorecorder success');
  } else {
    console.error('release videorecorder failed and error is ' + err.message);
  }
});

```

## release

```TypeScript
release(): Promise<void>
```

Releases resources used for video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when release completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.release().then(() => {
  console.info('release videorecorder success');
}).catch((err: BusinessError) => {
  console.error('release videorecorder failed and catch error is ' + err.message);
});

```

## reset

```TypeScript
reset(callback: AsyncCallback<void>): void
```

Resets video recording.
Before resetting video recording, you must call stop() to stop recording. After video recording is reset,
you must call prepare() to set the recording configurations for another recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | A callback instance used to return when reset completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.reset((err: BusinessError) => {
  if (err == null) {
    console.info('reset videorecorder success');
  } else {
    console.error('reset videorecorder failed and error is ' + err.message);
  }
});

```

## reset

```TypeScript
reset(): Promise<void>
```

Resets video recording.
Before resetting video recording, you must call stop() to stop recording. After video recording is reset,
you must call prepare() to set the recording configurations for another recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when reset completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.reset().then(() => {
  console.info('reset videorecorder success');
}).catch((err: BusinessError) => {
  console.error('reset videorecorder failed and catch error is ' + err.message);
});

```

## resume

```TypeScript
resume(callback: AsyncCallback<void>): void
```

Resumes video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | A callback instance used to return when resume completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.resume((err: BusinessError) => {
  if (err == null) {
    console.info('resume videorecorder success');
  } else {
    console.error('resume videorecorder failed and error is ' + err.message);
  }
});

```

## resume

```TypeScript
resume(): Promise<void>
```

Resumes video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when resume completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.resume().then(() => {
  console.info('resume videorecorder success');
}).catch((err: BusinessError) => {
  console.error('resume videorecorder failed and catch error is ' + err.message);
});

```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | A callback instance used to return when start completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.start((err: BusinessError) => {
  if (err == null) {
    console.info('start videorecorder success');
  } else {
    console.error('start videorecorder failed and error is ' + err.message);
  }
});

```

## start

```TypeScript
start(): Promise<void>
```

Starts video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when start completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.start().then(() => {
  console.info('start videorecorder success');
}).catch((err: BusinessError) => {
  console.error('start videorecorder failed and catch error is ' + err.message);
});

```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | A callback instance used to return when stop completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by callback. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by callback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by callback. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// asyncallback.
videoRecorder.stop((err: BusinessError) => {
  if (err == null) {
    console.info('stop videorecorder success');
  } else {
    console.error('stop videorecorder failed and error is ' + err.message);
  }
});

```

## stop

```TypeScript
stop(): Promise<void>
```

Stops video recording.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return when stop completed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// promise.
videoRecorder.stop().then(() => {
  console.info('stop videorecorder success');
}).catch((err: BusinessError) => {
  console.error('stop videorecorder failed and catch error is ' + err.message);
});

```

## state

```TypeScript
readonly state: VideoRecordState
```

video recorder state.

**类型：** VideoRecordState

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.VideoRecorder

**系统接口：** 此接口为系统接口。

