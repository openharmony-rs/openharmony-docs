# AVCastController

```TypeScript
interface AVCastController
```

AVCastController definition used to implement a remote control when a cast is connected

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## getAVPlaybackState

```TypeScript
getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void
```

Get the playback status of the current player

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | Yes | The triggered asyncCallback when (getAVPlaybackState). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.getAVPlaybackState((err: BusinessError, state: avSession.AVPlaybackState) => {
  if (err) {
    console.error(`Failed to get AV playback state, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting AV playback state.');
});
```

<a id="getavplaybackstate-1"></a>

## getAVPlaybackState

```TypeScript
getAVPlaybackState(): Promise<AVPlaybackState>
```

Get the playback status of the current player

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | (AVPlaybackState) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.getAVPlaybackState().then((state: avSession.AVPlaybackState) => {
  console.info('Succeeded in getting AV playback state.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get AV playback state, code: ${err.code}, message: ${err.message}`);
});
```

## getCurrentItem

```TypeScript
getCurrentItem(callback: AsyncCallback<AVQueueItem>): void
```

Get the current playing item

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt; | Yes | The triggered asyncCallback. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.getCurrentItem((err: BusinessError, value: avSession.AVQueueItem) => {
  if (err) {
    console.error(`Failed to get current item, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting current item.');
});
```

<a id="getcurrentitem-1"></a>

## getCurrentItem

```TypeScript
getCurrentItem(): Promise<AVQueueItem>
```

Get the current playing item

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt; | (AVQueueItem) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.getCurrentItem().then((value: avSession.AVQueueItem) => {
  console.info('Succeeded in getting current item.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get current item, code: ${err.code}, message: ${err.message}`);
});
```

## getRecommendedResolutionLevel

```TypeScript
getRecommendedResolutionLevel(decoderType: DecoderType): Promise<ResolutionLevel>
```

Get recommended resolution of remote player based on each decoder.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| decoderType | [DecoderType](arkts-avsession-avsession-decodertype-e.md) | Yes | The decoder type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResolutionLevel](arkts-avsession-avsession-resolutionlevel-e.md)&gt; | ResolutionLevel returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
let decoderType = avSession.DecoderType.OH_AVCODEC_MIMETYPE_VIDEO_AVC;
avCastController.getRecommendedResolutionLevel(decoderType).then((resolutionLevel: avSession.ResolutionLevel) => {
  console.info('Succeeded in getting recommended resolution level.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get recommended resolution level, code: ${err.code}, message: ${err.message}`);
});
```

## getSupportedDecoders

```TypeScript
getSupportedDecoders(): Promise<Array<DecoderType>>
```

Get supported decoders of remote player.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[DecoderType](arkts-avsession-avsession-decodertype-e.md)&gt;&gt; | (DecoderType) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.getSupportedDecoders().then((decoderTypes: avSession.DecoderType[]) => {
  console.info(`Succeeded in getting supported decoders, length: ${decoderTypes.length}`);
  if (decoderTypes.length > 0 ) {
    console.info(`Succeeded in getting supported decoder: ${decoderTypes[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get supported decoders, code: ${err.code}, message: ${err.message}`);
});
```

## getSupportedHdrCapabilities

```TypeScript
getSupportedHdrCapabilities(): Promise<Array<hdrCapability.HDRFormat>>
```

Get supported hdr capabilities of remote player.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[hdrCapability.HDRFormat](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-hdrcapability-hdrformat-e.md)&gt;&gt; | HDRFormat returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
import { type hdrCapability } from '@kit.ArkGraphics2D';

avCastController.getSupportedHdrCapabilities().then((hdrFormats: hdrCapability.HDRFormat[]) => {
  console.info(`Succeeded in getting supported HDR capabilities, length: ${hdrFormats.length}`);
  if (hdrFormats.length > 0 ) {
    console.info(`Succeeded in getting supported HDR capability: ${hdrFormats[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get supported HDR capabilities, code: ${err.code}, message: ${err.message}`);
});
```

## getSupportedPlaySpeeds

```TypeScript
getSupportedPlaySpeeds(): Promise<Array<number>>
```

Get supported speed of remote player.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | supported speed returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.getSupportedPlaySpeeds().then((nums: number[]) => {
  console.info(`Succeeded in getting supported play speeds, length: ${nums.length}`);
  if (nums.length > 0 ) {
    console.info(`Succeeded in getting supported play speed: ${nums[0]}`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get supported play speeds, code: ${err.code}, message: ${err.message}`);
});
```

## getValidCommands

```TypeScript
getValidCommands(callback: AsyncCallback<Array<AVCastControlCommandType>>): void
```

Get commands supported by the current cast controller

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md)&gt;&gt; | Yes | The triggered asyncCallback when (getValidCommands). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.getValidCommands((err: BusinessError, state: avSession.AVCastControlCommandType[]) => {
  if (err) {
    console.error(`Failed to get valid commands, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting valid commands.');
});
```

<a id="getvalidcommands-1"></a>

## getValidCommands

```TypeScript
getValidCommands(): Promise<Array<AVCastControlCommandType>>
```

Get commands supported by the current cast controller

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md)&gt;&gt; | array of AVCastControlCommandType promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.getValidCommands().then((state: avSession.AVCastControlCommandType[]) => {
  console.info('Succeeded in getting valid commands.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get valid commands, code: ${err.code}, message: ${err.message}`);
});
```

## off('playbackStateChange')

```TypeScript
off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void
```

Unregister playback state changed callback

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | Yes |  |
| callback | (state: AVPlaybackState) =&gt; void | No | The callback used to handle playback state changed event. The callback function provides the [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md) parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('playbackStateChange');
```

## off('mediaItemChange')

```TypeScript
off(type: 'mediaItemChange'): void
```

Unregister listener for current media item playback events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mediaItemChange' | Yes | Type of the playback event to listen for. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('mediaItemChange');
```

## off('playNext')

```TypeScript
off(type: 'playNext'): void
```

Unregister playback command callback sent by remote side or media center. When canceling the callback, need to update the supported commands list.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playNext' | Yes | Type of the 'playNext' event to listen for. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('playNext');
```

## off('playPrevious')

```TypeScript
off(type: 'playPrevious'): void
```

Unregister playback command callback sent by remote side or media center. When canceling the callback, need to update the supported commands list.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playPrevious' | Yes | Type of the 'playPrevious' to listen for. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('playPrevious');
```

## off('requestPlay')

```TypeScript
off(type: 'requestPlay', callback?: Callback<AVQueueItem>): void
```

Unregister requested playback command callback sent by remote side or media center.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'requestPlay' | Yes | Type of the 'requestPlay' to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt; | No | Used to handle 'requestPlay' command |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('requestPlay');
```

## off('endOfStream')

```TypeScript
off(type: 'endOfStream', callback?: Callback<void>): void
```

Unregister endOfStream state callback.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'endOfStream' | Yes | Type of the 'endOfStream' to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Used to handle 'endOfStream' command |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('endOfStream');
```

## off('seekDone')

```TypeScript
off(type: 'seekDone'): void
```

Unregister listens for playback events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'seekDone' | Yes | Type of the 'seekDone' to listen for. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('seekDone');
```

## off('validCommandChange')

```TypeScript
off(type: 'validCommandChange', callback?: Callback<Array<AVCastControlCommandType>>)
```

Unregister the valid commands of the casted session changed callback

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'validCommandChange' | Yes | 'validCommandChange' |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md)&gt;&gt; | No | The callback used to handle the changes. The callback function provides an array of AVCastControlCommandType. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avCastController.off('validCommandChange');
```

## off('videoSizeChange')

```TypeScript
off(type: 'videoSizeChange'): void
```

Unregister listener for video size change event, used at remote side.

**Since:** 12

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | Yes | Type of the 'videoSizeChange' to listen for. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('videoSizeChange');
```

## off('error')

```TypeScript
off(type: 'error'): void
```

Unregister listens for playback error events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Type of the 'error' to listen for. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [5400101](../../apis-media-kit/errorcode-media.md#5400101-memory-allocation-failed) | No memory. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-io-error) | I/O error. |
| [5400104](../../apis-media-kit/errorcode-media.md#5400104-operation-timeout) | Time out. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Service died. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-format-not-supported) | Unsupported format. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('error')
```

## off('castControlGenericError')

```TypeScript
off(type: 'castControlGenericError', callback?: ErrorCallback): void
```

Unregister listeners for cast control generic error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlGenericError' | Yes | Type of the 'castControlGenericError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
avCastController.off('castControlGenericError');
```

## off('castControlIoError')

```TypeScript
off(type: 'castControlIoError', callback?: ErrorCallback): void
```

Unregister listeners for cast control input/output error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlIoError' | Yes | Type of the 'castControlIoError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
avCastController.off('castControlIoError');
```

## off('castControlParsingError')

```TypeScript
off(type: 'castControlParsingError', callback?: ErrorCallback): void
```

Unregister listeners for cast control parsing error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlParsingError' | Yes | Type of the 'castControlParsingError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
avCastController.off('castControlParsingError');
```

## off('castControlDecodingError')

```TypeScript
off(type: 'castControlDecodingError', callback?: ErrorCallback): void
```

Unregister listeners for cast control decoding error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlDecodingError' | Yes | Type of the 'castControlDecodingError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
avCastController.off('castControlDecodingError');
```

## off('castControlAudioRendererError')

```TypeScript
off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void
```

Unregister listeners for cast control audio renderer error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlAudioRendererError' | Yes | Type of the 'castControlAudioRendererError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
avCastController.off('castControlAudioRendererError');
```

## off('castControlDrmError')

```TypeScript
off(type: 'castControlDrmError', callback?: ErrorCallback): void
```

Unregister listeners for cast control drm error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlDrmError' | Yes | Type of the 'castControlDrmError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | No | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Examples**

```TypeScript
avCastController.off('castControlDrmError');
```

## off('keyRequest')

```TypeScript
off(type: 'keyRequest', callback?: KeyRequestCallback): void
```

Unregister listener for drm key request.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyRequest' | Yes | Type of the 'keyRequest' to listen for. |
| callback | [KeyRequestCallback](arkts-avsession-avsession-keyrequestcallback-t.md) | No | Callback used to request drm key. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('keyRequest');
```

## off('customDataChange')

```TypeScript
off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void
```

Unregister listener for custom data sent from remote device.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'customDataChange' | Yes | Type of the 'customDataChange' to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Object&gt;&gt; | No | Callback used to retrieve custom data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.off('customDataChange');
```

## on('playbackStateChange')

```TypeScript
on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void
```

Register playback state changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | Yes |  |
| filter | Array&lt;keyof AVPlaybackState&gt; &#124; 'all' | Yes | The properties of [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md) that you cared about |
| callback | (state: AVPlaybackState) =&gt; void | Yes | The callback used to handle playback state changed event. The callback function provides the [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md) parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('playbackStateChange', 'all', (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});

let playbackFilter: Array<keyof avSession.AVPlaybackState> = ['state', 'speed', 'loopMode'];
avCastController.on('playbackStateChange', playbackFilter, (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});
```

## on('mediaItemChange')

```TypeScript
on(type: 'mediaItemChange', callback: Callback<AVQueueItem>): void
```

Register listener for current media item playback events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mediaItemChange' | Yes | Type of the playback event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt; | Yes | Callback used to listen for current item changed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('mediaItemChange', (item: avSession.AVQueueItem) => {
  console.info(`on mediaItemChange state : ${item.itemId}`);
});
```

## on('playNext')

```TypeScript
on(type: 'playNext', callback: Callback<void>): void
```

Register playback command callback sent by remote side or media center. Application needs update the new media resource when receive these commands by using playItem.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playNext' | Yes | Type of the 'playNext' event to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Used to handle 'playNext' command |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('playNext', () => {
  console.info('on playNext');
});
```

## on('playPrevious')

```TypeScript
on(type: 'playPrevious', callback: Callback<void>): void
```

Register playback command callback sent by remote side or media center. Application needs update the new media resource when receive these commands by using playItem.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'playPrevious' | Yes | Type of the 'playPrevious' to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Used to handle 'playPrevious' command |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('playPrevious', () => {
  console.info('on playPrevious');
});
```

## on('requestPlay')

```TypeScript
on(type: 'requestPlay', callback: Callback<AVQueueItem>): void
```

Register requested playback command callback sent by remote side or media center. The AVQueueItem may include the requested assetId, starting position and other configurations.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'requestPlay' | Yes | Type of the 'requestPlay' to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt; | Yes | Used to handle 'requestPlay' command |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('requestPlay', (item: avSession.AVQueueItem) => {
  console.info(`on requestPlay state : ${item.itemId}`);
});
```

## on('endOfStream')

```TypeScript
on(type: 'endOfStream', callback: Callback<void>): void
```

Register endOfStream state callback. Application needs update the new media resource when receive these commands by using playItem.

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'endOfStream' | Yes | Type of the 'endOfStream' to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Used to handle 'endOfStream' command |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('endOfStream', () => {
  console.info('on endOfStream');
});
```

## on('seekDone')

```TypeScript
on(type: 'seekDone', callback: Callback<number>): void
```

Register listens for playback events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'seekDone' | Yes | Type of the 'seekDone' to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to listen for the playback seekDone event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('seekDone', (pos: number) => {
  console.info(`on seekDone pos: ${pos} `);
});
```

## on('validCommandChange')

```TypeScript
on(type: 'validCommandChange', callback: Callback<Array<AVCastControlCommandType>>)
```

Register the valid commands of the casted session changed callback

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'validCommandChange' | Yes | 'validCommandChange' |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVCastControlCommandType](arkts-avsession-avsession-avcastcontrolcommandtype-t.md)&gt;&gt; | Yes | The callback used to handle the changes. The callback function provides an array of AVCastControlCommandType. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avCastController.on('validCommandChange', (validCommands: avSession.AVCastControlCommandType[]) => {
  console.info(`Succeeded in valid command change, size: ${validCommands.length}`);
  console.info(`Succeeded in valid command change, validCommands: ${validCommands.values()}`);
});
```

## on('videoSizeChange')

```TypeScript
on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void
```

Register listener for video size change event, used at remote side.

**Since:** 12

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | Yes | Type of the 'videoSizeChange' to listen for. |
| callback | (width: number, height: number) =&gt; void | Yes | Callback used to return video size. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('videoSizeChange', (width: number, height: number) => {
  console.info(`Succeeded in video size change, size: ${width}, ${height}`);
});
```

```TypeScript
// Obtain the avCastController instance through avSession.getAVCastController.
avCastController.on('videoSizeChange', (width: number, height: number) => {
  console.info(`width : ${width} `);
  console.info(`height: ${height} `);
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

Register listeners for playback error events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'error' | Yes | Type of the 'error' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to listen for the playback error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [5400101](../../apis-media-kit/errorcode-media.md#5400101-memory-allocation-failed) | No memory. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-unsupported-operation) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-io-error) | I/O error. |
| [5400104](../../apis-media-kit/errorcode-media.md#5400104-operation-timeout) | Time out. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-play-service-dead) | Service died. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-format-not-supported) | Unsupported format. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('error', (error: BusinessError) => {
  console.error(`error happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## on('castControlGenericError')

```TypeScript
on(type: 'castControlGenericError', callback: ErrorCallback): void
```

Register listeners for cast control generic error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlGenericError' | Yes | Type of the 'castControlGenericError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [6611000](../errorcode-avsession.md#6611000-unknown-error-in-the-cast-controller) | The error code for cast control is unspecified. |
| [6611001](../errorcode-avsession.md#6611001-unknown-error-in-the-remote-device) | An unspecified error occurs in the remote player. |
| [6611002](../errorcode-avsession.md#6611002-loading-position-exceeds-the-total-video-progress) | The playback position falls behind the live window. |
| [6611003](../errorcode-avsession.md#6611003-cast-controller-loading-timeout) | The process of cast control times out. |
| [6611004](../errorcode-avsession.md#6611004-runtime-check-failure) | The runtime check failed. |
| [6611100](../errorcode-avsession.md#6611100-cross-device-data-transmission-locked) | Cross-device data transmission is locked. |
| [6611101](../errorcode-avsession.md#6611101-unsupported-seek-mode) | The specified seek mode is not supported. |
| [6611102](../errorcode-avsession.md#6611102-invalid-seek-target) | The position to seek to is out of the range of the media asset or the specified seek mode is not supported. |
| [6611103](../errorcode-avsession.md#6611103-unsupported-playback-mode) | The specified playback mode is not supported. |
| [6611104](../errorcode-avsession.md#6611104-unsupported-playback-speed) | The specified playback speed is not supported. |
| [6611105](../errorcode-avsession.md#6611105-device-revocation) | The action failed because either the media source device or the media sink device has been revoked. |
| [6611106](../errorcode-avsession.md#6611106-invalid-input-parameter) | The parameter is invalid, for example, the url is illegal to play. |
| [6611107](../errorcode-avsession.md#6611107-memory-allocation-failure) | Allocation of memory failed. |
| [6611108](../errorcode-avsession.md#6611108-operation-not-allowed) | Operation is not allowed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlGenericError', (error: BusinessError) => {
  console.error(`castControlGenericError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## on('castControlIoError')

```TypeScript
on(type: 'castControlIoError', callback: ErrorCallback): void
```

Register listeners for cast control input/output error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlIoError' | Yes | Type of the 'castControlIoError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [6612000](../errorcode-avsession.md#6612000-unknown-io-error) | An unspecified input/output error occurs. |
| [6612001](../errorcode-avsession.md#6612001-network-connection-failure) | Network connection failure. |
| [6612002](../errorcode-avsession.md#6612002-network-timeout) | Network timeout. |
| [6612003](../errorcode-avsession.md#6612003-invalid-content-type-http-header) | Invalid "Content-Type" HTTP header. |
| [6612004](../errorcode-avsession.md#6612004-unexpected-http-response-status-code-from-the-http-server) | The HTTP server returns an unexpected HTTP response status code. |
| [6612005](../errorcode-avsession.md#6612005-file-does-not-exist) | The file does not exist. |
| [6612006](../errorcode-avsession.md#6612006-no-permission-for-io-operations) | No permission is granted to perform the IO operation. |
| [6612007](../errorcode-avsession.md#6612007-operation-not-allowed-by-network-security-configuration) | Access to cleartext HTTP traffic is not allowed by the app's network security configuration. |
| [6612008](../errorcode-avsession.md#6612008-data-to-read-out-of-range) | Reading data out of the data bound. |
| [6612100](../errorcode-avsession.md#6612100-no-playable-content) | The media does not contain any contents that can be played. |
| [6612101](../errorcode-avsession.md#6612101-failure-in-reading-media-assets) | The media cannot be read, for example, because of dust or scratches. |
| [6612102](../errorcode-avsession.md#6612102-resource-is-being-used) | This resource is already in use. |
| [6612103](../errorcode-avsession.md#6612103-content-expired) | The content using the validity interval has expired. |
| [6612104](../errorcode-avsession.md#6612104-requested-content-cannot-be-used) | Using the requested content to play is not allowed. |
| [6612105](../errorcode-avsession.md#6612105-unable-to-verify-the-allowed-content) | The use of the allowed content cannot be verified. |
| [6612106](../errorcode-avsession.md#6612106-frequent-resource-usage) | The number of times this content has been used as requested has reached the maximum allowed number of uses. |
| [6612107](../errorcode-avsession.md#6612107-failure-in-sending-resource-packages-to-the-remote-device) | An error occurs when sending packet from source device to sink device. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlIoError', (error: BusinessError) => {
  console.error(`castControlIoError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## on('castControlParsingError')

```TypeScript
on(type: 'castControlParsingError', callback: ErrorCallback): void
```

Register listeners for cast control parsing error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlParsingError' | Yes | Type of the 'castControlParsingError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [6613000](../errorcode-avsession.md#6613000-unknown-parsing-error) | Unspecified error related to content parsing. |
| [6613001](../errorcode-avsession.md#6613001-invalid-type) | Parsing error associated with media container format bit streams. |
| [6613002](../errorcode-avsession.md#6613002-error-in-parsing-media-manifest) | Parsing error associated with the media manifest. |
| [6613003](../errorcode-avsession.md#6613003-unsupported-media-format) | An error occurs when attempting to extract a file with an unsupported media container format or an unsupported media container feature. |
| [6613004](../errorcode-avsession.md#6613004-unsupported-feature-in-the-media-manifest) | Unsupported feature in the media manifest. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlParsingError', (error: BusinessError) => {
  console.error(`castControlParsingError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## on('castControlDecodingError')

```TypeScript
on(type: 'castControlDecodingError', callback: ErrorCallback): void
```

Register listeners for cast control decoding error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlDecodingError' | Yes | Type of the 'castControlDecodingError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [6614000](../errorcode-avsession.md#6614000-unknown-decoding-error) | Unspecified decoding error. |
| [6614001](../errorcode-avsession.md#6614001-decoder-initialization-failure) | Decoder initialization failed. |
| [6614002](../errorcode-avsession.md#6614002-decoder-query-failure) | Decoder query failed. |
| [6614003](../errorcode-avsession.md#6614003-media-sample-decoding-failure) | Decoding the media samples failed. |
| [6614004](../errorcode-avsession.md#6614004-content-format-is-beyond-the-device-capability) | The format of the content to decode exceeds the capabilities of the device. |
| [6614005](../errorcode-avsession.md#6614005-decoding-of-the-content-format-is-not-supported) | The format of the content to decode is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlDecodingError', (error: BusinessError) => {
  console.error(`castControlDecodingError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## on('castControlAudioRendererError')

```TypeScript
on(type: 'castControlAudioRendererError', callback: ErrorCallback): void
```

Register listeners for cast control audio renderer error error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlAudioRendererError' | Yes | Type of the 'castControlAudioRendererError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [6615000](../errorcode-avsession.md#6615000-unknown-error-related-to-the-audio-renderer) | Unspecified errors related to the audio renderer. |
| [6615001](../errorcode-avsession.md#6615001-audio-renderer-initialization-failure) | Initializing the audio renderer failed. |
| [6615002](../errorcode-avsession.md#6615002-audio-renderer-failure-in-writing-data) | The audio renderer fails to write data. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlAudioRendererError', (error: BusinessError) => {
  console.error(`castControlAudioRendererError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## on('castControlDrmError')

```TypeScript
on(type: 'castControlDrmError', callback: ErrorCallback): void
```

Register listeners for cast control drm error events.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'castControlDrmError' | Yes | Type of the 'castControlDrmError' to listen for. |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | Yes | Callback used to listen for the cast control error event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [6616000](../errorcode-avsession.md#6616000-unknown-drm-error) | Unspecified error related to DRM. |
| [6616001](../errorcode-avsession.md#6616001-device-does-not-support-the-selected-drm-solution) | The chosen DRM protection scheme is not supported by the device. |
| [6616002](../errorcode-avsession.md#6616002-device-provisioning-failure) | Device provisioning failed. |
| [6616003](../errorcode-avsession.md#6616003-drm-protected-content-to-play-is-incompatible) | The DRM-protected content to play is incompatible. |
| [6616004](../errorcode-avsession.md#6616004-license-obtaining-failure) | Failed to obtain a license. |
| [6616005](../errorcode-avsession.md#6616005-operation-not-allowed-by-the-license-policy) | The operation is disallowed by the license policy. |
| [6616006](../errorcode-avsession.md#6616006-drm-system-error) | An error occurs in the DRM system. |
| [6616007](../errorcode-avsession.md#6616007-drm-privileges-revoked) | The device has revoked DRM privileges. |
| [6616008](../errorcode-avsession.md#6616008-expired-drm-license-loaded) | The DRM license being loaded into the open DRM session has expired. |
| [6616100](../errorcode-avsession.md#6616100-error-in-processing-the-key-response) | An error occurs when the DRM processes the key response. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

avCastController.on('castControlDrmError', (error: BusinessError) => {
  console.error(`castControlDrmError happened, error code: ${error.code}, error message : ${error.message}.`)
})
```

## on('keyRequest')

```TypeScript
on(type: 'keyRequest', callback: KeyRequestCallback): void
```

Register listener for drm key request.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'keyRequest' | Yes | Type of the 'keyRequest' to listen for. |
| callback | [KeyRequestCallback](arkts-avsession-avsession-keyrequestcallback-t.md) | Yes | Callback used to request drm key. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
let keyRequestCallback: avSession.KeyRequestCallback = async(assetId: string, requestData: Uint8Array) => {
  console.info(`Succeeded in keyRequestCallback. assetId: ${assetId}, requestData: ${requestData}`);
}
avCastController.on('keyRequest', keyRequestCallback);
```

## on('customDataChange')

```TypeScript
on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void
```

Register listener for custom data sent from remote device.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'customDataChange' | Yes | Type of the 'customDataChange' to listen for. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Object&gt;&gt; | Yes | Callback used to retrieve custom data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.on('customDataChange', (data: Record<string, Object>) => {
    console.info(`Caught customDataChange event, the new data is: ${JSON.stringify(data)}`);
});
```

## prepare

```TypeScript
prepare(item: AVQueueItem, callback: AsyncCallback<void>): void
```

Load the current item and mediaUri can be null, this is needed for sink media information displaying

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | Yes | media item info. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
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
    albumCoverUri: 'http://resource1_album_address',
    lyricUri: 'http://resource1_lyric_address',
    appName: 'MyMusic'
  }
};
// Prepare for playback. This operation triggers loading and buffering, but not the actual playback.
avCastController.prepare(playItem, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to prepare, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in preparing.');
});
```

<a id="prepare-1"></a>

## prepare

```TypeScript
prepare(item: AVQueueItem): Promise<void>
```

Load the current item and mediaUri can be null, this is needed for sink media information displaying

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | Yes | media item info. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
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
    albumCoverUri: 'http://resource1_album_address',
    lyricUri: 'http://resource1_lyric_address',
    appName: 'MyMusic'
  }
};
// Prepare for playback. This operation triggers loading and buffering, but not the actual playback.
avCastController.prepare(playItem).then(() => {
  console.info('Succeeded in preparing.');
}).catch((err: BusinessError) => {
  console.error(`Failed to prepare, code: ${err.code}, message: ${err.message}`);
});
```

## processMediaKeyResponse

```TypeScript
processMediaKeyResponse(assetId: string, response: Uint8Array): Promise<void>
```

Process the response corresponding to the media key request obtained by the application.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| assetId | string | Yes | The assetId of resource which provides the response. |
| response | Uint8Array | Yes | Response corresponding to the request. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
let keyRequestCallback: avSession.KeyRequestCallback = async(assetId: string, requestData: Uint8Array) => {
  // Obtain the DRM URL based on the asset ID.
  let drmUrl = 'http://license.xxx.xxx.com:8080/drmproxy/getLicense';
  // Obtain a media key from the server. Assign a value based on service requirements.
  let licenseResponseData: Uint8Array = new Uint8Array();
  console.info(`Succeeded in get license by ${drmUrl}.`);
  avCastController.processMediaKeyResponse(assetId, licenseResponseData).then(() => {
    console.info('Succeeded in processing media key response.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to process media key response, code: ${err.code}, message: ${err.message}`);
  });
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Destroy the controller

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.release((err: BusinessError) => {
  if (err) {
    console.error(`Failed to release, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in releasing.');
});
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Destroy the controller

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
avCastController.release().then(() => {
  console.info('Succeeded in releasing.');
}).catch((err: BusinessError) => {
  console.error(`Failed to release, code: ${err.code}, message: ${err.message}`);
});
```

## sendControlCommand

```TypeScript
sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback<void>): void
```

Send control commands to remote player

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | [AVCastControlCommand](arkts-avsession-avsession-avcastcontrolcommand-i.md) | Yes | The command to be send. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
let avCommand: avSession.AVCastControlCommand = {command: 'play'};
avCastController.sendControlCommand(avCommand, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send control command, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in sending control command.');
});
```

<a id="sendcontrolcommand-1"></a>

## sendControlCommand

```TypeScript
sendControlCommand(command: AVCastControlCommand): Promise<void>
```

Send control commands to remote player

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | [AVCastControlCommand](arkts-avsession-avsession-avcastcontrolcommand-i.md) | Yes | The command to be send. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
let avCommand: avSession.AVCastControlCommand = {command: 'play'};
avCastController.sendControlCommand(avCommand).then(() => {
  console.info('Succeeded in sending control command.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send control command, code: ${err.code}, message: ${err.message}`);
});
```

## sendCustomData

```TypeScript
sendCustomData(data: Record<string, Object>): Promise<void>
```

Sends custom data to a remote device.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | Custom data populated by the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |

**Examples**

```TypeScript
avCastController.sendCustomData({customData: 'This is custom data'}).then(() => {
  console.info('Succeeded in sending custom data.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send custom data, code: ${err.code}, message: ${err.message}`);
});
```

## start

```TypeScript
start(item: AVQueueItem, callback: AsyncCallback<void>): void
```

Play the current item, should contain mediaUri otherwise the playback will fail.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | Yes | media item info. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
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
    albumCoverUri: 'http://resource1_album_address',
    lyricUri: 'http://resource1_lyric_address',
    appName: 'MyMusic'
  }
};

// Start playback.
avCastController.start(playItem, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to start, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in starting.');
});
```

<a id="start-1"></a>

## start

```TypeScript
start(item: AVQueueItem): Promise<void>
```

Play the current item, should contain mediaUri otherwise the playback will fail.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | Yes | media item info. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
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
    albumCoverUri: 'http://resource1_album_address',
    lyricUri: 'http://resource1_lyric_address',
    appName: 'MyMusic'
  }
};
// Start playback.
avCastController.start(playItem).then(() => {
  console.info('Succeeded in starting.');
}).catch((err: BusinessError) => {
  console.error(`Failed to start, code: ${err.code}, message: ${err.message}`);
});
```
