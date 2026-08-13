# AVSessionController

AVSessionController控制器可查看会话ID，并可完成对会话发送命令及事件，获取会话元数据，播放状态信息等操作。 > **说明：** > > - 本Interface首批接口从API version 10开始支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-avSession-interface AVSessionController--><!--Device-avSession-interface AVSessionController-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## destroy

```TypeScript
destroy(callback: AsyncCallback<void>): void
```

销毁当前控制器，销毁后当前控制器不可再用。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-destroy(callback: AsyncCallback<void>): void--><!--Device-AVSessionController-destroy(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当控制器销毁成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## destroy

```TypeScript
destroy(): Promise<void>
```

销毁当前控制器，销毁后当前控制器不可再用。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-destroy(): Promise<void>--><!--Device-AVSessionController-destroy(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当控制器销毁成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getAVCallState

```TypeScript
getAVCallState(callback: AsyncCallback<AVCallState>): void
```

获取通话状态数据。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getAVCallState(callback: AsyncCallback<AVCallState>): void--><!--Device-AVSessionController-getAVCallState(callback: AsyncCallback<AVCallState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 是 | 回调函数，返回通话状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getAVCallState

```TypeScript
getAVCallState(): Promise<AVCallState>
```

获取通话状态数据。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getAVCallState(): Promise<AVCallState>--><!--Device-AVSessionController-getAVCallState(): Promise<AVCallState>-End-->

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

## getAVMetadata

```TypeScript
getAVMetadata(callback: AsyncCallback<AVMetadata>): void
```

获取会话元数据。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getAVMetadata(callback: AsyncCallback<AVMetadata>): void--><!--Device-AVSessionController-getAVMetadata(callback: AsyncCallback<AVMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;AVMetadata&gt; | 是 | 回调函数，返回会话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getAVMetadata

```TypeScript
getAVMetadata(): Promise<AVMetadata>
```

获取会话元数据。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getAVMetadata(): Promise<AVMetadata>--><!--Device-AVSessionController-getAVMetadata(): Promise<AVMetadata>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVMetadata&gt; | Promise对象，返回会话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getAVMetadataSync

```TypeScript
getAVMetadataSync(): AVMetadata
```

使用同步方法获取会话元数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getAVMetadataSync(): AVMetadata--><!--Device-AVSessionController-getAVMetadataSync(): AVMetadata-End-->

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

## getAVPlaybackState

```TypeScript
getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void
```

获取当前的远端播放状态。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void--><!--Device-AVSessionController-getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | 是 | 回调函数，返回远端播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getAVPlaybackState

```TypeScript
getAVPlaybackState(): Promise<AVPlaybackState>
```

获取当前的远端播放状态。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getAVPlaybackState(): Promise<AVPlaybackState>--><!--Device-AVSessionController-getAVPlaybackState(): Promise<AVPlaybackState>-End-->

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

## getAVPlaybackStateSync

```TypeScript
getAVPlaybackStateSync(): AVPlaybackState
```

使用同步方法获取当前会话的播放状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getAVPlaybackStateSync(): AVPlaybackState--><!--Device-AVSessionController-getAVPlaybackStateSync(): AVPlaybackState-End-->

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

## getAVQueueItems

```TypeScript
getAVQueueItems(callback: AsyncCallback<Array<AVQueueItem>>): void
```

获取当前播放列表相关信息。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getAVQueueItems(callback: AsyncCallback<Array<AVQueueItem>>): void--><!--Device-AVSessionController-getAVQueueItems(callback: AsyncCallback<Array<AVQueueItem>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;&gt; | 是 | 回调函数，返回播放列表队列。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getAVQueueItems

```TypeScript
getAVQueueItems(): Promise<Array<AVQueueItem>>
```

获取当前会话播放列表相关信息。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getAVQueueItems(): Promise<Array<AVQueueItem>>--><!--Device-AVSessionController-getAVQueueItems(): Promise<Array<AVQueueItem>>-End-->

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

## getAVQueueItemsSync

```TypeScript
getAVQueueItemsSync(): Array<AVQueueItem>
```

使用同步方法获取当前会话播放列表相关信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getAVQueueItemsSync(): Array<AVQueueItem>--><!--Device-AVSessionController-getAVQueueItemsSync(): Array<AVQueueItem>-End-->

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

## getAVQueueTitle

```TypeScript
getAVQueueTitle(callback: AsyncCallback<string>): void
```

获取当前播放列表的名称。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getAVQueueTitle(callback: AsyncCallback<string>): void--><!--Device-AVSessionController-getAVQueueTitle(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，返回播放列表名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getAVQueueTitle

```TypeScript
getAVQueueTitle(): Promise<string>
```

获取当前会话播放列表的名称。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getAVQueueTitle(): Promise<string>--><!--Device-AVSessionController-getAVQueueTitle(): Promise<string>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回播放列表名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getAVQueueTitleSync

```TypeScript
getAVQueueTitleSync(): string
```

使用同步方法获取当前会话播放列表的名称。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getAVQueueTitleSync(): string--><!--Device-AVSessionController-getAVQueueTitleSync(): string-End-->

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

## getCallMetadata

```TypeScript
getCallMetadata(callback: AsyncCallback<CallMetadata>): void
```

获取通话会话的元数据。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getCallMetadata(callback: AsyncCallback<CallMetadata>): void--><!--Device-AVSessionController-getCallMetadata(callback: AsyncCallback<CallMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 是 | 回调函数，返回会话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getCallMetadata

```TypeScript
getCallMetadata(): Promise<CallMetadata>
```

获取通话会话的元数据。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getCallMetadata(): Promise<CallMetadata>--><!--Device-AVSessionController-getCallMetadata(): Promise<CallMetadata>-End-->

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

## getDesktopLyricState

```TypeScript
getDesktopLyricState(): Promise<DesktopLyricState>
```

获取当前会话桌面歌词状态。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-getDesktopLyricState(): Promise<DesktopLyricState>--><!--Device-AVSessionController-getDesktopLyricState(): Promise<DesktopLyricState>-End-->

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

## getExtras

```TypeScript
getExtras(callback: AsyncCallback<{[key: string]: Object}>): void
```

获取媒体提供方设置的自定义媒体数据包。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-AVSessionController-getExtras(callback: AsyncCallback<{[key: string]: Object}>): void--><!--Device-AVSessionController-getExtras(callback: AsyncCallback<{[key: string]: Object}>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;{[key: string]: Object}&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

## getExtras

```TypeScript
getExtras(callback: AsyncCallback<Record<string, Object>>): void
```

Get custom media packets provided by the corresponding session

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getExtras(callback: AsyncCallback<Record<string, Object>>): void--><!--Device-AVSessionController-getExtras(callback: AsyncCallback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | The triggered asyncCallback when (getExtras). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

## getExtras

```TypeScript
getExtras(): Promise<{[key: string]: Object}>
```

获取媒体提供方设置的自定义媒体数据包。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getExtras(): Promise<{[key: string]: Object}>--><!--Device-AVSessionController-getExtras(): Promise<{[key: string]: Object}>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{[key: string]: Object}&gt; | > } Promise对象，返回媒体提供方设置的自定义媒体数据包，数据包的内容与setExtras设置的内容完全一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

## getExtras

```TypeScript
getExtras(): Promise<Record<string, Object>>
```

Get custom media packets provided by the corresponding session

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getExtras(): Promise<Record<string, Object>>--><!--Device-AVSessionController-getExtras(): Promise<Record<string, Object>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, Object&gt;&gt; | 返回自定义的扩展数据 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

## getExtrasWithEvent

```TypeScript
getExtrasWithEvent(extraEvent: string): Promise<ExtraInfo>
```

根据远端分布式事件类型，获取远端分布式媒体提供方设置的自定义媒体数据包。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getExtrasWithEvent(extraEvent: string): Promise<ExtraInfo>--><!--Device-AVSessionController-getExtrasWithEvent(extraEvent: string): Promise<ExtraInfo>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| extraEvent | string | 是 | 远端分布式事件类型。可获取的事件类型来自于 setExtras)}。 &lt;br&gt;对Wearable设备类型，额外提供以下预设的事件类型： &lt;br&gt;'AUDIO_GET_VOLUME'：获取远端设备音量。 &lt;br&gt;'AUDIO_GET_AVAILABLE_DEVICES'：获取远端所有可连接设备。 &lt;br&gt;'AUDIO_GET_PREFERRED_OUTPUT_DEVICE_FOR_RENDERER_INFO'：获取远端实际发声设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ExtraInfo](arkts-avsession-avsession-extrainfo-t.md)&gt; | Promise对象，返回远端分布式媒体提供方设置的自定义媒体数据包。 &lt;br&gt;参数ExtraInfo支持的数据类型有：字符串、数字、布尔、对象、数组和文件描述符等，详细介绍请参见 [ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |

## getLaunchAbility

```TypeScript
getLaunchAbility(callback: AsyncCallback<WantAgent>): void
```

获取应用在会话中保存的WantAgent对象。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getLaunchAbility(callback: AsyncCallback<WantAgent>): void--><!--Device-AVSessionController-getLaunchAbility(callback: AsyncCallback<WantAgent>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)&gt; | 是 | 回调函数。返回在 [setLaunchAbility](arkts-avsession-avsession-avsession-i.md#setLaunchAbility)保存的对象，包括应用的相关属性信息，如 bundleName，abilityName，deviceId等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getLaunchAbility

```TypeScript
getLaunchAbility(): Promise<WantAgent>
```

获取应用在会话中保存的WantAgent对象。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getLaunchAbility(): Promise<WantAgent>--><!--Device-AVSessionController-getLaunchAbility(): Promise<WantAgent>-End-->

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

## getMediaCenterControlType

```TypeScript
getMediaCenterControlType(): Promise<Array<AVMediaCenterControlType>>
```

获取应用通过[setMediaCenterControlType](arkts-avsession-avsession-avsession-i.md#setMediaCenterControlType)接口设置优先显示的控制类型列表。使用Promise异步 回调。 如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-getMediaCenterControlType(): Promise<Array<AVMediaCenterControlType>>--><!--Device-AVSessionController-getMediaCenterControlType(): Promise<Array<AVMediaCenterControlType>>-End-->

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

## getOutputDevice

```TypeScript
getOutputDevice(callback: AsyncCallback<OutputDeviceInfo>): void
```

获取播放设备信息。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getOutputDevice(callback: AsyncCallback<OutputDeviceInfo>): void--><!--Device-AVSessionController-getOutputDevice(callback: AsyncCallback<OutputDeviceInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md)&gt; | 是 | 回调函数，返回播放设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 600101 | Session service exception. |
| 600103 | The session controller does not exist. |

## getOutputDevice

```TypeScript
getOutputDevice(): Promise<OutputDeviceInfo>
```

获取播放设备信息。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getOutputDevice(): Promise<OutputDeviceInfo>--><!--Device-AVSessionController-getOutputDevice(): Promise<OutputDeviceInfo>-End-->

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

## getOutputDeviceSync

```TypeScript
getOutputDeviceSync(): OutputDeviceInfo
```

使用同步方法获取当前输出设备信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getOutputDeviceSync(): OutputDeviceInfo--><!--Device-AVSessionController-getOutputDeviceSync(): OutputDeviceInfo-End-->

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

## getRealPlaybackPositionSync

```TypeScript
getRealPlaybackPositionSync(): long
```

使用同步方法获取当前播放位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getRealPlaybackPositionSync(): long--><!--Device-AVSessionController-getRealPlaybackPositionSync(): long-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 时间节点，毫秒数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getSupportedLoopModes

```TypeScript
getSupportedLoopModes(): Promise<Array<LoopMode>>
```

获取应用支持的循环模式列表。使用Promise异步回调。 该列表通过[setSupportedLoopModes](arkts-avsession-avsession-avsession-i.md#setSupportedLoopModes)接口设置。如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getSupportedLoopModes(): Promise<Array<LoopMode>>--><!--Device-AVSessionController-getSupportedLoopModes(): Promise<Array<LoopMode>>-End-->

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

## getSupportedPlaySpeeds

```TypeScript
getSupportedPlaySpeeds(): Promise<Array<double>>
```

获取应用支持的播放倍速列表。使用Promise异步回调。 该列表通过[setSupportedPlaySpeeds](arkts-avsession-avsession-avsession-i.md#setSupportedPlaySpeeds)接口设置。如果应用未设置或者设置为空列表，则返回空列表。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getSupportedPlaySpeeds(): Promise<Array<double>>--><!--Device-AVSessionController-getSupportedPlaySpeeds(): Promise<Array<double>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;double&gt;&gt; | Promise对象。返回支持的播放倍速列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getValidCommands

```TypeScript
getValidCommands(callback: AsyncCallback<Array<AVControlCommandType>>): void
```

获取会话支持的有效命令。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-getValidCommands(callback: AsyncCallback<Array<AVControlCommandType>>): void--><!--Device-AVSessionController-getValidCommands(callback: AsyncCallback<Array<AVControlCommandType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;&gt; | 是 | 回调函数，返回有效命令的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## getValidCommands

```TypeScript
getValidCommands(): Promise<Array<AVControlCommandType>>
```

获取会话支持的有效命令。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getValidCommands(): Promise<Array<AVControlCommandType>>--><!--Device-AVSessionController-getValidCommands(): Promise<Array<AVControlCommandType>>-End-->

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

## getValidCommandsSync

```TypeScript
getValidCommandsSync(): Array<AVControlCommandType>
```

使用同步方法获取会话支持的有效命令。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-getValidCommandsSync(): Array<AVControlCommandType>--><!--Device-AVSessionController-getValidCommandsSync(): Array<AVControlCommandType>-End-->

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

## isActive

```TypeScript
isActive(callback: AsyncCallback<boolean>): void
```

判断会话是否被激活。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-isActive(callback: AsyncCallback<boolean>): void--><!--Device-AVSessionController-isActive(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## isActive

```TypeScript
isActive(): Promise<boolean>
```

获取会话是否被激活。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-isActive(): Promise<boolean>--><!--Device-AVSessionController-isActive(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## isActiveSync

```TypeScript
isActiveSync(): boolean
```

使用同步方法判断会话是否被激活。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-isActiveSync(): boolean--><!--Device-AVSessionController-isActiveSync(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 会话是否为激活状态，true表示被激活，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## isDesktopLyricEnabled

```TypeScript
isDesktopLyricEnabled(): Promise<boolean>
```

查询是否启用桌面歌词功能。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-isDesktopLyricEnabled(): Promise<boolean>--><!--Device-AVSessionController-isDesktopLyricEnabled(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示启用桌面歌词功能；返回false表示不启用桌面歌词功能。 |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-isDesktopLyricVisible(): Promise<boolean>--><!--Device-AVSessionController-isDesktopLyricVisible(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示显示桌面歌词；返回false表示不显示桌面歌词。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-应用程序的桌面歌词功能未开启) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-当前设备不支持桌面歌词功能) | The desktop lyrics feature is not supported. |

## offActiveStateChange

```TypeScript
offActiveStateChange(callback?: Callback<boolean>): void
```

Unregister the active state of this session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offActiveStateChange(callback?: Callback<boolean>): void--><!--Device-AVSessionController-offActiveStateChange(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | The callback used to handle the active state of this session changed event. The callback function provides the changed session state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offCallMetadataChange

```TypeScript
offCallMetadataChange(callback?: Callback<CallMetadata>): void
```

Unregister call metadata changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offCallMetadataChange(callback?: Callback<CallMetadata>): void--><!--Device-AVSessionController-offCallMetadataChange(callback?: Callback<CallMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 否 | The callback used to handle call metadata changed event. The callback function provides the [CallMetadata](arkts-avsession-avsession-callmetadata-i.md#CallMetadata) parameter. It only contains the properties set in the filter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offCallStateChange

```TypeScript
offCallStateChange(callback?: Callback<AVCallState>): void
```

Unregister playback state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offCallStateChange(callback?: Callback<AVCallState>): void--><!--Device-AVSessionController-offCallStateChange(callback?: Callback<AVCallState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 否 | The callback used to handle call state changed event. The callback function provides the [AVCallState](arkts-avsession-avsession-avcallstate-i.md#AVCallState) parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offCustomDataChange

```TypeScript
offCustomDataChange(callback?: Callback<Record<string, Object>>): void
```

Unregister listener for custom data.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offCustomDataChange(callback?: Callback<Record<string, Object>>): void--><!--Device-AVSessionController-offCustomDataChange(callback?: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 否 | Callback used to retrieve custom data. |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-offDesktopLyricEnabled(callback?: Callback<boolean>): void--><!--Device-AVSessionController-offDesktopLyricEnabled(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有桌面歌词功能启用状态变更事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offDesktopLyricStateChanged

```TypeScript
offDesktopLyricStateChanged(callback?: Callback<DesktopLyricState>): void
```

取消桌面歌词状态变更事件监听，取消后将不再对该事件进行监听。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-offDesktopLyricStateChanged(callback?: Callback<DesktopLyricState>): void--><!--Device-AVSessionController-offDesktopLyricStateChanged(callback?: Callback<DesktopLyricState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md)&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有桌面歌词状态变更事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offDesktopLyricVisibilityChanged

```TypeScript
offDesktopLyricVisibilityChanged(callback?: Callback<boolean>): void
```

取消显示桌面歌词状态变更事件监听，取消后将不再对该事件进行监听。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-offDesktopLyricVisibilityChanged(callback?: Callback<boolean>): void--><!--Device-AVSessionController-offDesktopLyricVisibilityChanged(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有显示桌面歌词状态变更事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offExtrasChange

```TypeScript
offExtrasChange(callback?: Callback<Record<string, Object>>): void
```

Unregister the custom media packets change callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offExtrasChange(callback?: Callback<Record<string, Object>>): void--><!--Device-AVSessionController-offExtrasChange(callback?: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 否 | Used to handle custom media packets changed. The callback provides the new media packets. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offMediaCenterControlTypeChanged

```TypeScript
offMediaCenterControlTypeChanged(callback?: Callback<Array<AVMediaCenterControlType>>): void
```

取消控制类型列表变化的监听事件。 取消后将不再对该事件进行监听。其中控制类型列表由应用通过[setMediaCenterControlType](arkts-avsession-avsession-avsession-i.md#setMediaCenterControlType)接口设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-offMediaCenterControlTypeChanged(callback?: Callback<Array<AVMediaCenterControlType>>): void--><!--Device-AVSessionController-offMediaCenterControlTypeChanged(callback?: Callback<Array<AVMediaCenterControlType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md)&gt;&gt; | 否 | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有控制类型列表变化事件取消监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offMetadataChange

```TypeScript
offMetadataChange(callback?: Callback<AVMetadata>): void
```

Unregister metadata changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offMetadataChange(callback?: Callback<AVMetadata>): void--><!--Device-AVSessionController-offMetadataChange(callback?: Callback<AVMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;AVMetadata&gt; | 否 | The callback used to handle metadata changed event. The callback function provides the [AVMetadata](arkts-avsession-avsession-avmetadata-i.md#AVMetadata) parameter. It only contains the properties set in the filter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offOutputDeviceChange

```TypeScript
offOutputDeviceChange(callback?: ConnectionEvent): void
```

Unregister session output device change callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offOutputDeviceChange(callback?: ConnectionEvent): void--><!--Device-AVSessionController-offOutputDeviceChange(callback?: ConnectionEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ConnectionEvent](arkts-avsession-avsession-connectionevent-t.md) | 否 | Used to handle output device changed. The callback provide the new device info [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md#OutputDeviceInfo) and related connection state [ConnectionState](arkts-avsession-avsession-connectionstate-e.md#ConnectionState). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist |

## offPlaybackStateChange

```TypeScript
offPlaybackStateChange(callback?: Callback<AVPlaybackState>): void
```

Unregister playback state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offPlaybackStateChange(callback?: Callback<AVPlaybackState>): void--><!--Device-AVSessionController-offPlaybackStateChange(callback?: Callback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | 否 | The callback used to handle playback state changed event. The callback function provides the [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md#AVPlaybackState) parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offQueueItemsChange

```TypeScript
offQueueItemsChange(callback?: Callback<Array<AVQueueItem>>): void
```

Unregister session playlist change callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-offQueueItemsChange(callback?: Callback<Array<AVQueueItem>>): void--><!--Device-AVSessionController-offQueueItemsChange(callback?: Callback<Array<AVQueueItem>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;&gt; | 否 | Used to handle playlist changed. The callback provides the new array of AVQueueItem [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md#AVQueueItem) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offQueueTitleChange

```TypeScript
offQueueTitleChange(callback?: Callback<string>): void
```

Unregister the name of session playlist change callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offQueueTitleChange(callback?: Callback<string>): void--><!--Device-AVSessionController-offQueueTitleChange(callback?: Callback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 否 | Used to handle name of playlist changed. The callback provides the new name. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offSessionDestroy

```TypeScript
offSessionDestroy(callback?: NoParamCallback): void
```

Unregister current session destroyed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offSessionDestroy(callback?: NoParamCallback): void--><!--Device-AVSessionController-offSessionDestroy(callback?: NoParamCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [NoParamCallback](arkts-avsession-avsession-noparamcallback-t.md) | 否 | The callback used to handle current session destroyed event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offSessionEvent

```TypeScript
offSessionEvent(callback?: EventProcess): void
```

Unregister session event callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offSessionEvent(callback?: EventProcess): void--><!--Device-AVSessionController-offSessionEvent(callback?: EventProcess): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [EventProcess](arkts-avsession-avsession-eventprocess-t.md) | 否 | Used to cancel a specific listener The callback function provides the event string and key-value pair parameters. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offSupportedLoopModesChange

```TypeScript
offSupportedLoopModesChange(callback?: Callback<Array<LoopMode>>): void
```

取消支持的循环模式列表变化事件监听。 取消后将不再对该事件进行监听。其中循环模式列表由应用通过[setSupportedLoopModes](arkts-avsession-avsession-avsession-i.md#setSupportedLoopModes)接口设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-offSupportedLoopModesChange(callback?: Callback<Array<LoopMode>>): void--><!--Device-AVSessionController-offSupportedLoopModesChange(callback?: Callback<Array<LoopMode>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[LoopMode](arkts-avsession-avsession-loopmode-e.md)&gt;&gt; | 否 | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有支持的循环模式列表变化事件取消监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offSupportedPlaySpeedsChange

```TypeScript
offSupportedPlaySpeedsChange(callback?: Callback<Array<double>>): void
```

取消支持的播放倍速列表变化事件监听。 取消后将不再对该事件进行监听。其中播放倍速列表由应用通过[setSupportedPlaySpeeds](arkts-avsession-avsession-avsession-i.md#setSupportedPlaySpeeds)接口设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-offSupportedPlaySpeedsChange(callback?: Callback<Array<double>>): void--><!--Device-AVSessionController-offSupportedPlaySpeedsChange(callback?: Callback<Array<double>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;double&gt;&gt; | 否 | 回调函数。该参数为可选参数，若不填写该参数，则认为对所有支持的播放倍速列表变化事件取消监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offValidCommandChange

```TypeScript
offValidCommandChange(callback?: Callback<Array<AVControlCommandType>>): void
```

Unregister the valid commands of the session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-offValidCommandChange(callback?: Callback<Array<AVControlCommandType>>): void--><!--Device-AVSessionController-offValidCommandChange(callback?: Callback<Array<AVControlCommandType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;&gt; | 否 | The callback used to handle the changes. The callback function provides an array of AVControlCommandType. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_activeStateChange

```TypeScript
off(type: 'activeStateChange', callback?: (isActive: boolean) => void)
```

取消监听会话激活状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'activeStateChange', callback?: (isActive: boolean) => void)--><!--Device-AVSessionController-off(type: 'activeStateChange', callback?: (isActive: boolean) => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activeStateChange' | 是 | 取消对应的监听事件，支持事件`'activeStateChange'`。 |
| callback | (isActive: boolean) =&gt; void | 否 | 回调函数。参数isActive表示会话是否被激活。true表示被激活，false表示禁用。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_callMetadataChange

```TypeScript
off(type: 'callMetadataChange', callback?: Callback<CallMetadata>): void
```

取消设置通话元数据变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'callMetadataChange', callback?: Callback<CallMetadata>): void--><!--Device-AVSessionController-off(type: 'callMetadataChange', callback?: Callback<CallMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callMetadataChange' | 是 | 取消对应的监听事件，支持事件`'callMetadataChange'`。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 否 | 回调函数，参数calldata是变化后的通话原数据。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_callStateChange

```TypeScript
off(type: 'callStateChange', callback?: Callback<AVCallState>): void
```

取消设置通话状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'callStateChange', callback?: Callback<AVCallState>): void--><!--Device-AVSessionController-off(type: 'callStateChange', callback?: Callback<AVCallState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callStateChange' | 是 | 取消对应的监听事件，支持事件`'callStateChange'`。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 否 | 回调函数，参数callstate是变化后的通话状态。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_customDataChange

```TypeScript
off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void
```

取消自定义数据监听。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void--><!--Device-AVSessionController-off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'customDataChange' | 是 | 取消对应的监听事件，支持的事件是'customDataChange'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 否 | 注册监听事件时的回调函数。该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_extrasChange

```TypeScript
off(type: 'extrasChange', callback?: (extras: {[key: string]: Object}) => void): void
```

取消自定义媒体数据包变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'extrasChange', callback?: (extras: {[key: string]: Object}) => void): void--><!--Device-AVSessionController-off(type: 'extrasChange', callback?: (extras: {[key: string]: Object}) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'extrasChange' | 是 | 取消对应的监听事件，支持事件`'extrasChange'`。 |
| callback | (extras: {[key: string]: Object}) =&gt; void | 否 | 注册监听事件时的回调函数。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_metadataChange

```TypeScript
off(type: 'metadataChange', callback?: (data: AVMetadata) => void)
```

取消元数据变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'metadataChange', callback?: (data: AVMetadata) => void)--><!--Device-AVSessionController-off(type: 'metadataChange', callback?: (data: AVMetadata) => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'metadataChange' | 是 |  |
| callback | (data: AVMetadata) =&gt; void | 否 | 回调函数，参数data是需要更新的元数据。只包含需要更新的元数据属性，并不代表当前全量的元数据。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_outputDeviceChange

```TypeScript
off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void
```

取消监听分布式设备变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void--><!--Device-AVSessionController-off(type: 'outputDeviceChange', callback?: (state: ConnectionState, device: OutputDeviceInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'outputDeviceChange' | 是 | 取消对应的监听事件，支持事件`'outputDeviceChange'`。 |
| callback | (state: ConnectionState, device: OutputDeviceInfo) =&gt; void | 否 | 回调函数，参数device是设备相关信息。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist |

## off_playbackStateChange

```TypeScript
off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void)
```

取消播放状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void)--><!--Device-AVSessionController-off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | 是 |  |
| callback | (state: AVPlaybackState) =&gt; void | 否 | 回调函数，参数state是需要更新的播放状态。只包含需要更新的播放状态属性，并不代表当前全量的播放状态。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_queueItemsChange

```TypeScript
off(type: 'queueItemsChange', callback?: (items: Array<AVQueueItem>) => void): void
```

取消播放列表变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'queueItemsChange', callback?: (items: Array<AVQueueItem>) => void): void--><!--Device-AVSessionController-off(type: 'queueItemsChange', callback?: (items: Array<AVQueueItem>) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'queueItemsChange' | 是 | 取消对应的监听事件，支持事件`'queueItemsChange'`。 |
| callback | (items: Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;) =&gt; void | 否 | 回调函数，参数items是变化的播放列表。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_queueTitleChange

```TypeScript
off(type: 'queueTitleChange', callback?: (title: string) => void): void
```

取消播放列表名称变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'queueTitleChange', callback?: (title: string) => void): void--><!--Device-AVSessionController-off(type: 'queueTitleChange', callback?: (title: string) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'queueTitleChange' | 是 | 取消对应的监听事件，支持事件`'queueTitleChange'`。 |
| callback | (title: string) =&gt; void | 否 | 回调函数，参数items是变化的播放列表名称。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_sessionDestroy

```TypeScript
off(type: 'sessionDestroy', callback?: () => void)
```

取消监听会话的销毁事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'sessionDestroy', callback?: () => void)--><!--Device-AVSessionController-off(type: 'sessionDestroy', callback?: () => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | 是 | 取消对应的监听事件，支持事件`'sessionDestroy'`。 |
| callback | () =&gt; void | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_sessionEvent

```TypeScript
off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {[key: string]: Object}) => void): void
```

取消会话事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {[key: string]: Object}) => void): void--><!--Device-AVSessionController-off(type: 'sessionEvent', callback?: (sessionEvent: string, args: {[key: string]: Object}) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionEvent' | 是 | 取消对应的监听事件，支持事件`'sessionEvent'`。 |
| callback | (sessionEvent: string, args: {[key: string]: Object}) =&gt; void | 否 | 回调函数，参数sessionEvent是变化的事件名，args为事件的参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off_validCommandChange

```TypeScript
off(type: 'validCommandChange', callback?: (commands: Array<AVControlCommandType>) => void)
```

取消监听会话有效命令变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-off(type: 'validCommandChange', callback?: (commands: Array<AVControlCommandType>) => void)--><!--Device-AVSessionController-off(type: 'validCommandChange', callback?: (commands: Array<AVControlCommandType>) => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'validCommandChange' | 是 | 取消对应的监听事件，支持事件`'validCommandChange'`。 |
| callback | (commands: Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;) =&gt; void | 否 | 回调函数。参数commands是有效命令的集合。 &lt;br&gt;该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onActiveStateChange

```TypeScript
onActiveStateChange(callback: Callback<boolean>): void
```

Register the active state of this session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onActiveStateChange(callback: Callback<boolean>): void--><!--Device-AVSessionController-onActiveStateChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | The callback used to handle the active state of this session changed event. The callback function provides the changed session state. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onCallMetadataChange

```TypeScript
onCallMetadataChange(filter: Array<string>, callback: Callback<CallMetadata>): void
```

Register call metadata changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onCallMetadataChange(filter: Array<string>, callback: Callback<CallMetadata>): void--><!--Device-AVSessionController-onCallMetadataChange(filter: Array<string>, callback: Callback<CallMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | Array&lt;string&gt; | 是 | The properties of [CallMetadata](arkts-avsession-avsession-callmetadata-i.md#CallMetadata) that you cared about |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 是 | The callback used to handle call metadata changed event. The callback function provides the [CallMetadata](arkts-avsession-avsession-callmetadata-i.md#CallMetadata) parameter. It only contains the properties set in the filter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onCallMetadataChangeAll

```TypeScript
onCallMetadataChangeAll(callback: Callback<CallMetadata>): void
```

Register call metadata changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onCallMetadataChangeAll(callback: Callback<CallMetadata>): void--><!--Device-AVSessionController-onCallMetadataChangeAll(callback: Callback<CallMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 是 | The callback used to handle call metadata changed event. The callback function provides the [CallMetadata](arkts-avsession-avsession-callmetadata-i.md#CallMetadata) parameter. It only contains the properties set in the filter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onCallStateChange

```TypeScript
onCallStateChange(filter: Array<string>, callback: Callback<AVCallState>): void
```

Register call state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onCallStateChange(filter: Array<string>, callback: Callback<AVCallState>): void--><!--Device-AVSessionController-onCallStateChange(filter: Array<string>, callback: Callback<AVCallState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | Array&lt;string&gt; | 是 | The properties of [AVCallState](arkts-avsession-avsession-avcallstate-i.md#AVCallState) that you cared about |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 是 | The callback used to handle call state changed event. The callback function provides the [AVCallState](arkts-avsession-avsession-avcallstate-i.md#AVCallState) parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onCallStateChangeAll

```TypeScript
onCallStateChangeAll(callback: Callback<AVCallState>): void
```

Register call state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onCallStateChangeAll(callback: Callback<AVCallState>): void--><!--Device-AVSessionController-onCallStateChangeAll(callback: Callback<AVCallState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 是 | The callback used to handle call state changed event. The callback function provides the [AVCallState](arkts-avsession-avsession-avcallstate-i.md#AVCallState) parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onCustomDataChange

```TypeScript
onCustomDataChange(callback: Callback<Record<string, Object>>): void
```

Register listener for custom data.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onCustomDataChange(callback: Callback<Record<string, Object>>): void--><!--Device-AVSessionController-onCustomDataChange(callback: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | Callback used to retrieve custom data. |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-onDesktopLyricEnabled(callback: Callback<boolean>): void--><!--Device-AVSessionController-onDesktopLyricEnabled(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示桌面歌词功能启用；返回false表示桌面歌词功能未启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onDesktopLyricStateChanged

```TypeScript
onDesktopLyricStateChanged(callback: Callback<DesktopLyricState>): void
```

桌面歌词状态变更的监听事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-onDesktopLyricStateChanged(callback: Callback<DesktopLyricState>): void--><!--Device-AVSessionController-onDesktopLyricStateChanged(callback: Callback<DesktopLyricState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md)&gt; | 是 | 回调函数。返回桌面歌词状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onDesktopLyricVisibilityChanged

```TypeScript
onDesktopLyricVisibilityChanged(callback: Callback<boolean>): void
```

显示桌面歌词状态变更的监听事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-onDesktopLyricVisibilityChanged(callback: Callback<boolean>): void--><!--Device-AVSessionController-onDesktopLyricVisibilityChanged(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示开启显示桌面歌词状态；返回false表示关闭显示桌面歌词状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onExtrasChange

```TypeScript
onExtrasChange(callback: Callback<Record<string, Object>>): void
```

Register the custom media packets change callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onExtrasChange(callback: Callback<Record<string, Object>>): void--><!--Device-AVSessionController-onExtrasChange(callback: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | Used to handle custom media packets changed. The callback provides the new media packets. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onMediaCenterControlTypeChanged

```TypeScript
onMediaCenterControlTypeChanged(callback: Callback<Array<AVMediaCenterControlType>>): void
```

注册控制类型列表变化的监听事件。使用callback异步回调。 其中控制类型列表由应用通过[setMediaCenterControlType](arkts-avsession-avsession-avsession-i.md#setMediaCenterControlType)接口设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-onMediaCenterControlTypeChanged(callback: Callback<Array<AVMediaCenterControlType>>): void--><!--Device-AVSessionController-onMediaCenterControlTypeChanged(callback: Callback<Array<AVMediaCenterControlType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[AVMediaCenterControlType](arkts-avsession-avsession-avmediacentercontroltype-t.md)&gt;&gt; | 是 | 回调函数。返回变化后的控制类型列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onMetadataChange

```TypeScript
onMetadataChange(filter: Array<string>, callback: Callback<AVMetadata>): void
```

Register metadata changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onMetadataChange(filter: Array<string>, callback: Callback<AVMetadata>): void--><!--Device-AVSessionController-onMetadataChange(filter: Array<string>, callback: Callback<AVMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | Array&lt;string&gt; | 是 | The properties of [AVMetadata](arkts-avsession-avsession-avmetadata-i.md#AVMetadata) that you cared about |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;AVMetadata&gt; | 是 | The callback used to handle metadata changed event. The callback function provides the [AVMetadata](arkts-avsession-avsession-avmetadata-i.md#AVMetadata) parameter. It only contains the properties set in the filter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onMetadataChangeAll

```TypeScript
onMetadataChangeAll(callback: Callback<AVMetadata>): void
```

Register metadata changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onMetadataChangeAll(callback: Callback<AVMetadata>): void--><!--Device-AVSessionController-onMetadataChangeAll(callback: Callback<AVMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;AVMetadata&gt; | 是 | The callback used to handle metadata changed event. The callback function provides the [AVMetadata](arkts-avsession-avsession-avmetadata-i.md#AVMetadata) parameter. It only contains the properties set in the filter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onOutputDeviceChange

```TypeScript
onOutputDeviceChange(callback: ConnectionEvent): void
```

Register session output device change callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onOutputDeviceChange(callback: ConnectionEvent): void--><!--Device-AVSessionController-onOutputDeviceChange(callback: ConnectionEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ConnectionEvent](arkts-avsession-avsession-connectionevent-t.md) | 是 | Used to handle output device changed. The callback provide the new device info [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md#OutputDeviceInfo) and related connection state [ConnectionState](arkts-avsession-avsession-connectionstate-e.md#ConnectionState). |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist |

## onPlaybackStateChange

```TypeScript
onPlaybackStateChange(filter: Array<string>, callback: Callback<AVPlaybackState>): void
```

Register playback state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onPlaybackStateChange(filter: Array<string>, callback: Callback<AVPlaybackState>): void--><!--Device-AVSessionController-onPlaybackStateChange(filter: Array<string>, callback: Callback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | Array&lt;string&gt; | 是 | The properties of [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md#AVPlaybackState) that you cared about |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | 是 | The callback used to handle playback state changed event. The callback function provides the [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md#AVPlaybackState) parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onPlaybackStateChangeAll

```TypeScript
onPlaybackStateChangeAll(callback: Callback<AVPlaybackState>): void
```

Register playback state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onPlaybackStateChangeAll(callback: Callback<AVPlaybackState>): void--><!--Device-AVSessionController-onPlaybackStateChangeAll(callback: Callback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md)&gt; | 是 | The callback used to handle playback state changed event. The callback function provides the [AVPlaybackState](arkts-avsession-avsession-avplaybackstate-i.md#AVPlaybackState) parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onQueueItemsChange

```TypeScript
onQueueItemsChange(callback: Callback<Array<AVQueueItem>>): void
```

Register session playlist change callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onQueueItemsChange(callback: Callback<Array<AVQueueItem>>): void--><!--Device-AVSessionController-onQueueItemsChange(callback: Callback<Array<AVQueueItem>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md)&gt;&gt; | 是 | Used to handle playlist changed. The callback provides the new array of AVQueueItem [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md#AVQueueItem) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onQueueTitleChange

```TypeScript
onQueueTitleChange(callback: Callback<string>): void
```

Register the name of session playlist change callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onQueueTitleChange(callback: Callback<string>): void--><!--Device-AVSessionController-onQueueTitleChange(callback: Callback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 是 | Used to handle name of playlist changed. The callback provides the new name. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onSessionDestroy

```TypeScript
onSessionDestroy(callback: NoParamCallback): void
```

Register current session destroyed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onSessionDestroy(callback: NoParamCallback): void--><!--Device-AVSessionController-onSessionDestroy(callback: NoParamCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [NoParamCallback](arkts-avsession-avsession-noparamcallback-t.md) | 是 | The callback used to handle current session destroyed event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onSessionEvent

```TypeScript
onSessionEvent(callback: EventProcess): void
```

Register session event callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onSessionEvent(callback: EventProcess): void--><!--Device-AVSessionController-onSessionEvent(callback: EventProcess): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [EventProcess](arkts-avsession-avsession-eventprocess-t.md) | 是 | The callback used to handle session event changed event. The callback function provides the event string and key-value pair parameters. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onSupportedLoopModesChange

```TypeScript
onSupportedLoopModesChange(callback: Callback<Array<LoopMode>>): void
```

注册支持的循环模式列表变化的监听事件。使用callback异步回调。 其中循环模式列表由应用通过[setSupportedLoopModes](arkts-avsession-avsession-avsession-i.md#setSupportedLoopModes)接口设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-onSupportedLoopModesChange(callback: Callback<Array<LoopMode>>): void--><!--Device-AVSessionController-onSupportedLoopModesChange(callback: Callback<Array<LoopMode>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[LoopMode](arkts-avsession-avsession-loopmode-e.md)&gt;&gt; | 是 | 回调函数。返回变化后支持的循环模式列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onSupportedPlaySpeedsChange

```TypeScript
onSupportedPlaySpeedsChange(callback: Callback<Array<double>>): void
```

注册支持的播放倍速列表变化的监听事件。使用callback异步回调。 其中播放倍速列表由应用通过[setSupportedPlaySpeeds](arkts-avsession-avsession-avsession-i.md#setSupportedPlaySpeeds)接口设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-onSupportedPlaySpeedsChange(callback: Callback<Array<double>>): void--><!--Device-AVSessionController-onSupportedPlaySpeedsChange(callback: Callback<Array<double>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;double&gt;&gt; | 是 | 回调函数。返回变化后支持的播放倍速列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onValidCommandChange

```TypeScript
onValidCommandChange(callback: Callback<Array<AVControlCommandType>>): void
```

Register the valid commands of the session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-onValidCommandChange(callback: Callback<Array<AVControlCommandType>>): void--><!--Device-AVSessionController-onValidCommandChange(callback: Callback<Array<AVControlCommandType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[AVControlCommandType](arkts-avsession-avsession-avcontrolcommandtype-t.md)&gt;&gt; | 是 | The callback used to handle the changes. The callback function provides an array of AVControlCommandType. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_activeStateChange

```TypeScript
on(type: 'activeStateChange', callback: (isActive: boolean) => void)
```

会话的激活状态的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'activeStateChange', callback: (isActive: boolean) => void)--><!--Device-AVSessionController-on(type: 'activeStateChange', callback: (isActive: boolean) => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'activeStateChange' | 是 | 事件回调类型，支持事件`'activeStateChange'`：当检测到会话的激活状态发生改变时，触发该事件。 |
| callback | (isActive: boolean) =&gt; void | 是 | 回调函数。参数isActive表示会话是否被激活。true表示被激活，false表示禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_callMetadataChange

```TypeScript
on(type: 'callMetadataChange', filter: Array<keyof CallMetadata> | 'all', callback: Callback<CallMetadata>): void
```

设置通话元数据变化的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'callMetadataChange', filter: Array<keyof CallMetadata> | 'all', callback: Callback<CallMetadata>): void--><!--Device-AVSessionController-on(type: 'callMetadataChange', filter: Array<keyof CallMetadata> | 'all', callback: Callback<CallMetadata>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callMetadataChange' | 是 | 事件回调类型，支持事件`'callMetadataChange'`：当通话元数据变化时，触发该事件。 |
| filter | Array&lt;keyof CallMetadata&gt; \| 'all' | 是 | 'all'表示关注通话元数据所有字段变化；Array&lt;keyof CallMetadata&gt; 表示关注Array中的字 段变化。\| 'all'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CallMetadata](arkts-avsession-avsession-callmetadata-i.md)&gt; | 是 | 回调函数，参数callmetadata是变化后的通话元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_callStateChange

```TypeScript
on(type: 'callStateChange', filter: Array<keyof AVCallState> | 'all', callback: Callback<AVCallState>): void
```

设置通话状态变化的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'callStateChange', filter: Array<keyof AVCallState> | 'all', callback: Callback<AVCallState>): void--><!--Device-AVSessionController-on(type: 'callStateChange', filter: Array<keyof AVCallState> | 'all', callback: Callback<AVCallState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'callStateChange' | 是 | 事件回调类型，支持事件`'callStateChange'`：当通话状态变化时，触发该事件。 |
| filter | Array&lt;keyof AVCallState&gt; \| 'all' | 是 | 'all' 表示关注通话状态所有字段变化；Array&lt;keyof AVCallState&gt;表示关注Array中的字段变 化。\| 'all'。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AVCallState](arkts-avsession-avsession-avcallstate-i.md)&gt; | 是 | 回调函数，参数callstate是变化后的通话状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_customDataChange

```TypeScript
on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void
```

注册从远程设备发送的自定义数据的监听器。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void--><!--Device-AVSessionController-on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'customDataChange' | 是 | 事件回调类型，支持事件'customDataChange'，当媒体提供方发送自定义数据时，触发该事件。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | 回调函数，用于接收自定义数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_extrasChange

```TypeScript
on(type: 'extrasChange', callback: (extras: {[key: string]: Object}) => void): void
```

媒体控制器设置自定义媒体数据包事件变化的监听器。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'extrasChange', callback: (extras: {[key: string]: Object}) => void): void--><!--Device-AVSessionController-on(type: 'extrasChange', callback: (extras: {[key: string]: Object}) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'extrasChange' | 是 | 事件回调类型，支持事件`'extrasChange'`：当媒体提供方设置自定义媒体数据包时，触发该事件。 |
| callback | (extras: {[key: string]: Object}) =&gt; void | 是 | 回调函数，extras为媒体提供方新设置的自定义媒体数据包，该自定义媒体数据包与dispatchSessionEvent方法设置的数据包完全一致。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_metadataChange

```TypeScript
on(type: 'metadataChange', filter: Array<keyof AVMetadata> | 'all', callback: (data: AVMetadata) => void)
```

设置元数据变化的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'metadataChange', filter: Array<keyof AVMetadata> | 'all', callback: (data: AVMetadata) => void)--><!--Device-AVSessionController-on(type: 'metadataChange', filter: Array<keyof AVMetadata> | 'all', callback: (data: AVMetadata) => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'metadataChange' | 是 |  |
| filter | Array&lt;keyof AVMetadata&gt; \| 'all' | 是 | 'all'表示关注元数据所有字段变化；Array&lt;keyof AVMetadata&gt;表示关注Array中的字段变化。 |
| callback | (data: AVMetadata) =&gt; void | 是 | 回调函数，参数data是需要更新的元数据。只包含需要更新的元数据属性，不代表当前全量的元数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_outputDeviceChange

```TypeScript
on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void
```

设置播放设备变化的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void--><!--Device-AVSessionController-on(type: 'outputDeviceChange', callback: (state: ConnectionState, device: OutputDeviceInfo) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'outputDeviceChange' | 是 | 事件回调类型，支持事件为`'outputDeviceChange'`：当播放设备变化时，触发该事件）。 |
| callback | (state: ConnectionState, device: OutputDeviceInfo) =&gt; void | 是 | 回调函数，参数device是设备相关信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist |

## on_playbackStateChange

```TypeScript
on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void)
```

设置播放状态变化的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void)--><!--Device-AVSessionController-on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | 是 |  |
| filter | Array&lt;keyof AVPlaybackState&gt; \| 'all' | 是 | 'all'表示关注播放状态所有字段更新。 &lt;br&gt;Array&lt;keyof AVPlaybackstate&gt; 表示关注Array中的字段更新。 |
| callback | (state: AVPlaybackState) =&gt; void | 是 | 回调函数，参数state是需要更新的播放状态。只包含需要更新的播放状态属性，并不代表当前全量的播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_queueItemsChange

```TypeScript
on(type: 'queueItemsChange', callback: (items: Array<AVQueueItem>) => void): void
```

媒体控制器设置会话自定义播放列表变化的监听器。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'queueItemsChange', callback: (items: Array<AVQueueItem>) => void): void--><!--Device-AVSessionController-on(type: 'queueItemsChange', callback: (items: Array<AVQueueItem>) => void): void-End-->

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

## on_queueTitleChange

```TypeScript
on(type: 'queueTitleChange', callback: (title: string) => void): void
```

媒体控制器设置会话自定义播放列表的名称变化的监听器。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'queueTitleChange', callback: (title: string) => void): void--><!--Device-AVSessionController-on(type: 'queueTitleChange', callback: (title: string) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'queueTitleChange' | 是 | 事件回调类型，支持事件`'queueTitleChange'`：当session修改播放列表名称时，触发该事件。 |
| callback | (title: string) =&gt; void | 是 | 回调函数，title为变化的播放列表名称。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_sessionDestroy

```TypeScript
on(type: 'sessionDestroy', callback: () => void)
```

会话销毁的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'sessionDestroy', callback: () => void)--><!--Device-AVSessionController-on(type: 'sessionDestroy', callback: () => void)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionDestroy' | 是 |  |
| callback | () =&gt; void | 是 | 回调函数。当监听事件注册成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_sessionEvent

```TypeScript
on(type: 'sessionEvent', callback: (sessionEvent: string, args: {[key: string]: Object}) => void): void
```

媒体控制器设置会话自定义事件变化的监听器。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'sessionEvent', callback: (sessionEvent: string, args: {[key: string]: Object}) => void): void--><!--Device-AVSessionController-on(type: 'sessionEvent', callback: (sessionEvent: string, args: {[key: string]: Object}) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sessionEvent' | 是 | 事件回调类型，支持事件`'sessionEvent'`：当会话事件变化时，触发该事件。 |
| callback | (sessionEvent: string, args: {[key: string]: Object}) =&gt; void | 是 | 回调函数，sessionEvent为变化的会话事件名，args为事件的参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on_validCommandChange

```TypeScript
on(type: 'validCommandChange', callback: (commands: Array<AVControlCommandType>) => void)
```

会话支持的有效命令变化监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-on(type: 'validCommandChange', callback: (commands: Array<AVControlCommandType>) => void)--><!--Device-AVSessionController-on(type: 'validCommandChange', callback: (commands: Array<AVControlCommandType>) => void)-End-->

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

## sendAVKeyEvent

```TypeScript
sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback<void>): void
```

发送按键事件到会话。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback<void>): void--><!--Device-AVSessionController-sendAVKeyEvent(event: KeyEvent, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | 是 | 按键事件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当事件发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 600105 | Invalid session command. |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 600106 | The session is not activated. |
| 600101 | Session service exception. |
| 600103 | The session controller does not exist. |
| 600102 | The session does not exist. |

## sendAVKeyEvent

```TypeScript
sendAVKeyEvent(event: KeyEvent): Promise<void>
```

发送按键事件到控制器对应的会话。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-sendAVKeyEvent(event: KeyEvent): Promise<void>--><!--Device-AVSessionController-sendAVKeyEvent(event: KeyEvent): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [KeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md) | 是 | 按键事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当事件发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 600105 | Invalid session command. |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 600106 | The session is not activated. |
| 600101 | Session service exception. |
| 600103 | The session controller does not exist. |
| 600102 | The session does not exist. |

## sendCommonCommand

```TypeScript
sendCommonCommand(command: string, args: {[key: string]: Object}, callback: AsyncCallback<void>): void
```

通过会话控制器发送自定义命令到其对应的会话。结果通过callback异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-AVSessionController-sendCommonCommand(command: string, args: {[key: string]: Object}, callback: AsyncCallback<void>): void--><!--Device-AVSessionController-sendCommonCommand(command: string, args: {[key: string]: Object}, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | 需要设置的自定义控制命令的名称。 |
| args | {[key: string]: Object} | 是 | 需要传递的控制命令键值对。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

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

## sendCommonCommand

```TypeScript
sendCommonCommand(command: string, args: Record<string, Object>, callback: AsyncCallback<void>): void
```

Send common commands to this session

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-sendCommonCommand(command: string, args: Record<string, Object>, callback: AsyncCallback<void>): void--><!--Device-AVSessionController-sendCommonCommand(command: string, args: Record<string, Object>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | The command name to be sent. &lt;br&gt;通用控制命令 |
| args | Record&lt;string, Object&gt; | 是 | The parameters of session event |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | The asyncCallback triggered when the command is executed successfully. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-会话未激活) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

## sendCommonCommand

```TypeScript
sendCommonCommand(command: string, args: {[key: string]: Object}): Promise<void>
```

通过会话控制器发送自定义控制命令到其对应的会话。结果通过Promise异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-sendCommonCommand(command: string, args: {[key: string]: Object}): Promise<void>--><!--Device-AVSessionController-sendCommonCommand(command: string, args: {[key: string]: Object}): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | 需要设置的自定义控制命令的名称。 |
| args | {[key: string]: Object} | 是 | 需要传递的控制命令键值对。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果。 |

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

## sendCommonCommand

```TypeScript
sendCommonCommand(command: string, args: Record<string, Object>): Promise<void>
```

Send common commands to this session

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-sendCommonCommand(command: string, args: Record<string, Object>): Promise<void>--><!--Device-AVSessionController-sendCommonCommand(command: string, args: Record<string, Object>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | string | 是 | The command name to be sent. |
| args | Record&lt;string, Object&gt; | 是 | The parameters of session event |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | void promise when executed successfully |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command. |
| [6600106](../errorcode-avsession.md#6600106-会话未激活) | The session is not activated. |
| [6600107](../errorcode-avsession.md#6600107-命令消息过载) | Too many commands or events. |

## sendControlCommand

```TypeScript
sendControlCommand(command: AVControlCommand, callback: AsyncCallback<void>): void
```

通过会话控制器发送命令到其对应的会话。结果通过callback异步回调方式返回。 > **说明：** > > 媒体控制方在使用sendControlCommand命令前，需要确保控制对应的媒体会话注册了对应的监听，注册媒体会话相关监听的方法请参见接口 > on('play')、 > on('pause')等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-sendControlCommand(command: AVControlCommand, callback: AsyncCallback<void>): void--><!--Device-AVSessionController-sendControlCommand(command: AVControlCommand, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | 是 | 会话的相关命令和命令相关参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

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

## sendControlCommand

```TypeScript
sendControlCommand(command: AVControlCommand): Promise<void>
```

通过控制器发送命令到其对应的会话。结果通过Promise异步回调方式返回。 > **说明：** > > 媒体控制方在使用sendControlCommand命令前，需要确保控制对应的媒体会话注册了对应的监听，注册媒体会话相关监听的方法请参见接口 > on('play')、 > on('pause')等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-sendControlCommand(command: AVControlCommand): Promise<void>--><!--Device-AVSessionController-sendControlCommand(command: AVControlCommand): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [AVControlCommand](arkts-avsession-avsession-avcontrolcommand-i.md) | 是 | 会话的相关命令和命令相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当命令发送成功，无返回结果，否则返回错误对象。 |

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

## sendCustomData

```TypeScript
sendCustomData(data: Record<string, Object>): Promise<void>
```

发送私有数据到远端设备。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-sendCustomData(data: Record<string, Object>): Promise<void>--><!--Device-AVSessionController-sendCustomData(data: Record<string, Object>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 应用程序填充的自定义数据。服务端仅解析key为'customData'，且Object为string类型的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## setDesktopLyricState

```TypeScript
setDesktopLyricState(state: DesktopLyricState): Promise<void>
```

设置当前会话桌面歌词状态。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-setDesktopLyricState(state: DesktopLyricState): Promise<void>--><!--Device-AVSessionController-setDesktopLyricState(state: DesktopLyricState): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [DesktopLyricState](arkts-avsession-avsession-desktoplyricstate-i.md) | 是 | 桌面歌词状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-应用程序的桌面歌词功能未开启) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-当前设备不支持桌面歌词功能) | The desktop lyrics feature is not supported. |

## setDesktopLyricVisible

```TypeScript
setDesktopLyricVisible(visible: boolean): Promise<void>
```

设置当前会话桌面歌词的显示状态。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVSessionController-setDesktopLyricVisible(visible: boolean): Promise<void>--><!--Device-AVSessionController-setDesktopLyricVisible(visible: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| visible | boolean | 是 | 是否显示桌面歌词。true表示显示；false表示不显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |
| [6600110](../errorcode-avsession.md#6600110-应用程序的桌面歌词功能未开启) | The desktop lyrics feature of this application is not enabled. |
| [6600111](../errorcode-avsession.md#6600111-当前设备不支持桌面歌词功能) | The desktop lyrics feature is not supported. |

## skipToQueueItem

```TypeScript
skipToQueueItem(itemId: int, callback: AsyncCallback<void>): void
```

设置指定播放列表单项的ID，发送给session端处理，session端可以选择对这个单项歌曲进行播放。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AVSessionController-skipToQueueItem(itemId: int, callback: AsyncCallback<void>): void--><!--Device-AVSessionController-skipToQueueItem(itemId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemId | int | 是 | 播放列表单项的ID值，用以表示选中的播放列表单项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当播放状态设置成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## skipToQueueItem

```TypeScript
skipToQueueItem(itemId: int): Promise<void>
```

设置指定播放列表单项的ID，发送给session端处理，session端可以选择对这个单项歌曲进行播放。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-skipToQueueItem(itemId: int): Promise<void>--><!--Device-AVSessionController-skipToQueueItem(itemId: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemId | int | 是 | 播放列表单项的ID值，用以表示选中的播放列表单项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当播放列表单项ID设置成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-会话不存在) | The session does not exist. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## sessionId

```TypeScript
readonly sessionId: string
```

AVSessionController对象唯一的会话标识。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVSessionController-readonly sessionId: string--><!--Device-AVSessionController-readonly sessionId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

