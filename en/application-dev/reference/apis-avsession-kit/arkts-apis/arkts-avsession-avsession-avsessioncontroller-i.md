# AVSessionController

```TypeScript
interface AVSessionController
```

Session controller,used to control media playback and get media information

@interface AVSessionController [since 10 - 11]

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## destroy

```TypeScript
destroy(callback: AsyncCallback<void>): void
```

Destroy the server controller

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.destroy((err: BusinessError) => {
  if (err) {
    console.error(`Failed to destroy controller, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in destroying.');
});
```

<a id="destroy-1"></a>

## destroy

```TypeScript
destroy(): Promise<void>
```

Destroy the server controller

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.destroy().then(() => {
  console.info('Succeeded in destroying.');
});
```

## getAVCallState

```TypeScript
getAVCallState(callback: AsyncCallback<AVCallState>): void
```

Get the call status of the current session

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | Yes | The triggered asyncCallback when (getAVCallState). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVCallState((err: BusinessError, callstate: avSession.AVCallState) => {
  if (err) {
    console.error(`Failed to get AV call state, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting AV call state: ${callstate.state}`);
});
```

<a id="getavcallstate-1"></a>

## getAVCallState

```TypeScript
getAVCallState(): Promise<AVCallState>
```

Get the call status of the current session

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | (AVCallState) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVCallState().then((callstate: avSession.AVCallState) => {
  console.info(`Succeeded in getting AV call state: ${callstate.state}`);
});
```

## getAVMetadata

```TypeScript
getAVMetadata(callback: AsyncCallback<AVMetadata>): void
```

Get the metadata of the current session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVMetadata](arkts-avsession-avsession-avmetadata-i.md)&gt; | Yes | The triggered asyncCallback when (getAVMetadata). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVMetadata((err: BusinessError, metadata: avSession.AVMetadata) => {
  if (err) {
    console.error(`Failed to get AV metadata, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting AV metadata, assetId: ${metadata.assetId}`);
});
```

<a id="getavmetadata-1"></a>

## getAVMetadata

```TypeScript
getAVMetadata(): Promise<AVMetadata>
```

Get the metadata of the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVMetadata](arkts-avsession-avsession-avmetadata-i.md)&gt; | (AVMetadata) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVMetadata().then((metadata: avSession.AVMetadata) => {
  console.info(`Succeeded in getting AV metadata, assetId: ${metadata.assetId}`);
});
```

## getAVMetadataSync

```TypeScript
getAVMetadataSync(): AVMetadata
```

Get the metadata of the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| [AVMetadata](arkts-avsession-avsession-avmetadata-i.md) | (AVMetadata) returned |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let metaData: avSession.AVMetadata = avcontroller.getAVMetadataSync();
```

## getAVPlaybackState

```TypeScript
getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void
```

Get the playback status of the current session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | Yes | The triggered asyncCallback when (getAVPlaybackState). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVPlaybackState((err: BusinessError, state: avSession.AVPlaybackState) => {
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

Get the playback status of the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | (AVPlaybackState) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVPlaybackState().then((state: avSession.AVPlaybackState) => {
  console.info('Succeeded in getting AV playback state.');
});
```

## getAVPlaybackStateSync

```TypeScript
getAVPlaybackStateSync(): AVPlaybackState
```

Get the playback status of the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md) | (AVPlaybackState) returned |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let playbackState: avSession.AVPlaybackState = avcontroller.getAVPlaybackStateSync();
```

## getAVQueueItems

```TypeScript
getAVQueueItems(callback: AsyncCallback<Array<AVQueueItem>>): void
```

Get the playlist of the current session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;&gt; | Yes | The triggered asyncCallback when (getAVQueueItems). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVQueueItems((err: BusinessError, items: avSession.AVQueueItem[]) => {
  if (err) {
    console.error(`Failed to get AV queue items, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting AV queue items, length: ${items.length}`);
});
```

<a id="getavqueueitems-1"></a>

## getAVQueueItems

```TypeScript
getAVQueueItems(): Promise<Array<AVQueueItem>>
```

Get the playlist of the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;&gt; | (Array&lt;AVQueueItem&gt;) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVQueueItems().then((items: avSession.AVQueueItem[]) => {
  console.info(`Succeeded in getting AV queue items, length: ${items.length}`);
});
```

## getAVQueueItemsSync

```TypeScript
getAVQueueItemsSync(): Array<AVQueueItem>
```

Get the playlist of the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt; | (Array&lt;AVQueueItem&gt;) returned |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let currentQueueItems: Array<avSession.AVQueueItem> = avcontroller.getAVQueueItemsSync();
```

## getAVQueueTitle

```TypeScript
getAVQueueTitle(callback: AsyncCallback<string>): void
```

Get the name of the playlist of the current session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | The triggered asyncCallback when (getAVQueueTitle). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVQueueTitle((err: BusinessError, title: string) => {
  if (err) {
    console.error(`Failed to get AV queue title, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting AV queue title: ${title}`);
});
```

<a id="getavqueuetitle-1"></a>

## getAVQueueTitle

```TypeScript
getAVQueueTitle(): Promise<string>
```

Get the name of the playlist of the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | (string) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getAVQueueTitle().then((title: string) => {
  console.info(`Succeeded in getting AV queue title: ${title}`);
});
```

## getAVQueueTitleSync

```TypeScript
getAVQueueTitleSync(): string
```

Get the name of the playlist of the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | (string) returned |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let currentQueueTitle: string = avcontroller.getAVQueueTitleSync();
```

## getCallMetadata

```TypeScript
getCallMetadata(callback: AsyncCallback<CallMetadata>): void
```

Get the call metadata of the current session

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | Yes | The triggered asyncCallback when (getCallMetadata). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getCallMetadata((err: BusinessError, calldata: avSession.CallMetadata) => {
  if (err) {
    console.error(`Failed to get call metadata, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting call metadata, name: ${calldata.name}`);
});
```

<a id="getcallmetadata-1"></a>

## getCallMetadata

```TypeScript
getCallMetadata(): Promise<CallMetadata>
```

Get the call metadata of the current session

**Since:** 11

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | (CallMetadata) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getCallMetadata().then((calldata: avSession.CallMetadata) => {
  console.info(`Succeeded in getting call metadata, name: ${calldata.name}`);
});
```

## getDesktopLyricState

```TypeScript
getDesktopLyricState(): Promise<DesktopLyricState>
```

Get desktop lyric state such as lock state for this session.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md)&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-desktop-lyrics-not-enabled-for-the-application) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-desktop-lyrics-not-supported-for-the-current-device) | The desktop lyrics feature is not supported. |

**Examples**

```TypeScript
avcontroller.getDesktopLyricState();
```

## getExtras

```TypeScript
getExtras(callback: AsyncCallback<{[key: string]: Object}>): void
```

Get custom media packets provided by the corresponding session

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{[key: string]: Object}&gt; | Yes | The triggered asyncCallback when (getExtras). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-too-many-commands-or-events) | Too many commands or events. |

**Examples**

```TypeScript
avcontroller.getExtras((err: BusinessError, extras) => {
  if (err) {
    console.error(`Failed to get extras, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting extras: ${extras}`);
});
```

<a id="getextras-2"></a>

## getExtras

```TypeScript
getExtras(): Promise<{[key: string]: Object}>
```

Get custom media packets provided by the corresponding session

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{[key: string]: Object}&gt; | the parameters of extras |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-too-many-commands-or-events) | Too many commands or events. |

**Examples**

```TypeScript
// Index.ets
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  private tag: string = "createNewSession";
  private sessionId: string = "";
  private controller: avSession.AVSessionController | undefined = undefined;
  private currentAVSession?: avSession.AVSession;

  aboutToAppear(): void {

    avSession.createAVSession(this.getUIContext().getHostContext(), this.tag, "audio")
      .then(async (data: avSession.AVSession) => {
        this.currentAVSession = data;
        this.sessionId = this.currentAVSession.sessionId;
        this.controller = await this.currentAVSession.getController();
        console.info(`Succeeded in creating AV session, sessionId: ${this.sessionId}`);
        (this.controller as avSession.AVSessionController).getExtras().then((extras) => {
          console.info(`Succeeded in getting extras: ${extras}`);
        });
      });
  }

  build() {
    Column() {
      Text('AVSession Demo')
        .fontSize(20)
        .margin(10)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

## getExtrasWithEvent

```TypeScript
getExtrasWithEvent(extraEvent: string): Promise<ExtraInfo>
```

Get extra information for remote device, such as volume level, connected devices.

**Since:** 18

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| extraEvent | string | Yes | the event name to get |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ExtraInfo](arkts-avsession-avsession-extrainfo-t.md)&gt; | the value returned for such event |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |

**Examples**

```TypeScript
let controller: avSession.AVSessionController | undefined;
const COMMON_COMMAND_STRING_1 = 'AUDIO_GET_VOLUME';
const COMMON_COMMAND_STRING_2 = 'AUDIO_GET_AVAILABLE_DEVICES';
const COMMON_COMMAND_STRING_3 = 'AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO';
if (controller !== undefined) {
  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_1).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_1]}`);
  })

  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_2).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_2]}`);
  })

  controller.getExtrasWithEvent(COMMON_COMMAND_STRING_3).then(() => {
    console.info(`${[COMMON_COMMAND_STRING_3]}`);
  })
}
```

## getLaunchAbility

```TypeScript
getLaunchAbility(callback: AsyncCallback<WantAgent>): void
```

Get the [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md) of this session that can launch the session ability

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)&gt; | Yes | The asyncCallback triggered when getting the WantAgent. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
import { WantAgent } from '@kit.AbilityKit';

avcontroller.getLaunchAbility((err: BusinessError, agent: WantAgent) => {
  if (err) {
    console.error(`Failed to get launch ability, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting launch ability: ${agent}`);
});
```

<a id="getlaunchability-1"></a>

## getLaunchAbility

```TypeScript
getLaunchAbility(): Promise<WantAgent>
```

Get the [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md) of this session that can launch the session ability

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)&gt; | WantAgent promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
import { WantAgent } from '@kit.AbilityKit';

avcontroller.getLaunchAbility().then((agent: WantAgent) => {
  console.info(`Succeeded in getting launch ability: ${agent}`);
});
```

## getMediaCenterControlType

```TypeScript
getMediaCenterControlType(): Promise<Array<AVMediaCenterControlType>>
```

Get media control type that the can be displayed on the media center.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md)&gt;&gt; | The control types that the app sets to be displayed on the media center. The default value is empty, indicating that the types of the customized display control is not set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getMediaCenterControlType().then((types: avSession.AVMediaCenterControlType[]) => {
  console.info(`Succeeded in getting media center control types, size: ${types.length}`);
});
```

## getOutputDevice

```TypeScript
getOutputDevice(callback: AsyncCallback<OutputDeviceInfo>): void
```

Get output device information

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md)&gt; | Yes | The triggered asyncCallback when (getOutputDevice). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getOutputDevice((err: BusinessError, deviceInfo: avSession.OutputDeviceInfo) => {
  if (err) {
    console.error(`Failed to get output device, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting output device.');
});
```

<a id="getoutputdevice-1"></a>

## getOutputDevice

```TypeScript
getOutputDevice(): Promise<OutputDeviceInfo>
```

Get output device information

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md)&gt; | (OutputDeviceInfo) returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getOutputDevice().then((deviceInfo: avSession.OutputDeviceInfo) => {
  console.info('Succeeded in getting output device.');
});
```

## getOutputDeviceSync

```TypeScript
getOutputDeviceSync(): OutputDeviceInfo
```

Get output device information

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) | (OutputDeviceInfo) returned |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let currentOutputDevice: avSession.OutputDeviceInfo = avcontroller.getOutputDeviceSync();
```

## getRealPlaybackPositionSync

```TypeScript
getRealPlaybackPositionSync(): number
```

Get the adjusted playback position. The time automatically calculated by the system taking into account factors such as playback status, playback speed, and application update time.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | current playback position in ms.Note that the returns value of each call will be different. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let time: number = avcontroller.getRealPlaybackPositionSync();
```

## getSupportedLoopModes

```TypeScript
getSupportedLoopModes(): Promise<Array<LoopMode>>
```

Get supported loop modes supplied by application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[LoopMode](arkts-avsession-avsession-loopmode-e.md)&gt;&gt; | supported loop modes returned through promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getSupportedLoopModes().then((loopModes: avSession.LoopMode[]) => {
  console.info(`Succeeded in getting supported loop modes, size: ${loopModes.length}`);
});
```

## getSupportedPlaySpeeds

```TypeScript
getSupportedPlaySpeeds(): Promise<Array<number>>
```

Get supported speeds supplied by application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getSupportedPlaySpeeds().then((speeds: number[]) => {
  console.info(`Succeeded in getting supported play speeds, size: ${speeds.length}`);
});
```

## getValidCommands

```TypeScript
getValidCommands(callback: AsyncCallback<Array<AVControlCommandType>>): void
```

Get commands supported by the current session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;&gt; | Yes | The triggered asyncCallback when (getValidCommands). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getValidCommands((err: BusinessError, validCommands: avSession.AVControlCommandType[]) => {
  if (err) {
    console.error(`Failed to get valid commands, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting valid commands, size: ${validCommands.length}`);
});
```

<a id="getvalidcommands-1"></a>

## getValidCommands

```TypeScript
getValidCommands(): Promise<Array<AVControlCommandType>>
```

Get commands supported by the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;&gt; | array of AVControlCommandType promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.getValidCommands().then((validCommands: avSession.AVControlCommandType[]) => {
  console.info(`Succeeded in getting valid commands, size: ${validCommands.length}`);
});
```

## getValidCommandsSync

```TypeScript
getValidCommandsSync(): Array<AVControlCommandType>
```

Get commands supported by the current session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt; | array of AVControlCommandType |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let validCommands: Array<avSession.AVControlCommandType> = avcontroller.getValidCommandsSync();
```

## isActive

```TypeScript
isActive(callback: AsyncCallback<boolean>): void
```

Check if the current session is active

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | The triggered asyncCallback when (isActive). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.isActive((err: BusinessError, isActive: boolean) => {
  if (err) {
    console.error(`Failed to check active state, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking active state: ${isActive}`);
});
```

<a id="isactive-1"></a>

## isActive

```TypeScript
isActive(): Promise<boolean>
```

Check if the current session is active

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | boolean promise |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.isActive().then((isActive: boolean) => {
  console.info(`Succeeded in checking active state: ${isActive}`);
});
```

## isActiveSync

```TypeScript
isActiveSync(): boolean
```

Check if the current session is active

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | boolean |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let isActive: boolean = avcontroller.isActiveSync();
```

## isDesktopLyricEnabled

```TypeScript
isDesktopLyricEnabled(): Promise<boolean>
```

Query desktop lyric enabled state for this session.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | return the enabled status |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600111](../errorcode-avsession.md#6600111-desktop-lyrics-not-supported-for-the-current-device) | The desktop lyrics feature is not supported. |

## isDesktopLyricVisible

```TypeScript
isDesktopLyricVisible(): Promise<boolean>
```

Query desktop lyric visible state for this session.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | return desktop lyric visible state |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-desktop-lyrics-not-enabled-for-the-application) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-desktop-lyrics-not-supported-for-the-current-device) | The desktop lyrics feature is not supported. |

**Examples**

```TypeScript
avcontroller.isDesktopLyricVisible();
```

## off('metadataChange')

```TypeScript
off(type: 'metadataChange', callback?: (data: AVMetadata) => void)
```

Unregister metadata changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'metadataChange' | Yes |  |
| callback | (data: AVMetadata) =&gt; void | No | The callback used to handle metadata changed event. The callback function provides the [AVMetadata](arkts-avsession-avsession-avmetadata-i.md) parameter. It only contains the properties set in the filter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('metadataChange');
```

## off('playbackStateChange')

```TypeScript
off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void)
```

Unregister playback state changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

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
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('playbackStateChange');
```

## off('callMetadataChange')

```TypeScript
off(type: 'callMetadataChange', callback?: Callback<CallMetadata>): void
```

Unregister call metadata changed callback

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'callMetadataChange' | Yes | 'callMetadataChange' |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | No | The callback used to handle call metadata changed event. The callback function provides the [CallMetadata](arkts-avsession-avsession-callmetadata-i.md) parameter. It only contains the properties set in the filter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('callMetadataChange');
```

## off('callStateChange')

```TypeScript
off(type: 'callStateChange', callback?: Callback<AVCallState>): void
```

Unregister playback state changed callback

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'callStateChange' | Yes | 'callStateChange' |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | No | The callback used to handle call state changed event. The callback function provides the [AVCallState](arkts-avsession-avsession-avcallstate-i.md) parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('callStateChange');
```

## off('sessionDestroy')

```TypeScript
off(type: 'sessionDestroy', callback?: () => void)
```

Unregister current session destroyed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | Yes | 'sessionDestroy' |
| callback | () =&gt; void | No | The callback used to handle current session destroyed event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('sessionDestroy');
```

## off('activeStateChange')

```TypeScript
off(type: 'activeStateChange', callback?: (isActive: boolean) => void)
```

Unregister the active state of this session changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'activeStateChange' | Yes | 'activeStateChange' |
| callback | (isActive: boolean) =&gt; void | No | The callback used to handle the active state of this session changed event. The callback function provides the changed session state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('activeStateChange');
```

## off('validCommandChange')

```TypeScript
off(type: 'validCommandChange', callback?: (commands: Array<AVControlCommandType>) => void)
```

Unregister the valid commands of the session changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'validCommandChange' | Yes | 'validCommandChange' |
| callback | (commands: Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;) =&gt; void | No | The callback used to handle the changes. The callback function provides an array of AVControlCommandType. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('validCommandChange');
```

## off('outputDeviceChange')

```TypeScript
off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void
```

Unregister session output device change callback

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'outputDeviceChange' | Yes | Registration Type 'outputDeviceChange' |
| callback | (state: ConnectionState, device: OutputDeviceInfo) =&gt; void | No | Used to handle output device changed. The callback provide the new device info [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) and related connection state [ConnectionState](arkts-avsession-avsession-connectionstate-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('outputDeviceChange');
```

## off('sessionEvent')

```TypeScript
off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {[key: string]: Object}) => void): void
```

Unregister session event callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sessionEvent' | Yes | 'sessionEvent' |
| callback | (sessionEvent: string, args: {[key: string]: Object}) =&gt; void | No | Used to cancel a specific listener The callback function provides the event string and key-value pair parameters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('sessionEvent');
```

## off('queueItemsChange')

```TypeScript
off(type: 'queueItemsChange', callback?: (items: Array<AVQueueItem>) => void): void
```

Unregister session playlist change callback

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'queueItemsChange' | Yes | Registration Type 'queueItemsChange' |
| callback | (items: Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;) =&gt; void | No | Used to handle playlist changed. The callback provides the new array of AVQueueItem [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

## off('queueTitleChange')

```TypeScript
off(type: 'queueTitleChange', callback?: (title: string) => void): void
```

Unregister the name of session playlist change callback

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'queueTitleChange' | Yes | Registration Type 'queueTitleChange' |
| callback | (title: string) =&gt; void | No | Used to handle name of playlist changed. The callback provides the new name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('queueTitleChange');
```

## off('extrasChange')

```TypeScript
off(type: 'extrasChange', callback?: (extras: {[key: string]: Object}) => void): void
```

Unregister the custom media packets change callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'extrasChange' | Yes | Registration Type 'extrasChange' |
| callback | (extras: {[key: string]: Object}) =&gt; void | No | Used to handle custom media packets changed. The callback provides the new media packets. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('extrasChange');
```

## off('customDataChange')

```TypeScript
off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void
```

Unregister listener for custom data.

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
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.off('customDataChange');
```

## offDesktopLyricEnabled

```TypeScript
offDesktopLyricEnabled(callback?: Callback<boolean>): void
```

Unregister desktop lyric enable state change callback.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | a callback to receive desktop lyric enable state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.offDesktopLyricEnabled();
```

## offDesktopLyricStateChanged

```TypeScript
offDesktopLyricStateChanged(callback?: Callback<DesktopLyricState>): void
```

Unregister desktop lyric state changed callback.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md)&gt; | No | a callback to receive desktop lyric state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.offDesktopLyricStateChanged();
```

## offDesktopLyricVisibilityChanged

```TypeScript
offDesktopLyricVisibilityChanged(callback?: Callback<boolean>): void
```

Unregister desktop lyric visible state change callback.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | No | a callback to receive desktop lyric window visible state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.offDesktopLyricVisibilityChanged();
```

## offMediaCenterControlTypeChanged

```TypeScript
offMediaCenterControlTypeChanged(callback?: Callback<Array<AVMediaCenterControlType>>): void
```

Unregister media center control type changed callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md)&gt;&gt; | No | Callback to receive the changed control types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.offMediaCenterControlTypeChanged();
```

## offSupportedLoopModesChange

```TypeScript
offSupportedLoopModesChange(callback?: Callback<Array<LoopMode>>): void
```

Unregister listener for supported loop modes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[LoopMode](arkts-avsession-avsession-loopmode-e.md)&gt;&gt; | No | Callback used to retrieve supported loop modes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

## offSupportedPlaySpeedsChange

```TypeScript
offSupportedPlaySpeedsChange(callback?: Callback<Array<number>>): void
```

Unregister listener for supported play speeds.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | No | Callback used to retrieve supported play speeds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.offSupportedPlaySpeedsChange();
```

## on('metadataChange')

```TypeScript
on(type: 'metadataChange', filter: Array<keyof AVMetadata> | 'all', callback: (data: AVMetadata) => void)
```

Register metadata changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'metadataChange' | Yes |  |
| filter | Array&lt;keyof AVMetadata&gt; &#124; 'all' | Yes | The properties of [AVMetadata](arkts-avsession-avsession-avmetadata-i.md) that you cared about |
| callback | (data: AVMetadata) =&gt; void | Yes | The callback used to handle metadata changed event. The callback function provides the [AVMetadata](arkts-avsession-avsession-avmetadata-i.md) parameter. It only contains the properties set in the filter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('metadataChange', 'all', (metadata: avSession.AVMetadata) => {
  console.info(`on metadataChange assetId : ${metadata.assetId}`);
});

avcontroller.on('metadataChange', ['assetId', 'title', 'description'], (metadata: avSession.AVMetadata) => {
  console.info(`on metadataChange assetId : ${metadata.assetId}`);
});
```

## on('playbackStateChange')

```TypeScript
on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void)
```

Register playback state changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

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
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('playbackStateChange', 'all', (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});

avcontroller.on('playbackStateChange', ['state', 'speed', 'loopMode'], (playbackState: avSession.AVPlaybackState) => {
  console.info(`on playbackStateChange state : ${playbackState.state}`);
});
```

## on('callMetadataChange')

```TypeScript
on(type: 'callMetadataChange', filter: Array<keyof CallMetadata> | 'all', callback: Callback<CallMetadata>): void
```

Register call metadata changed callback

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'callMetadataChange' | Yes | 'callMetadataChange' |
| filter | Array&lt;keyof CallMetadata&gt; &#124; 'all' | Yes | The properties of [CallMetadata](arkts-avsession-avsession-callmetadata-i.md) that you cared about |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | Yes | The callback used to handle call metadata changed event. The callback function provides the [CallMetadata](arkts-avsession-avsession-callmetadata-i.md) parameter. It only contains the properties set in the filter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('callMetadataChange', 'all', (callmetadata: avSession.CallMetadata) => {
  console.info(`on callMetadataChange state : ${callmetadata.name}`);
});

avcontroller.on('callMetadataChange', ['name'], (callmetadata: avSession.CallMetadata) => {
  console.info(`on callMetadataChange state : ${callmetadata.name}`);
});
```

## on('callStateChange')

```TypeScript
on(type: 'callStateChange', filter: Array<keyof AVCallState> | 'all', callback: Callback<AVCallState>): void
```

Register call state changed callback

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'callStateChange' | Yes | 'callStateChange' |
| filter | Array&lt;keyof AVCallState&gt; &#124; 'all' | Yes | The properties of [AVCallState](arkts-avsession-avsession-avcallstate-i.md) that you cared about |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | Yes | The callback used to handle call state changed event. The callback function provides the [AVCallState](arkts-avsession-avsession-avcallstate-i.md) parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('callStateChange', 'all', (callstate: avSession.AVCallState) => {
  console.info(`on callStateChange state : ${callstate.state}`);
});

avcontroller.on('callStateChange', ['state'], (callstate: avSession.AVCallState) => {
  console.info(`on callStateChange state : ${callstate.state}`);
});
```

## on('sessionDestroy')

```TypeScript
on(type: 'sessionDestroy', callback: () => void)
```

Register current session destroyed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | Yes |  |
| callback | () =&gt; void | Yes | The callback used to handle current session destroyed event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('sessionDestroy', () => {
  console.info('Succeeded in session destroy.');
});
```

## on('activeStateChange')

```TypeScript
on(type: 'activeStateChange', callback: (isActive: boolean) => void)
```

Register the active state of this session changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'activeStateChange' | Yes | 'activeStateChange' |
| callback | (isActive: boolean) =&gt; void | Yes | The callback used to handle the active state of this session changed event. The callback function provides the changed session state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('activeStateChange', (isActive: boolean) => {
  console.info(`Succeeded in active state change: ${isActive}`);
});
```

## on('validCommandChange')

```TypeScript
on(type: 'validCommandChange', callback: (commands: Array<AVControlCommandType>) => void)
```

Register the valid commands of the session changed callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'validCommandChange' | Yes | 'validCommandChange' |
| callback | (commands: Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;) =&gt; void | Yes | The callback used to handle the changes. The callback function provides an array of AVControlCommandType. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('validCommandChange', (validCommands: avSession.AVControlCommandType[]) => {
  console.info(`Succeeded in valid command change, size: ${validCommands.length}`);
  console.info(`Succeeded in valid command change, validCommands: ${validCommands.values()}`);
});
```

## on('outputDeviceChange')

```TypeScript
on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void
```

Register session output device change callback

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'outputDeviceChange' | Yes | Registration Type 'outputDeviceChange' |
| callback | (state: ConnectionState, device: OutputDeviceInfo) =&gt; void | Yes | Used to handle output device changed. The callback provide the new device info [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) and related connection state [ConnectionState](arkts-avsession-avsession-connectionstate-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('outputDeviceChange', (state: avSession.ConnectionState, device: avSession.OutputDeviceInfo) => {
  console.info(`on outputDeviceChange state: ${state}, device : ${device}`);
});
```

## on('sessionEvent')

```TypeScript
on(type: 'sessionEvent', callback: (sessionEvent: string, args: {[key: string]: Object}) => void): void
```

Register session event callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sessionEvent' | Yes | 'sessionEvent' |
| callback | (sessionEvent: string, args: {[key: string]: Object}) =&gt; void | Yes | The callback used to handle session event changed event. The callback function provides the event string and key-value pair parameters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
// Index.ets
avcontroller.on('sessionEvent', (sessionEvent, args) => {
  console.info(`OnSessionEvent, sessionEvent is ${sessionEvent}, args: ${JSON.stringify(args)}`);
});
```

## on('queueItemsChange')

```TypeScript
on(type: 'queueItemsChange', callback: (items: Array<AVQueueItem>) => void): void
```

Register session playlist change callback

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'queueItemsChange' | Yes | Registration Type 'queueItemsChange' |
| callback | (items: Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;) =&gt; void | Yes | Used to handle playlist changed. The callback provides the new array of AVQueueItem [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

## on('queueTitleChange')

```TypeScript
on(type: 'queueTitleChange', callback: (title: string) => void): void
```

Register the name of session playlist change callback

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'queueTitleChange' | Yes | Registration Type 'queueTitleChange' |
| callback | (title: string) =&gt; void | Yes | Used to handle name of playlist changed. The callback provides the new name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('queueTitleChange', (title: string) => {
  console.info(`queueTitleChange, title is ${title}`);
});
```

## on('extrasChange')

```TypeScript
on(type: 'extrasChange', callback: (extras: {[key: string]: Object}) => void): void
```

Register the custom media packets change callback

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'extrasChange' | Yes | Registration Type 'extrasChange' |
| callback | (extras: {[key: string]: Object}) =&gt; void | Yes | Used to handle custom media packets changed. The callback provides the new media packets. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('extrasChange', (extras) => {
  console.info(`Caught extrasChange event,the new extra is: ${JSON.stringify(extras)}`);
});
```

## on('customDataChange')

```TypeScript
on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void
```

Register listener for custom data.

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
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.on('customDataChange', (data) => {
  console.info(`Caught customDataChange event,the new data is: ${JSON.stringify(data)}`);
});
```

## onDesktopLyricEnabled

```TypeScript
onDesktopLyricEnabled(callback: Callback<boolean>): void
```

Register desktop lyric enable state change callback.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | a callback to receive desktop lyric enable state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.onDesktopLyricEnabled((enabled: boolean) => {
  console.info(`desktop lyric enabled state : ${enabled}`);
})
```

## onDesktopLyricStateChanged

```TypeScript
onDesktopLyricStateChanged(callback: Callback<DesktopLyricState>): void
```

Register desktop lyric state changed callback.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md)&gt; | Yes | a callback to receive desktop lyric state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.onDesktopLyricStateChanged((state: avSession.DesktopLyricState) => {
  console.info(`desktop lyric isLocked : ${state.isLocked}`);
})
```

## onDesktopLyricVisibilityChanged

```TypeScript
onDesktopLyricVisibilityChanged(callback: Callback<boolean>): void
```

Register desktop lyric visible state change callback.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | a callback to receive desktop lyric window visible state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.onDesktopLyricVisibilityChanged((visible: boolean) => {
  console.info(`desktop lyric visible state: ${visible}`);
});
```

## onMediaCenterControlTypeChanged

```TypeScript
onMediaCenterControlTypeChanged(callback: Callback<Array<AVMediaCenterControlType>>): void
```

Register media center control type changed callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md)&gt;&gt; | Yes | Callback to receive the changed control types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.onMediaCenterControlTypeChanged((types: avSession.AVMediaCenterControlType[]) => {
  console.info(`Media center control types changed, size: ${types.length}`);
});
```

## onSupportedLoopModesChange

```TypeScript
onSupportedLoopModesChange(callback: Callback<Array<LoopMode>>): void
```

Register listener for supported loop modes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[LoopMode](arkts-avsession-avsession-loopmode-e.md)&gt;&gt; | Yes | Callback used to retrieve supported loop modes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.onSupportedLoopModesChange((loopModes: avSession.LoopMode[]) => {
  console.info(`Supported loop modes changed, size: ${loopModes.length}`);
});
```

## onSupportedPlaySpeedsChange

```TypeScript
onSupportedPlaySpeedsChange(callback: Callback<Array<number>>): void
```

Register listener for supported play speeds.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback used to retrieve supported play speeds. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
avcontroller.onSupportedPlaySpeedsChange((speeds: number[]) => {
  console.info(`Supported play speeds changed, size: ${speeds.length}`);
});
```

## sendAVKeyEvent

```TypeScript
sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback<void>): void
```

Send media key event to this session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | Yes | The KeyEvent |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-session-not-activated) | The session is not activated. |

**Examples**

```TypeScript
import { Key, KeyEvent } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyItem: Key = {code:0x49, pressedTime:2, deviceId:0};
let event:KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};
avcontroller.sendAVKeyEvent(event, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send AV key event, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in sending AV key event.');
});
```

<a id="sendavkeyevent-1"></a>

## sendAVKeyEvent

```TypeScript
sendAVKeyEvent(event: KeyEvent): Promise<void>
```

Send media key event to this session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | Yes | The KeyEvent |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-session-not-activated) | The session is not activated. |

**Examples**

```TypeScript
import { Key, KeyEvent } from '@kit.InputKit';

let keyItem: Key = {code:0x49, pressedTime:2, deviceId:0};
let event:KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};

avcontroller.sendAVKeyEvent(event).then(() => {
  console.info('Succeeded in sending AV key event.');
});
```

## sendCommonCommand

```TypeScript
sendCommonCommand(command: string, args: {[key: string]: Object}, callback: AsyncCallback<void>): void
```

Send common commands to this session

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | string | Yes | The command name to be sent. |
| args | {[key: string]: Object} | Yes | The parameters of session event |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-session-not-activated) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-too-many-commands-or-events) | Too many commands or events. |

**Examples**

```TypeScript
let commandName = "my_command";
avcontroller.sendCommonCommand(commandName, {command : "This is my command"}, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send common command, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in sending common command.');
})
```

<a id="sendcommoncommand-2"></a>

## sendCommonCommand

```TypeScript
sendCommonCommand(command: string, args: {[key: string]: Object}): Promise<void>
```

Send common commands to this session

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | string | Yes | The command name to be sent. |
| args | {[key: string]: Object} | Yes | The parameters of session event |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-session-not-activated) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-too-many-commands-or-events) | Too many commands or events. |

**Examples**

```TypeScript
let commandName = "my_command";
avcontroller.sendCommonCommand(commandName, {command : "This is my command"}).then(() => {
  console.info('Succeeded in sending common command.');
});
```

## sendControlCommand

```TypeScript
sendControlCommand(command: AVControlCommand, callback: AsyncCallback<void>): void
```

Send control commands to this session

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | Yes | The command to be sent. See [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-session-not-activated) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-too-many-commands-or-events) | Too many commands or events. |

**Examples**

```TypeScript
let avCommand: avSession.AVControlCommand = {command:'play'};
avcontroller.sendControlCommand(avCommand, (err: BusinessError) => {
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
sendControlCommand(command: AVControlCommand): Promise<void>
```

Send control commands to this session

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| command | [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | Yes | The command to be sent. See [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-invalid-session-command) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-session-not-activated) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-too-many-commands-or-events) | Too many commands or events. |

**Examples**

```TypeScript
let avCommand: avSession.AVControlCommand = {command:'play'};
avcontroller.sendControlCommand(avCommand).then(() => {
  console.info('Succeeded in sending control command.');
});
```

## sendCustomData

```TypeScript
sendCustomData(data: Record<string, Object>): Promise<void>
```

Send custom data to this avsession.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | Yes | The custom data populated by application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void result promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. You are advised to:1.Scheduled retry.2.Destroy the current session or session controller and re-create it. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
// Index.ets
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  private tag: string = "createNewSession";
  private sessionId: string = "";
  private controller: avSession.AVSessionController | undefined = undefined;
  private currentAVSession?: avSession.AVSession;

  aboutToAppear(): void {
    avSession.createAVSession(this.getUIContext().getHostContext(), this.tag, "audio")
      .then(async (data: avSession.AVSession) => {
        this.currentAVSession = data;
        this.sessionId = this.currentAVSession.sessionId;
        this.controller = await this.currentAVSession.getController();
        console.info(`Succeeded in creating AV session, sessionId: ${this.sessionId}`);
        (this.controller as avSession.AVSessionController).sendCustomData({ customData: "This is my data" });
      });
  }

  build() {
    Column() {
      Text('AVSession Demo')
        .fontSize(20)
        .margin(10)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

## setDesktopLyricState

```TypeScript
setDesktopLyricState(state: DesktopLyricState): Promise<void>
```

Set desktop lyric state such as lock state for this session.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md) | Yes | The desktop lyric state |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-desktop-lyrics-not-enabled-for-the-application) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-desktop-lyrics-not-supported-for-the-current-device) | The desktop lyrics feature is not supported. |

**Examples**

```TypeScript
let state: avSession.DesktopLyricState = {
  isLocked: true,
};
avcontroller.setDesktopLyricState(state);
```

## setDesktopLyricVisible

```TypeScript
setDesktopLyricVisible(visible: boolean): Promise<void>
```

Set desktop lyric visible state for this session.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| visible | boolean | Yes | make desktop lyric window visible or not |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-desktop-lyrics-not-enabled-for-the-application) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-desktop-lyrics-not-supported-for-the-current-device) | The desktop lyrics feature is not supported. |

**Examples**

```TypeScript
avcontroller.setDesktopLyricVisible(true);
```

## skipToQueueItem

```TypeScript
skipToQueueItem(itemId: number, callback: AsyncCallback<void>): void
```

Set the item in the playlist to be played

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| itemId | number | Yes | The serial number of the item to be played |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The asyncCallback triggered when the command is executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let queueItemId = 0;
avcontroller.skipToQueueItem(queueItemId, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to skip to queue item, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in skipping to queue item.');
});
```

<a id="skiptoqueueitem-1"></a>

## skipToQueueItem

```TypeScript
skipToQueueItem(itemId: number): Promise<void>
```

Set the item in the playlist to be played

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| itemId | number | Yes | The serial number of the item to be played |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-session-controller-does-not-exist) | The session controller does not exist. |

**Examples**

```TypeScript
let queueItemId = 0;
avcontroller.skipToQueueItem(queueItemId).then(() => {
  console.info('Succeeded in skipping to queue item.');
});
```

## sessionId

```TypeScript
readonly sessionId: string
```

Unique session Id

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core
