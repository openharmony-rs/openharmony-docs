# Interface (AVCastController)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

After a casting connection is set up, you can call [avSession.getAVCastController](arkts-apis-avsession-AVSession.md#getavcastcontroller10) to obtain the cast controller. Through the controller, you can query the session ID, send commands and events to a session, and obtain session metadata and playback state information.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 10.

## Modules to Import

```ts
import { avSession } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';
```

## getAVPlaybackState<sup>10+</sup>

getAVPlaybackState(callback: AsyncCallback\<AVPlaybackState>): void

Obtains the remote playback state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                                       | Mandatory| Description                                                        |
| --------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback  | AsyncCallback<[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)\> | Yes  | Callback used to return the remote playback state.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.getAVPlaybackState((err: BusinessError, state: avSession.AVPlaybackState) => {
  if (err) {
    console.error(`Failed to get AV playback state: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting AV playback state.');
});
```

## getAVPlaybackState<sup>10+</sup>

getAVPlaybackState(): Promise\<AVPlaybackState>

Obtains the remote playback state. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise<[AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)\>  | Promise used to return the remote playback state.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.getAVPlaybackState().then((state: avSession.AVPlaybackState) => {
  console.info('Succeeded in getting AV playback state.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get AV playback state: ${err.message}`);
});
```

## getSupportedDecoders<sup>19+</sup>

getSupportedDecoders(): Promise\<Array\<DecoderType>>

Obtains the decoding modes supported by the current remote device. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise\<Array\<[DecoderType](arkts-apis-avsession-e.md#decodertype19)\>\> | Promise used to return an array of decoding modes supported by the remote device.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.getSupportedDecoders().then((decoderTypes: avSession.DecoderType[]) => {
  console.info(`Succeeded in getting supported decoders, length: ${decoderTypes.length}`);
  if (decoderTypes.length > 0 ) {
    console.info(`Succeeded in getting supported decoder: ${decoderTypes[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get supported decoders: ${err.message}`);
});
```

## getRecommendedResolutionLevel<sup>19+</sup>

getRecommendedResolutionLevel(decoderType: DecoderType): Promise\<ResolutionLevel>

Obtains the recommended resolution level based on the passed decoding mode. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                     | Mandatory| Description                      |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| decoderType | [DecoderType](arkts-apis-avsession-e.md#decodertype19) | Yes| Decoding format supported by the device.<br>The following decoding formats are supported by the device:<br>**'OH_AVCODEC_MIMETYPE_VIDEO_AVC'**: VIDEO AVC.<br>**'OH_AVCODEC_MIMETYPE_VIDEO_HEVC'**: VIDEO HEVC.<br>**'OH_AVCODEC_MIMETYPE_AUDIO_VIVID'**: AUDIO AV3A.|

**Return value**

| Type                                                       | Description                                                        |
| --------- | ------------------------------------------------------------ |
| Promise\<[ResolutionLevel](arkts-apis-avsession-e.md#resolutionlevel19)\> | Promise used to return the recommended resolution level of the remote device.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |

**Example**

```ts
let decoderType = avSession.DecoderType.OH_AVCODEC_MIMETYPE_VIDEO_AVC;
avCastController.getRecommendedResolutionLevel(decoderType).then((resolutionLevel: avSession.ResolutionLevel) => {
  console.info('Succeeded in getting recommended resolution level.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get recommended resolution level: ${err.message}`);
});
```

## getSupportedHdrCapabilities<sup>19+</sup>

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
| 6600101  | Session service exception. |

**Example**

```ts
import  { type hdrCapability } from '@kit.ArkGraphics2D';

avCastController.getSupportedHdrCapabilities().then((hdrFormats: hdrCapability.HDRFormat[]) => {
  console.info(`Succeeded in getting supported HDR capabilities, length: ${hdrFormats.length}`);
  if (hdrFormats.length > 0 ) {
    console.info(`Succeeded in getting supported HDR capability: ${hdrFormats[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get supported HDR capabilities: ${err.message}`);
});
```

## getSupportedPlaySpeeds<sup>19+</sup>

getSupportedPlaySpeeds(): Promise\<Array\<number>>

Obtains the playback speeds supported by the remote device. This API is only supported for devices connected using the Cast+ protocol. This API uses a promise to return the result.

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
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.getSupportedPlaySpeeds().then((nums: number[]) => {
  console.info(`Succeeded in getting supported play speeds, length: ${nums.length}`);
  if (nums.length > 0 ) {
    console.info(`Succeeded in getting supported play speed: ${nums[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get supported play speeds: ${err.message}`);
});
```

## sendControlCommand<sup>10+</sup>

sendControlCommand(command: AVCastControlCommand): Promise\<void>

Sends a control command to the session through the controller. This API uses a promise to return the result.


**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| command | [AVCastControlCommand](arkts-apis-avsession-i.md#avcastcontrolcommand10) | Yes  | Command to send.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600105  | Invalid session command. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
let avCommand: avSession.AVCastControlCommand = {command:'play'};
avCastController.sendControlCommand(avCommand).then(() => {
  console.info('Succeeded in sending control command.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send control command: ${err.message}`);
});
```

## sendControlCommand<sup>10+</sup>

sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback\<void>): void

Sends a control command to the session through the controller. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                 | Mandatory| Description                          |
| -------- | ------------------------------------- | ---- | ------------------------------ |
| command  | [AVCastControlCommand](arkts-apis-avsession-i.md#avcastcontrolcommand10) | Yes  | Command to send.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.                    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600105  | Invalid session command. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
let avCommand: avSession.AVCastControlCommand = {command:'play'};
avCastController.sendControlCommand(avCommand, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send control command: ${err.message}`);
    return;
  }
  console.info('Succeeded in sending control command.');
});
```

## sendCustomData<sup>20+</sup>

sendCustomData(data: Record\<string, Object>): Promise\<void>

Sends custom data to the remote device. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type                  | Mandatory| Description                                                        |
| ------ | ---------------------- | ---- | ------------------------------------------------------------ |
| data   | Record\<string, Object> | Yes  | Custom data filled by the application.<br>The server processes only the key **'customData'** when the associated value is a string object.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 6600101  | Session service exception.You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Example**

```ts
avCastController.sendCustomData({customData : "This is custom data"}).then(() => {
  console.info('Succeeded in sending custom data.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send custom data: ${err.message}`);
});
```

## prepare<sup>10+</sup>

prepare(item: AVQueueItem, callback: AsyncCallback\<void>): void

Prepares for the playback of a media asset, that is, loads and buffers a media asset. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| item | [AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10) | Yes  | Properties of an item in the playlist.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
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
avCastController.prepare(playItem, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to prepare: ${err.message}`);
    return;
  }
  console.info('Succeeded in preparing.');
});
```

## prepare<sup>10+</sup>

prepare(item: AVQueueItem): Promise\<void>

Prepares for the playback of a media asset, that is, loads and buffers a media asset. This API uses a promise to return the result.


**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| item | [AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10) | Yes  | Properties of an item in the playlist.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
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
avCastController.prepare(playItem).then(() => {
  console.info('Succeeded in preparing.');
}).catch((err: BusinessError) => {
  console.error(`Failed to prepare: ${err.message}`);
});
```

## start<sup>10+</sup>

start(item: AVQueueItem, callback: AsyncCallback\<void>): void

Prepares for the playback of a media asset. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> In the audio and video casting scenario, when the application sequentially calls the [prepare](#prepare10) and **start** APIs and the asset ID remains unchanged, if a valid **mediaUri** or **fdSrc** is passed to the **prepare** API, the **start** API will reuse the complete **AVMediaDescription** object information in the prepare phase.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| item | [AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10) | Yes  | Properties of an item in the playlist.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
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
avCastController.start(playItem, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to start: ${err.message}`);
    return;
  }
  console.info('Succeeded in starting.');
});
```

## start<sup>10+</sup>

start(item: AVQueueItem): Promise\<void>

Prepares for the playback of a media asset. This API uses a promise to return the result.

> **NOTE**
>
> In the audio and video casting scenario, when the application sequentially calls the [prepare](#prepare10) and **start** APIs and the asset ID remains unchanged, if a valid **mediaUri** or **fdSrc** is passed to the **prepare** API, the **start** API will reuse the complete **AVMediaDescription** object information in the prepare phase.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name   | Type                                 | Mandatory| Description                          |
| ------- | ------------------------------------- | ---- | ------------------------------ |
| item | [AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10) | Yes  | Properties of an item in the playlist.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
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
avCastController.start(playItem).then(() => {
  console.info('Succeeded in starting.');
}).catch((err: BusinessError) => {
  console.error(`Failed to start: ${err.message}`);
});
```

## getCurrentItem<sup>10+</sup>

getCurrentItem(callback: AsyncCallback\<AVQueueItem>): void

Obtains the information about the media asset that is being played. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback\<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.getCurrentItem((err: BusinessError, value: avSession.AVQueueItem) => {
  if (err) {
    console.error(`Failed to get current item: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting current item.');
});
```

## getCurrentItem<sup>10+</sup>

getCurrentItem(): Promise\<AVQueueItem>

Obtains the information about the media asset that is being played. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)> | Promise used to return the media asset obtained. If the operation fails, an error object is returned.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.getCurrentItem().then((value: avSession.AVQueueItem) => {
  console.info('Succeeded in getting current item.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get current item: ${err.message}`);
});
```

## getValidCommands<sup>11+</sup>

getValidCommands(callback: AsyncCallback<Array\<AVCastControlCommandType>>): void

Obtains the supported commands. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback<Array<[AVCastControlCommandType](arkts-apis-avsession-t.md#avcastcontrolcommandtype10)>> | Yes| Callback used to return the supported commands.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.getValidCommands((err: BusinessError, state: avSession.AVCastControlCommandType[]) => {
  if (err) {
    console.error(`Failed to get valid commands: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting valid commands.');
});
```

## getValidCommands<sup>11+</sup>

getValidCommands(): Promise<Array\<AVCastControlCommandType>>

Obtains the supported commands. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Return value**

| Type| Description|
| -------------- | ----------------------------- |
| Promise<Array\<[AVCastControlCommandType](arkts-apis-avsession-t.md#avcastcontrolcommandtype10)>> | Promise used to return the supported commands.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.getValidCommands().then((state: avSession.AVCastControlCommandType[]) => {
  console.info('Succeeded in getting valid commands.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get valid commands: ${err.message}`);
});
```

## processMediaKeyResponse<sup>12+</sup>

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

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |

**Example**

```ts
let keyRequestCallback: avSession.KeyRequestCallback = async(assetId: string, requestData: Uint8Array) => {
  // Obtain the DRM URL based on the asset ID.
  let drmUrl = 'http://license.xxx.xxx.com:8080/drmproxy/getLicense';
  // Obtain a media key from the server. Assign a value based on service requirements.
  let licenseResponseData: Uint8Array = new Uint8Array();
  console.info(`Succeeded in get license by ${drmUrl}.`);
  avCastController.processMediaKeyResponse(assetId, licenseResponseData).then(() => {
    console.info('Succeeded in processing media key response.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to process media key response: ${err.message}`);
  });
}
```

## release<sup>11+</sup>

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
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release: ${err.message}`);
    return;
  }
  console.info('Succeeded in releasing.');
});
```

## release<sup>11+</sup>

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
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.release().then(() => {
  console.info('Succeeded in releasing.');
}).catch((err: BusinessError) => {
  console.error(`Failed to release: ${err.message}`);
});

```

## on('playbackStateChange')<sup>10+</sup>

on(type: 'playbackStateChange', filter: Array\<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void

Subscribes to playback state change events. This API uses an asynchronous callback to return the result.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'playbackStateChange'** is triggered when the playback state changes.|
| filter   |  Array\<keyof AVPlaybackState>\|'all'| Yes  | The value **'all'** indicates that any playback state field change will trigger the event, and **Array\<keyof AVPlaybackstate>** indicates that only changes to the listed playback state field will trigger the event.|
| callback | (state: [AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)) => void         | Yes  | Callback function, where the **state** parameter indicates the new playback state.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('playbackStateChange', 'all', (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});

let playbackFilter: Array<keyof avSession.AVPlaybackState> = ['state', 'speed', 'loopMode'];
avCastController.on('playbackStateChange', playbackFilter, (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});
```

## off('playbackStateChange')<sup>10+</sup>

off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void

Unsubscribes from playback state change events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'playbackStateChange'** in this case.   |
| callback | (state: [AVPlaybackState](arkts-apis-avsession-i.md#avplaybackstate10)) => void         | No  | Callback function, where the **state** parameter indicates the new playback state.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('playbackStateChange');
```

## on('mediaItemChange')<sup>10+</sup>

on(type: 'mediaItemChange', callback: Callback\<AVQueueItem>): void

Subscribes to media asset change events. This API uses an asynchronous callback to return the result.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'mediaItemChange'** is triggered when the media content being played changes.|
| callback | Callback<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)>         | Yes  | Callback function, where the **AVQueueItem** parameter specifies the media asset that is being played.                     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('mediaItemChange', (item: avSession.AVQueueItem) => {
  console.info(`on mediaItemChange state : ${item.itemId}`);
});
```

## off('mediaItemChange')<sup>10+</sup>

off(type: 'mediaItemChange'): void

Unsubscribes from media asset change events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'mediaItemChange'** in this case.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('mediaItemChange');
```

## on('playNext')<sup>10+</sup>

on(type: 'playNext', callback: Callback\<void>): void

Subscribes to playNext command events.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'playNext'** is triggered when the command for playing the next item is received.|
| callback | Callback\<void\>         | Yes  | Callback used to return the result.                     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('playNext', () => {
  console.info('on playNext');
});
```

## off('playNext')<sup>10+</sup>

off(type: 'playNext'): void

Unsubscribes from playNext command events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'playNext'** in this case.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('playNext');
```

## on('playPrevious')<sup>10+</sup>

on(type: 'playPrevious', callback: Callback\<void>): void

Subscribes to playPrevious command events.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'playPrevious'** is triggered when the command for playing the previous event is received.|
| callback | Callback\<void\>         | Yes  | Callback used to return the result.                     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('playPrevious', () => {
  console.info('on playPrevious');
});
```

## off('playPrevious')<sup>10+</sup>

off(type: 'playPrevious'): void

Unsubscribes from playPrevious command events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'playPrevious'** in this case.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('playPrevious');
```

## on('requestPlay')<sup>11+</sup>

on(type: 'requestPlay', callback: Callback\<AVQueueItem>): void

Subscribes to playback request events.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'requestPlay'** is triggered when a playback request is received.|
| callback | Callback\<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)>                | Yes  | Callback function, where the **AVQueueItem** parameter specifies the media asset that is being played. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object. | 

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('requestPlay', (item: avSession.AVQueueItem) => {
  console.info(`on requestPlay state : ${item.itemId}`);
});
```

## off('requestPlay')<sup>11+</sup>

off(type: 'requestPlay', callback?: Callback\<AVQueueItem>): void

Unsubscribes from playback request events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------| ---- | ----------------------------------------------------- |
| type     | string                                                      | Yes  | Event type, which is **'requestPlay'** in this case.   |
| callback | Callback\<[AVQueueItem](arkts-apis-avsession-i.md#avqueueitem10)>             | No  | Callback function, where the **AVQueueItem** parameter specifies the media asset that is being played. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('requestPlay');
```

## on('endOfStream')<sup>11+</sup>

on(type: 'endOfStream', callback: Callback\<void>): void

Subscribes to playback end events.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | string                                                      | Yes  | Event type. The event **'endOfStream'** is triggered when the playback operation is complete.|
| callback | Callback\<void\>                                            | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('endOfStream', () => {
  console.info('on endOfStream');
});
```

## off('endOfStream')<sup>11+</sup>

off(type: 'endOfStream', callback?: Callback\<void>): void

Unsubscribes from the playback end events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------| ---- | ----------------------------------------------------- |
| type     | string                                                      | Yes  | Event type, which is **'endOfStream'** in this case.   |
| callback | Callback\<void\>                                            | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('endOfStream');
```

## on('seekDone')<sup>10+</sup>

on(type: 'seekDone', callback: Callback\<number>): void

Subscribes to seek done events.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'seekDone'** is triggered when the seek operation is complete.|
| callback | Callback\<number\>         | Yes  | Callback used to return the position after the seek operation.                     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('seekDone', (pos: number) => {
  console.info(`on seekDone pos: ${pos} `);
});
```

## off('seekDone')<sup>10+</sup>

off(type: 'seekDone'): void

Unsubscribes from the seek done events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                    |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'seekDone'** in this case.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('seekDone');
```

## on('validCommandChange')<sup>11+</sup>

on(type: 'validCommandChange', callback: Callback\<Array\<AVCastControlCommandType>>)

Subscribes to valid command change events.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'validCommandChange'** is triggered when the valid commands supported by the session changes.|
| callback | Callback<Array<[AVCastControlCommandType](arkts-apis-avsession-t.md#avcastcontrolcommandtype10)\>\>   | Yes  | Callback used for subscription. The **commands** parameter in the callback is a set of valid commands.                    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types.|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avCastController.on('validCommandChange', (validCommands: avSession.AVCastControlCommandType[]) => {
  console.info(`Succeeded in valid command change, size: ${validCommands.length}`);
  console.info(`Succeeded in valid command change, validCommands: ${validCommands.values()}`);
});
```

## off('validCommandChange')<sup>11+</sup>

off(type: 'validCommandChange', callback?: Callback\<Array\<AVCastControlCommandType>>)

Unsubscribes from valid command change events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                       |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'validCommandChange'** in this case.        |
| callback | Callback<Array<[AVCastControlCommandType](arkts-apis-avsession-t.md#avcastcontrolcommandtype10)\>\> | No  | Callback used for unsubscription. The **commands** parameter in the callback is a set of valid commands.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message          |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types.|
| 6600101  | Session service exception. |
| 6600103  | The session controller does not exist. |

**Example**

```ts
avCastController.off('validCommandChange');
```

## on('videoSizeChange')<sup>12+</sup>
on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void

Subscribes to video size change events.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'videoSizeChange'** is triggered when the valid commands supported by the session changes.|
| callback | (width: number, height: number) => void   | Yes  | Callback used to return the result.                   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('videoSizeChange', (width: number, height: number) => {
  console.info(`Succeeded in video size change, size: ${width}, ${height}`);
});
```

## off('videoSizeChange')<sup>12+</sup>

off(type: 'videoSizeChange'): void

Unsubscribes from video size change events. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The event **'videoSizeChange'** is triggered when the valid commands supported by the session changes.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ------------------------------ |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('videoSizeChange');
```

## on('error')<sup>10+</sup>

on(type: 'error', callback: ErrorCallback): void

Subscribes to remote player errors. This event is used only for error prompt and does not require the user to stop playback control.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'error'** in this case. This event can be triggered by both user operations and the system.|
| callback | ErrorCallback | Yes  | Callback used to return the error code ID and error message.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 5400101  | No memory.            |
| 5400102  | Operation not allowed.   |
| 5400103  | I/O error.             |
| 5400104  | Time out.      |
| 5400105  | Service died.         |
| 5400106  | Unsupport format.     |
| 6600101  | Session service exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('error', (error: BusinessError) => {
  console.info(`error happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## off('error')<sup>10+</sup>

off(type: 'error'): void

Unsubscribes from remote player errors. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| type   | string | Yes  | Event type, which is **'error'** in this case.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Media Error Codes](../apis-media-kit/errorcode-media.md), and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 5400101  | No memory.            |
| 5400102  | Operation not allowed.   |
| 5400103  | I/O error.             |
| 5400104  | Time out.      |
| 5400105  | Service died.         |
| 5400106  | Unsupport format.     |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('error')
```

## on('keyRequest')<sup>12+</sup>

on(type: 'keyRequest', callback: KeyRequestCallback): void

Subscribes to media key requests during the cast of online DRM resources.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| type     | string  | Yes  | Event type. The event **'keyRequest'** is triggered when a media key request is required during the cast of online DRM resources.|
| callback | [KeyRequestCallback](arkts-apis-avsession-t.md#keyrequestcallback12)  | Yes  | Callback used to request the media resources and media key.|


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message          |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
let keyRequestCallback: avSession.KeyRequestCallback = async(assetId: string, requestData: Uint8Array) => {
  console.info(`Succeeded in keyRequestCallback. assetId: ${assetId}, requestData: ${requestData}`);
}
avCastController.on('keyRequest', keyRequestCallback);
```

## off('keyRequest')<sup>12+</sup>

off(type: 'keyRequest', callback?: KeyRequestCallback): void

Unsubscribes from media key requests during the cast of online DRM resources. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name| Type  | Mandatory| Description                                     |
| ------ | ------ | ---- | ----------------------------------------- |
| type     | string                                                       | Yes  | Event type, which is **'keyRequest'** in this case.|
| callback |  [KeyRequestCallback](arkts-apis-avsession-t.md#keyrequestcallback12)  | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message          |
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('keyRequest');
```

## on('castControlGenericError')<sup>13+</sup>

on(type: 'castControlGenericError', callback: ErrorCallback): void

Subscribes to generic error events during cast control.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlGenericError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

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
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlGenericError', (error: BusinessError) => {
  console.info(`castControlGenericError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## off('castControlGenericError')<sup>13+</sup>

off(type: 'castControlGenericError', callback?: ErrorCallback): void

Unsubscribes from generic error events during cast control. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  |  Event type, which is **'castControlGenericError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
avCastController.off('castControlGenericError');
```

## on('castControlIoError')<sup>13+</sup>

on(type: 'castControlIoError', callback: ErrorCallback): void

Subscribes to input/output error events during cast control.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlIoError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

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
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlIoError', (error: BusinessError) => {
  console.info(`castControlIoError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## off('castControlIoError')<sup>13+</sup>

off(type: 'castControlIoError', callback?: ErrorCallback): void

Unsubscribes from input/output error events during cast control. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlIoError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
avCastController.off('castControlIoError');
```

## on('castControlParsingError')<sup>13+</sup>

on(type: 'castControlParsingError', callback: ErrorCallback): void

Subscribes to parsing error events during cast control.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlParsingError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

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
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlParsingError', (error: BusinessError) => {
  console.info(`castControlParsingError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## off('castControlParsingError')<sup>13+</sup>

off(type: 'castControlParsingError', callback?: ErrorCallback): void

Unsubscribes from parsing error events during cast control. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  |  Event type, which is **'castControlParsingError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
avCastController.off('castControlParsingError');
```

## on('castControlDecodingError')<sup>13+</sup>

on(type: 'castControlDecodingError', callback: ErrorCallback): void

Subscribes to decoding error events during cast control.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlDecodingError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

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
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlDecodingError', (error: BusinessError) => {
  console.info(`castControlDecodingError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## off('castControlDecodingError')<sup>13+</sup>

off(type: 'castControlDecodingError', callback?: ErrorCallback): void

Unsubscribes from decoding error events during cast control. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  |  Event type, which is **'castControlDecodingError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
avCastController.off('castControlDecodingError');
```

## on('castControlAudioRendererError')<sup>13+</sup>

on(type: 'castControlAudioRendererError', callback: ErrorCallback): void

Subscribes to audio renderer error events during cast control.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlAudioRendererError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 6615000  | Unspecified errors related to the audio renderer.     |
| 6615001  | Initializing the audio renderer failed.   |
| 6615002  | The audio renderer fails to write data.     |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlAudioRendererError', (error: BusinessError) => {
  console.info(`castControlAudioRendererError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## off('castControlAudioRendererError')<sup>13+</sup>

off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void

Unsubscribes from audio renderer error events during cast control. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlAudioRendererError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|

**Example**

```ts
avCastController.off('castControlAudioRendererError');
```

## on('castControlDrmError')<sup>13+</sup>

on(type: 'castControlDrmError', callback: ErrorCallback): void

Subscribes to DRM error events during cast control.

Multiple callbacks can be registered for this event. To ensure only the latest callback executes, unregister previous listeners first. Otherwise, all registered callbacks will fire on state changes.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlDrmError'** in this case.|
| callback | ErrorCallback | Yes  | Callback invoked when the event is triggered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

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
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlDrmError', (error: BusinessError) => {
  console.info(`castControlDrmError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## off('castControlDrmError')<sup>13+</sup>

off(type: 'castControlDrmError', callback?: ErrorCallback): void

Unsubscribes from DRM error events during cast control. If a callback is specified, the corresponding listener is unregistered. If no callback is specified, all listeners for the specified event are unregistered.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type    | Mandatory| Description                                                        |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | Yes  | Event type, which is **'castControlDrmError'** in this case.|
| callback | ErrorCallback | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message             |
| -------- | --------------------- |
| 401 |  Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
avCastController.off('castControlDrmError');
```

## on('customDataChange')<sup>20+</sup>

on(type: 'customDataChange', callback: Callback\<Record\<string, Object>>): void

Subscribes to events indicating that custom data is sent to a remote device.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type | string | Yes| Event type. The event **'customDataChange'** is triggered when the provider sends custom data.|
| callback | Callback\<Record\<string, Object>> | Yes  | Callback used to receive the custom data.                              |

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('customDataChange', (callback) => {
    console.info(`Caught customDataChange event,the new callback is: ${JSON.stringify(callback)}`);
});
```

## off('customDataChange')<sup>20+</sup>

off(type: 'customDataChange', callback?: Callback\<Record\<string, Object>>): void

Unsubscribes from events indicating that custom data is sent to a remote device.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                           | Yes  | Event type, which is **'customDataChange'** in this case.        |
| callback | Callback\<Record\<string, Object>> | No  | Callback used for unsubscription. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('customDataChange');
```
