# AVSessionController

AVSessionController控制器可查看会话ID，并可完成对会话发送命令及事件，获取会话元数据，播放状态信息等操作。

> **说明：**
> 
> - 本Interface首批接口从API version 10开始支持。
@interface AVSessionController [since 10 - 11]

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## destroy

```TypeScript
destroy(callback: AsyncCallback<void>): void
```

销毁当前控制器，销毁后当前控制器不可再用。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当控制器销毁成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.destroy((err: BusinessError) => {
  if (err) {
    console.error(`Failed to destroy, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in destroying.');
});
```

```TypeScript
avcontroller.destroy((err: BusinessError) => {
  if (err) {
    console.error(`Failed to destroy controller, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in destroying.');
});
```

## destroy

```TypeScript
destroy(): Promise<void>
```

销毁当前控制器，销毁后当前控制器不可再用。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。当控制器销毁成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
currentAVSession.destroy().then(() => {
  console.info('Succeeded in destroying.');
});
```

```TypeScript
avcontroller.destroy().then(() => {
  console.info('Succeeded in destroying.');
});
```

## getAVCallState

```TypeScript
getAVCallState(callback: AsyncCallback<AVCallState>): void
```

获取通话状态数据。结果通过callback异步回调方式返回。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 是 | 回调函数，返回通话状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getAVCallState((err: BusinessError, callstate: avSession.AVCallState) => {
  if (err) {
    console.error(`Failed to get AV call state, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting AV call state: ${callstate.state}`);
});
```

## getAVCallState

```TypeScript
getAVCallState(): Promise<AVCallState>
```

获取通话状态数据。结果通过Promise异步回调方式返回。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | Promise对象，返回通话状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getAVCallState().then((callstate: avSession.AVCallState) => {
  console.info(`Succeeded in getting AV call state: ${callstate.state}`);
});
```

## getAVMetadata

```TypeScript
getAVMetadata(callback: AsyncCallback<AVMetadata>): void
```

获取会话元数据。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AVMetadata&gt; | 是 | 回调函数，返回会话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getAVMetadata((err: BusinessError, metadata: avSession.AVMetadata) => {
  if (err) {
    console.error(`Failed to get AV metadata, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting AV metadata, assetId: ${metadata.assetId}`);
});
```

## getAVMetadata

```TypeScript
getAVMetadata(): Promise<AVMetadata>
```

获取会话元数据。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;AVMetadata & gt; | Promise对象，返回会话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getAVMetadata().then((metadata: avSession.AVMetadata) => {
  console.info(`Succeeded in getting AV metadata, assetId: ${metadata.assetId}`);
});
```

## getAVMetadataSync

```TypeScript
getAVMetadataSync(): AVMetadata
```

使用同步方法获取会话元数据。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AVMetadata | 会话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
let metaData: avSession.AVMetadata = avcontroller.getAVMetadataSync();
```

## getAVPlaybackState

```TypeScript
getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void
```

获取当前的远端播放状态。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | 是 | 回调函数，返回远端播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avCastController.getAVPlaybackState((err: BusinessError, state: avSession.AVPlaybackState) => {
  if (err) {
    console.error(`Failed to get AV playback state, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting AV playback state.');
});
```

```TypeScript
avcontroller.getAVPlaybackState((err: BusinessError, state: avSession.AVPlaybackState) => {
  if (err) {
    console.error(`Failed to get AV playback state, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting AV playback state.');
});
```

## getAVPlaybackState

```TypeScript
getAVPlaybackState(): Promise<AVPlaybackState>
```

获取当前的远端播放状态。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | Promise对象,返回远端播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avCastController.getAVPlaybackState().then((state: avSession.AVPlaybackState) => {
  console.info('Succeeded in getting AV playback state.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get AV playback state, code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
avcontroller.getAVPlaybackState().then((state: avSession.AVPlaybackState) => {
  console.info('Succeeded in getting AV playback state.');
});
```

## getAVPlaybackStateSync

```TypeScript
getAVPlaybackStateSync(): AVPlaybackState
```

使用同步方法获取当前会话的播放状态。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md) | 当前会话的播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
let playbackState: avSession.AVPlaybackState = avcontroller.getAVPlaybackStateSync();
```

## getAVQueueItems

```TypeScript
getAVQueueItems(callback: AsyncCallback<Array<AVQueueItem>>): void
```

获取当前播放列表相关信息。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;&gt; | 是 | 回调函数，返回播放列表队列。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getAVQueueItems((err: BusinessError, items: avSession.AVQueueItem[]) => {
  if (err) {
    console.error(`Failed to get AV queue items, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting AV queue items, length: ${items.length}`);
});
```

## getAVQueueItems

```TypeScript
getAVQueueItems(): Promise<Array<AVQueueItem>>
```

获取当前会话播放列表相关信息。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;&gt; | Promise对象。返回播放列表队列。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getAVQueueItems().then((items: avSession.AVQueueItem[]) => {
  console.info(`Succeeded in getting AV queue items, length: ${items.length}`);
});
```

## getAVQueueItemsSync

```TypeScript
getAVQueueItemsSync(): Array<AVQueueItem>
```

使用同步方法获取当前会话播放列表相关信息。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt; | 当前会话播放列表队列。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
let currentQueueItems: Array<avSession.AVQueueItem> = avcontroller.getAVQueueItemsSync();
```

## getAVQueueTitle

```TypeScript
getAVQueueTitle(callback: AsyncCallback<string>): void
```

获取当前播放列表的名称。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回播放列表名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getAVQueueTitle((err: BusinessError, title: string) => {
  if (err) {
    console.error(`Failed to get AV queue title, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting AV queue title: ${title}`);
});
```

## getAVQueueTitle

```TypeScript
getAVQueueTitle(): Promise<string>
```

获取当前会话播放列表的名称。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象。返回播放列表名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getAVQueueTitle().then((title: string) => {
  console.info(`Succeeded in getting AV queue title: ${title}`);
});
```

## getAVQueueTitleSync

```TypeScript
getAVQueueTitleSync(): string
```

使用同步方法获取当前会话播放列表的名称。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 当前会话播放列表名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
let currentQueueTitle: string = avcontroller.getAVQueueTitleSync();
```

## getCallMetadata

```TypeScript
getCallMetadata(callback: AsyncCallback<CallMetadata>): void
```

获取通话会话的元数据。结果通过callback异步回调方式返回。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 是 | 回调函数，返回会话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getCallMetadata((err: BusinessError, calldata: avSession.CallMetadata) => {
  if (err) {
    console.error(`Failed to get call metadata, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting call metadata, name: ${calldata.name}`);
});
```

## getCallMetadata

```TypeScript
getCallMetadata(): Promise<CallMetadata>
```

获取通话会话的元数据。结果通过Promise异步回调方式返回。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | Promise对象，返回会话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getCallMetadata().then((calldata: avSession.CallMetadata) => {
  console.info(`Succeeded in getting call metadata, name: ${calldata.name}`);
});
```

## getDesktopLyricState

```TypeScript
getDesktopLyricState(): Promise<DesktopLyricState>
```

获取当前会话桌面歌词状态。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md)&gt; | Promise对象。返回桌面歌词状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-应用程序的桌面歌词功能未开启) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-当前设备不支持桌面歌词功能) | The desktop lyrics feature is not supported. |

**示例**

```TypeScript
if (currentAVSession !== undefined) {
  (currentAVSession as avSession.AVSession).getDesktopLyricState()
    .then((state: avSession.DesktopLyricState) => {
    console.info(`getDesktopLyricState: ${state.isLocked}`);
  })
}
```

```TypeScript
avcontroller.getDesktopLyricState();
```

## getExtras

```TypeScript
getExtras(callback: AsyncCallback<{[key: string]: Object}>): void
```

获取媒体提供方设置的自定义媒体数据包。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;{[key: string]: Object}&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

**示例**

```TypeScript
avcontroller.getExtras((err: BusinessError, extras) => {
  if (err) {
    console.error(`Failed to get extras, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting extras: ${extras}`);
});
```

## getExtras

```TypeScript
getExtras(): Promise<{[key: string]: Object}>
```

获取媒体提供方设置的自定义媒体数据包。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;{[key: string]: Object | > } Promise对象，返回媒体提供方设置的自定义媒体数据包，数据包的内容与setExtras设置的内容完全一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

**示例**

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

根据远端分布式事件类型，获取远端分布式媒体提供方设置的自定义媒体数据包。使用Promise异步回调。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extraEvent | string | 是 | 远端分布式事件类型。可获取的事件类型来自于 setExtras)}。 对Wearable设备类型，额外提供以下预设的事件类型： 'AUDIO_GET_VOLUME'：获取远端设备音量。 'AUDIO_GET_AVAILABLE_DEVICES'：获取远端所有可连接设备。 'AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO'：获取远端实际发声设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ExtraInfo](arkts-avsession-avsession-extrainfo-t.md)&gt; | Promise对象，返回远端分布式媒体提供方设置的自定义媒体数据包。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |

**示例**

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

获取应用在会话中保存的WantAgent对象。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)&gt; | 是 | 回调函数。返回在 [setLaunchAbility](arkts-avsession-avsession-avsession-i.md#setlaunchability)保存的对象，包括应用的相关属性信息，如 bundleName，abilityName，deviceId等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getLaunchAbility((err: BusinessError, agent: WantAgent) => {
  if (err) {
    console.error(`Failed to get launch ability, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting launch ability: ${agent}`);
});
```

## getLaunchAbility

```TypeScript
getLaunchAbility(): Promise<WantAgent>
```

获取应用在会话中保存的WantAgent对象。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)&gt; | Promise对象，返回在 [setLaunchAbility]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getLaunchAbility().then((agent: WantAgent) => {
  console.info(`Succeeded in getting launch ability: ${agent}`);
});
```

## getMediaCenterControlType

```TypeScript
getMediaCenterControlType(): Promise<Array<AVMediaCenterControlType>>
```

获取应用通过[setMediaCenterControlType](arkts-avsession-avsession-avsession-i.md#setmediacentercontroltype)接口设置优先显示的控制类型列表。使用Promise异步 回调。如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md)&gt;&gt; | Promise对象。返回应用希望优先显示的控制类型列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getMediaCenterControlType().then((types: avSession.AVMediaCenterControlType[]) => {
  console.info(`Succeeded in getting media center control types, size: ${types.length}`);
});
```

## getOutputDevice

```TypeScript
getOutputDevice(callback: AsyncCallback<OutputDeviceInfo>): void
```

获取播放设备信息。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md)&gt; | 是 | 回调函数，返回播放设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 600101 | Session service exception. |
| 600103 | The session controller does not exist. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

currentAVSession.getOutputDevice((err: BusinessError, outputDeviceInfo: avSession.OutputDeviceInfo) => {
  if (err) {
    console.error(`Failed to get output device, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting output device, devices length: ${outputDeviceInfo.devices.length}`);
});
```

```TypeScript
avcontroller.getOutputDevice((err: BusinessError, deviceInfo: avSession.OutputDeviceInfo) => {
  if (err) {
    console.error(`Failed to get output device, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting output device.');
});
```

## getOutputDevice

```TypeScript
getOutputDevice(): Promise<OutputDeviceInfo>
```

获取播放设备信息。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md)&gt; | Promise对象，返回播放设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 600101 | Session service exception. |
| 600103 | The session controller does not exist. |

**示例**

```TypeScript
currentAVSession.getOutputDevice().then((outputDeviceInfo: avSession.OutputDeviceInfo) => {
  console.info(`Succeeded in getting output device, devices length: ${outputDeviceInfo.devices.length}`);
})
```

```TypeScript
avcontroller.getOutputDevice().then((deviceInfo: avSession.OutputDeviceInfo) => {
  console.info('Succeeded in getting output device.');
});
```

## getOutputDeviceSync

```TypeScript
getOutputDeviceSync(): OutputDeviceInfo
```

使用同步方法获取当前输出设备信息。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) | 当前输出设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
let currentOutputDevice: avSession.OutputDeviceInfo = currentAVSession.getOutputDeviceSync();
```

```TypeScript
let currentOutputDevice: avSession.OutputDeviceInfo = avcontroller.getOutputDeviceSync();
```

## getRealPlaybackPositionSync

```TypeScript
getRealPlaybackPositionSync(): number
```

使用同步方法获取当前播放位置。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 时间节点，毫秒数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
let time: number = avcontroller.getRealPlaybackPositionSync();
```

## getSupportedLoopModes

```TypeScript
getSupportedLoopModes(): Promise<Array<LoopMode>>
```

获取应用支持的循环模式列表。使用Promise异步回调。该列表通过[setSupportedLoopModes](arkts-avsession-avsession-avsession-i.md#setsupportedloopmodes)接口设置。如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[LoopMode](arkts-avsession-avsession-loopmode-e.md)&gt;&gt; | Promise对象。返回支持的循环模式列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getSupportedLoopModes().then((loopModes: avSession.LoopMode[]) => {
  console.info(`Succeeded in getting supported loop modes, size: ${loopModes.length}`);
});
```

## getSupportedPlaySpeeds

```TypeScript
getSupportedPlaySpeeds(): Promise<Array<number>>
```

获取应用支持的播放倍速列表。使用Promise异步回调。该列表通过[setSupportedPlaySpeeds](arkts-avsession-avsession-avsession-i.md#setsupportedplayspeeds)接口设置。如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;number & gt; & gt; | Promise对象。返回支持的播放倍速列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

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

```TypeScript
avcontroller.getSupportedPlaySpeeds().then((speeds: number[]) => {
  console.info(`Succeeded in getting supported play speeds, size: ${speeds.length}`);
});
```

## getValidCommands

```TypeScript
getValidCommands(callback: AsyncCallback<Array<AVControlCommandType>>): void
```

获取会话支持的有效命令。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;&gt; | 是 | 回调函数，返回有效命令的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getValidCommands((err: BusinessError, validCommands: avSession.AVControlCommandType[]) => {
  if (err) {
    console.error(`Failed to get valid commands, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting valid commands, size: ${validCommands.length}`);
});
```

## getValidCommands

```TypeScript
getValidCommands(): Promise<Array<AVControlCommandType>>
```

获取会话支持的有效命令。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;&gt; | Promise对象。返回有效命令的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.getValidCommands().then((validCommands: avSession.AVControlCommandType[]) => {
  console.info(`Succeeded in getting valid commands, size: ${validCommands.length}`);
});
```

## getValidCommandsSync

```TypeScript
getValidCommandsSync(): Array<AVControlCommandType>
```

使用同步方法获取会话支持的有效命令。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt; | 会话支持的有效命令的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
let validCommands: Array<avSession.AVControlCommandType> = avcontroller.getValidCommandsSync();
```

## isActive

```TypeScript
isActive(callback: AsyncCallback<boolean>): void
```

判断会话是否被激活。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.isActive((err: BusinessError, isActive: boolean) => {
  if (err) {
    console.error(`Failed to check active state, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking active state: ${isActive}`);
});
```

## isActive

```TypeScript
isActive(): Promise<boolean>
```

获取会话是否被激活。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象，返回会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.isActive().then((isActive: boolean) => {
  console.info(`Succeeded in checking active state: ${isActive}`);
});
```

## isActiveSync

```TypeScript
isActiveSync(): boolean
```

使用同步方法判断会话是否被激活。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| 会话是否为激活状态，true表示被激活，false表示禁用。 | 会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
let isActive: boolean = avcontroller.isActiveSync();
```

## isDesktopLyricEnabled

```TypeScript
isDesktopLyricEnabled(): Promise<boolean>
```

查询是否启用桌面歌词功能。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象。返回true表示启用桌面歌词功能；返回false表示不启用桌面歌词功能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600111](../errorcode-avsession.md#6600111-当前设备不支持桌面歌词功能) | The desktop lyrics feature is not supported. |

## isDesktopLyricVisible

```TypeScript
isDesktopLyricVisible(): Promise<boolean>
```

查询当前会话桌面歌词的显示状态。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象。返回true表示显示桌面歌词；返回false表示不显示桌面歌词。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-应用程序的桌面歌词功能未开启) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-当前设备不支持桌面歌词功能) | The desktop lyrics feature is not supported. |

**示例**

```TypeScript
if (currentAVSession !== undefined) {
  (currentAVSession as avSession.AVSession).isDesktopLyricVisible().then((visible: boolean) => {
    console.info(`isDesktopLyricVisible: ${visible}`);
  })
}
```

```TypeScript
avcontroller.isDesktopLyricVisible();
```

## off('metadataChange')

```TypeScript
off(type: 'metadataChange', callback?: (data: AVMetadata) => void)
```

取消元数据变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'metadataChange' | 是 |  |
| callback | (data: AVMetadata) = & gt; void | 否 | 回调函数，参数data是需要更新的元数据。只包含需要更新的元数据属性，并不代表当前全量的元数据。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('playbackStateChange')

```TypeScript
off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void)
```

取消播放状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | 是 |  |
| callback | (state: AVPlaybackState) = & gt; void | 否 | 回调函数，参数state是需要更新的播放状态。只包含需要更新的播放状态属性，并不代表当前全量的播放状态。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('callMetadataChange')

```TypeScript
off(type: 'callMetadataChange', callback?: Callback<CallMetadata>): void
```

取消设置通话元数据变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callMetadataChange' | 是 | 取消对应的监听事件，支持事件`'callMetadataChange'`。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 否 | 回调函数，参数calldata是变化后的通话原数据。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('callStateChange')

```TypeScript
off(type: 'callStateChange', callback?: Callback<AVCallState>): void
```

取消设置通话状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callStateChange' | 是 | 取消对应的监听事件，支持事件`'callStateChange'`。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 否 | 回调函数，参数callstate是变化后的通话状态。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('sessionDestroy')

```TypeScript
off(type: 'sessionDestroy', callback?: () => void)
```

取消监听会话的销毁事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | 是 | 取消对应的监听事件，支持事件`'sessionDestroy'`。 |
| callback | () = & gt; void | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('activeStateChange')

```TypeScript
off(type: 'activeStateChange', callback?: (isActive: boolean) => void)
```

取消监听会话激活状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activeStateChange' | 是 | 取消对应的监听事件，支持事件`'activeStateChange'`。 |
| callback | (isActive: boolean) = & gt; void | 否 | 回调函数。参数isActive表示会话是否被激活。true表示被激活，false表示禁用。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('validCommandChange')

```TypeScript
off(type: 'validCommandChange', callback?: (commands: Array<AVControlCommandType>) => void)
```

取消监听会话有效命令变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'validCommandChange' | 是 | 取消对应的监听事件，支持事件`'validCommandChange'`。 |
| callback | (commands: Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;) =&gt; void | 否 | 回调函数。参数commands是有效命令的集合。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('outputDeviceChange')

```TypeScript
off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void
```

取消监听分布式设备变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'outputDeviceChange' | 是 | 取消对应的监听事件，支持事件`'outputDeviceChange'`。 |
| callback | (state: ConnectionState, device: OutputDeviceInfo) = & gt; void | 否 | 回调函数，参数device是设备相关信息。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist |

## off('sessionEvent')

```TypeScript
off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {[key: string]: Object}) => void): void
```

取消会话事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionEvent' | 是 | 取消对应的监听事件，支持事件`'sessionEvent'`。 |
| callback | (sessionEvent: string, args: {[key: string]: Object}) = & gt; void | 否 | 回调函数，参数sessionEvent是变化的事件名，args为事件的参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('queueItemsChange')

```TypeScript
off(type: 'queueItemsChange', callback?: (items: Array<AVQueueItem>) => void): void
```

取消播放列表变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'queueItemsChange' | 是 | 取消对应的监听事件，支持事件`'queueItemsChange'`。 |
| callback | (items: Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;) =&gt; void | 否 | 回调函数，参数items是变化的播放列表。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('queueTitleChange')

```TypeScript
off(type: 'queueTitleChange', callback?: (title: string) => void): void
```

取消播放列表名称变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'queueTitleChange' | 是 | 取消对应的监听事件，支持事件`'queueTitleChange'`。 |
| callback | (title: string) = & gt; void | 否 | 回调函数，参数items是变化的播放列表名称。 该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('extrasChange')

```TypeScript
off(type: 'extrasChange', callback?: (extras: {[key: string]: Object}) => void): void
```

取消自定义媒体数据包变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'extrasChange' | 是 | 取消对应的监听事件，支持事件`'extrasChange'`。 |
| callback | (extras: {[key: string]: Object}) = & gt; void | 否 | 注册监听事件时的回调函数。 该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off('customDataChange')

```TypeScript
off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void
```

取消自定义数据监听。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'customDataChange' | 是 | 取消对应的监听事件，支持的事件是'customDataChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Object&gt;&gt; | 否 | 注册监听事件时的回调函数。该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offDesktopLyricEnabled

```TypeScript
offDesktopLyricEnabled(callback?: Callback<boolean>): void
```

取消桌面歌词启用状态变更事件监听，取消后将不再对该事件进行监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 该参数为可选参数，若不填写该参数，则认为取消所有桌面歌词功能启用状态变更事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.offDesktopLyricEnabled();
```

## offDesktopLyricStateChanged

```TypeScript
offDesktopLyricStateChanged(callback?: Callback<DesktopLyricState>): void
```

取消桌面歌词状态变更事件监听，取消后将不再对该事件进行监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md)&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 该参数为可选参数，若不填写该参数，则认为取消所有桌面歌词状态变更事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
if (currentAVSession !== undefined) {
  (currentAVSession as avSession.AVSession).offDesktopLyricStateChanged();
}
```

```TypeScript
avcontroller.offDesktopLyricStateChanged();
```

## offDesktopLyricVisibilityChanged

```TypeScript
offDesktopLyricVisibilityChanged(callback?: Callback<boolean>): void
```

取消显示桌面歌词状态变更事件监听，取消后将不再对该事件进行监听。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 该参数为可选参数，若不填写该参数，则认为取消所有显示桌面歌词状态变更事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
if (currentAVSession !== undefined) {
  (currentAVSession as avSession.AVSession).offDesktopLyricVisibilityChanged();
}
```

```TypeScript
avcontroller.offDesktopLyricVisibilityChanged();
```

## offMediaCenterControlTypeChanged

```TypeScript
offMediaCenterControlTypeChanged(callback?: Callback<Array<AVMediaCenterControlType>>): void
```

取消控制类型列表变化的监听事件。取消后将不再对该事件进行监听。其中控制类型列表由应用通过[setMediaCenterControlType](arkts-avsession-avsession-avsession-i.md#setmediacentercontroltype)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md)&gt;&gt; | 否 | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有控制类型列表变化事件取消监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.offMediaCenterControlTypeChanged();
```

## offSupportedLoopModesChange

```TypeScript
offSupportedLoopModesChange(callback?: Callback<Array<LoopMode>>): void
```

取消支持的循环模式列表变化事件监听。取消后将不再对该事件进行监听。其中循环模式列表由应用通过[setSupportedLoopModes](arkts-avsession-avsession-avsession-i.md#setsupportedloopmodes)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[LoopMode](arkts-avsession-avsession-loopmode-e.md)&gt;&gt; | 否 | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有支持的循环模式列表变化事件取消监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.offSupportedLoopModesChange();
```

## offSupportedPlaySpeedsChange

```TypeScript
offSupportedPlaySpeedsChange(callback?: Callback<Array<number>>): void
```

取消支持的播放倍速列表变化事件监听。取消后将不再对该事件进行监听。其中播放倍速列表由应用通过[setSupportedPlaySpeeds](arkts-avsession-avsession-avsession-i.md#setsupportedplayspeeds)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | 否 | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有支持的播放倍速列表变化事件取消监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.offSupportedPlaySpeedsChange();
```

## on('metadataChange')

```TypeScript
on(type: 'metadataChange', filter: Array<keyof AVMetadata> | 'all', callback: (data: AVMetadata) => void)
```

设置元数据变化的监听事件。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'metadataChange' | 是 |  |
| filter | Array & lt;keyof AVMetadata & gt; \ | 'all' | 是 | 'all'表示关注元数据所有字段变化；Array & lt;keyof AVMetadata & gt;表示关注Array中的字段变化。 |
| callback | (data: AVMetadata) = & gt; void | 是 | 回调函数，参数data是需要更新的元数据。只包含需要更新的元数据属性，不代表当前全量的元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('playbackStateChange')

```TypeScript
on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void)
```

设置播放状态变化的监听事件。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | 是 |  |
| filter | Array & lt;keyof AVPlaybackState & gt; \ | 'all' | 是 | 'all'表示关注播放状态所有字段更新。 Array & lt;keyof AVPlaybackstate & gt; 表示关注Array中的字段更新。 |
| callback | (state: AVPlaybackState) = & gt; void | 是 | 回调函数，参数state是需要更新的播放状态。只包含需要更新的播放状态属性，并不代表当前全量的播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('callMetadataChange')

```TypeScript
on(type: 'callMetadataChange', filter: Array<keyof CallMetadata> | 'all', callback: Callback<CallMetadata>): void
```

设置通话元数据变化的监听事件。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callMetadataChange' | 是 | 事件回调类型，支持事件`'callMetadataChange'`：当通话元数据变化时，触发该事件。 |
| filter | Array & lt;keyof CallMetadata & gt; \ | 'all' | 是 | 'all'表示关注通话元数据所有字段变化；Array & lt;keyof CallMetadata & gt; 表示关注Array中的字 段变化。\ | 'all'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 是 | 回调函数，参数callmetadata是变化后的通话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('callStateChange')

```TypeScript
on(type: 'callStateChange', filter: Array<keyof AVCallState> | 'all', callback: Callback<AVCallState>): void
```

设置通话状态变化的监听事件。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callStateChange' | 是 | 事件回调类型，支持事件`'callStateChange'`：当通话状态变化时，触发该事件。 |
| filter | Array & lt;keyof AVCallState & gt; \ | 'all' | 是 | 'all' 表示关注通话状态所有字段变化；Array & lt;keyof AVCallState & gt;表示关注Array中的字段变 化。\ | 'all'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 是 | 回调函数，参数callstate是变化后的通话状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('sessionDestroy')

```TypeScript
on(type: 'sessionDestroy', callback: () => void)
```

会话销毁的监听事件。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | 是 |  |
| callback | () = & gt; void | 是 | 回调函数。当监听事件注册成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('activeStateChange')

```TypeScript
on(type: 'activeStateChange', callback: (isActive: boolean) => void)
```

会话的激活状态的监听事件。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activeStateChange' | 是 | 事件回调类型，支持事件`'activeStateChange'`：当检测到会话的激活状态发生改变时，触发该事件。 |
| callback | (isActive: boolean) = & gt; void | 是 | 回调函数。参数isActive表示会话是否被激活。true表示被激活，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('validCommandChange')

```TypeScript
on(type: 'validCommandChange', callback: (commands: Array<AVControlCommandType>) => void)
```

会话支持的有效命令变化监听事件。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'validCommandChange' | 是 | 事件回调类型，支持事件`'validCommandChange'`：当检测到会话的合法命令发生改变时，触发该事件。 |
| callback | (commands: Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;) =&gt; void | 是 | 回调函数。参数commands是有效命令的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('outputDeviceChange')

```TypeScript
on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void
```

设置播放设备变化的监听事件。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'outputDeviceChange' | 是 | 事件回调类型，支持事件为`'outputDeviceChange'`：当播放设备变化时，触发该事件）。 |
| callback | (state: ConnectionState, device: OutputDeviceInfo) = & gt; void | 是 | 回调函数，参数device是设备相关信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist |

## on('sessionEvent')

```TypeScript
on(type: 'sessionEvent', callback: (sessionEvent: string, args: {[key: string]: Object}) => void): void
```

媒体控制器设置会话自定义事件变化的监听器。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionEvent' | 是 | 事件回调类型，支持事件`'sessionEvent'`：当会话事件变化时，触发该事件。 |
| callback | (sessionEvent: string, args: {[key: string]: Object}) = & gt; void | 是 | 回调函数，sessionEvent为变化的会话事件名，args为事件的参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('queueItemsChange')

```TypeScript
on(type: 'queueItemsChange', callback: (items: Array<AVQueueItem>) => void): void
```

媒体控制器设置会话自定义播放列表变化的监听器。每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'queueItemsChange' | 是 | 事件回调类型，支持事件`'queueItemsChange'`：当session修改播放列表时，触发该事件。 |
| callback | (items: Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;) =&gt; void | 是 | 回调函数，items为变化的播放列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('queueTitleChange')

```TypeScript
on(type: 'queueTitleChange', callback: (title: string) => void): void
```

媒体控制器设置会话自定义播放列表的名称变化的监听器。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'queueTitleChange' | 是 | 事件回调类型，支持事件`'queueTitleChange'`：当session修改播放列表名称时，触发该事件。 |
| callback | (title: string) = & gt; void | 是 | 回调函数，title为变化的播放列表名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('extrasChange')

```TypeScript
on(type: 'extrasChange', callback: (extras: {[key: string]: Object}) => void): void
```

媒体控制器设置自定义媒体数据包事件变化的监听器。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'extrasChange' | 是 | 事件回调类型，支持事件`'extrasChange'`：当媒体提供方设置自定义媒体数据包时，触发该事件。 |
| callback | (extras: {[key: string]: Object}) = & gt; void | 是 | 回调函数，extras为媒体提供方新设置的自定义媒体数据包，该自定义媒体数据包与dispatchSessionEvent方法设置的数据包完全一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('customDataChange')

```TypeScript
on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void
```

注册从远程设备发送的自定义数据的监听器。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'customDataChange' | 是 | 事件回调类型，支持事件'customDataChange'，当媒体提供方发送自定义数据时，触发该事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | 回调函数，用于接收自定义数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onDesktopLyricEnabled

```TypeScript
onDesktopLyricEnabled(callback: Callback<boolean>): void
```

桌面歌词功能启用状态变更的监听事件。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示桌面歌词功能启用；返回false表示桌面歌词功能未启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.onDesktopLyricEnabled((enabled: boolean) => {
  console.info(`desktop lyric enabled state : ${enabled}`);
})
```

## onDesktopLyricStateChanged

```TypeScript
onDesktopLyricStateChanged(callback: Callback<DesktopLyricState>): void
```

桌面歌词状态变更的监听事件。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md)&gt; | 是 | 回调函数。返回桌面歌词状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
if (currentAVSession !== undefined) {
  (currentAVSession as avSession.AVSession).onDesktopLyricStateChanged((state: avSession.DesktopLyricState) => {
    console.info(`desktop lyric isLocked : ${state.isLocked}`);
  })
}
```

```TypeScript
avcontroller.onDesktopLyricStateChanged((state: avSession.DesktopLyricState) => {
  console.info(`desktop lyric isLocked : ${state.isLocked}`);
})
```

## onDesktopLyricVisibilityChanged

```TypeScript
onDesktopLyricVisibilityChanged(callback: Callback<boolean>): void
```

显示桌面歌词状态变更的监听事件。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示开启显示桌面歌词状态；返回false表示关闭显示桌面歌词状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
if (currentAVSession !== undefined) {
  (currentAVSession as avSession.AVSession).onDesktopLyricVisibilityChanged((visible: boolean) => {
    console.info(`desktop lyric visible state: ${visible}`);
  });
}
```

```TypeScript
avcontroller.onDesktopLyricVisibilityChanged((visible: boolean) => {
  console.info(`desktop lyric visible state: ${visible}`);
});
```

## onMediaCenterControlTypeChanged

```TypeScript
onMediaCenterControlTypeChanged(callback: Callback<Array<AVMediaCenterControlType>>): void
```

注册控制类型列表变化的监听事件。使用callback异步回调。其中控制类型列表由应用通过[setMediaCenterControlType](arkts-avsession-avsession-avsession-i.md#setmediacentercontroltype)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md)&gt;&gt; | 是 | 回调函数。返回变化后的控制类型列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.onMediaCenterControlTypeChanged((types: avSession.AVMediaCenterControlType[]) => {
  console.info(`Media center control types changed, size: ${types.length}`);
});
```

## onSupportedLoopModesChange

```TypeScript
onSupportedLoopModesChange(callback: Callback<Array<LoopMode>>): void
```

注册支持的循环模式列表变化的监听事件。使用callback异步回调。其中循环模式列表由应用通过[setSupportedLoopModes](arkts-avsession-avsession-avsession-i.md#setsupportedloopmodes)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[LoopMode](arkts-avsession-avsession-loopmode-e.md)&gt;&gt; | 是 | 回调函数。返回变化后支持的循环模式列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.onSupportedLoopModesChange((loopModes: avSession.LoopMode[]) => {
  console.info(`Supported loop modes changed, size: ${loopModes.length}`);
});
```

## onSupportedPlaySpeedsChange

```TypeScript
onSupportedPlaySpeedsChange(callback: Callback<Array<number>>): void
```

注册支持的播放倍速列表变化的监听事件。使用callback异步回调。其中播放倍速列表由应用通过[setSupportedPlaySpeeds](arkts-avsession-avsession-avsession-i.md#setsupportedplayspeeds)接口设置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 回调函数。返回变化后支持的播放倍速列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avcontroller.onSupportedPlaySpeedsChange((speeds: number[]) => {
  console.info(`Supported play speeds changed, size: ${speeds.length}`);
});
```

## sendAVKeyEvent

```TypeScript
sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback<void>): void
```

发送按键事件到会话。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | 是 | 按键事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当事件发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 600101 | Session service exception. |
| 600102 | The session does not exist. |
| 600103 | The session controller does not exist. |
| 600105 | Invalid session command. |
| 600106 | The session is not activated. |

**示例**

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

## sendAVKeyEvent

```TypeScript
sendAVKeyEvent(event: KeyEvent): Promise<void>
```

发送按键事件到控制器对应的会话。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | 是 | 按键事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。当事件发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 600101 | Session service exception. |
| 600102 | The session does not exist. |
| 600103 | The session controller does not exist. |
| 600105 | Invalid session command. |
| 600106 | The session is not activated. |

**示例**

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

通过会话控制器发送自定义命令到其对应的会话。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | 需要设置的自定义控制命令的名称。 |
| args | {[key: string]: Object} | 是 | 需要传递的控制命令键值对。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-会话未激活) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

**示例**

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

## sendCommonCommand

```TypeScript
sendCommonCommand(command: string, args: {[key: string]: Object}): Promise<void>
```

通过会话控制器发送自定义控制命令到其对应的会话。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | 需要设置的自定义控制命令的名称。 |
| args | {[key: string]: Object} | 是 | 需要传递的控制命令键值对。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-会话未激活) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

**示例**

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

通过会话控制器发送命令到其对应的会话。结果通过callback异步回调方式返回。

> **说明：**
> 
> 媒体控制方在使用sendControlCommand命令前，需要确保控制对应的媒体会话注册了对应的监听，注册媒体会话相关监听的方法请参见接口
> on('play')、
> on('pause')等。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | 是 | 会话的相关命令和命令相关参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-会话未激活) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

**示例**

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

## sendControlCommand

```TypeScript
sendControlCommand(command: AVControlCommand): Promise<void>
```

通过控制器发送命令到其对应的会话。结果通过Promise异步回调方式返回。

> **说明：**
> 
> 媒体控制方在使用sendControlCommand命令前，需要确保控制对应的媒体会话注册了对应的监听，注册媒体会话相关监听的方法请参见接口
> on('play')、
> on('pause')等。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | 是 | 会话的相关命令和命令相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。当命令发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-会话未激活) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

**示例**

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

发送私有数据到远端设备。使用Promise异步回调。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record & lt;string, Object & gt; | 是 | 应用程序填充的自定义数据。服务端仅解析key为'customData'，且Object为string类型的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

```TypeScript
avCastController.sendCustomData({customData: 'This is custom data'}).then(() => {
  console.info('Succeeded in sending custom data.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send custom data, code: ${err.code}, message: ${err.message}`);
});
```

```TypeScript
currentAVSession.sendCustomData({customData : "This is custom data"}).then(() => {
  console.info('Succeeded in sending custom data.');
});
```

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

设置当前会话桌面歌词状态。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md) | 是 | 桌面歌词状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-应用程序的桌面歌词功能未开启) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-当前设备不支持桌面歌词功能) | The desktop lyrics feature is not supported. |

**示例**

```TypeScript
let state: avSession.DesktopLyricState = {
  isLocked: true,
};
currentAVSession.setDesktopLyricState(state).then(() => {
  console.info('Succeeded in setting desktop lyric state.');
})
```

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

设置当前会话桌面歌词的显示状态。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | 是否显示桌面歌词。true表示显示；false表示不显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-应用程序的桌面歌词功能未开启) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-当前设备不支持桌面歌词功能) | The desktop lyrics feature is not supported. |

**示例**

```TypeScript
currentAVSession.setDesktopLyricVisible(true).then(() => {
  console.info('Succeeded in setting desktop lyric visible.');
});
```

```TypeScript
avcontroller.setDesktopLyricVisible(true);
```

## skipToQueueItem

```TypeScript
skipToQueueItem(itemId: number, callback: AsyncCallback<void>): void
```

设置指定播放列表单项的ID，发送给session端处理，session端可以选择对这个单项歌曲进行播放。结果通过callback异步回调方式返回。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemId | number | 是 | 播放列表单项的ID值，用以表示选中的播放列表单项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当播放状态设置成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

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

## skipToQueueItem

```TypeScript
skipToQueueItem(itemId: number): Promise<void>
```

设置指定播放列表单项的ID，发送给session端处理，session端可以选择对这个单项歌曲进行播放。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemId | number | 是 | 播放列表单项的ID值，用以表示选中的播放列表单项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。当播放列表单项ID设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

**示例**

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

AVSessionController对象唯一的会话标识。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core
