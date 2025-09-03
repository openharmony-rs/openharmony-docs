# @ohos.multimedia.avsession (AVSession Management)

The AVSession module provides APIs for media playback control so that applications can access the system's Media Controller.

This module provides the following typical features related to media sessions:

- [AVSession](#avsession10): used to set session metadata, playback state information, and more.
- [AVSessionController](#avsessioncontroller10): used to obtain session IDs, send commands and events to sessions, and obtain the session metadata and playback state information.
- [AVCastController](#avcastcontroller10): used to control playback, listen for remote playback state changes, and obtain the remote playback state in casting scenarios.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { avSession } from '@kit.AVSessionKit';
```

## avSession.createAVSession<sup>10+</sup>

createAVSession(context: Context, tag: string, type: AVSessionType): Promise\<AVSession>

Creates a media session. This API uses a promise to return the result. An ability can have only one session, and repeated calling of this API fails.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name| Type                           | Mandatory| Description                          |
| ------ | ------------------------------- | ---- | ------------------------------ |
| context| [Context](../apis-ability-kit/js-apis-inner-app-context.md) | Yes| Context of the UIAbility, which is used to obtain information about the application component.|
| tag    | string                          | Yes  | Custom session name.            |
| type   | [AVSessionType](#avsessiontype10) | Yes  | Session type.|

**Return value**

| Type                             | Description                                                        |
| --------------------------------- | ------------------------------------------------------------ |
| Promise<[AVSession](#avsession10)\> | Promise used to return the media session obtained, which can be used to obtain the session ID, set the metadata and playback state information, and send key events.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() { 
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;
            let sessionId: string;  // Used as an input parameter of subsequent functions.

            avSession.createAVSession(context, tag, "audio").then(async (data: avSession.AVSession) => {
            currentAVSession = data;
            sessionId = currentAVSession.sessionId;
            console.info(`CreateAVSession : SUCCESS : sessionId = ${sessionId}`);
            }).catch((err: BusinessError) => {
            console.error(`CreateAVSession BusinessError: code: ${err.code}, message: ${err.message}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.createAVSession<sup>10+</sup>

createAVSession(context: Context, tag: string, type: AVSessionType, callback: AsyncCallback\<AVSession>): void

Creates a media session. This API uses an asynchronous callback to return the result. An ability can have only one session, and repeated calling of this API fails.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context| [Context](../apis-ability-kit/js-apis-inner-app-context.md) | Yes| Context of the UIAbility, which is used to obtain information about the application component.    |
| tag      | string                                  | Yes  | Custom session name.                                          |
| type     | [AVSessionType](#avsessiontype10)         | Yes  | Session type.                              |
| callback | AsyncCallback<[AVSession](#avsession10)\> | Yes  | Callback used to return the media session obtained, which can be used to obtain the session ID, set the metadata and playback state information, and send key events.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(()=>{
          let currentAVSession: avSession.AVSession;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let sessionId: string;  // Used as an input parameter of subsequent functions.

          avSession.createAVSession(context, tag, "audio", async (err: BusinessError, data: avSession.AVSession) => {
            if (err) {
              console.error(`CreateAVSession BusinessError: code: ${err.code}, message: ${err.message}`);
            } else {
              currentAVSession = data;
              sessionId = currentAVSession.sessionId;
              console.info(`CreateAVSession : SUCCESS : sessionId = ${sessionId}`);
            }
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## ProtocolType<sup>11+</sup>

Enumerates the protocol types supported by the remote device.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| TYPE_LOCAL<sup>11+</sup>      | 0    | Local device, which can be the built-in speaker or audio jack of the device, or an A2DP device.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| TYPE_CAST_PLUS_STREAM<sup>11+</sup>      | 2    | Cast+ stream mode, indicating that the media asset is being displayed on another device.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| TYPE_DLNA<sup>12+</sup>      | 4    | DLNA protocol, indicating that the media asset is being displayed on another device.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| TYPE_CAST_PLUS_AUDIO<sup>20+</sup>      | 8    | PCM mode, indicating that the media asset is being displayed on another device.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## AVSessionType<sup>10+<sup>

type AVSessionType = 'audio' | 'video' | 'voice_call' | 'video_call'

Defines the session type supported by the session.

You can use the strings listed in the following table.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Type | Description|
| -----  | ---- |
| 'audio' | Audio session.|
| 'video' | Video session.|
| 'voice_call'<sup>11+<sup> | Voice call.|
| 'video_call'<sup>12+<sup> | Video call.|

## AVSession<sup>10+</sup>

An AVSession object is created by calling [avSession.createAVSession](#avsessioncreateavsession10). The object enables you to obtain the session ID and set the metadata and playback state. 

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name     | Type  | Read-Only| Optional| Description                         |
| :-------- | :----- | :--- | :--- | :---------------------------- |
| sessionId | string | Yes  | No  | Unique session ID of the AVSession object.|
| sessionType| [AVSessionType](#avsessiontype10) | Yes  | No  | AVSession type.|

**Example**

```ts
let sessionId: string = currentAVSession.sessionId;
let sessionType: avSession.AVSessionType = currentAVSession.sessionType;
```

### setAVMetadata<sup>10+</sup>

setAVMetadata(data: AVMetadata): Promise\<void>

Sets session metadata. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name| Type                     | Mandatory| Description        |
| ------ | ------------------------- | ---- | ------------ |
| data   | [AVMetadata](#avmetadata10) | Yes  | Session metadata.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let metadata: avSession.AVMetadata = {
  assetId: "121278",
  title: "lose yourself",
  artist: "Eminem",
  author: "ST",
  album: "Slim shady",
  writer: "ST",
  composer: "ST",
  duration: 2222,
  mediaImage: "https://www.example.com/example.jpg",
  subtitle: "8 Mile",
  description: "Rap",
  // The LRC contains two types of elements: time tag + lyrics, and ID tag.
  // Example: [00:25.44]xxx\r\n[00:26.44]xxx\r\n
  lyric: "Lyrics in LRC format",
  // The singleLyricText field stores a single line of lyric text without timestamps.
  // Example: "Content of a single lyric line"
  singleLyricText: "Content of a single lyric line",
  previousAssetId: "121277",
  nextAssetId: "121279"
};
currentAVSession.setAVMetadata(metadata).then(() => {
  console.info('SetAVMetadata successfully');
}).catch((err: BusinessError) => {
  console.error(`SetAVMetadata BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### setAVMetadata<sup>10+</sup>

setAVMetadata(data: AVMetadata, callback: AsyncCallback\<void>): void

Sets session metadata. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                 |
| -------- | ------------------------- | ---- | ------------------------------------- |
| data     | [AVMetadata](#avmetadata10) | Yes  | Session metadata.                         |
| callback | AsyncCallback\<void>      | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let metadata: avSession.AVMetadata = {
  assetId: "121278",
  title: "lose yourself",
  artist: "Eminem",
  author: "ST",
  album: "Slim shady",
  writer: "ST",
  composer: "ST",
  duration: 2222,
  mediaImage: "https://www.example.com/example.jpg",
  subtitle: "8 Mile",
  description: "Rap",
  // The LRC contains two types of elements: time tag + lyrics, and ID tag.
  // Example: [00:25.44]xxx\r\n[00:26.44]xxx\r\n
  lyric: "Lyrics in LRC format",
  // The singleLyricText field stores a single line of lyric text without timestamps.
  // Example: "Content of a single lyric line"
  singleLyricText: "Content of a single lyric line",
  previousAssetId: "121277",
  nextAssetId: "121279"
};
currentAVSession.setAVMetadata(metadata, (err: BusinessError) => {
  if (err) {
    console.error(`SetAVMetadata BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('SetAVMetadata successfully');
  }
});
```

### setCallMetadata<sup>11+</sup>

setCallMetadata(data: CallMetadata): Promise\<void>

Sets call metadata. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name| Type                     | Mandatory| Description        |
| ------ | ------------------------- | ---- | ------------ |
| data   | [CallMetadata](#callmetadata11) | Yes  | Call metadata.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let value = await resourceManager.getSystemResourceManager().getRawFileContent('IMAGE_URI');
    let imageSource = await image.createImageSource(value.buffer);
    let imagePixel = await imageSource.createPixelMap({desiredSize:{width: 150, height: 150}});
    let calldata: avSession.CallMetadata = {
      name: "xiaoming",
      phoneNumber: "111xxxxxxxx",
      avatar: imagePixel
    };
currentAVSession.setCallMetadata(calldata).then(() => {
  console.info('setCallMetadata successfully');
}).catch((err: BusinessError) => {
  console.error(`setCallMetadata BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### setCallMetadata<sup>11+</sup>

setCallMetadata(data: CallMetadata, callback: AsyncCallback\<void>): void

Sets call metadata. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                 |
| -------- | ------------------------- | ---- | ------------------------------------- |
| data     | [CallMetadata](#callmetadata11) | Yes  | Call metadata.                         |
| callback | AsyncCallback\<void>      | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function setCallMetadata() {
  let value = await resourceManager.getSystemResourceManager().getRawFileContent('IMAGE_URI');
  let imageSource = await image.createImageSource(value.buffer);
  let imagePixel = await imageSource.createPixelMap({desiredSize:{width: 150, height: 150}});
  let calldata: avSession.CallMetadata = {
    name: "xiaoming",
    phoneNumber: "111xxxxxxxx",
    avatar: imagePixel
  };
  currentAVSession.setCallMetadata(calldata, (err: BusinessError) => {
    if (err) {
      console.error(`setCallMetadata BusinessError: code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('setCallMetadata successfully');
    }
  });
}
```

### setAVCallState<sup>11+</sup>

setAVCallState(state: AVCallState): Promise\<void>

Sets the call state. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name| Type                     | Mandatory| Description        |
| ------ | ------------------------- | ---- | ------------ |
| state   | [AVCallState](#avcallstate11) | Yes  | Call state.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let calldata: avSession.AVCallState = {
  state: avSession.CallState.CALL_STATE_ACTIVE,
  muted: false
};
currentAVSession.setAVCallState(calldata).then(() => {
  console.info('setAVCallState successfully');
}).catch((err: BusinessError) => {
  console.error(`setAVCallState BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### setAVCallState<sup>11+</sup>

setAVCallState(state: AVCallState, callback: AsyncCallback\<void>): void

Sets the call state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                 |
| -------- | ------------------------- | ---- | ------------------------------------- |
| state     | [AVCallState](#avcallstate11) | Yes  | Call state.                         |
| callback | AsyncCallback\<void>      | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avcalldata: avSession.AVCallState = {
  state: avSession.CallState.CALL_STATE_ACTIVE,
  muted: false
};
currentAVSession.setAVCallState(avcalldata, (err: BusinessError) => {
  if (err) {
    console.error(`setAVCallState BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('setAVCallState successfully');
  }
});
```

### setAVPlaybackState<sup>10+</sup>

setAVPlaybackState(state: AVPlaybackState): Promise\<void>

Sets information related to the session playback state. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name| Type                               | Mandatory| Description                                          |
| ------ | ----------------------------------- | ---- | ---------------------------------------------- |
| state   | [AVPlaybackState](#avplaybackstate10) | Yes  | Information related to the session playback state.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let playbackState: avSession.AVPlaybackState = {
  state:avSession.PlaybackState.PLAYBACK_STATE_PLAY,
  speed: 1.0,
  position:{elapsedTime:10, updateTime:(new Date()).getTime()},
  bufferedTime:1000,
  loopMode:avSession.LoopMode.LOOP_MODE_SINGLE,
  isFavorite:true
};
currentAVSession.setAVPlaybackState(playbackState).then(() => {
  console.info('SetAVPlaybackState successfully');
}).catch((err: BusinessError) => {
  console.error(`SetAVPlaybackState BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### setAVPlaybackState<sup>10+</sup>

setAVPlaybackState(state: AVPlaybackState, callback: AsyncCallback\<void>): void

Sets information related to the session playback state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                               | Mandatory| Description                                          |
| -------- | ----------------------------------- | ---- | ---------------------------------------------- |
| state     | [AVPlaybackState](#avplaybackstate10) | Yes  | Information related to the session playback state.|
| callback | AsyncCallback\<void>                | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.         |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let PlaybackState: avSession.AVPlaybackState = {
  state:avSession.PlaybackState.PLAYBACK_STATE_PLAY,
  speed: 1.0,
  position:{elapsedTime:10, updateTime:(new Date()).getTime()},
  bufferedTime:1000,
  loopMode:avSession.LoopMode.LOOP_MODE_SINGLE,
  isFavorite:true
};
currentAVSession.setAVPlaybackState(PlaybackState, (err: BusinessError) => {
  if (err) {
    console.error(`SetAVPlaybackState BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('SetAVPlaybackState successfully');
  }
});
```

### setLaunchAbility<sup>10+</sup>

setLaunchAbility(ability: WantAgent): Promise\<void>

Sets a launcher ability. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name | Type                                         | Mandatory| Description                                                       |
| ------- | --------------------------------------------- | ---- | ----------------------------------------------------------- |
| ability | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md) | Yes  | Application properties, such as the bundle name, ability name, and deviceID.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { wantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// WantAgentInfo object.
let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      deviceId: "deviceId",
      bundleName: "com.example.myapplication",
      abilityName: "EntryAbility",
      action: "action1",
      entities: ["entity1"],
      type: "MIMETYPE",
      uri: "key = {true,true,false}",
      parameters:
        {
          mykey0: 2222,
          mykey1: [1, 2, 3],
          mykey2: "[1, 2, 3]",
          mykey3: "ssssssssssssssssssssssssss",
          mykey4: [false, true, false],
          mykey5: ["qqqqq", "wwwwww", "aaaaaaaaaaaaaaaaa"],
          mykey6: true
        }
    }
  ],
  operationType: wantAgent.OperationType.START_ABILITIES,
  requestCode: 0,
  wantAgentFlags:[wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
}

wantAgent.getWantAgent(wantAgentInfo).then((agent) => {
  currentAVSession.setLaunchAbility(agent).then(() => {
    console.info('SetLaunchAbility successfully');
  }).catch((err: BusinessError) => {
    console.error(`SetLaunchAbility BusinessError: code: ${err.code}, message: ${err.message}`);
  });
});
```

### setLaunchAbility<sup>10+</sup>

setLaunchAbility(ability: WantAgent, callback: AsyncCallback\<void>): void

Sets a launcher ability. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                         | Mandatory| Description                                                        |
| -------- | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| ability  | [WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md) | Yes  | Application properties, such as the bundle name, ability name, and deviceID. |
| callback | AsyncCallback\<void>                          | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { wantAgent } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// WantAgentInfo object.
let wantAgentInfo: wantAgent.WantAgentInfo = {
  wants: [
    {
      deviceId: "deviceId",
      bundleName: "com.example.myapplication",
      abilityName: "EntryAbility",
      action: "action1",
      entities: ["entity1"],
      type: "MIMETYPE",
      uri: "key = {true,true,false}",
      parameters:
        {
          mykey0: 2222,
          mykey1: [1, 2, 3],
          mykey2: "[1, 2, 3]",
          mykey3: "ssssssssssssssssssssssssss",
          mykey4: [false, true, false],
          mykey5: ["qqqqq", "wwwwww", "aaaaaaaaaaaaaaaaa"],
          mykey6: true
        }
    }
  ],
  operationType: wantAgent.OperationType.START_ABILITIES,
  requestCode: 0,
  wantAgentFlags:[wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
}

wantAgent.getWantAgent(wantAgentInfo).then((agent) => {
  currentAVSession.setLaunchAbility(agent, (err: BusinessError) => {
    if (err) {
      console.error(`SetLaunchAbility BusinessError: code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('SetLaunchAbility successfully');
    }
  });
});
```

### dispatchSessionEvent<sup>10+</sup>

dispatchSessionEvent(event: string, args: {[key: string]: Object}): Promise\<void>

Dispatches a custom event in the session, including the event name and event content in key-value pair format. This API uses a promise to return the result. It is called by the provider.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name | Type                                         | Mandatory| Description                                                       |
| ------- | --------------------------------------------- | ---- | ----------------------------------------------------------- |
| event | string | Yes  | Name of the session event.|
| args | {[key: string]: Object} | Yes  | Content of the session event.|

> **NOTE**
> The **args** parameter supports the following data types: string, number, Boolean, object, array, and file descriptor. For details, see [@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md).

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() { 
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (err: BusinessError, data: avSession.AVSession) => {
            if (err) {
                console.error(`CreateAVSession BusinessError: code: ${err.code}, message: ${err.message}`);
            } else {
                currentAVSession = data;
            }
            });
            let eventName = "dynamic_lyric";
            if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).dispatchSessionEvent(eventName, {lyric : "This is lyric"}).then(() => {
                console.info('dispatchSessionEvent successfully');
            }).catch((err: BusinessError) => {
                console.error(`dispatchSessionEvent BusinessError: code: ${err.code}, message: ${err.message}`);
            })
            }
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

### dispatchSessionEvent<sup>10+</sup>

dispatchSessionEvent(event: string, args: {[key: string]: Object}, callback: AsyncCallback\<void>): void

Dispatches a custom event in the session, including the event name and event content in key-value pair format. This API uses an asynchronous callback to return the result. It is called by the provider.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name | Type                                         | Mandatory| Description                                                       |
| ------- | --------------------------------------------- | ---- | ----------------------------------------------------------- |
| event | string | Yes  | Name of the session event.|
| args | {[key: string]: Object} | Yes  | Content of the session event.|
| callback | AsyncCallback\<void>                          | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

> **NOTE**

> The **args** parameter supports the following data types: string, number, Boolean, object, array, and file descriptor. For details, see [@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md).

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() { 
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (err: BusinessError, data: avSession.AVSession) => {
            if (err) {
                console.error(`CreateAVSession BusinessError: code: ${err.code}, message: ${err.message}`);
            } else {
                currentAVSession = data;
            }
            });
            let eventName: string = "dynamic_lyric";
            if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).dispatchSessionEvent(eventName, {lyric : "This is lyric"}, (err: BusinessError) => {
                if (err) {
                console.error(`dispatchSessionEvent BusinessError: code: ${err.code}, message: ${err.message}`);
                }
            })
            }
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

### setAVQueueItems<sup>10+</sup>

setAVQueueItems(items: Array\<AVQueueItem>): Promise\<void>

Sets a playlist. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name | Type                                | Mandatory| Description                              |
| ------ | ------------------------------------ | ---- | ---------------------------------- |
| items  | Array<[AVQueueItem](#avqueueitem10)\> | Yes  | Playlist to set.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function setAVQueueItems() {
  let value = await resourceManager.getSystemResourceManager().getRawFileContent('IMAGE_URI');
  let imageSource = await image.createImageSource(value.buffer);
  let imagePixel = await imageSource.createPixelMap({desiredSize:{width: 150, height: 150}});
  let queueItemDescription_1: avSession.AVMediaDescription = {
    assetId: '001',
    title: 'music_name',
    subtitle: 'music_sub_name',
    description: 'music_description',
    mediaImage : imagePixel,
    extras: {extras:'any'}
  };
  let queueItem_1: avSession.AVQueueItem = {
    itemId: 1,
    description: queueItemDescription_1
  };
  let queueItemDescription_2: avSession.AVMediaDescription = {
    assetId: '002',
    title: 'music_name',
    subtitle: 'music_sub_name',
    description: 'music_description',
    mediaImage: imagePixel,
    extras: {extras:'any'}
  };
  let queueItem_2: avSession.AVQueueItem = {
    itemId: 2,
    description: queueItemDescription_2
  };
  let queueItemsArray: avSession.AVQueueItem[] = [queueItem_1, queueItem_2];
  currentAVSession.setAVQueueItems(queueItemsArray).then(() => {
    console.info('SetAVQueueItems successfully');
  }).catch((err: BusinessError) => {
    console.error(`SetAVQueueItems BusinessError: code: ${err.code}, message: ${err.message}`);
  });
}
```

### setAVQueueItems<sup>10+</sup>

setAVQueueItems(items: Array\<AVQueueItem>, callback: AsyncCallback\<void>): void

Sets a playlist. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                 | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ----------------------------------------------------------- |
| items    | Array<[AVQueueItem](#avqueueitem10)\> | Yes  | Playlist to set.                         |
| callback | AsyncCallback\<void>                 | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function setAVQueueItems() {
  let value = await resourceManager.getSystemResourceManager().getRawFileContent('IMAGE_URI');
  let imageSource = await image.createImageSource(value.buffer);
  let imagePixel = await imageSource.createPixelMap({desiredSize:{width: 150, height: 150}});
  let queueItemDescription_1: avSession.AVMediaDescription = {
    assetId: '001',
    title: 'music_name',
    subtitle: 'music_sub_name',
    description: 'music_description',
    mediaImage : imagePixel,
    extras: {extras:'any'}
  };
  let queueItem_1: avSession.AVQueueItem = {
    itemId: 1,
    description: queueItemDescription_1
  };
  let queueItemDescription_2: avSession.AVMediaDescription = {
    assetId: '002',
    title: 'music_name',
    subtitle: 'music_sub_name',
    description: 'music_description',
    mediaImage: imagePixel,
    extras: {extras:'any'}
  };
  let queueItem_2: avSession.AVQueueItem = {
    itemId: 2,
    description: queueItemDescription_2
  };
  let queueItemsArray: avSession.AVQueueItem[] = [queueItem_1, queueItem_2];
  currentAVSession.setAVQueueItems(queueItemsArray, (err: BusinessError) => {
    if (err) {
      console.error(`SetAVQueueItems BusinessError: code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('SetAVQueueItems successfully');
    }
  });
}
```

### setAVQueueTitle<sup>10+</sup>

setAVQueueTitle(title: string): Promise\<void>

Sets a name for the playlist. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name | Type  | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| title  | string | Yes  | Name of the playlist.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let queueTitle = 'QUEUE_TITLE';
currentAVSession.setAVQueueTitle(queueTitle).then(() => {
  console.info('SetAVQueueTitle successfully');
}).catch((err: BusinessError) => {
  console.error(`SetAVQueueTitle BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### setAVQueueTitle<sup>10+</sup>

setAVQueueTitle(title: string, callback: AsyncCallback\<void>): void

Sets a name for the playlist. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                 | Mandatory| Description                                                        |
| -------- | --------------------- | ---- | ----------------------------------------------------------- |
| title    | string                | Yes  | Name of the playlist.                         |
| callback | AsyncCallback\<void>  | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let queueTitle = 'QUEUE_TITLE';
currentAVSession.setAVQueueTitle(queueTitle, (err: BusinessError) => {
  if (err) {
    console.error(`SetAVQueueTitle BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('SetAVQueueTitle successfully');
  }
});
```

### setExtras<sup>10+</sup>

setExtras(extras: {[key: string]: Object}): Promise\<void>

Sets a custom media packet in the form of key-value pairs. This API uses a promise to return the result. It is called by the provider.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name | Type                                         | Mandatory| Description                                                       |
| ------- | --------------------------------------------- | ---- | ----------------------------------------------------------- |
| extras | {[key: string]: Object} | Yes  | Key-value pairs of the custom media packet.|

> **NOTE**

> The **extras** parameter supports the following data types: string, number, Boolean, object, array, and file descriptor. For details, see [@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md).

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the setting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() { 
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (err: BusinessError, data: avSession.AVSession) => {
            if (err) {
                console.error(`CreateAVSession BusinessError: code: ${err.code}, message: ${err.message}`);
            } else {
                currentAVSession = data;
            }
            });
            if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).setExtras({extras : "This is custom media packet"}).then(() => {
                console.info('setExtras successfully');
            }).catch((err: BusinessError) => {
                console.error(`setExtras BusinessError: code: ${err.code}, message: ${err.message}`);
            })
            }
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

### setExtras<sup>10+</sup>

setExtras(extras: {[key: string]: Object}, callback: AsyncCallback\<void>): void

Sets a custom media packet in the form of key-value pairs. This API uses an asynchronous callback to return the result. It is called by the provider.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name | Type                                         | Mandatory| Description                                                       |
| ------- | --------------------------------------------- | ---- | ----------------------------------------------------------- |
| extras | {[key: string]: Object} | Yes  | Key-value pairs of the custom media packet.|
| callback | AsyncCallback\<void>                          | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

> **NOTE**

> The **extras** parameter supports the following data types: string, number, Boolean, object, array, and file descriptor. For details, see [@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md).

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() { 
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (err: BusinessError, data: avSession.AVSession) => {
            if (err) {
                console.error(`CreateAVSession BusinessError: code: ${err.code}, message: ${err.message}`);
            } else {
                currentAVSession = data;
            }
            });
            if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).setExtras({extras : "This is custom media packet"}, (err: BusinessError) => {
                if (err) {
                console.error(`setExtras BusinessError: code: ${err.code}, message: ${err.message}`);
                }
            })
            }
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

### getController<sup>10+</sup>

getController(): Promise\<AVSessionController>

Obtains the controller corresponding to this session. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                                | Description                         |
| ---------------------------------------------------- | ----------------------------- |
| Promise<[AVSessionController](#avsessioncontroller10)> | Promise used to return the session controller.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';
  build() {
    Column() {
      Text(this.message)
        .onClick(async ()=>{
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, 'SESSION_NAME', 'audio');
          let avsessionController: avSession.AVSessionController;
          currentAVSession.getController().then(async (avcontroller: avSession.AVSessionController) => {
            avsessionController = avcontroller;
            console.info(`GetController : SUCCESS : sessionid : ${avsessionController.sessionId}`);
          }).catch((err: BusinessError) => {
            console.error(`GetController BusinessError: code: ${err.code}, message: ${err.message}`);
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### getController<sup>10+</sup>

getController(callback: AsyncCallback\<AVSessionController>): void

Obtains the controller corresponding to this session. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                       | Mandatory| Description                      |
| -------- | ----------------------------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[AVSessionController](#avsessioncontroller10)\> | Yes  | Callback used to return the session controller.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          let context: Context = this.getUIContext().getHostContext() as Context;
          let currentAVSession: avSession.AVSession = await avSession.createAVSession(context, 'SESSION_NAME', 'audio');
          let avsessionController: avSession.AVSessionController;
          currentAVSession.getController((err: BusinessError, avcontroller: avSession.AVSessionController) => {
            if (err) {
              console.error(`GetController BusinessError: code: ${err.code}, message: ${err.message}`);
            } else {
              avsessionController = avcontroller;
              console.info(`GetController : SUCCESS : sessionid : ${avsessionController.sessionId}`);
            }
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### getAVCastController<sup>10+</sup>

getAVCastController(): Promise\<AVCastController>

Obtains the cast controller when a casting connection is set up. This API uses a promise to return the result. If the session is not in the cast state, the controller returns **null**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise<[AVCastController](#avcastcontroller10)\>  | Promise used to return the cast controller.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | --------------------------------------- |
| 6600102| The session does not exist.           |
| 6600109| The remote connection is not established. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let aVCastController: avSession.AVCastController;
currentAVSession.getAVCastController().then((avcontroller: avSession.AVCastController) => {
  aVCastController = avcontroller;
  console.info('getAVCastController : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`getAVCastController BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getAVCastController<sup>10+</sup>

getAVCastController(callback: AsyncCallback\<AVCastController>): void

Obtains the cast controller when a casting connection is set up. This API uses an asynchronous callback to return the result. If the session is not in the cast state, the controller returns **null**.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                                       | Mandatory| Description                                                        |
| --------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback  | AsyncCallback<[AVCastController](#avcastcontroller10)\> | Yes  | Callback used to return the cast controller.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message                                 |
| -------- |---------------------------------------|
| 6600102| The session does not exist.           |
| 6600109| The remote connection is not established. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let aVCastController: avSession.AVCastController;
currentAVSession.getAVCastController((err: BusinessError, avcontroller: avSession.AVCastController) => {
  if (err) {
    console.error(`getAVCastController BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    aVCastController = avcontroller;
    console.info('getAVCastController : SUCCESS');
  }
});
```

### getOutputDevice<sup>10+</sup>

getOutputDevice(): Promise\<OutputDeviceInfo>

Obtains information about the output device for this session. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                          | Description                             |
| ---------------------------------------------- | --------------------------------- |
| Promise<[OutputDeviceInfo](#outputdeviceinfo10)> | Promise used to return the output device information.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.getOutputDevice().then((outputDeviceInfo: avSession.OutputDeviceInfo) => {
  console.info(`GetOutputDevice : SUCCESS : devices length : ${outputDeviceInfo.devices.length}`);
}).catch((err: BusinessError) => {
  console.error(`GetOutputDevice BusinessError: code: ${err.code}, message: ${err.message}`);
})
```

### getOutputDevice<sup>10+</sup>

getOutputDevice(callback: AsyncCallback\<OutputDeviceInfo>): void

Obtains information about the output device for this session. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                 | Mandatory| Description                          |
| -------- | ----------------------------------------------------- | ---- | ------------------------------ |
| callback | AsyncCallback<[OutputDeviceInfo](#outputdeviceinfo10)\> | Yes  | Callback used to return the information obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.getOutputDevice((err: BusinessError, outputDeviceInfo: avSession.OutputDeviceInfo) => {
  if (err) {
    console.error(`GetOutputDevice BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`GetOutputDevice : SUCCESS : devices length : ${outputDeviceInfo.devices.length}`);
  }
});
```

### activate<sup>10+</sup>

activate(): Promise\<void>

Activates this session. A session can be used only after being activated. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the session is activated, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.activate().then(() => {
  console.info('Activate : SUCCESS ');
}).catch((err: BusinessError) => {
  console.error(`Activate BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### activate<sup>10+</sup>

activate(callback: AsyncCallback\<void>): void

Activates this session. A session can be used only after being activated. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description      |
| -------- | -------------------- | ---- | ---------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the session is activated, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.activate((err: BusinessError) => {
  if (err) {
    console.error(`Activate BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Activate : SUCCESS ');
  }
});
```

### deactivate<sup>10+</sup>

deactivate(): Promise\<void>

Deactivates this session. You can use [activate](#activate10) to activate the session again. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the session is deactivated, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.deactivate().then(() => {
  console.info('Deactivate : SUCCESS ');
}).catch((err: BusinessError) => {
  console.error(`Deactivate BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### deactivate<sup>10+</sup>

deactivate(callback: AsyncCallback\<void>): void

Deactivates this session. This API uses an asynchronous callback to return the result.

Deactivates this session. You can use [activate](#activate10) to activate the session again.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description      |
| -------- | -------------------- | ---- | ---------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the session is deactivated, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.deactivate((err: BusinessError) => {
  if (err) {
    console.error(`Deactivate BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Deactivate : SUCCESS ');
  }
});
```

### destroy<sup>10+</sup>

destroy(): Promise\<void>

Destroys this session. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the session is destroyed, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.destroy().then(() => {
  console.info('Destroy : SUCCESS ');
}).catch((err: BusinessError) => {
  console.error(`Destroy BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### destroy<sup>10+</sup>

destroy(callback: AsyncCallback\<void>): void

Destroys this session. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description      |
| -------- | -------------------- | ---- | ---------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the session is destroyed, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.destroy((err: BusinessError) => {
  if (err) {
    console.error(`Destroy BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Destroy : SUCCESS ');
  }
});
```

### on('play')<sup>10+</sup>

on(type: 'play', callback: () => void): void

Subscribes to play command events. The subscription means that the application supports the play command.

Only one callback can be registered for each playback command. If a new callback is registered, the previous callback is replaced.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'play'** is triggered when the command for starting playback is sent to the session.|
| callback | () => void | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.                                       |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('play', () => {
  console.info('on play entry');
});
```

### on('pause')<sup>10+</sup>

on(type: 'pause', callback: () => void): void

Subscribes to pause command events. The subscription means that the application supports the pause command.

Only one callback can be registered for each playback command. If a new callback is registered, the previous callback is replaced.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'pause'** is triggered when the command for pausing the playback is sent to the session.|
| callback | () => void | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('pause', () => {
  console.info('on pause entry');
});
```

### on('stop')<sup>10+</sup>

on(type:'stop', callback: () => void): void

Subscribes to stop command events. The subscription means that the application supports the stop command.

Only one callback can be registered for each playback command. If a new callback is registered, the previous callback is replaced.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'stop'** is triggered when the command for stopping the playback is sent to the session.|
| callback | () => void | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.         |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('stop', () => {
  console.info('on stop entry');
});
```

### on('playNext')<sup>10+</sup>

on(type:'playNext', callback: () => void): void

Subscribes to playNext command events. The subscription means that the application supports the playNext command.

Only one callback can be registered for each playback command. If a new callback is registered, the previous callback is replaced.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'playNext'** is triggered when the command for playing the next item is sent to the session.|
| callback | () => void | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.    |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('playNext', () => {
  console.info('on playNext entry');
});
```

### on('playPrevious')<sup>10+</sup>

on(type:'playPrevious', callback: () => void): void

Subscribes to playPrevious command events. The subscription means that the application supports the playPrevious command.

Only one callback can be registered for each playback command. If a new callback is registered, the previous callback is replaced.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'playPrevious'** is triggered when the command for playing the previous item sent to the session.|
| callback | () => void | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.      |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('playPrevious', () => {
  console.info('on playPrevious entry');
});
```

### on('fastForward')<sup>10+</sup>

on(type: 'fastForward', callback: (time?: number) => void): void

Subscribes to fastForward command events. The subscription means that the application supports the fastForward command.

Only one callback can be registered for each playback command. If a new callback is registered, the previous callback is replaced.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'fastForward'** is triggered when the command for fast forwarding is sent to the session.|
| callback | (time?: number) => void | Yes  | Callback used for subscription. The **time** parameter in the callback indicates the time to seek to, in seconds.   |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('fastForward', (time?: number) => {
  console.info('on fastForward entry');
});
```

### on('rewind')<sup>10+</sup>

on(type:'rewind', callback: (time?: number) => void): void

Subscribes to rewind command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'rewind'** is triggered when the command for rewinding is sent to the session.|
| callback | (time?: number) => void | Yes  | Callback used for subscription. The **time** parameter in the callback indicates the time to seek to, in seconds.     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('rewind', (time?: number) => {
  console.info('on rewind entry');
});
```

### on('playFromAssetId')<sup>(deprecated)</sup>

on(type:'playFromAssetId', callback: (assetId: number) => void): void

Subscribes to playback events with a given media asset ID.

> **NOTE**
>
> This API is supported since API version 11 and deprecated since API version 20. You are advised to use [on('playWithAssetId')](#onplaywithassetid20) instead.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'playFromAssetId'** is triggered when the media asset ID is played.|
| callback | (assetId: number) => void | Yes  | Callback The **assetId** parameter in the callback indicates the media asset ID.     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('playFromAssetId', (assetId: number) => {
  console.info('on playFromAssetId entry');
});
```

### off('playFromAssetId')<sup>(deprecated)</sup>

off(type: 'playFromAssetId', callback?: (assetId: number) => void): void

Unsubscribes from playback events with a given media asset ID.

> **NOTE**
>
> This API is supported since API version 11 and deprecated since API version 20. You are advised to use [off('playWithAssetId')](#offplaywithassetid20) instead.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'playFromAssetId'** in this case.|
| callback | (assetId: number) => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session. The **assetId** parameter in the callback indicates the media asset ID.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('playFromAssetId');
```

### on('playWithAssetId')<sup>20+</sup>

on(type:'playWithAssetId', callback: Callback\<string>): void

Subscribes to playback events with a given media asset ID.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'playWithAssetId'** is triggered when the media asset ID is played.|
| callback | Callback\<string> | Yes  | Callback The **assetId** parameter in the callback indicates the media asset ID.     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**Example**

```ts
let playWithAssetIdCallback = (assetId: string) => {
  console.info(`on playWithAssetId entry,  assetId = ${assetId}`);
}
currentAVSession.on('playWithAssetId', playWithAssetIdCallback);
```


### off('playWithAssetId')<sup>20+</sup>

off(type: 'playWithAssetId', callback?: Callback\<string>): void

Unsubscribes from playback events with a given media asset ID.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'playWithAssetId'** in this case.|
| callback | Callback\<string> | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session. The **assetId** parameter in the callback indicates the media asset ID.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('playWithAssetId');
```

### on('seek')<sup>10+</sup>

on(type: 'seek', callback: (time: number) => void): void

Subscribes to seek command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| type     | string                 | Yes  | Event type. The event **'seek'** is triggered when the seek command is sent to the session.|
| callback | (time: number) => void | Yes  | Callback used for subscription. The **time** parameter in the callback indicates the time to seek to, in milliseconds.                  |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('seek', (time: number) => {
  console.info(`on seek entry time : ${time}`);
});
```

### on('setSpeed')<sup>10+</sup>

on(type: 'setSpeed', callback: (speed: number) => void): void

Subscribes to setSpeed command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | Yes  | Event type. The event **'setSpeed'** is triggered when the command for setting the playback speed is sent to the session.|
| callback | (speed: number) => void | Yes  | Callback used for subscription. The **speed** parameter in the callback indicates the playback speed.                             |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('setSpeed', (speed: number) => {
  console.info(`on setSpeed speed : ${speed}`);
});
```

### on('setLoopMode')<sup>10+</sup>

on(type: 'setLoopMode', callback: (mode: LoopMode) => void): void

Subscribes to setLoopMode command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                                  | Mandatory| Description |
| -------- | ------------------------------------- | ---- | ---- |
| type     | string                                | Yes  | Event type. The event **'setLoopMode'** is triggered when the command for setting the loop mode is sent to the session.|
| callback | (mode: [LoopMode](#loopmode10)) => void | Yes  | Callback used for subscription. The **mode** parameter in the callback indicates the loop mode.                              |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('setLoopMode', (mode: avSession.LoopMode) => {
  console.info(`on setLoopMode mode : ${mode}`);
});
```

### on('setTargetLoopMode')<sup>18+</sup>

on(type: 'setTargetLoopMode', callback: Callback\<LoopMode>): void

Subscribes to setTargetLoopMode command events.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                                  | Mandatory| Description |
| -------- | ------------------------------------- | ---- | ---- |
| type     | string                                | Yes  | Event type. The event **'setTargetLoopMode'**<br>is triggered when the command for setting the target loop mode is sent to the session.|
| callback | Callback<[LoopMode](#loopmode10)> | Yes  | Callback used for subscription. The **LoopMode** parameter in the callback indicates the target loop mode.                              |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('setTargetLoopMode', (mode: avSession.LoopMode) => {
  console.info(`on setTargetLoopMode mode : ${mode}`);
});
```

### on('toggleFavorite')<sup>10+</sup>

on(type: 'toggleFavorite', callback: (assetId: string) => void): void

Subscribes to toggleFavorite command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                    | Yes  | Event type. The event **'toggleFavorite'** is triggered when the command for favoriting the media asset is sent to the session.|
| callback | (assetId: string) => void | Yes  | Callback used for subscription. The **assetId** parameter in the callback indicates the media asset ID.                             |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('toggleFavorite', (assetId: string) => {
  console.info(`on toggleFavorite mode : ${assetId}`);
});
```

### on('skipToQueueItem')<sup>10+</sup>

on(type: 'skipToQueueItem', callback: (itemId: number) => void): void

Subscribes to the event that indicates an item in the playlist is selected. The session can play the selected item.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                                                     |
| -------- | ------------------------ | ---- | ---------------------------------------------------------------------------------------- |
| type     | string                   | Yes  | Event type. The event **'skipToQueueItem'** is triggered when an item in the playlist is selected.|
| callback | (itemId: number) => void | Yes  | Callback used for subscription. The **itemId** parameter in the callback indicates the ID of the selected item.                                               |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('skipToQueueItem', (itemId: number) => {
  console.info(`on skipToQueueItem id : ${itemId}`);
});
```

### on('handleKeyEvent')<sup>10+</sup>

on(type: 'handleKeyEvent', callback: (event: KeyEvent) => void): void

Subscribes to key events of external devices such as Bluetooth and wired devices to listen for the play, pause, previous, next, fast-forward, and rewind commands in the key events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'handleKeyEvent'** is triggered when a key event is sent to the session.|
| callback | (event: [KeyEvent](../apis-input-kit/js-apis-keyevent.md)) => void | Yes  | Callback used for subscription. The **event** parameter in the callback indicates the key event.                             |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { KeyEvent } from '@kit.InputKit';

currentAVSession.on('handleKeyEvent', (event: KeyEvent) => {
  console.info(`on handleKeyEvent event : ${event}`);
});

```

### on('outputDeviceChange')<sup>10+</sup>

on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void

Subscribes to output device change events. After the application integrates the [AVCastPicker component](ohos-multimedia-avcastpicker.md), the application receives the device change callback when the user switches the device through the component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                  | Yes  | Event type. The event **'outputDeviceChange'** is triggered when the output device changes.|
| callback | (state: [ConnectionState](#connectionstate10), device: [OutputDeviceInfo](#outputdeviceinfo10)) => void | Yes  | Callback function, where the **device** parameter specifies the output device information.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                        |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('outputDeviceChange', (state: avSession.ConnectionState, device: avSession.OutputDeviceInfo) => {
  console.info(`on outputDeviceChange device : ${device}`);
});
```

### on('commonCommand')<sup>10+</sup>

on(type: 'commonCommand', callback: (command: string, args: {[key: string]: Object}) => void): void

Subscribes to custom control command change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'commonCommand'** is triggered when a custom control command changes.|
| callback | (command: string, args: {[key: string]: Object}) => void         | Yes  | Callback used for subscription. The **command** parameter in the callback indicates the name of the changed custom control command, and **args** indicates the parameters carried in the command. The parameters must be the same as those set in [sendCommonCommand](#sendcommoncommand10).         |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() { 
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession | undefined = undefined;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;

            avSession.createAVSession(context, tag, "audio", (err: BusinessError, data: avSession.AVSession) => {
            if (err) {
                console.error(`CreateAVSession BusinessError: code: ${err.code}, message: ${err.message}`);
            } else {
                currentAVSession = data;
            }
            });
            if (currentAVSession !== undefined) {
            (currentAVSession as avSession.AVSession).on('commonCommand', (commonCommand, args) => {
                console.info(`OnCommonCommand, the command is ${commonCommand}, args: ${JSON.stringify(args)}`);
            });
            }
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

### off('play')<sup>10+</sup>

off(type: 'play', callback?: () => void): void

Unsubscribes from play command events.

After the callback is canceled, the list of supported commands must be updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'play'** in this case.|
| callback | () => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('play');
```

### off('pause')<sup>10+</sup>

off(type: 'pause', callback?: () => void): void

Unsubscribes from pause command events.

After the callback is canceled, the list of supported commands must be updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'pause'** in this case.|
| callback | () => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('pause');
```

### off('stop')<sup>10+</sup>

off(type: 'stop', callback?: () => void): void

Unsubscribes from stop command events.

After the callback is canceled, the list of supported commands must be updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'stop'** in this case.|
| callback | () => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('stop');
```

### off('playNext')<sup>10+</sup>

off(type: 'playNext', callback?: () => void): void

Unsubscribes from playNext command events.

After the callback is canceled, the list of supported commands must be updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'playNext'** in this case.|
| callback | () => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('playNext');
```

### off('playPrevious')<sup>10+</sup>

off(type: 'playPrevious', callback?: () => void): void

Unsubscribes from playPrevious command events.

After the callback is canceled, the list of supported commands must be updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'playPrevious'** in this case.|
| callback | () => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('playPrevious');
```

### off('fastForward')<sup>10+</sup>

off(type: 'fastForward', callback?: () => void): void

Unsubscribes from fastForward command events.

After the callback is canceled, the list of supported commands must be updated.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'fastForward'** in this case.|
| callback | () => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('fastForward');
```

### off('rewind')<sup>10+</sup>

off(type: 'rewind', callback?: () => void): void

Unsubscribes from rewind command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'rewind'** in this case.|
| callback | () => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('rewind');
```

### off('seek')<sup>10+</sup>

off(type: 'seek', callback?: (time: number) => void): void

Unsubscribes from seek command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                         |
| -------- | ---------------------- | ---- | ----------------------------------------- |
| type     | string                 | Yes  | Event type, which is **'seek'** in this case.      |
| callback | (time: number) => void | No  | Callback used for unsubscription. The **time** parameter in the callback indicates the time to seek to, in milliseconds.<br>If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.       |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('seek');
```

### off('setSpeed')<sup>10+</sup>

off(type: 'setSpeed', callback?: (speed: number) => void): void

Unsubscribes from setSpeed command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                          |
| -------- | ----------------------- | ---- | -------------------------------------------|
| type     | string                  | Yes  | Event type, which is **'setSpeed'** in this case.   |
| callback | (speed: number) => void | No  | Callback used for unsubscription. The **speed** parameter in the callback indicates the playback speed.<br>If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('setSpeed');
```

### off('setLoopMode')<sup>10+</sup>

off(type: 'setLoopMode', callback?: (mode: LoopMode) => void): void

Unsubscribes from setLoopMode command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                 | Mandatory| Description    |
| -------- | ------------------------------------- | ---- | ----- |
| type     | string | Yes  | Event type, which is **'setLoopMode'** in this case.|
| callback | (mode: [LoopMode](#loopmode10)) => void | No  | Callback used for unsubscription. The **mode** parameter in the callback indicates the loop mode.<br>- If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>- The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('setLoopMode');
```

### off('setTargetLoopMode')<sup>18+</sup>

off(type: 'setTargetLoopMode', callback?: Callback\<LoopMode>): void

Unsubscribes from setTargetLoopMode command events.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                 | Mandatory| Description    |
| -------- | ------------------------------------- | ---- | ----- |
| type     | string | Yes  | Event type, which is **'setTargetLoopMode'** in this case.|
| callback | Callback<[LoopMode](#loopmode10)> | No  | Callback used for unsubscription. The **LoopMode** parameter in the callback indicates the target loop mode.<br>- If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>- The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('setTargetLoopMode');
```

### off('toggleFavorite')<sup>10+</sup>

off(type: 'toggleFavorite', callback?: (assetId: string) => void): void

Unsubscribes from toggleFavorite command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                        |
| -------- | ------------------------- | ---- | -------------------------------------------------------- |
| type     | string                    | Yes  | Event type, which is **'toggleFavorite'** in this case.           |
| callback | (assetId: string) => void | No  | Callback used for unsubscription. The **assetId** parameter in the callback indicates the media asset ID.<br>If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                              |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('toggleFavorite');
```

### off('skipToQueueItem')<sup>10+</sup>

off(type: 'skipToQueueItem', callback?: (itemId: number) => void): void

Unsubscribes from the event that indicates an item in the playlist is selected.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                     | Mandatory| Description                                                                                                                                                       |
| -------- | ------------------------ | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type     | string                   | Yes  | Event type, which is **'skipToQueueItem'** in this case.                                                                                                         |
| callback | (itemId: number) => void | No  | Callback used for unsubscription. The **itemId** parameter in the callback indicates the ID of the item.<br>If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('skipToQueueItem');
```

### off('handleKeyEvent')<sup>10+</sup>

off(type: 'handleKeyEvent', callback?: (event: KeyEvent) => void): void

Unsubscribes from key events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type, which is **'handleKeyEvent'** in this case.            |
| callback | (event: [KeyEvent](../apis-input-kit/js-apis-keyevent.md)) => void | No  | Callback used for unsubscription. The **event** parameter in the callback indicates the key event.<br>If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                             |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('handleKeyEvent');
```

### off('outputDeviceChange')<sup>10+</sup>

off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void

Unsubscribes from playback device change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                     |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | string                                                  | Yes  | Event type, which is **'outputDeviceChange'** in this case.    |
| callback | (state: [ConnectionState](#connectionstate10), device: [OutputDeviceInfo](#outputdeviceinfo10)) => void | No  | Callback function, where the **device** parameter specifies the output device information.<br>If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                       |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('outputDeviceChange');
```


### off('commonCommand')<sup>10+</sup>

off(type: 'commonCommand', callback?: (command: string, args: {[key:string]: Object}) => void): void

Unsubscribes from custom control command change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'commonCommand'** in this case.   |
| callback | (command: string, args: {[key:string]: Object}) => void         | No  | Callback used for unsubscription. The **command** parameter in the callback indicates the name of the changed custom control command, and **args** indicates the parameters carried in the command.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('commonCommand');
```

### on('answer')<sup>11+</sup>

on(type: 'answer', callback: Callback\<void>): void

Subscribes to call answer events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'answer'** is triggered when a call is answered.|
| callback | Callback\<void>                                               | Yes  | Callback used to return the result.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('answer', () => {
  console.info('on call answer');
});
```

### off('answer')<sup>11+</sup>

off(type: 'answer', callback?: Callback\<void>): void

Unsubscribes from call answer events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'answer'** in this case.|
| callback | Callback\<void>     | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.   |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('answer');
```

### on('hangUp')<sup>11+</sup>

on(type: 'hangUp', callback: Callback\<void>): void

Subscribes to call hangup events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'hangUp'** is triggered when a call is hung up.|
| callback | Callback\<void>                                               | Yes  | Callback used to return the result.                                            |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('hangUp', () => {
  console.info('on call hangUp');
});
```

### off('hangUp')<sup>11+</sup>

off(type: 'hangUp', callback?: Callback\<void>): void

Unsubscribes from call answer events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'hangUp'** in this case.|
| callback | Callback\<void>      | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('hangUp');
```

### on('toggleCallMute')<sup>11+</sup>

on(type: 'toggleCallMute', callback: Callback\<void>): void

Subscribes to call mute events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'toggleCallMute'** is triggered when a call is muted or unmuted.|
| callback | Callback\<void>                                               | Yes  | Callback used to return the result.                                            |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.on('toggleCallMute', () => {
  console.info('on call toggleCallMute');
});
```

### off('toggleCallMute')<sup>11+</sup>

off(type: 'toggleCallMute', callback?: Callback\<void>): void

Unsubscribes from call mute events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string               | Yes  | Event type, which is **'toggleCallMute'** in this case.|
| callback | Callback\<void>    | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('toggleCallMute');
```

### on('castDisplayChange')<sup>12+</sup>

on(type: 'castDisplayChange', callback: Callback\<CastDisplayInfo>): void

Subscribes to cast display change events in the case of extended screens.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string                                                       | Yes  | Event type. The event **'castDisplayChange'** is triggered when the cast display in the case of extended screens changes.|
| callback | Callback<[CastDisplayInfo](#castdisplayinfo12)>   | Yes  | Callback used to return the information about the cast display.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
let castDisplay: avSession.CastDisplayInfo;
currentAVSession.on('castDisplayChange', (display: avSession.CastDisplayInfo) => {
    if (display.state === avSession.CastDisplayState.STATE_ON) {
        castDisplay = display;
        console.info(`Succeeded in castDisplayChange display : ${display.id} ON`);
    } else if (display.state === avSession.CastDisplayState.STATE_OFF){
        console.info(`Succeeded in castDisplayChange display : ${display.id} OFF`);
    }
});
```
### off('castDisplayChange')<sup>12+</sup>

 off(type: 'castDisplayChange', callback?: Callback\<CastDisplayInfo>): void

Unsubscribes from cast display change events in the case of extended screens.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

**Parameters**

| Name   | Type                 | Mandatory| Description                                                                                                                        |
| -------- | -------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'castDisplayChange'** in this case.|
| callback | Callback<[CastDisplayInfo](#castdisplayinfo12)>   | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |

**Example**

```ts
currentAVSession.off('castDisplayChange');
```

### stopCasting<sup>10+</sup>

stopCasting(callback: AsyncCallback\<void>): void

Stops castings. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600109  | The remote connection is not established. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.stopCasting((err: BusinessError) => {
  if (err) {
    console.error(`stopCasting BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('stopCasting successfully');
  }
});
```

### stopCasting<sup>10+</sup>

stopCasting(): Promise\<void>

Stops castings. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If casting stops, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600109  | The remote connection is not established. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.stopCasting().then(() => {
  console.info('stopCasting successfully');
}).catch((err: BusinessError) => {
  console.error(`stopCasting BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getOutputDeviceSync<sup>10+</sup>

getOutputDeviceSync(): OutputDeviceInfo

Obtains the output device information. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                           | Description                             |
| ----------------------------------------------- | --------------------------------- |
| [OutputDeviceInfo](#outputdeviceinfo10) | Information about the output device.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID  | Error Message|
|---------| --------------------------------------- |
| 6600101 | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102 | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let currentOutputDevice: avSession.OutputDeviceInfo = currentAVSession.getOutputDeviceSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`getOutputDeviceSync error, error code: ${error.code}, error message: ${error.message}`);
}
```
### getAllCastDisplays<sup>12+</sup>

getAllCastDisplays(): Promise<Array\<CastDisplayInfo>>

Obtains all displays that support extended screen projection in the current system. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

**Return value**

| Type                                           | Description                             |
| ----------------------------------------------- | --------------------------------- |
| Promise<Array<[CastDisplayInfo](#castdisplayinfo12)>>| Promise used to return the information about all the cast displays.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID  | Error Message|
|---------| --------------------------------------- |
| 6600101 | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102 | The session does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let castDisplay: avSession.CastDisplayInfo;
currentAVSession.getAllCastDisplays().then((data: Array< avSession.CastDisplayInfo >) => {
    if (data.length >= 1) {
       castDisplay = data[0];
     }
   }).catch((err: BusinessError) => {
     console.error(`Failed to getAllCastDisplay. Code: ${err.code}, message: ${err.message}`);
   });
```

## AVCastControlCommandType<sup>10+</sup>

type AVCastControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setVolume' | 'setSpeed' | 'setLoopMode' | 'toggleFavorite' | 'toggleMute'

Defines the commands that can be sent by a cast controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Type            | Description        |
| ---------------- | ------------ |
| 'play'           | Play the media. No parameter is required.|
| 'pause'          | Pause the playback. No parameter is required.  |
| 'stop'           | Stop the playback. No parameter is required.        |
| 'playNext'       | Play the next media asset. No parameter is required.      |
| 'playPrevious'   | Play the previous media asset. No parameter is required.      |
| 'fastForward'    | Fast-forward. No parameter is required.      |
| 'rewind'         | Rewind. No parameter is required.       |
| 'seek'           | Seek to a playback position. The corresponding parameter is of the number type.|
| 'setVolume'      | Set the volume. The corresponding parameter is of the number type. You can use [AVPlaybackState.maxVolume](#avplaybackstate10) to obtain the maximum system volume.    |
| 'setSpeed'       | Set the playback speed. The corresponding parameter is [media.PlaybackSpeed](../apis-media-kit/arkts-apis-media-e.md#playbackspeed8).|
| 'setLoopMode'    | Set the loop mode. The corresponding parameter is [LoopMode](#loopmode10).|
| 'toggleFavorite' | Favorite the media asset. The corresponding parameter is [AVMetadata.assetId](#avmetadata10).   |
| 'toggleMute'     | Set the muted status. No parameter is required.|

## AVCastControlCommand<sup>10+</sup>

Describes the command that can be sent by a cast controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name     | Type                                             | Mandatory| Description          |
| --------- | ------------------------------------------------- | ---- | -------------- |
| command   | [AVCastControlCommandType](#avcastcontrolcommandtype10)     | Yes  | Command. The parameters carried in each command are different. For details, see [AVCastControlCommandType](#avcastcontrolcommandtype10).|
| parameter | [media.PlaybackSpeed](../apis-media-kit/arkts-apis-media-e.md#playbackspeed8) &#124; number &#124; string &#124; [LoopMode](#loopmode10) | No  | Parameters carried in the command.|

## AVCastController<sup>10+</sup>

After a casting connection is set up, you can call [avSession.getAVCastController](#getavcastcontroller10) to obtain the cast controller. Through the controller, you can query the session ID, send commands and events to a session, and obtain session metadata and playback state information.

### getAVPlaybackState<sup>10+</sup>

getAVPlaybackState(callback: AsyncCallback\<AVPlaybackState>): void

Obtains the remote playback state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                                       | Mandatory| Description                                                        |
| --------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback  | AsyncCallback<[AVPlaybackState](#avplaybackstate10)\> | Yes  | Callback used to return the remote playback state.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.getAVPlaybackState((err: BusinessError, state: avSession.AVPlaybackState) => {
  if (err) {
    console.error(`getAVPlaybackState BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getAVPlaybackState : SUCCESS');
  }
});
```

### getAVPlaybackState<sup>10+</sup>

getAVPlaybackState(): Promise\<AVPlaybackState>

Obtains the remote playback state. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise<[AVPlaybackState](#avplaybackstate10)\>  | Promise used to return the remote playback state.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.getAVPlaybackState().then((state: avSession.AVPlaybackState) => {
  console.info('getAVPlaybackState : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`getAVPlaybackState BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getSupportedDecoders<sup>19+</sup>

getSupportedDecoders(): Promise\<Array\<DecoderType>>

Obtains the decoding modes supported by the current remote device. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise\<Array\<[DecoderType](#decodertype19)\>\> | Promise used to return an array of decoding modes supported by the remote device.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.getSupportedDecoders().then((decoderTypes: avSession.DecoderType[]) => {
  console.info(`getSupportedDecoders : SUCCESS : decoderTypes.length : ${decoderTypes.length}`);
  if (decoderTypes.length > 0 ) {
    console.info(`getSupportedDecoders : SUCCESS : decoderTypes[0] : ${decoderTypes[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`getSupportedDecoders BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getRecommendedResolutionLevel<sup>19+</sup>

getRecommendedResolutionLevel(decoderType: DecoderType): Promise\<ResolutionLevel>

Obtains the recommended resolution level based on the passed decoding mode. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**
| Name  | Type                                     | Mandatory| Description                      |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| decoderType | [DecoderType](#decodertype19) | Yes| Decoding format supported by the device.<br>The following decoding formats are supported by the device:<br>**'OH_AVCODEC_MIMETYPE_VIDEO_AVC'**: VIDEO AVC.<br>**'OH_AVCODEC_MIMETYPE_VIDEO_HEVC'**: VIDEO HEVC.<br>**'OH_AVCODEC_MIMETYPE_AUDIO_VIVID'**: AUDIO AV3A.|

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise\<[ResolutionLevel](#resolutionlevel19)\> | Promise used to return the recommended resolution level of the remote device.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let decoderType = avSession.DecoderType.OH_AVCODEC_MIMETYPE_VIDEO_AVC;
let resolutionLeve = avSession.ResolutionLevel;
aVCastController.getRecommendedResolutionLevel(decoderType).then((resolutionLeve) => {
  console.info('getRecommendedResolutionLevel successfully');
}).catch((err: BusinessError) => {
  console.error(`getRecommendedResolutionLevel BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getSupportedHdrCapabilities<sup>19+</sup>

getSupportedHdrCapabilities(): Promise\<Array\<hdrCapability.HDRFormat>>

Obtains the HDR capabilities supported by the current remote device. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise\<Array\<[hdrCapability.HDRFormat](../apis-arkgraphics2d/js-apis-hdrCapability.md#hdrformat)\>\> | Promise used to return an array of HDR capabilities supported by the remote device.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import type hdrCapability from './@ohos.graphics.hdrCapability';

aVCastController.getSupportedHdrCapabilities().then((hdrFormats: hdrCapability.HDRFormat[]) => {
  console.info(`getSupportedHdrCapabilities : SUCCESS : hdrFormats.length : ${hdrFormats.length}`);
  if (hdrFormats.length > 0 ) {
    console.info(`getSupportedHdrCapabilities : SUCCESS : descriptors[0] : ${hdrFormats[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`getSupportedHdrCapabilities BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getSupportedPlaySpeeds<sup>19+</sup>

getSupportedPlaySpeeds(): Promise\<Array\<number>>

Obtains the playback speeds supported by the current remote device. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise\<Array\<number\>\> | Promise used to return an array of playback speeds supported by the remote device.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.getSupportedPlaySpeeds().then((nums: number[]) => {
  console.info(`getSupportedPlaySpeeds : SUCCESS : hdrFormats.length : ${nums.length}`);
  if (nums.length > 0 ) {
    console.info(`getSupportedPlaySpeeds : SUCCESS : descriptors[0] : ${nums[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`getSupportedPlaySpeeds BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### sendControlCommand<sup>10+</sup>

sendControlCommand(command: AVCastControlCommand): Promise\<void>

Sends a control command to the session through the controller. This API uses a promise to return the result.


**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| command | [AVCastControlCommand](#avcastcontrolcommand10) | Yes  | Command to send.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avCommand: avSession.AVCastControlCommand = {command:'play'};
aVCastController.sendControlCommand(avCommand).then(() => {
  console.info('SendControlCommand successfully');
}).catch((err: BusinessError) => {
  console.error(`SendControlCommand BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### sendControlCommand<sup>10+</sup>

sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback\<void>): void

Sends a control command to the session through the controller. This API uses an asynchronous callback to return the result.


**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                 | Mandatory| Description                          |
| -------- | ------------------------------------- | ---- | ------------------------------ |
| command  | [AVCastControlCommand](#avcastcontrolcommand10) | Yes  | Command to send.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.                    |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avCommand: avSession.AVCastControlCommand = {command:'play'};
aVCastController.sendControlCommand(avCommand, (err: BusinessError) => {
  if (err) {
    console.error(`SendControlCommand BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('SendControlCommand successfully');
  }
});
```

### prepare<sup>10+</sup>

prepare(item: AVQueueItem, callback: AsyncCallback\<void>): void

Prepares for the playback of a media asset, that is, loads and buffers a media asset. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| item | [AVQueueItem](#avqueueitem10) | Yes  | Properties of an item in the playlist.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.|   

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Set playback parameters.
let playItem: avSession.AVQueueItem = {
  itemId: 0,
  description: {
    assetId: '12345',
    mediaType: 'AUDIO',
    mediaUri: 'http://resource1_address',
    mediaSize: 12345,
    startPosition: 0,
    duration: 0,
    artist: 'mysong',
    albumTitle: 'song1_title',
    albumCoverUri: "http://resource1_album_address",
    lyricUri: "http://resource1_lyric_address",
    appName: 'MyMusic'
  }
};
// Prepare for playback. This operation triggers loading and buffering, but not the actual playback.
aVCastController.prepare(playItem, (err: BusinessError) => {
  if (err) {
    console.error(`prepare BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('prepare successfully');
  }
});
```


### prepare<sup>10+</sup>

prepare(item: AVQueueItem): Promise\<void>

Prepares for the playback of a media asset, that is, loads and buffers a media asset. This API uses a promise to return the result.


**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| item | [AVQueueItem](#avqueueitem10) | Yes  | Properties of an item in the playlist.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600109  | The remote connection is not established. |


**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Set playback parameters.
let playItem: avSession.AVQueueItem = {
  itemId: 0,
  description: {
    assetId: '12345',
    mediaType: 'AUDIO',
    mediaUri: 'http://resource1_address',
    mediaSize: 12345,
    startPosition: 0,
    duration: 0,
    artist: 'mysong',
    albumTitle: 'song1_title',
    albumCoverUri: "http://resource1_album_address",
    lyricUri: "http://resource1_lyric_address",
    appName: 'MyMusic'
  }
};
// Prepare for playback. This operation triggers loading and buffering, but not the actual playback.
aVCastController.prepare(playItem).then(() => {
  console.info('prepare successfully');
}).catch((err: BusinessError) => {
  console.error(`prepare BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### start<sup>10+</sup>

start(item: AVQueueItem, callback: AsyncCallback\<void>): void

Prepares for the playback of a media asset. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| item | [AVQueueItem](#avqueueitem10) | Yes  | Properties of an item in the playlist.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.|   

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Set playback parameters.
let playItem: avSession.AVQueueItem = {
  itemId: 0,
  description: {
    assetId: '12345',
    mediaType: 'AUDIO',
    mediaUri: 'http://resource1_address',
    mediaSize: 12345,
    startPosition: 0,
    duration: 0,
    artist: 'mysong',
    albumTitle: 'song1_title',
    albumCoverUri: "http://resource1_album_address",
    lyricUri: "http://resource1_lyric_address",
    appName: 'MyMusic'
  }
};

// Start playback.
aVCastController.start(playItem, (err: BusinessError) => {
  if (err) {
    console.error(`start BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('start successfully');
  }
});
```

### start<sup>10+</sup>

start(item: AVQueueItem): Promise\<void>

Prepares for the playback of a media asset. This API uses a promise to return the result.


**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| item | [AVQueueItem](#avqueueitem10) | Yes  | Properties of an item in the playlist.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600109  | The remote connection is not established. |


**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Set playback parameters.
let playItem: avSession.AVQueueItem = {
  itemId: 0,
  description: {
    assetId: '12345',
    mediaType: 'AUDIO',
    mediaUri: 'http://resource1_address',
    mediaSize: 12345,
    startPosition: 0,
    duration: 0,
    artist: 'mysong',
    albumTitle: 'song1_title',
    albumCoverUri: "http://resource1_album_address",
    lyricUri: "http://resource1_lyric_address",
    appName: 'MyMusic'
  }
};
// Start playback.
aVCastController.start(playItem).then(() => {
  console.info('start successfully');
}).catch((err: BusinessError) => {
  console.error(`start BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getCurrentItem<sup>10+</sup>

getCurrentItem(callback: AsyncCallback\<AVQueueItem>): void

Obtains the information about the media asset that is being played. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback\<[AVQueueItem](#avqueueitem10)>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.getCurrentItem((err: BusinessError, value: avSession.AVQueueItem) => {
  if (err) {
    console.error(`getCurrentItem BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getCurrentItem successfully');
  }
});
```

### getCurrentItem<sup>10+</sup>

getCurrentItem(): Promise\<AVQueueItem>

Obtains the information about the media asset that is being played. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<[AVQueueItem](#avqueueitem10)> | Promise used to return the media asset obtained. If the operation fails, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.getCurrentItem().then((value: avSession.AVQueueItem) => {
  console.info('getCurrentItem successfully');
}).catch((err: BusinessError) => {
  console.error(`getCurrentItem BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getValidCommands<sup>11+</sup>

getValidCommands(callback: AsyncCallback<Array\<AVCastControlCommandType>>): void

Obtains the supported commands. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback<Array<[AVCastControlCommandType](#avcastcontrolcommandtype10)>> | Yes| Callback return the supported commands.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.getValidCommands((err: BusinessError, state: avSession.AVCastControlCommandType[]) => {
  if (err) {
    console.error(`getValidCommands BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getValidCommands successfully');
  }
});
```

### getValidCommands<sup>11+</sup>

getValidCommands(): Promise<Array\<AVCastControlCommandType>>

Obtains the supported commands. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type| Description|
| -------------- | ----------------------------- |
| Promise<Array\<[AVCastControlCommandType](#avcastcontrolcommandtype10)>> | Promise used to return the supported commands.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.getValidCommands().then((state: avSession.AVCastControlCommandType[]) => {
  console.info('getValidCommands successfully');
}).catch((err: BusinessError) => {
  console.error(`getValidCommands BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### processMediaKeyResponse<sup>12+</sup>

processMediaKeyResponse(assetId: string, response: Uint8Array): Promise\<void>

Processes the response to a media key request during online DRM resource projection. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| assetId | string                  | Yes  | Media asset ID.|
| response | Uint8Array             | Yes  | Response to the media key request.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the response is processed successfully, no result is returned. Otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
let keyRequestCallback: avSession.KeyRequestCallback = async(assetId: string, requestData: Uint8Array) => {
  // Obtain the DRM URL based on the asset ID.
  let drmUrl = 'http://license.xxx.xxx.com:8080/drmproxy/getLicense';
  // Obtain a media key from the server. Assign a value based on service requirements.
  let licenseResponseData: Uint8Array = new Uint8Array();
  console.info(`Succeeded in get license by ${drmUrl}.`);
  aVCastController.processMediaKeyResponse(assetId, licenseResponseData);
}
```

### release<sup>11+</sup>

release(callback: AsyncCallback\<void>): void

Releases this cast controller. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                      | Mandatory| Description                                                        |
| -------- | -------------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<void>       | Yes  | Callback used to return the result. If the controller is released, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | -------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.release((err: BusinessError) => {
  if (err) {
    console.error(`release BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('release successfully');
  }
});
```

### release<sup>11+</sup>

release(): Promise\<void>

Releases this cast controller. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the controller is released, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.release().then(() => {
  console.info('release successfully');
}).catch((err: BusinessError) => {
  console.error(`release BusinessError: code: ${err.code}, message: ${err.message}`);
});

```

### on('playbackStateChange')<sup>10+</sup>

on(type: 'playbackStateChange', filter: Array\<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void

Subscribes to playback state change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'playbackStateChange'** is triggered when the playback state changes.|
| filter   | Array\<keyof&nbsp;[AVPlaybackState](#avplaybackstate10)\>&nbsp;&#124;&nbsp;'all' | Yes  | The value **'all'** indicates that any playback state field change will trigger the event, and **Array<keyof&nbsp;[AVPlaybackState](#avplaybackstate10)\>** indicates that only changes to the listed playback state field will trigger the event.|
| callback | (state: [AVPlaybackState](#avplaybackstate10)) => void         | Yes  | Callback used for subscription. The **state** parameter in the callback indicates the changed playback state.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.on('playbackStateChange', 'all', (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});

let playbackFilter: Array<keyof avSession.AVPlaybackState> = ['state', 'speed', 'loopMode'];
aVCastController.on('playbackStateChange', playbackFilter, (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});
```

### off('playbackStateChange')<sup>10+</sup>

off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void

Unsubscribes from playback state change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'playbackStateChange'** in this case.   |
| callback | (state: [AVPlaybackState](#avplaybackstate10)) => void         | No  | Callback function, where the **state** parameter indicates the new playback state.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('playbackStateChange');
```

### on('mediaItemChange')<sup>10+</sup>

on(type: 'mediaItemChange', callback: Callback\<AVQueueItem>): void

Subscribes to media asset change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'mediaItemChange'** is triggered when the media content being played changes.|
| callback | Callback<[AVQueueItem](#avqueueitem10)>         | Yes  | Callback used for subscription. **AVQueueItem** is the media asset that is being played.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.on('mediaItemChange', (item: avSession.AVQueueItem) => {
  console.info(`on mediaItemChange state : ${item.itemId}`);
});
```

### off('mediaItemChange')<sup>10+</sup>

off(type: 'mediaItemChange'): void

Unsubscribes from media asset change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'mediaItemChange'** in this case.   |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('mediaItemChange');
```

### on('playNext')<sup>10+</sup>

on(type: 'playNext', callback: Callback\<void>): void

Subscribes to playNext command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'playNext'** is triggered when the command for playing the next item is received.|
| callback | Callback\<void\>         | Yes  | Callback used to return the result.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.on('playNext', () => {
  console.info('on playNext');
});
```

### off('playNext')<sup>10+</sup>

off(type: 'playNext'): void

Unsubscribes from playNext command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'playNext'** in this case.   |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('playNext');
```

### on('playPrevious')<sup>10+</sup>

on(type: 'playPrevious', callback: Callback\<void>): void

Subscribes to playPrevious command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'playPrevious'** is triggered when the command for playing the previous event is received.|
| callback | Callback\<void\>         | Yes  | Callback used to return the result.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.on('playPrevious', () => {
  console.info('on playPrevious');
});
```

### off('playPrevious')<sup>10+</sup>

off(type: 'playPrevious'): void

Unsubscribes from playPrevious command events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'playPrevious'** in this case.   |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('playPrevious');
```

### on('requestPlay')<sup>11+</sup>

on(type: 'requestPlay', callback: Callback\<AVQueueItem>): void

Subscribes to playback request events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'requestPlay'** is triggered when a playback request is received.|
| callback | Callback\<[AVQueueItem](#avqueueitem10)>                | Yes  | Callback function, where the **AVQueueItem** parameter specifies the media asset that is being played. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object. | 

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.on('requestPlay', (item: avSession.AVQueueItem) => {
  console.info(`on requestPlay state : ${item.itemId}`);
});
```

### off('requestPlay')<sup>11+</sup>

off(type: 'requestPlay', callback?: Callback\<AVQueueItem>): void

Unsubscribes from playback request events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------| ---- | ----------------------------------------------------- |
| type     | string                                                      | Yes  | Event type, which is **'requestPlay'** in this case.   |
| callback | Callback\<[AVQueueItem](#avqueueitem10)>             | No  | Callback function, where the **AVQueueItem** parameter specifies the media asset that is being played. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('requestPlay');
```

### on('endOfStream')<sup>11+</sup>

on(type: 'endOfStream', callback: Callback\<void>): void

Subscribes to playback end events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | string                                                      | Yes  | Event type. The event **'endOfStream'** is triggered when the playback operation is complete.|
| callback | Callback\<void\>                                            | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.on('endOfStream', () => {
  console.info('on endOfStream');
});
```

### off('endOfStream')<sup>11+</sup>

off(type: 'endOfStream', callback?: Callback\<void>): void

Unsubscribes from the playback end events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------| ---- | ----------------------------------------------------- |
| type     | string                                                      | Yes  | Event type, which is **'endOfStream'** in this case.   |
| callback | Callback\<void\>                                            | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.  |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('endOfStream');
```

### on('seekDone')<sup>10+</sup>

on(type: 'seekDone', callback: Callback\<number>): void

Subscribes to seek done events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'seekDone'** is triggered when the seek operation is complete.|
| callback | Callback\<number\>         | Yes  | Callback used to return the position after the seek operation.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.on('seekDone', (pos: number) => {
  console.info(`on seekDone pos: ${pos} `);
});
```

### off('seekDone')<sup>10+</sup>

off(type: 'seekDone'): void

Unsubscribes from the seek done events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'seekDone'** in this case.   |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('seekDone');
```

### on('validCommandChange')<sup>11+</sup>

on(type: 'validCommandChange', callback: Callback\<Array\<AVCastControlCommandType>>)

Subscribes to valid command change events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'validCommandChange'** is triggered when the valid commands supported by the session changes.|
| callback | Callback<Array<[AVCastControlCommandType](#avcastcontrolcommandtype10)\>\>   | Yes  | Callback used for subscription. The **commands** parameter in the callback is a set of valid commands.                    |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
aVCastController.on('validCommandChange', (validCommands: avSession.AVCastControlCommandType[]) => {
  console.info(`validCommandChange : SUCCESS : size : ${validCommands.length}`);
  console.info(`validCommandChange : SUCCESS : validCommands : ${validCommands.values()}`);
});
```

### off('validCommandChange')<sup>11+</sup>

off(type: 'validCommandChange', callback?: Callback\<Array\<AVCastControlCommandType>>)

Unsubscribes from valid command change events. This API is called by the controller.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'validCommandChange'** in this case.        |
| callback | Callback<Array<[AVCastControlCommandType](#avcastcontrolcommandtype10)\>\> | No  | Callback used for unsubscription. The **commands** parameter in the callback is a set of valid commands.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.         |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message          |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
aVCastController.off('validCommandChange');
```

### on('error')<sup>10+</sup>

on(type: 'error', callback: ErrorCallback): void

Subscribes to remote AVPlayer errors. This event is used only for error prompt and does not require the user to stop playback control.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'error'** in this case. This event can be triggered by both user operations and the system.|
| callback | ErrorCallback | Yes  | Callback used to return the error code ID and error message.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 5400101  | No memory.            |
| 5400102  | Operation not allowed.   |
| 5400103  | I/O error.             |
| 5400104  | Time out.      |
| 5400105  | Service died.         |
| 5400106  | Unsupport format.     |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

aVCastController.on('error', (error: BusinessError) => {
  console.info(`error happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

### off('error')<sup>10+</sup>

off(type: 'error'): void

Unsubscribes from remote AVPlayer errors.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| type   | string | Yes  | Event type, which is **'error'** in this case.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 5400101  | No memory.            |
| 5400102  | Operation not allowed.   |
| 5400103  | I/O error.             |
| 5400104  | Time out.      |
| 5400105  | Service died.         |
| 5400106  | Unsupport format.     |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('error')
```

### on('keyRequest')<sup>12+</sup>

on(type: 'keyRequest', callback: KeyRequestCallback): void

Subscribes to media key requests during the cast of online DRM resources.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| type     | string  | Yes  | Event type. The event **'keyRequest'** is triggered when a media key request is required during the cast of online DRM resources.|
| callback | [KeyRequestCallback](#keyrequestcallback12)  | Yes  | Callback used to request the media resources and media key.|


**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message          |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
let keyRequestCallback: avSession.KeyRequestCallback = async(assetId: string, requestData: Uint8Array) => {
  console.info(`Succeeded in keyRequestCallback. assetId: ${assetId}, requestData: ${requestData}`);
}
aVCastController.on('keyRequest', keyRequestCallback);
```
### off('keyRequest')<sup>12+</sup>

off(type: 'keyRequest', callback?: KeyRequestCallback): void

Unsubscribes from media key requests during the cast of online DRM resources.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'keyRequest'** in this case.|
| callback |  [KeyRequestCallback](#keyrequestcallback12)  | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message          |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
aVCastController.off('keyRequest');
```

### on('castControlGenericError')<sup>13+</sup>

on(type: 'castControlGenericError', callback: ErrorCallback): void

Subscribes to generic error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlGenericError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 6611000  | The error code for cast control is unspecified.      |
| 6611001  | An unspecified error occurs in the remote player.   |
| 6611002  | The playback position falls behind the live window.     |
| 6611003  | The process of cast control times out.    |
| 6611004  | The runtime check failed.      |
| 6611100  | Cross-device data transmission is locked.    |
| 6611101  | The specified seek mode is not supported.   |
| 6611102  | The position to seek to is out of the range of the media asset or the specified seek mode is not supported.  |
| 6611103  | The specified playback mode is not supported.       |
| 6611104  | The specified playback speed is not supported.    |
| 6611105  | The action failed because either the media source device or the media sink device has been revoked.   |
| 6611106  | The parameter is invalid, for example, the url is illegal to play.  |
| 6611107  | Allocation of memory failed.  |
| 6611108  | Operation is not allowed.    |

**Example**

```ts
aVCastController.on('castControlGenericError', (error: BusinessError) => {
  console.info(`castControlGenericError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

### off('castControlGenericError')<sup>13+</sup>

off(type: 'castControlGenericError', callback?: ErrorCallback): void

Unsubscribes from generic error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | 	Event type, which is **'castControlGenericError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
aVCastController.off('castControlGenericError');
```

### on('castControlIoError')<sup>13+</sup>

on(type: 'castControlIoError', callback: ErrorCallback): void

Subscribes to input/output error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlIoError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 6612000  | An unspecified input/output error occurs.     |
| 6612001  | Network connection failure.   |
| 6612002  | Network timeout.     |
| 6612003  | Invalid "Content-Type" HTTP header.    |
| 6612004  | The HTTP server returns an unexpected HTTP response status code.      |
| 6612005  | The file does not exist.    |
| 6612006  | No permission is granted to perform the IO operation.   |
| 6612007  | Access to cleartext HTTP traffic is not allowed by the app's network security configuration. |
| 6612008  | Reading data out of the data bound.    |
| 6612100  | The media does not contain any contents that can be played.   |
| 6612101  | The media cannot be read, for example, because of dust or scratches.   |
| 6612102  | This resource is already in use. |
| 6612103  | The content using the validity interval has expired.  |
| 6612104  | Using the requested content to play is not allowed.    |
| 6612105  | The use of the allowed content cannot be verified.  |
| 6612106  | The number of times this content has been used as requested has reached the maximum allowed number of uses.  |
| 6612107  | An error occurs when sending packet from source device to sink device.    |

**Example**

```ts
aVCastController.on('castControlIoError', (error: BusinessError) => {
  console.info(`castControlIoError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

### off('castControlIoError')<sup>13+</sup>

off(type: 'castControlIoError', callback?: ErrorCallback): void

Unsubscribes from input/output error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | 	Event type, which is **'castControlIoError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
aVCastController.off('castControlIoError');
```

### on('castControlParsingError')<sup>13+</sup>

on(type: 'castControlParsingError', callback: ErrorCallback): void

Subscribes to parsing error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlParsingError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

| ID | Error Message             |
| -------- | --------------------- |
| 401      |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 6613000  | Unspecified error related to content parsing.     |
| 6613001  | Parsing error associated with media container format bit streams.   |
| 6613002  | Parsing error associated with the media manifest.     |
| 6613003  | An error occurs when attempting to extract a file with an unsupported media container format or an unsupported media container feature.    |
| 6613004  | Unsupported feature in the media manifest.    |

**Example**

```ts
aVCastController.on('castControlParsingError', (error: BusinessError) => {
  console.info(`castControlParsingError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

### off('castControlParsingError')<sup>13+</sup>

off(type: 'castControlParsingError', callback?: ErrorCallback): void

Unsubscribes from parsing error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | 	Event type, which is **'castControlParsingError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
aVCastController.off('castControlParsingError');
```

### on('castControlDecodingError')<sup>13+</sup>

on(type: 'castControlDecodingError', callback: ErrorCallback): void

Subscribes to decoding error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlDecodingError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 6614000  | Unspecified decoding error.     |
| 6614001  | Decoder initialization failed.   |
| 6614002  | Decoder query failed.     |
| 6614003  | Decoding the media samples failed.    |
| 6614004  | The format of the content to decode exceeds the capabilities of the device.    |
| 6614005  | The format of the content to decode is not supported.    |

**Example**

```ts
aVCastController.on('castControlDecodingError', (error: BusinessError) => {
  console.info(`castControlDecodingError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```
### off('castControlDecodingError')<sup>13+</sup>

off(type: 'castControlDecodingError', callback?: ErrorCallback): void

Unsubscribes from decoding error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | 	Event type, which is **'castControlDecodingError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
aVCastController.off('castControlDecodingError');
```

### on('castControlAudioRendererError')<sup>13+</sup>

on(type: 'castControlAudioRendererError', callback: ErrorCallback): void

Subscribes to audio renderer error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlAudioRendererError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

For details about the error codes, see [Media Error Codes](../apis-media-kit/errorcode-media.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 6615000  | Unspecified errors related to the audio renderer.     |
| 6615001  | Initializing the audio renderer failed.   |
| 6615002  | The audio renderer fails to write data.     |

**Example**

```ts
aVCastController.on('castControlAudioRendererError', (error: BusinessError) => {
  console.info(`castControlAudioRendererError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```
### off('castControlAudioRendererError')<sup>13+</sup>

off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void

Unsubscribes from audio renderer error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | 	Event type, which is **'castControlAudioRendererError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|

**Example**

```ts
aVCastController.off('castControlAudioRendererError');
```

### on('castControlDrmError')<sup>13+</sup>

on(type: 'castControlDrmError', callback: ErrorCallback): void

Subscribes to DRM error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlDrmError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 6616000  | Unspecified error related to DRM.     |
| 6616001  | The chosen DRM protection scheme is not supported by the device.  |
| 6616002  | Device provisioning failed.    |
| 6616003  | The DRM-protected content to play is incompatible.     |
| 6616004  | Failed to obtain a license.   |
| 6616005  | The operation is disallowed by the license policy.     |
| 6616006  | An error occurs in the DRM system.     |
| 6616007  | The device has revoked DRM privileges.   |
| 6616008  | The DRM license being loaded into the open DRM session has expired.      |
| 6616100  | An error occurs when the DRM processes the key response.     |

**Example**

```ts
aVCastController.on('castControlDrmError', (error: BusinessError) => {
  console.info(`castControlDrmError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

### off('castControlDrmError')<sup>13+</sup>

off(type: 'castControlDrmError', callback?: ErrorCallback): void

Unsubscribes from DRM error events during cast control.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | 	Event type, which is **'castControlDrmError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
aVCastController.off('castControlDrmError');
```

## ExtraInfo<sup>18+</sup>
type ExtraInfo = { [key: string]: Object; }

Defines the custom media packet set by the provider.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| [key: string]: Object   | **key** specifies the remote distributed event type. Currently, the following event types are supported:<br>**'AUDIO_GET_VOLUME'**: obtains the volume of the remote device.<br>**'AUDIO_GET_AVAILABLE_DEVICES'**: obtains all remote devices that can be connected.<br>**'AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO'**: obtains the actual remote audio device.<br>The provider returns the corresponding media packet object based on the event type.|

## KeyRequestCallback<sup>12+</sup>
type KeyRequestCallback = (assetId: string, requestData: Uint8Array) => void

Defines the callback invoked for the media key request event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| assetId     | string  | Yes  | Media asset ID.|
| requestData |  Uint8Array  | Yes  | Data carried in the media key request.                           |

**Example**
<!--code_no_check-->
```ts
let keyRequestCallback: avSession.KeyRequestCallback = async(assetId: string, requestData: Uint8Array) => {
  console.info(`Succeeded in keyRequestCallback. assetId: ${assetId}, requestData: ${requestData}`);
}
```

## CastDisplayState<sup>12+</sup>

Enumerates the states of the cast display.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| STATE_OFF      | 1    | The device is disconnected, and the extended screen does not display any content.   |
| STATE_ON      | 2    | The device is connected, and the extended screen is available.|


## CastDisplayInfo<sup>12+</sup>

Describes the information about the cast display in the case of extended screens.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.ExtendedDisplayCast

| Name           | Type                     | Read-Only| Optional| Description                                                                 |
| --------------- |-------------------------| ---- | ---- |---------------------------------------------------------------------|
| id            | number                  | No   | No   | ID of the cast display. The value must be an integer. |
| name     | string                  | No   | No   | Name of the cast display.          |
| state          | [CastDisplayState](#castdisplaystate12)          | No   | No   |State of the cast display.           |
| width          | number          | No   | No   | Screen width of the cast display, in px. The value must be an integer.         |  
| height          | number          | No   | No   | Screen height of the cast display, in px. The value must be an integer.           |  

## ConnectionState<sup>10+</sup>

Enumerates the connection states.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| STATE_CONNECTING      | 0    | The device is connecting.   |
| STATE_CONNECTED      | 1    | The device is connected.|
| STATE_DISCONNECTED      | 6    | The device is disconnected.|

## AVMetadata<sup>10+</sup>

Describes the media metadata.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name           | Type                     | Read-Only| Optional| Description                                                                 |
| --------------- |-------------------------| ---- | ---- |---------------------------------------------------------------------|
| assetId         | string                  | No  | No  | Media asset ID. It is the unique ID of a song and defined by the application.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                    |
| title           | string                  | No  | Yes  | Title.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                |
| artist          | string                  | No  | Yes  | Artist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                               |
| author          | string                  | No  | Yes  | Author.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                              |
| avQueueName<sup>12+</sup>       | string                  | No  | Yes  | Playlist name.                                                              |
| avQueueId<sup>11+</sup>       | string                  | No  | Yes  | Unique ID of the playlist.                                                              |
| avQueueImage<sup>11+</sup>    | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) &#124; string | No  | Yes  | Cover image of the playlist, which can be pixel data of an image or an image path (local path or Internet path). Applications call **setAVMetadata** to set the image data.<br>- If the data type is set to **PixelMap**, the data obtained by calling **getAVMetadata** is the pixel data of an image.<br>- If the data type is set to **url**, the data obtained is an image path. |
| album           | string                  | No  | Yes  | Album name.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                              |
| writer          | string                  | No  | Yes  | Writer.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                               |
| composer        | string                  | No  | Yes  | composer.                                                               |
| duration        | number                  | No  | Yes  | Media duration, in ms.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                 |
| mediaImage      | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) &#124; string | No  | Yes  | Pixel map or image path (local path or network path) of the image. Applications call **setAVMetadata** to set the image data.<br>- If the data type is set to **PixelMap**, the data obtained by calling **getAVMetadata** is the pixel data of an image.<br>- If the data type is set to **url**, the data obtained is an image path.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                            |
| bundleIcon<sup>18+</sup>      | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | Yes  | Yes  | Pixel data of the image that is used as the application icon. It is read-only and cannot be set on the application side.|
| publishDate     | Date                    | No  | Yes  | Release date.                                                            |
| subtitle        | string                  | No  | Yes  | Subtitle.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                               |
| description     | string                  | No  | Yes  | Media description.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                              |
| lyric           | string                  | No  | Yes  | Lyrics. The application needs to combine the lyrics into a string.<br>The string length must be less than 40960 bytes.<br>**NOTE**: The system supports lyrics in the simple LRC format. If the lyrics are not standard (for example, having duplicate timestamps), the lyrics fail to be parsed and cannot be displayed properly in the system.|
| singleLyricText<sup>17+</sup> | string    | No  | Yes  | Lyrics of a single media asset. The application must combine the lyrics into a string (excluding the timestamp).<br>The string length must be less than 40960 bytes.<br>**Atomic service API**: This API can be used in atomic services since API version 17.|
| previousAssetId | string                  | No  | Yes  | ID of the previous media asset.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                           |
| nextAssetId     | string                  | No  | Yes  | ID of the next media asset.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                           |
| filter<sup>11+</sup>        | number         | No  | Yes  | Protocol supported by the media session. The default value is **TYPE_CAST_PLUS_STREAM**. For details, see [ProtocolType](#protocoltype11).<br>**Atomic service API**: This API can be used in atomic services since API version 12.                  |
| drmSchemes<sup>12+</sup>        | Array\<string>         | No  | Yes  | DRM scheme supported by the media session. The value is the UUID of the DRM scheme.|
| skipIntervals<sup>11+</sup>  | [SkipIntervals](#skipintervals11)        | No  | Yes  | Intervals supported for fast-forwarding and rewinding. The default value is **SECONDS_15**, that is, 15 seconds.                           |
|displayTags<sup>11+</sup>     | number                           | No  | Yes  | Display tags of the media asset. For details, see [DisplayTag](#displaytag11).                                                         |

## AVMediaDescription<sup>10+</sup>

Describes the properties related to the media metadata in the playlist.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name        | Type                   | Read-Only | Optional | Description                    |
| ------------ | ----------------------- | ---- | ---- | ----------------------- |
| assetId      | string                  | No  | No  | Media ID in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.         |
| title        | string                  | No  | Yes  | Name of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.       |
| subtitle     | string                  | No  | Yes  | Subname of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.     |
| description  | string                  | No  | Yes  | Description of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.  |
| mediaImage | image.PixelMap \| string   | No  | Yes  | Pixel map of the image of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| extras       | {[key: string]: Object}    | No  | Yes  | Additional fields of the media asset in the playlist.    |
| mediaUri     | string                  | No  | Yes  | URI of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| mediaType     | string                  | No  | Yes  | Type of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| mediaSize     | number                  | No  | Yes  | Size of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| albumTitle     | string                  | No  | Yes  | Album name of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| albumCoverUri     | string                  | No  | Yes  | URI of the album title of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.   |
| lyricContent     | string                  | No  | Yes  | Lyric content of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| lyricUri     | string                  | No  | Yes  | Lyric URI of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| artist     | string                  | No  | Yes  | Author of the lyric of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| fdSrc     | media.AVFileDescriptor        | No  | Yes  | Handle to the local media file in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| dataSrc<sup>12+</sup>     | media.AVDataSrcDescriptor        | No  | Yes  | Descriptor of the data source in the playlist.        |
| pcmSrc<sup>20+</sup>     | boolean        | No  | Yes  | Whether the playlist uses a PCM data source. **true** if the PCM data source used, **false** otherwise.<br>Due to device limitations, this parameter is temporarily unavailable and will be supported in future versions.        |
| drmScheme<sup>12+</sup>     | string        | No  | Yes  | DRM scheme supported by the playlist. The value is the UUID of the DRM scheme.      |
| duration     | number                  | No  | Yes  | Playback duration of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| startPosition     | number                  | No  | Yes  | Start position for playing the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| creditsPosition     | number                  | No  | Yes  | Position for playing the closing credits of the media asset in the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
| appName     | string                  | No  | Yes  | Name of the application provided by the playlist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.        |
|displayTags<sup>11+</sup>     | number | No  | Yes  | Display tags of the media asset. For details, see [DisplayTag](#displaytag11).<br>**Atomic service API**: This API can be used in atomic services since API version 12.       |

## AVQueueItem<sup>10+</sup>

Describes the properties of an item in the playlist.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name        | Type                                       | Mandatory| Description                       |
| ------------ | ------------------------------------------ | ---- | --------------------------- |
| itemId       | number                                     | Yes  | ID of an item in the playlist.         |
| description  | [AVMediaDescription](#avmediadescription10)  | No  | Media metadata of the item in the playlist.  |

## AVPlaybackState<sup>10+</sup>

Describes the information related to the media playback state.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name        | Type                                 | Mandatory| Description    |
| ------------ | ------------------------------------- | ---- | ------- |
| state        | [PlaybackState](#playbackstate10)       | No  | Playback state.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| speed        | number                                | No  | Playback speed.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| position     | [PlaybackPosition](#playbackposition10) | No  | Playback position.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| bufferedTime | number                                | No  | Buffered time.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| loopMode     | [LoopMode](#loopmode10)                 | No  | Loop mode.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| isFavorite   | boolean                               | No  | Whether the media asset is favorited. The value **true** means that the media asset is favorited.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| activeItemId<sup>10+</sup> | number                  | No  | ID of the item that is being played.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| volume<sup>10+</sup> | number                  | No  | Media volume.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| maxVolume<sup>11+</sup> | number                    | No  | Maximum volume.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| muted<sup>11+</sup>     | boolean                   | No  | Mute status. The value **true** means the muted state.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| duration<sup>11+</sup>     | number                   | No  | Duration of the media asset.|
| videoWidth<sup>11+</sup>  | number                  | No  | Video width of the media asset, in px.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| videoHeight<sup>11+</sup> |  number                 | No  | Video height of the media asset, in px.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| extras<sup>10+</sup> | {[key: string]: Object}       | No  | Custom media data.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## PlaybackPosition<sup>10+</sup>

Describes the information related to the playback position.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name       | Type  | Mandatory| Description              |
| ----------- | ------ | ---- | ------------------ |
| elapsedTime | number | Yes  | Elapsed time, in ms.|
| updateTime  | number | Yes  | Updated time, in ms.|

## CallMetadata<sup>11+</sup>

Describes the properties related to call metadata.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name           | Type                     | Mandatory| Description                                                                 |
| --------------- |-------------------------| ---- |---------------------------------------------------------------------|
| name            | string                  | No   | Name (alias) of the caller.   |                                                                                                                      
| phoneNumber     | string                  | No   | Phone number of the caller.           |                                                   
| avatar          | [image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)          | No   | Profile picture of the caller.           |                                                   

## AVCallState<sup>11+</sup>

Describes the properties related to the call state.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name           | Type                     | Mandatory| Description                                                                 |
| --------------- |-------------------------  | ---- |---------------------------------------------------------------------|
| state           | [CallState](#callstate11)                 | Yes   | Call state.     |                                                                                                                      
| muted           | boolean                   | Yes   | Whether the microphone is muted.<br>**true**: The microphone is muted.<br>**false**: The microphone is not muted.|                                                                  
 
## CallState<sup>11+</sup>

Enumerates the call states.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name                       | Value  | Description     |
| --------------------------  | ---- | -------- |
| CALL_STATE_IDLE             | 0    | The phone is idle.  |
| CALL_STATE_INCOMING         | 1    | The phone is ringing.    |
| CALL_STATE_ACTIVE           | 2    | The call is connected.    |
| CALL_STATE_DIALING          | 3    | The caller is dialing.    |
| CALL_STATE_WAITING          | 4    | The call is waiting for connection. |
| CALL_STATE_HOLDING          | 5    | The call is placed on hold.    |
| CALL_STATE_DISCONNECTING    | 6    | The call is disconnecting.    |

## DisplayTag<sup>11+</sup>

Enumerates the display tags of the media asset. The display tag is a special type identifier of the media audio source.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name                       | Value  | Description          |
| --------------------------  | ---- | ------------ |
| TAG_AUDIO_VIVID             | 1    | AUDIO VIVID  |

## DecoderType<sup>19+</sup>

Enumerates the decoding formats supported by the device.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name                       | Value  | Description          |
| --------------------------  | ---- | ------------ |
| OH_AVCODEC_MIMETYPE_VIDEO_AVC      | "video/avc"  | VIDEO AVC. |
| OH_AVCODEC_MIMETYPE_VIDEO_HEVC     | "video/hevc" | VIDEO HEVC. |
| OH_AVCODEC_MIMETYPE_AUDIO_VIVID    | "audio/av3a" | AUDIO AV3A. |


## ResolutionLevel<sup>19+</sup>

Enumerates the resolution levels supported by the device.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name                       | Value  | Description          |
| --------------------------  | ---- | ------------ |
| RESOLUTION_480P             | 0    | 480p (640 x 480 dpi).    |
| RESOLUTION_720P             | 1    | 720p (1280 x 720 dpi).   |
| RESOLUTION_1080P            | 2    | 1080p (1920 x 1080 dpi).  |
| RESOLUTION_2K               | 3    | 2K (2560 x 1440 dpi).  |
| RESOLUTION_4K               | 4    | 4K (4096 x 3840 dpi).  |

## AVCastCategory<sup>10+</sup>

Enumerates the cast categories.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| CATEGORY_LOCAL      | 0    | Local playback. The sound is played from the local device or a connected Bluetooth headset by default.    |
| CATEGORY_REMOTE      | 1    | Remote playback. The sound or images are played from a remote device. |

## DeviceType<sup>10+</sup>

Enumerates the output device types.

**Atomic service API**: This API can be used in atomic services since API version 12.

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| DEVICE_TYPE_LOCAL      | 0    | Local device.<br> **System capability**: SystemCapability.Multimedia.AVSession.Core|
| DEVICE_TYPE_BLUETOOTH      | 10   | Bluetooth device.<br> **System capability**: SystemCapability.Multimedia.AVSession.Core|
| DEVICE_TYPE_TV      | 2    | TV.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| DEVICE_TYPE_SMART_SPEAKER      | 3   | Speaker.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast|

## DeviceInfo<sup>10+</sup>

Describes the information related to the output device.

| Name      | Type          | Mandatory| Description                  |
| ---------- | -------------- | ---- | ---------------------- |
| castCategory   | AVCastCategory        | Yes  | Cast category.<br> **System capability**: SystemCapability.Multimedia.AVSession.Core<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| deviceId   | string | Yes  | ID of the output device.<br> **System capability**: SystemCapability.Multimedia.AVSession.Core<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| deviceName | string | Yes  | Name of the output device.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| deviceType | DeviceType | Yes  | Type of the output device.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| supportedProtocols<sup>11+</sup> | number | No  | Protocol supported by the output device. The default value is **TYPE_LOCAL**. For details, see [ProtocolType](#protocoltype11).<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| supportedDrmCapabilities<sup>12+</sup> | Array\<string> | No  | DRM capability supported by the output device.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| manufacturer<sup>13+</sup> | string | No  | Manufacturer of the output device.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| modelName<sup>13+</sup> | string | No  | Model name of the output device.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast<br>**Atomic service API**: This API can be used in atomic services since API version 13.|
| audioCapabilities<sup>20+</sup> | [AudioCapabilities](#audiocapabilities20) | No  | Audio capabilities supported by the output device.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast|

## OutputDeviceInfo<sup>10+</sup>

Describes the information related to the output device.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name      | Type          | Mandatory| Description                  |
| ---------- | -------------- | ---- | ---------------------- |
| devices | Array\<DeviceInfo\> | Yes  | Output devices.   |

## LoopMode<sup>10+</sup>

Enumerates the loop modes of media playback.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name              | Value  | Description    |
| ------------------ | ---- | -------- |
| LOOP_MODE_SEQUENCE | 0    | Sequential playback.|
| LOOP_MODE_SINGLE   | 1    | Single loop.|
| LOOP_MODE_LIST     | 2    | Playlist loop.|
| LOOP_MODE_SHUFFLE  | 3    | Shuffle.|
| LOOP_MODE_CUSTOM<sup>11+</sup>   | 4    | Custom playback. |

## PlaybackState<sup>10+</sup>

Enumerates the media playback states.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| PLAYBACK_STATE_INITIAL      | 0    | Initial.    |
| PLAYBACK_STATE_PREPARE      | 1    | Preparing. |
| PLAYBACK_STATE_PLAY         | 2    | Playing.    |
| PLAYBACK_STATE_PAUSE        | 3    | Paused.        |
| PLAYBACK_STATE_FAST_FORWARD | 4    | Fast-forwarding.        |
| PLAYBACK_STATE_REWIND       | 5    | Rewinding.        |
| PLAYBACK_STATE_STOP         | 6    | Stopped.        |
| PLAYBACK_STATE_COMPLETED    | 7    | Playback complete.    |
| PLAYBACK_STATE_RELEASED     | 8    | Released.        |
| PLAYBACK_STATE_ERROR        | 9    | Error.        |
| PLAYBACK_STATE_IDLE<sup>11+</sup>        | 10    | Idle.    |
| PLAYBACK_STATE_BUFFERING<sup>11+</sup>         | 11    | Buffering.  |

## AVSessionController<sup>10+</sup>

Through the AV session controller, you can query the session ID, send commands and events to a session, and obtain session metadata and playback state information.

### Properties

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name     | Type  | Read-Only| Optional| Description                                   |
| :-------- | :----- | :--- | :--- | :-------------------------------------- |
| sessionId | string | Yes  | No  | Unique session ID of the AVSessionController object.|


**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let AVSessionController: avSession.AVSessionController;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  AVSessionController = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
}).catch((err: BusinessError) => {
  console.error(`CreateController BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getAVPlaybackState<sup>10+</sup>

getAVPlaybackState(callback: AsyncCallback\<AVPlaybackState>): void

Obtains the remote playback state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                                                       | Mandatory| Description                                                        |
| --------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback  | AsyncCallback<[AVPlaybackState](#avplaybackstate10)\> | Yes  | Callback used to return the remote playback state.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVPlaybackState((err: BusinessError, state: avSession.AVPlaybackState) => {
  if (err) {
    console.error(`getAVPlaybackState BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('getAVPlaybackState : SUCCESS');
  }
});
```

### getAVPlaybackState<sup>10+</sup>

getAVPlaybackState(): Promise\<AVPlaybackState>

Obtains the remote playback state. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise<[AVPlaybackState](#avplaybackstate10)\>  | Promise used to return the remote playback state. |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVPlaybackState().then((state: avSession.AVPlaybackState) => {
  console.info('getAVPlaybackState : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`getAVPlaybackState BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getAVMetadata<sup>10+</sup>

getAVMetadata(): Promise\<AVMetadata>

Obtains the session metadata. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| Promise<[AVMetadata](#avmetadata10)\> | Promise used to return the metadata obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVMetadata().then((metadata: avSession.AVMetadata) => {
  console.info(`GetAVMetadata : SUCCESS : assetId : ${metadata.assetId}`);
}).catch((err: BusinessError) => {
  console.error(`GetAVMetadata BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getAVMetadata<sup>10+</sup>

getAVMetadata(callback: AsyncCallback\<AVMetadata>): void

Obtains the session metadata. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                      |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[AVMetadata](#avmetadata10)\> | Yes  | Callback used to return the metadata obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVMetadata((err: BusinessError, metadata: avSession.AVMetadata) => {
  if (err) {
    console.error(`GetAVMetadata BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`GetAVMetadata : SUCCESS : assetId : ${metadata.assetId}`);
  }
});
```

### getAVQueueTitle<sup>10+</sup>

getAVQueueTitle(): Promise\<string>

Obtains the name of the playlist. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type            | Description                          |
| ---------------- | ----------------------------- |
| Promise<string\> | Promise used to return the playlist name.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVQueueTitle().then((title: string) => {
  console.info(`GetAVQueueTitle : SUCCESS : title : ${title}`);
}).catch((err: BusinessError) => {
  console.error(`GetAVQueueTitle BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getAVQueueTitle<sup>10+</sup>

getAVQueueTitle(callback: AsyncCallback\<string>): void

Obtains the name of the playlist. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                     |
| -------- | ---------------------- | ---- | ------------------------- |
| callback | AsyncCallback<string\> | Yes  | Callback used to return the playlist name.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVQueueTitle((err: BusinessError, title: string) => {
  if (err) {
    console.error(`GetAVQueueTitle BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`GetAVQueueTitle : SUCCESS : title : ${title}`);
  }
});
```

### getAVQueueItems<sup>10+</sup>

getAVQueueItems(): Promise\<Array\<AVQueueItem>>

Obtains the information related to the items in the queue. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                         | Description                          |
| --------------------------------------------- | ----------------------------- |
| Promise<Array<[AVQueueItem](#avqueueitem10)\>\> | Promise used to return the items in the queue.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVQueueItems().then((items: avSession.AVQueueItem[]) => {
  console.info(`GetAVQueueItems : SUCCESS : length : ${items.length}`);
}).catch((err: BusinessError) => {
  console.error(`GetAVQueueItems BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getAVQueueItems<sup>10+</sup>

getAVQueueItems(callback: AsyncCallback\<Array\<AVQueueItem>>): void

Obtains the information related to the items in the playlist. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                | Mandatory| Description                     |
| -------- | --------------------------------------------------- | ---- | ------------------------- |
| callback | AsyncCallback<Array<[AVQueueItem](#avqueueitem10)\>\> | Yes  | Callback used to return the items in the playlist.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVQueueItems((err: BusinessError, items: avSession.AVQueueItem[]) => {
  if (err) {
    console.error(`GetAVQueueItems BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`GetAVQueueItems : SUCCESS : length : ${items.length}`);
  }
});
```

### skipToQueueItem<sup>10+</sup>

skipToQueueItem(itemId: number): Promise\<void>

Sends the ID of an item in the playlist to the session for processing. The session can play the song. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name | Type   | Mandatory| Description                                       |
| ------ | ------- | ---- | ------------------------------------------- |
| itemId | number  | Yes  | ID of an item in the playlist.|

**Return value**

| Type          | Description                                                            |
| -------------- | --------------------------------------------------------------- |
| Promise\<void> | Promise used to return the result. If the item ID is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let queueItemId = 0;
avsessionController.skipToQueueItem(queueItemId).then(() => {
  console.info('SkipToQueueItem successfully');
}).catch((err: BusinessError) => {
  console.error(`SkipToQueueItem BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### skipToQueueItem<sup>10+</sup>

skipToQueueItem(itemId: number, callback: AsyncCallback\<void>): void

Sends the ID of an item in the playlist to the session for processing. The session can play the song. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                 | Mandatory| Description                                                       |
| -------- | --------------------- | ---- | ----------------------------------------------------------- |
| itemId   | number                | Yes  | ID of an item in the playlist.               |
| callback | AsyncCallback\<void>  | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let queueItemId = 0;
avsessionController.skipToQueueItem(queueItemId, (err: BusinessError) => {
  if (err) {
    console.error(`SkipToQueueItem BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('SkipToQueueItem successfully');
  }
});
```

### getOutputDevice<sup>10+</sup>

getOutputDevice(): Promise\<OutputDeviceInfo>

Obtains the output device information. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                           | Description                             |
| ----------------------------------------------- | --------------------------------- |
| Promise<[OutputDeviceInfo](#outputdeviceinfo10)\> | Promise used to return the information obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getOutputDevice().then((deviceInfo: avSession.OutputDeviceInfo) => {
  console.info('GetOutputDevice : SUCCESS');
}).catch((err: BusinessError) => {
  console.error(`GetOutputDevice BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getOutputDevice<sup>10+</sup>

getOutputDevice(callback: AsyncCallback\<OutputDeviceInfo>): void

Obtains the output device information. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                 | Mandatory| Description                          |
| -------- | ----------------------------------------------------- | ---- | ------------------------------ |
| callback | AsyncCallback<[OutputDeviceInfo](#outputdeviceinfo10)\> | Yes  | Callback used to return the information obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getOutputDevice((err: BusinessError, deviceInfo: avSession.OutputDeviceInfo) => {
  if (err) {
    console.error(`GetOutputDevice BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('GetOutputDevice : SUCCESS');
  }
});
```

### sendAVKeyEvent<sup>10+</sup>

sendAVKeyEvent(event: KeyEvent): Promise\<void>

Sends a key event to the session corresponding to this controller. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name| Type                                                        | Mandatory| Description      |
| ------ | ------------------------------------------------------------ | ---- | ---------- |
| event  | [KeyEvent](../apis-input-kit/js-apis-keyevent.md) | Yes  | Key event.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 600102  | The session does not exist. |
| 600103  | The session controller does not exist. |
| 600105  | Invalid session command. |
| 600106  | The session is not activated. |

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the event is sent, no value is returned; otherwise, an error object is returned.|

**Example**

```ts
import { Key, KeyEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyItem: Key = {code:0x49, pressedTime:2, deviceId:0};
let event:KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};


avsessionController.sendAVKeyEvent(event).then(() => {
  console.info('SendAVKeyEvent Successfully');
}).catch((err: BusinessError) => {
  console.error(`SendAVKeyEvent BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### sendAVKeyEvent<sup>10+</sup>

sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback\<void>): void

Sends a key event to the session corresponding to this controller. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description      |
| -------- | ------------------------------------------------------------ | ---- | ---------- |
| event    | [KeyEvent](../apis-input-kit/js-apis-keyevent.md) | Yes  | Key event.|
| callback | AsyncCallback\<void>                                         | Yes  | Callback used to return the result. If the event is sent, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 600102  | The session does not exist. |
| 600103  | The session controller does not exist. |
| 600105  | Invalid session command. |
| 600106  | The session is not activated. |

**Example**

```ts
import { Key, KeyEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyItem: Key = {code:0x49, pressedTime:2, deviceId:0};
let event:KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};
avsessionController.sendAVKeyEvent(event, (err: BusinessError) => {
  if (err) {
    console.error(`SendAVKeyEvent BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('SendAVKeyEvent Successfully');
  }
});
```

### getLaunchAbility<sup>10+</sup>

getLaunchAbility(): Promise\<WantAgent>

Obtains the WantAgent object saved by the application in the session. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                                   | Description                                                        |
| ------------------------------------------------------- | ------------------------------------------------------------ |
| Promise<[WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md)\> | Promise used to return the object saved by calling [setLaunchAbility](#setlaunchability10). The object includes the application property, such as the bundle name, ability name, and device ID.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getLaunchAbility().then((agent: object) => {
  console.info(`GetLaunchAbility : SUCCESS : wantAgent : ${agent}`);
}).catch((err: BusinessError) => {
  console.error(`GetLaunchAbility BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getLaunchAbility<sup>10+</sup>

getLaunchAbility(callback: AsyncCallback\<WantAgent>): void

Obtains the WantAgent object saved by the application in the session. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<[WantAgent](../apis-ability-kit/js-apis-app-ability-wantAgent.md)\> | Yes  | Callback used to return the object saved by calling [setLaunchAbility](#setlaunchability10). The object includes the application property, such as the bundle name, ability name, and device ID.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getLaunchAbility((err: BusinessError, agent: object) => {
  if (err) {
    console.error(`GetLaunchAbility BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`GetLaunchAbility : SUCCESS : wantAgent : ${agent}`);
  }
});
```

### getRealPlaybackPositionSync<sup>10+</sup>

getRealPlaybackPositionSync(): number

Obtains the playback position.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| number | Playback position, in milliseconds.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
let time: number = avsessionController.getRealPlaybackPositionSync();
```

### isActive<sup>10+</sup>

isActive(): Promise\<boolean>

Checks whether the session is activated. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type             | Description                                                        |
| ----------------- | ------------------------------------------------------------ |
| Promise<boolean\> | Promise used to return the activation state. If the session is activated, **true** is returned; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.isActive().then((isActive: boolean) => {
  console.info(`IsActive : SUCCESS : isactive : ${isActive}`);
}).catch((err: BusinessError) => {
  console.error(`IsActive BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### isActive<sup>10+</sup>

isActive(callback: AsyncCallback\<boolean>): void

Checks whether the session is activated. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback<boolean\> | Yes  | Callback used to return the activation state. If the session is activated, **true** is returned; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.isActive((err: BusinessError, isActive: boolean) => {
  if (err) {
    console.error(`IsActive BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`IsActive : SUCCESS : isactive : ${isActive}`);
  }
});
```

### destroy<sup>10+</sup>

destroy(): Promise\<void>

Destroys this controller. A controller can no longer be used after being destroyed. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the controller is destroyed, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.destroy().then(() => {
  console.info('Destroy : SUCCESS ');
}).catch((err: BusinessError) => {
  console.error(`Destroy BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### destroy<sup>10+</sup>

destroy(callback: AsyncCallback\<void>): void

Destroys this controller. A controller can no longer be used after being destroyed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                | Mandatory| Description      |
| -------- | -------------------- | ---- | ---------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the controller is destroyed, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.destroy((err: BusinessError) => {
  if (err) {
    console.error(`Destroy BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Destroy : SUCCESS ');
  }
});
```

### getValidCommands<sup>10+</sup>

getValidCommands(): Promise\<Array\<AVControlCommandType>>

Obtains valid commands supported by the session. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                                        | Description                             |
| ------------------------------------------------------------ | --------------------------------- |
| Promise<Array<[AVControlCommandType](#avcontrolcommandtype10)\>\> | Promise used to return a set of valid commands.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getValidCommands().then((validCommands: avSession.AVControlCommandType[]) => {
  console.info(`GetValidCommands : SUCCESS : size : ${validCommands.length}`);
}).catch((err: BusinessError) => {
  console.error(`GetValidCommands BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getValidCommands<sup>10+</sup>

getValidCommands(callback: AsyncCallback\<Array\<AVControlCommandType>>): void

Obtains valid commands supported by the session. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                          |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| callback | AsyncCallback\<Array\<[AVControlCommandType](#avcontrolcommandtype10)\>\> | Yes  | Callback used to return a set of valid commands.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getValidCommands((err: BusinessError, validCommands: avSession.AVControlCommandType[]) => {
  if (err) {
    console.error(`GetValidCommands BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`GetValidCommands : SUCCESS : size : ${validCommands.length}`);
  }
});
```

### sendControlCommand<sup>10+</sup>

sendControlCommand(command: AVControlCommand): Promise\<void>

Sends a control command to the session through the controller. This API uses a promise to return the result.

> **NOTE**
>
> Before using **sendControlCommand**, the controller must ensure that the corresponding listeners are registered for the media session. For details about how to register the listeners, see [on'play'](#onplay10), [on'pause'](#onpause10), and the like.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| command | [AVControlCommand](#avcontrolcommand10) | Yes  | Command to send.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |
| 6600106  | The session is not activated. |
| 6600107  | Too many commands or events.Controls the frequency of sending self-query and control commands. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avCommand: avSession.AVControlCommand = {command:'play'};
avsessionController.sendControlCommand(avCommand).then(() => {
  console.info('SendControlCommand successfully');
}).catch((err: BusinessError) => {
  console.error(`SendControlCommand BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### sendControlCommand<sup>10+</sup>

sendControlCommand(command: AVControlCommand, callback: AsyncCallback\<void>): void

Sends a control command to the session through the controller. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> Before using **sendControlCommand**, the controller must ensure that the corresponding listeners are registered for the media session. For details about how to register the listeners, see [on'play'](#onplay10), [on'pause'](#onpause10), and the like.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                 | Mandatory| Description                          |
| -------- | ------------------------------------- | ---- | ------------------------------ |
| command  | [AVControlCommand](#avcontrolcommand10) | Yes  | Command to send.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.                    |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist.     |
| 6600103  | The session controller does not exist.   |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |
| 6600106  | The session is not activated.                |
| 6600107  | Too many commands or events.Controls the frequency of sending self-query and control commands. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let avCommand: avSession.AVControlCommand = {command:'play'};
avsessionController.sendControlCommand(avCommand, (err: BusinessError) => {
  if (err) {
    console.error(`SendControlCommand BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('SendControlCommand successfully');
  }
});
```

### sendCommonCommand<sup>10+</sup>

sendCommonCommand(command: string, args: {[key: string]: Object}): Promise\<void>

Sends a custom control command to the session through the controller. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| command | string | Yes  | Name of the custom control command.|
| args | {[key: string]: Object} | Yes  | Parameters in key-value pair format carried in the custom control command.|

> **NOTE**
>
> The **args** parameter supports the following data types: string, number, Boolean, object, array, and file descriptor. For details, see [@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md).

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |
| 6600106  | The session is not activated. |
| 6600107  | Too many commands or events.Controls the frequency of sending self-query and control commands. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
}).catch((err: BusinessError) => {
  console.error('CreateAVSession BusinessError:code: ${err.code}, message: ${err.message}')
});
let commandName = "my_command";
if (controller !== undefined) {
  (controller as avSession.AVSessionController).sendCommonCommand(commandName, {command : "This is my command"}).then(() => {
    console.info('SendCommonCommand successfully');
  }).catch((err: BusinessError) => {
    console.error(`SendCommonCommand BusinessError: code: ${err.code}, message: ${err.message}`);
  })
}
```

### sendCommonCommand<sup>10+</sup>

sendCommonCommand(command: string, args: {[key: string]: Object}, callback: AsyncCallback\<void>): void

Sends a custom control command to the session through the controller. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| command | string | Yes  | Name of the custom control command.|
| args | {[key: string]: Object} | Yes  | Parameters in key-value pair format carried in the custom control command.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.                    |

> **NOTE**
> The **args** parameter supports the following data types: string, number, Boolean, object, array, and file descriptor. For details, see [@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md).

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed.|
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist.     |
| 6600103  | The session controller does not exist.   |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |
| 6600106  | The session is not activated.                |
| 6600107  | Too many commands or events.Controls the frequency of sending self-query and control commands. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
          
let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
}).catch((err: BusinessError) => {
  console.error('CreateAVSession BusinessError:code: ${err.code}, message: ${err.message}')
});
let commandName = "my_command";
if (controller !== undefined) {
  (controller as avSession.AVSessionController).sendCommonCommand(commandName, {command : "This is my command"}, (err: BusinessError) => {
    if (err) {
      console.error(`SendCommonCommand BusinessError: code: ${err.code}, message: ${err.message}`);
    }
  })
}
```

### getExtras<sup>10+</sup>

getExtras(): Promise\<{[key: string]: Object}>

Obtains the custom media packet set by the provider. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| Promise<{[key: string]: Object}\>   | Promise used to return the custom media packet. The content of the packet is the same as that set in **setExtras**.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |
| 6600107  | Too many commands or events.Controls the frequency of sending self-query and control commands. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
         
let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
}).catch((err: BusinessError) => {
  console.error('CreateAVSession BusinessError:code: ${err.code}, message: ${err.message}')
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).getExtras().then((extras) => {
    console.info(`getExtras : SUCCESS : ${extras}`);
  }).catch((err: BusinessError) => {
    console.error(`getExtras BusinessError: code: ${err.code}, message: ${err.message}`);
  });
}
    
```

### getExtras<sup>10+</sup>

getExtras(callback: AsyncCallback\<{[key: string]: Object}>): void

Obtains the custom media packet set by the provider. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                      |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<{[key: string]: Object}\> | Yes  | Callback used to return the custom media packet. The content of the packet is the same as that set in **setExtras**.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |
| 6600107  |Too many commands or events.Controls the frequency of sending self-query and control commands. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
}).catch((err: BusinessError) => {
  console.error('CreateAVSession BusinessError:code: ${err.code}, message: ${err.message}')
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).getExtras((err, extras) => {
    if (err) {
      console.error(`getExtras BusinessError: code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`getExtras : SUCCESS : ${extras}`);
    }
  });
}
```

### getExtrasWithEvent<sup>18+</sup>

getExtrasWithEvent(extraEvent: string): Promise\<ExtraInfo>

Obtains the custom media packet set by the remote distributed media provider based on the remote distributed event type. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                      |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| extraEvent | string | Yes| Remote distributed event type.<br>Currently, the following event types are supported:<br>**'AUDIO_GET_VOLUME'**: obtains the volume of the remote device.<br>**'AUDIO_GET_AVAILABLE_DEVICES'**: obtains all remote devices that can be connected.<br>**'AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO'**: obtains the actual remote audio device.|

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| Promise<[ExtraInfo](#extrainfo18)\>   | Promise used to return the custom media packet set by the remote distributed media provider.<br>The **ExtraInfo** parameter supports the following data types: string, number, Boolean, object, array, and file descriptor. For details, see [@ohos.app.ability.Want(Want)](../apis-ability-kit/js-apis-app-ability-want.md).|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |
| 6600105  | Invalid session command.Stop sending the command or event,sending commands supported by the controlled end. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let controller: avSession.AVSessionController | ESObject;
const COMMON_COMMAND_STRING_1 = 'AUDIO_GET_VOLUME';
const COMMON_COMMAND_STRING_2 = 'AUDIO_GET_AVAILABLE_DEVICES';
const COMMON_COMMAND_STRING_3 = 'AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO';
if (controller !== undefined) {
  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_1).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_1]}`);
  }).catch((err: BusinessError) => {
    console.error(`getExtrasWithEvent failed with err: ${err.code}, ${err.message}`);
  })

  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_2).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_2]}`);
  }).catch((err: BusinessError) => {
    console.error(`getExtrasWithEvent failed with err: ${err.code}, ${err.message}`);
  })

  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_3).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_3]}`);
  }).catch((err: BusinessError) => {
    console.error(`getExtrasWithEvent failed with err: ${err.code}, ${err.message}`);
  })
}
```

### on('metadataChange')<sup>10+</sup>

on(type: 'metadataChange', filter: Array\<keyof AVMetadata> | 'all', callback: (data: AVMetadata) => void)

Subscribes to metadata change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'metadataChange'** is triggered when the session metadata changes.|
| filter   | Array\<keyof&nbsp;[AVMetadata](#avmetadata10)\>&nbsp;&#124;&nbsp;'all' | Yes  | The value **'all'** indicates that any metadata field change will trigger the event, and **Array<keyof&nbsp;[AVMetadata](#avmetadata10)\>** indicates that only changes to the listed metadata field will trigger the event.|
| callback | (data: [AVMetadata](#avmetadata10)) => void                    | Yes  | Callback used for subscription. The **data** parameter in the callback indicates the changed metadata.                        |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('metadataChange', 'all', (metadata: avSession.AVMetadata) => {
  console.info(`on metadataChange assetId : ${metadata.assetId}`);
});

avsessionController.on('metadataChange', ['assetId', 'title', 'description'], (metadata: avSession.AVMetadata) => {
  console.info(`on metadataChange assetId : ${metadata.assetId}`);
});

```

### off('metadataChange')<sup>10+</sup>

off(type: 'metadataChange', callback?: (data: AVMetadata) => void)

Unsubscribes from metadata change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                              | Mandatory| Description                                                   |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------ |
| type     | string                                           | Yes  | Event type, which is **'metadataChange'** in this case.        |
| callback | (data: [AVMetadata](#avmetadata10)) => void        | No  | Callback used for subscription. The **data** parameter in the callback indicates the changed metadata.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                        |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('metadataChange');
```

### on('playbackStateChange')<sup>10+</sup>

on(type: 'playbackStateChange', filter: Array\<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void)

Subscribes to playback state change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type      | Mandatory| Description     |
| --------| -----------|-----|------------|
| type     | string    | Yes  | Event type. The event **'playbackStateChange'** is triggered when the playback state changes.|
| filter   | Array\<keyof&nbsp;[AVPlaybackState](#avplaybackstate10)\>&nbsp;&#124;&nbsp;'all' | Yes  | The value **'all'** indicates that any playback state field change will trigger the event, and **Array<keyof&nbsp;[AVPlaybackState](#avplaybackstate10)\>** indicates that only changes to the listed playback state field will trigger the event.|
| callback | (state: [AVPlaybackState](#avplaybackstate10)) => void       | Yes  | Callback used for subscription. The **state** parameter in the callback indicates the changed playback state.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('playbackStateChange', 'all', (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});

avsessionController.on('playbackStateChange', ['state', 'speed', 'loopMode'], (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});
```

### off('playbackStateChange')<sup>10+</sup>

off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void)

Unsubscribes from playback state change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'playbackStateChange'** in this case.   |
| callback | (state: [AVPlaybackState](#avplaybackstate10)) => void         | No  | Callback function, where the **state** parameter indicates the new playback state.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('playbackStateChange');
```

### on('callMetadataChange')<sup>11+</sup>

on(type: 'callMetadataChange', filter: Array\<keyof CallMetadata> | 'all', callback: Callback\<CallMetadata>): void

Subscribes to call metadata change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type      | Mandatory| Description     |
| --------| -----------|-----|------------|
| type     | string    | Yes  | Event type. The event **'callMetadataChange'** is triggered when the call metadata changes.|
| filter   | Array\<keyof&nbsp;[CallMetadata](#callmetadata11)\>&nbsp;&#124;&nbsp;'all' | Yes  | The value **'all'** indicates that any call metadata field change will trigger the event, and **Array<keyof&nbsp;[CallMetadata](#callmetadata11)\>** indicates that only changes to the listed metadata field will trigger the event.|
| callback | Callback<[CallMetadata](#callmetadata11)\>   | Yes  | Callback used for subscription. The **callmetadata** parameter in the callback indicates the changed call metadata.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('callMetadataChange', 'all', (callmetadata: avSession.CallMetadata) => {
  console.info(`on callMetadataChange state : ${callmetadata.name}`);
});

avsessionController.on('callMetadataChange', ['name'], (callmetadata: avSession.CallMetadata) => {
  console.info(`on callMetadataChange state : ${callmetadata.name}`);
});
```

### off('callMetadataChange')<sup>11+</sup>

off(type: 'callMetadataChange', callback?: Callback\<CallMetadata>): void

Unsubscribes from call metadata change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'callMetadataChange'** in this case.   |
| callback | Callback<[CallMetadata](#callmetadata11)\>       | No  | Callback used for unsubscription. The **calldata** parameter in the callback indicates the changed call metadata.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('callMetadataChange');
```

### on('callStateChange')<sup>11+</sup>

on(type: 'callStateChange', filter: Array\<keyof AVCallState> | 'all', callback: Callback\<AVCallState>): void

Subscribes to call state change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type      | Mandatory| Description     |
| --------| -----------|-----|------------|
| type     | string    | Yes  | Event type. The event **'callStateChange'** is triggered when the call state changes.|
| filter   | Array<keyof&nbsp;[AVCallState](#avcallstate11)\>&nbsp;&#124;&nbsp;'all' | Yes  | The value **'all'** indicates that any call state field change will trigger the event, and **Array<keyof&nbsp;[AVCallState](#avcallstate11)\>** indicates that only changes to the listed call state field will trigger the event.|
| callback | Callback<[AVCallState](#avcallstate11)\>       | Yes  | Callback function, where the **callstate** parameter indicates the new call state.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('callStateChange', 'all', (callstate: avSession.AVCallState) => {
  console.info(`on callStateChange state : ${callstate.state}`);
});

avsessionController.on('callStateChange', ['state'], (callstate: avSession.AVCallState) => {
  console.info(`on callStateChange state : ${callstate.state}`);
});
```

### off('callStateChange')<sup>11+</sup>

off(type: 'callStateChange', callback?: Callback\<AVCallState>): void

Unsubscribes from call state change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'callStateChange'** in this case.   |
| callback | Callback<[AVCallState](#avcallstate11)\>           | No  | Callback function, where the **callstate** parameter indicates the new call metadata.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('callMetadataChange');
```

### on('sessionDestroy')<sup>10+</sup>

on(type: 'sessionDestroy', callback: () => void)

Subscribes to session destruction events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type      | Mandatory| Description                                                        |
| -------- | ---------- | ---- | ------------------------------------------------------------ |
| type     | string     | Yes  | Event type. The event **'sessionDestroy'** is triggered when a session is destroyed.|
| callback | () => void | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.                 |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('sessionDestroy', () => {
  console.info('on sessionDestroy : SUCCESS ');
});
```

### off('sessionDestroy')<sup>10+</sup>

off(type: 'sessionDestroy', callback?: () => void)

Unsubscribes from session destruction events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type      | Mandatory| Description                                                     |
| -------- | ---------- | ---- | ----------------------------------------------------- |
| type     | string     | Yes  | Event type, which is **'sessionDestroy'** in this case.        |
| callback | () => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                                              |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('sessionDestroy');
```

### on('activeStateChange')<sup>10+</sup>

on(type: 'activeStateChange', callback: (isActive: boolean) => void)

Subscribes to session activation state change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                       | Mandatory| Description                                                        |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                      | Yes  | Event type. The event **'activeStateChange'** is triggered when the activation state of the session changes.|
| callback | (isActive: boolean) => void | Yes  | Callback used for subscription. The **isActive** parameter in the callback specifies whether the session is activated. The value **true** means that the service is activated, and **false** means the opposite.                  |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ----------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  |The session controller does not exist. |

**Example**

```ts
avsessionController.on('activeStateChange', (isActive: boolean) => {
  console.info(`on activeStateChange : SUCCESS : isActive ${isActive}`);
});
```

### off('activeStateChange')<sup>10+</sup>

off(type: 'activeStateChange', callback?: (isActive: boolean) => void)

Unsubscribes from session activation state change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                       | Mandatory| Description                                                     |
| -------- | --------------------------- | ---- | ----------------------------------------------------- |
| type     | string                      | Yes  | Event type, which is **'activeStateChange'** in this case.     |
| callback | (isActive: boolean) => void | No  | Callback used for unsubscription. The **isActive** parameter in the callback specifies whether the session is activated. The value **true** means that the session is activated, and **false** means the opposite.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                  |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('activeStateChange');
```

### on('validCommandChange')<sup>10+</sup>

on(type: 'validCommandChange', callback: (commands: Array\<AVControlCommandType>) => void)

Subscribes to valid command change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'validCommandChange'** is triggered when the valid commands supported by the session changes.|
| callback | (commands: Array<[AVControlCommandType](#avcontrolcommandtype10)\>) => void | Yes  | Callback used for subscription. The **commands** parameter in the callback is a set of valid commands.                    |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('validCommandChange', (validCommands: avSession.AVControlCommandType[]) => {
  console.info(`validCommandChange : SUCCESS : size : ${validCommands.length}`);
  console.info(`validCommandChange : SUCCESS : validCommands : ${validCommands.values()}`);
});
```

### off('validCommandChange')<sup>10+</sup>

off(type: 'validCommandChange', callback?: (commands: Array\<AVControlCommandType>) => void)

Unsubscribes from valid command change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'validCommandChange'** in this case.        |
| callback | (commands: Array<[AVControlCommandType](#avcontrolcommandtype10)\>) => void | No  | Callback used for unsubscription. The **commands** parameter in the callback is a set of valid commands.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.         |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message          |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('validCommandChange');
```

### on('outputDeviceChange')<sup>10+</sup>

on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void

Subscribes to output device change events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                  | Yes  | Event type. The event **'outputDeviceChange'** is triggered when the output device changes.|
| callback | (state: [ConnectionState](#connectionstate10), device: [OutputDeviceInfo](#outputdeviceinfo10)) => void | Yes  | Callback used for subscription. The **device** parameter in the callback indicates the output device information.                        |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ----------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('outputDeviceChange', (state: avSession.ConnectionState, device: avSession.OutputDeviceInfo) => {
  console.info(`on outputDeviceChange state: ${state}, device : ${device}`);
});
```

### off('outputDeviceChange')<sup>10+</sup>

off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void

Unsubscribes from output device change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                   | Mandatory| Description                                                     |
| -------- | ------------------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | string                                                  | Yes  | Event type, which is **'outputDeviceChange'** in this case.     |
| callback | (state: [ConnectionState](#connectionstate10), device: [OutputDeviceInfo](#outputdeviceinfo10)) => void | No  | Callback function, where the **device** parameter specifies the output device information.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                        |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID | Error Message         |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('outputDeviceChange');
```

### on('sessionEvent')<sup>10+</sup>

on(type: 'sessionEvent', callback: (sessionEvent: string, args: {[key: string]: Object}) => void): void

Subscribes to session event change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'sessionEvent'** is triggered when the session event changes.|
| callback | (sessionEvent: string, args: {[key: string]: Object}) => void         | Yes  | Callback used for subscription. **sessionEvent** in the callback indicates the name of the session event that changes, and **args** indicates the parameters carried in the event.         |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';
       
let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
}).catch((err: BusinessError) => {
  console.error('CreateAVSession BusinessError:code: ${err.code}, message: ${err.message}')
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).on('sessionEvent', (sessionEvent, args) => {
    console.info(`OnSessionEvent, sessionEvent is ${sessionEvent}, args: ${JSON.stringify(args)}`);
  });
}
```

### off('sessionEvent')<sup>10+</sup>

off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {[key: string]: Object}) => void): void

Unsubscribes from session event change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'sessionEvent'** in this case.   |
| callback | (sessionEvent: string, args: {[key: string]: Object}) => void         | No  | Callback used for unsubscription. **sessionEvent** in the callback indicates the name of the session event that changes, and **args** indicates the parameters carried in the event.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                     |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('sessionEvent');
```

### on('queueItemsChange')<sup>10+</sup>

on(type: 'queueItemsChange', callback: (items: Array<[AVQueueItem](#avqueueitem10)\>) => void): void

Subscribes to playlist item change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                  | Mandatory| Description                                                                        |
| -------- | ----------------------------------------------------- | ---- | ---------------------------------------------------------------------------- |
| type     | string                                                | Yes  | Event type. The event **'queueItemsChange'** is triggered when one or more items in the playlist changes.|
| callback | (items: Array<[AVQueueItem](#avqueueitem10)\>) => void  | Yes  | Callback used for subscription. The **items** parameter in the callback indicates the changed items in the playlist.                           |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('queueItemsChange', (items: avSession.AVQueueItem[]) => {
  console.info(`OnQueueItemsChange, items length is ${items.length}`);
});
```

### off('queueItemsChange')<sup>10+</sup>

off(type: 'queueItemsChange', callback?: (items: Array<[AVQueueItem](#avqueueitem10)\>) => void): void

Unsubscribes from playback item change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                                                | Mandatory| Description                                                                                               |
| -------- | ---------------------------------------------------- | ---- | --------------------------------------------------------------------------------------------------- |
| type     | string                                               | Yes  | Event type, which is **'queueItemsChange'** in this case.                                                    |
| callback | (items: Array<[AVQueueItem](#avqueueitem10)\>) => void | No  | Callback used for unsubscription. The **items** parameter in the callback indicates the changed items in the playlist.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('queueItemsChange');
```

### on('queueTitleChange')<sup>10+</sup>

on(type: 'queueTitleChange', callback: (title: string) => void): void

Subscribes to playlist name change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                    | Mandatory| Description                                                                            |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------- |
| type     | string                  | Yes  | Event type. The event **'queueTitleChange'** is triggered when the playlist name changes.|
| callback | (title: string) => void | Yes  | Callback used for subscription. The **title** parameter in the callback indicates the changed playlist name.                               |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.on('queueTitleChange', (title: string) => {
  console.info(`queueTitleChange, title is ${title}`);
});
```

### off('queueTitleChange')<sup>10+</sup>

off(type: 'queueTitleChange', callback?: (title: string) => void): void

Unsubscribes from playlist name change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                   | Mandatory| Description                                                                                                   |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| type     | string                  | Yes  | Event type, which is **'queueTitleChange'** in this case.                                                        |
| callback | (title: string) => void | No  | Callback used for unsubscription. The **items** parameter in the callback indicates the changed playlist name.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('queueTitleChange');
```

### on('extrasChange')<sup>10+</sup>

on(type: 'extrasChange', callback: (extras: {[key:string]: Object}) => void): void

Subscribes to custom media packet change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'extrasChange'** is triggered when the provider sets a custom media packet.|
| callback | (extras: {[key:string]: Object}) => void         | Yes  | Callback used for subscription. The **extras** parameter in the callback indicates the custom media packet set by the provider. This packet is the same as that set in **dispatchSessionEvent**.         |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { avSession } from '@kit.AVSessionKit';

let tag: string = "createNewSession";
let sessionId: string = "";
let controller:avSession.AVSessionController | undefined = undefined;
avSession.createAVSession(context, tag, "audio").then(async (data:avSession.AVSession)=> {
  currentAVSession = data;
  sessionId = currentAVSession.sessionId;
  controller = await currentAVSession.getController();
  console.info('CreateAVSession : SUCCESS :sessionid = ${sessionid}');
}).catch((err: BusinessError) => {
  console.error('CreateAVSession BusinessError:code: ${err.code}, message: ${err.message}')
});
if (controller !== undefined) {
  (controller as avSession.AVSessionController).on('extrasChange', (extras) => {
    console.info(`Caught extrasChange event,the new extra is: ${JSON.stringify(extras)}`);
  });
}
```

### off('extrasChange')<sup>10+</sup>

off(type: 'extrasChange', callback?: (extras: {[key:string]: Object}) => void): void

Unsubscribes from custom media packet change events. This API is called by the controller.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name   | Type                   | Mandatory| Description                                                                                                   |
| -------- | ----------------------- | ---- | ------------------------------------------------------------------------------------------------------- |
| type     | string                  | Yes  | Event type, which is **'extrasChange'** in this case.                                                        |
| callback | (extras: {[key:string]: Object}) => void | No  | Callback used for unsubscription.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ----------------                       |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avsessionController.off('extrasChange');
```

### getAVPlaybackStateSync<sup>10+</sup>

getAVPlaybackStateSync(): AVPlaybackState;

Obtains the playback state of this session. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| [AVPlaybackState](#avplaybackstate10)  | Playback state of the session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let playbackState: avSession.AVPlaybackState = avsessionController.getAVPlaybackStateSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`getAVPlaybackStateSync error, error code: ${error.code}, error message: ${error.message}`);
}
```

### getAVMetadataSync<sup>10+</sup>

getAVMetadataSync(): AVMetadata

Obtains the session metadata. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| [AVMetadata](#avmetadata10) | Session metadata.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**
```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let metaData: avSession.AVMetadata = avsessionController.getAVMetadataSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`getAVMetadataSync error, error code: ${error.code}, error message: ${error.message}`);
}
```

### getAVCallState<sup>11+</sup>

getAVCallState(): Promise\<AVCallState>

Obtains the call state. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| Promise<[AVCallState](#avcallstate11)\> | Promise used to return the call state obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVCallState().then((callstate: avSession.AVCallState) => {
  console.info(`getAVCallState : SUCCESS : state : ${callstate.state}`);
}).catch((err: BusinessError) => {
  console.error(`getAVCallState BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getAVCallState<sup>11+</sup>

getAVCallState(callback: AsyncCallback\<AVCallState>): void

Obtains the call state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                      |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[AVCallState](#avcallstate11)\> | Yes  | Callback used to return the call state obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getAVCallState((err: BusinessError, callstate: avSession.AVCallState) => {
  if (err) {
    console.error(`getAVCallState BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`getAVCallState : SUCCESS : state : ${callstate.state}`);
  }
});
```

### getCallMetadata<sup>11+</sup>

getCallMetadata(): Promise\<CallMetadata>

Obtains the call metadata. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                               | Description                         |
| ----------------------------------- | ----------------------------- |
| Promise<[CallMetadata](#callmetadata11)\> | Promise used to return the metadata obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getCallMetadata().then((calldata: avSession.CallMetadata) => {
  console.info(`getCallMetadata : SUCCESS : name : ${calldata.name}`);
}).catch((err: BusinessError) => {
  console.error(`getCallMetadata BusinessError: code: ${err.code}, message: ${err.message}`);
});
```

### getCallMetadata<sup>11+</sup>

getCallMetadata(callback: AsyncCallback\<CallMetadata>): void

Obtains the call metadata. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                     | Mandatory| Description                      |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<[CallMetadata](#callmetadata11)\> | Yes  | Callback used to return the metadata obtained.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avsessionController.getCallMetadata((err: BusinessError, calldata: avSession.CallMetadata) => {
  if (err) {
    console.error(`getCallMetadata BusinessError: code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`getCallMetadata : SUCCESS : name : ${calldata.name}`);
  }
});
```

### getAVQueueTitleSync<sup>10+</sup>

getAVQueueTitleSync(): string

Obtains the name of the playlist of this session. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type            | Description                          |
| ---------------- | ----------------------------- |
| string | Playlist name.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let currentQueueTitle: string = avsessionController.getAVQueueTitleSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`getAVQueueTitleSync error, error code: ${error.code}, error message: ${error.message}`);
}
```

### getAVQueueItemsSync<sup>10+</sup>

getAVQueueItemsSync(): Array\<AVQueueItem\>

Obtains the information related to the items in the playlist of this session. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                         | Description                          |
| --------------------------------------------- | ----------------------------- |
| Array<[AVQueueItem](#avqueueitem10)\> | Items in the queue.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let currentQueueItems: Array<avSession.AVQueueItem> = avsessionController.getAVQueueItemsSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`getAVQueueItemsSync error, error code: ${error.code}, error message: ${error.message}`);
}
```

### getOutputDeviceSync<sup>10+</sup>

getOutputDeviceSync(): OutputDeviceInfo

Obtains the output device information. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                           | Description                             |
| ----------------------------------------------- | --------------------------------- |
| [OutputDeviceInfo](#outputdeviceinfo10) | Information about the output device.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let currentOutputDevice: avSession.OutputDeviceInfo = avsessionController.getOutputDeviceSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`getOutputDeviceSync error, error code: ${error.code}, error message: ${error.message}`);
}
```

### isActiveSync<sup>10+</sup>

isActiveSync(): boolean

Checks whether the session is activated. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type             | Description                                                        |
| ----------------- | ------------------------------------------------------------ |
| boolean | Returns **true** is returned if the session is activated; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let isActive: boolean = avsessionController.isActiveSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`isActiveSync error, error code: ${error.code}, error message: ${error.message}`);
}
```

### getValidCommandsSync<sup>10+</sup>

getValidCommandsSync(): Array\<AVControlCommandType\>

Obtains valid commands supported by the session. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                                                        | Description                             |
| ------------------------------------------------------------ | --------------------------------- |
| Array<[AVControlCommandType](#avcontrolcommandtype10)\> | A set of valid commands.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| 6600102  | The session does not exist. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let validCommands: Array<avSession.AVControlCommandType> = avsessionController.getValidCommandsSync();
} catch (err) {
  let error = err as BusinessError;
  console.error(`getValidCommandsSync error, error code: ${error.code}, error message: ${error.message}`);
}
```

## AVControlCommandType<sup>10+</sup>

type AVControlCommandType = 'play' | 'pause' | 'stop' | 'playNext' | 'playPrevious' | 'fastForward' | 'rewind' |
  'seek' | 'setSpeed' | 'setLoopMode' | 'setTargetLoopMode' | 'toggleFavorite' | 'playFromAssetId' | 'playWithAssetId' | 'answer' | 'hangUp' | 'toggleCallMute'

Defines the commands that can be sent to a session.

You can use the union of the strings listed in the following table.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Type            | Description        |
| ---------------- | ------------ |
| 'play'           | Play the media. No parameter is required.|
| 'pause'          | Pause the playback. No parameter is required.|
| 'stop'           | Stop the playback. No parameter is required.|
| 'playNext'       | Play the next media asset. No parameter is required.|
| 'playPrevious'   | Play the previous media asset. No parameter is required.|
| 'fastForward'    | Fast-forward. No parameter is required.|
| 'rewind'         | Rewind. No parameter is required.|
| 'seek'           | Seek to a playback position. The corresponding parameter is of the number type.|
| 'setSpeed'       | Set the playback speed. The corresponding parameter is of the number type.|
| 'setLoopMode'    | Set the loop mode. The corresponding parameter is [LoopMode](#loopmode10).|
| 'setTargetLoopMode' <sup>18+</sup>   | Set the target loop mode. The recommended parameter is [LoopMode](#loopmode10).|
| 'toggleFavorite' | Favorite the media asset. The corresponding parameter is [AVMetadata.assetId](#avmetadata10).    |
| 'playFromAssetId'| Play the media asset with the specified asset ID.|
| 'playWithAssetId' <sup>20+</sup>    | Play the media asset with the specified asset ID. The corresponding parameter is [AVMetadata.assetId](#avmetadata10).<br>The string length must be less than 40960 bytes.<br>|
|'answer'          | Answer a call. No parameter is required.       |
| 'hangUp'         | The call is disconnecting. No parameter is required.       |
|'toggleCallMute'  | Set the mute status for a call. No parameter is required.|

## AVControlCommand<sup>10+</sup>

Describes the command that can be sent to the session.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name     | Type                                             | Mandatory| Description          |
| --------- | ------------------------------------------------- | ---- | -------------- |
| command   | [AVControlCommandType](#avcontrolcommandtype10)     | Yes  | Command. The parameters carried in each command are different. For details, see [AVControlCommandType](#avcontrolcommandtype10).      |
| parameter | [LoopMode](#loopmode10) &#124; string &#124; number | No  | Parameters carried in the command.|


## AVCastPickerOptions<sup>14+</sup>

Describes the properties related to the semi-modal window that is started for casting purposes.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name           | Type                     | Mandatory| Description                                                                 |
| --------------- |-------------------------| ---- |---------------------------------------------------------------------|
| sessionType         | [AVSessionType](#avsessiontype10)  | No  | Session type. The default value is **'audio'**.<br>Currently, only the **'audio'** and **'video'** session types are supported. If **'voice_call'** and **'video_call'** are passed, they are treated as the default value **'audio'**.           |

## AVCastPickerHelper<sup>14+</sup>

Implements a semi-modal object used for casting. It displays a semi-modal window for users to select a target cast device. Before using the APIs of this class, you need to create an AVCastPickerHelper instance.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

### constructor<sup>14+</sup>

constructor(context: Context)

Creates an AVCastPickerHelper instance. For details about how to obtain the context, see [getContext](../apis-arkui/arkts-apis-uicontext-uicontext.md#gethostcontext12).

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                                       | Mandatory| Description                                                        |
| --------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| context  | Context | Yes  | Application context. (Only [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) is supported.)|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { avSession } from '@kit.AVSessionKit';
@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(40)
          .fontWeight(FontWeight.Bold)
          .onClick(()=>{
            let context = this.getUIContext().getHostContext() as Context;
            let avCastPicker = new avSession.AVCastPickerHelper(context);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### select<sup>14+</sup>

select(options?: AVCastPickerOptions): Promise\<void>

Starts the AVCastPicker dialog box, where users can select the target cast device. This API uses a promise to return the result. You can pass in **AVCastPickerOptions** to specify the properties for selection.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                                       | Mandatory| Description                                                        |
| --------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| options  | [AVCastPickerOptions](#avcastpickeroptions14) | No  | AVCastPicker selection options. If this parameter is not specified, the default value of **AVCastPickerOptions** is used.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function avCastPicker(context: common.Context) {
  let avCastPickerOptions : avSession.AVCastPickerOptions = {
    sessionType : 'video',
  }
  let avCastPicker = new avSession.AVCastPickerHelper(context);
  avCastPicker.select(avCastPickerOptions).then(() => {
    console.info('select successfully');
  }).catch((err: BusinessError) => {
    console.error(`AVCastPicker.select failed with err: ${err.code}, ${err.message}`);
  });
}
```
### on('pickerStateChange')<sup>14+</sup>

on(type: 'pickerStateChange', callback: Callback<AVCastPickerState\>) : void

Subscribes to semi-modal window change events.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type      | Mandatory| Description     |
| --------| -----------|-----|------------|
| type     | string    | Yes  | Event type. The event **'pickerStateChange'** is triggered when the semi-modal window changes.|
| callback | Callback\<[AVCastPickerState](js-apis-avCastPickerParam.md#avcastpickerstate11)>       | Yes  | Callback function, where the **state** parameter indicates the new state of the semi-modal window.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { common } from '@kit.AbilityKit';
import { AVCastPickerState } from '@kit.AVSessionKit';

async function onPickerStateChange(context: common.Context) {
  let avCastPicker = new avSession.AVCastPickerHelper(context);
  avCastPicker.on('pickerStateChange', (state: AVCastPickerState) => {
    console.info(`picker state change : ${state}`);
  });
}
```

### off('pickerStateChange')<sup>14+</sup>

off(type: 'pickerStateChange', callback?: Callback<AVCastPickerState\>) : void

Unsubscribes from semi-modal window change events. After the unsubscription, the event callback is not triggered.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                              | Mandatory| Description                                                   |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------ |
| type     | string                                           | Yes  | Event type, which is **'pickerStateChange'** in this case.        |
| callback | Callback\<[AVCastPickerState](js-apis-avCastPickerParam.md#avcastpickerstate11)> | No  | Callback function, where the **state** parameter indicates the new state of the semi-modal window.<br>If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                          |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
import { common } from '@kit.AbilityKit';

async function onPickerStateChange(context: common.Context) {
  let avCastPicker = new avSession.AVCastPickerHelper(context);
  avCastPicker.off('pickerStateChange');
}
```

## AVSessionErrorCode<sup>10+</sup>

Enumerates the error codes used in the media session.

| Name                                  | Value     | Description                            |
| -------------------------------------- | ------- | ------------------------------- |
| ERR_CODE_SERVICE_EXCEPTION             | 6600101 | The session server is abnormal.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_SESSION_NOT_EXIST             | 6600102 | The session does not exist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_CONTROLLER_NOT_EXIST          | 6600103 | The session controller does not exist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_REMOTE_CONNECTION_ERR         | 6600104 | Connection to the remote session fails.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_COMMAND_INVALID               | 6600105 | The session command is invalid.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_SESSION_INACTIVE              | 6600106 | The session is not activated.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_MESSAGE_OVERLOAD              | 6600107 | Too many commands or messages.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_DEVICE_CONNECTION_FAILED      | 6600108 | Connection to the device fails.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_REMOTE_CONNECTION_NOT_EXIST   | 6600109 | The remote session does not exist.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br>**System capability**: SystemCapability.Multimedia.AVSession.Core|
| ERR_CODE_CAST_CONTROL_UNSPECIFIED<sup>13+</sup>    | 6611000 | An undefined error occurs during cast control.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_REMOTE_ERROR<sup>13+</sup>    | 6611001 | An unknown error occurs in the remote player.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_BEHIND_LIVE_WINDOW<sup>13+</sup>     | 6611002 | The playback is delayed.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_TIMEOUT<sup>13+</sup>     | 6611003 | The cast control process times out.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_RUNTIME_CHECK_FAILED<sup>13+</sup>      | 6611004 | The runtime check fails.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_PLAYER_NOT_WORKING<sup>13+</sup>      | 6611100 | Cross-device data transfer is locked.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_SEEK_MODE_UNSUPPORTED<sup>13+</sup>      | 6611101 | The specified seek mode is not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_ILLEGAL_SEEK_TARGET<sup>13+</sup>      | 6611102 | The seek position is out of the media range, or the current seek mode is not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_PLAY_MODE_UNSUPPORTED<sup>13+</sup>      | 6611103 |  The specified playback mode is not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_PLAY_SPEED_UNSUPPORTED<sup>13+</sup>      | 6611104 | The specified playback speed is not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DEVICE_MISSING<sup>13+</sup>      | 6611105 | Operation failed because the media source device or media receiver device has been destroyed.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_INVALID_PARAM<sup>13+</sup>       | 6611106 | The parameter is invalid.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_NO_MEMORY<sup>13+</sup>       | 6611107 | Failed to allocate memory.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_OPERATION_NOT_ALLOWED<sup>13+</sup>       | 6611108 | The operation is not allowed.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_UNSPECIFIED<sup>13+</sup>       | 6612000 | An unspecified input/output error occurs.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_NETWORK_CONNECTION_FAILED<sup>13+</sup>       | 6612001 | Network connection fails.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_NETWORK_CONNECTION_TIMEOUT<sup>13+</sup>       | 6612002 | Network connection times out.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_INVALID_HTTP_CONTENT_TYPE <sup>13+</sup>      | 6612003 | The value of **Content-Type** is invalid.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_BAD_HTTP_STATUS<sup>13+</sup>        | 6612004 | The HTTP server returns an unexpected HTTP response status code.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_FILE_NOT_FOUND<sup>13+</sup>   | 6612005 | The file does not exist.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_NO_PERMISSION<sup>13+</sup>    | 6612006 | The input/output operation is not allowed.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_CLEARTEXT_NOT_PERMITTED<sup>13+</sup>    | 6612007 | The network security configuration of the application does not allow access to plaintext HTTP traffic.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_READ_POSITION_OUT_OF_RANGE<sup>13+</sup>        | 6612008 | Data is read from data binding.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_NO_CONTENTS<sup>13+</sup>     | 6612100 | No content can be played in the media.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_READ_ERROR<sup>13+</sup>        | 6612101 | The media cannot be read.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_CONTENT_BUSY<sup>13+</sup>         | 6612102 | The resource is in use.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_CONTENT_EXPIRED<sup>13+</sup>    | 6612103 | The input/output request content has expired.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_USE_FORBIDDEN<sup>13+</sup>    | 6612104 | The requested content cannot be played.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_NOT_VERIFIED<sup>13+</sup>     | 6612105 | The allowed content cannot be verified.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_EXHAUSTED_ALLOWED_USES<sup>13+</sup>     | 6612106 | The number of times that the content can be used has reached the maximum.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_IO_NETWORK_PACKET_SENDING_FAILED<sup>13+</sup>   | 6612107 | An error occurs when the source device sends data packets to the destination device.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_PARSING_UNSPECIFIED<sup>13+</sup>    | 6613000 | An unspecified content parsing error occurs.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_PARSING_CONTAINER_MALFORMED<sup>13+</sup>    | 6613001 | The format of the media container bit stream is incorrectly parsed.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_PARSING_MANIFEST_MALFORMED<sup>13+</sup>     | 6613002 | An error occurred when parsing the media list.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_PARSING_CONTAINER_UNSUPPORTED<sup>13+</sup>   | 6613003 | The media container format or feature of the file is not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_PARSING_MANIFEST_UNSUPPORTED<sup>13+</sup>      | 6613004 | The feature is not supported in the media list.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DECODING_UNSPECIFIED<sup>13+</sup>     | 6614000 | An unspecified decoding error occurs.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DECODING_INIT_FAILED<sup>13+</sup>   | 6614001 | Initializing the decoder fails.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DECODING_QUERY_FAILED<sup>13+</sup>     | 6614002 | Querying the decoder fails.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DECODING_FAILED<sup>13+</sup>     | 6614003 | Decoding the media sample fails.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DECODING_FORMAT_EXCEEDS_CAPABILITIES<sup>13+</sup>    | 6614004 | The device cannot decode the current format.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DECODING_FORMAT_UNSUPPORTED<sup>13+</sup>    | 6614005 | The decoding format is not supported.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_UNSPECIFIED<sup>13+</sup>       | 6615000 | An unspecified audio renderer error occurs.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_INIT_FAILED <sup>13+</sup>     | 6615001 | Initializing the audio renderer fails.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_AUDIO_RENDERER_WRITE_FAILED<sup>13+</sup>    | 6615002 | Writing data to the audio renderer fails.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_UNSPECIFIED<sup>13+</sup>      | 6616000 | An unspecified DRM-related error occurs.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_SCHEME_UNSUPPORTED<sup>13+</sup>  | 6616001 | The device does not support the selected DRM scheme.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_PROVISIONING_FAILED<sup>13+</sup>   | 6616002 | Device configurations fail.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_CONTENT_ERROR<sup>13+</sup>  | 6616003 | The DRM-protected content cannot be played.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_LICENSE_ACQUISITION_FAILED<sup>13+</sup>    | 6616004 | Obtaining a license fails.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_DISALLOWED_OPERATION<sup>13+</sup>     | 6616005 | The license policy does not allow this operation.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_SYSTEM_ERROR<sup>13+</sup>     | 6616006 | An error occurs in the DRM system.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_DEVICE_REVOKED<sup>13+</sup>     | 6616007 | The DRM permission has been revoked from the device.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_LICENSE_EXPIRED<sup>13+</sup>   | 6616008 | The DRM license that is being loaded has expired.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|
| ERR_CODE_CAST_CONTROL_DRM_PROVIDE_KEY_RESPONSE_ERROR<sup>13+</sup>    | 6616100 | An error occurs when the DRM processes the key response.<br>**Atomic service API**: This API can be used in atomic services since API version 13.<br>**System capability**: SystemCapability.Multimedia.AVSession.AVCast|

## SkipIntervals<sup>11+</sup>

Enumerates the fast-forward or rewind intervals supported by the media session.

**System capability**: SystemCapability.Multimedia.AVSession.Core

| Name                  | Value| Description                    |
| ---------------------- | -- | ----------------------- |
| SECONDS_10             | 10 | The time is 10 seconds.            |
| SECONDS_15             | 15 | The time is 15 seconds.            |
| SECONDS_30             | 30 | The time is 30 seconds.            |

## AudioCapabilities<sup>20+</sup>

Describes the audio capabilities supported by the casting device.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name           | Type                     | Read-Only| Optional| Description                                                                 |
| --------------- |-------------------------| ---- | ---- |---------------------------------------------------------------------|
| streamInfos            | Array\<[audio.AudioStreamInfo](../apis-audio-kit/arkts-apis-audio-i.md#audiostreaminfo8)>                  | Yes   | No   | Audio capability parameters. |
