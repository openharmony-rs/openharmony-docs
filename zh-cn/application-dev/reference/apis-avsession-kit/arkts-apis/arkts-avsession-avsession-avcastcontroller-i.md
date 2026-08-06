# AVCastController

在投播建立后，调用[avSession.getAVCastController]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_后，返回会话控制器实例。控制器可查看会话ID，并可完成对会话发送命令及事件， 获取会话元数据，播放状态信息等操作。 > **说明：** > > - 本Interface首批接口从API version 10开始支持。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-interface AVCastController--><!--Device-avSession-interface AVCastController-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## getAVPlaybackState

```TypeScript
getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void
```

获取当前的远端播放状态。结果通过callback异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-AVCastController-getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void--><!--Device-AVCastController-getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVPlaybackState&gt; | 是 | 回调函数，返回远端播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## getAVPlaybackState

```TypeScript
getAVPlaybackState(): Promise<AVPlaybackState>
```

获取当前的远端播放状态。结果通过Promise异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-getAVPlaybackState(): Promise<AVPlaybackState>--><!--Device-AVCastController-getAVPlaybackState(): Promise<AVPlaybackState>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVPlaybackState&gt; | Promise对象。返回远端播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## getCurrentItem

```TypeScript
getCurrentItem(callback: AsyncCallback<AVQueueItem>): void
```

获取当前投播的资源信息。结果通过callback异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-AVCastController-getCurrentItem(callback: AsyncCallback<AVQueueItem>): void--><!--Device-AVCastController-getCurrentItem(callback: AsyncCallback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVQueueItem&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## getCurrentItem

```TypeScript
getCurrentItem(): Promise<AVQueueItem>
```

获取当前投播的资源信息。结果通过Promise异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-getCurrentItem(): Promise<AVQueueItem>--><!--Device-AVCastController-getCurrentItem(): Promise<AVQueueItem>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;AVQueueItem&gt; | Promise对象，返回当前的播放资源，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## getRecommendedResolutionLevel

```TypeScript
getRecommendedResolutionLevel(decoderType: DecoderType): Promise<ResolutionLevel>
```

通过传递解码方式，获取推荐的分辨率。使用Promise异步回调。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-getRecommendedResolutionLevel(decoderType: DecoderType): Promise<ResolutionLevel>--><!--Device-AVCastController-getRecommendedResolutionLevel(decoderType: DecoderType): Promise<ResolutionLevel>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decoderType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设备所支持的解码格式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_设备所支持的解码格式包括：\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_'OH\_\_\_ESCAPED\_UNDERSCORE\_\_\_AVCODEC\_\_\_ESCAPED\_UNDERSCORE\_\_\_MIMETYPE\_\_\_ESCAPED\_UNDERSCORE\_\_\_VIDEO\_\_\_ESCAPED\_UNDERSCORE\_\_\_AVC'：VIDEO AVC，\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_'OH\_\_\_ESCAPED\_UNDERSCORE\_\_\_AVCODEC\_\_\_ESCAPED\_UNDERSCORE\_\_\_MIMETYPE\_\_\_ESCAPED\_UNDERSCORE\_\_\_VIDEO\_\_\_ESCAPED\_UNDERSCORE\_\_\_HEVC'：VIDEO HEVC，\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_3\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_'OH\_\_\_ESCAPED\_UNDERSCORE\_\_\_AVCODEC\_\_\_ESCAPED\_UNDERSCORE\_\_\_MIMETYPE\_\_\_ESCAPED\_UNDERSCORE\_\_\_AUDIO\_\_\_ESCAPED\_UNDERSCORE\_\_\_VIVID'：AUDIO AV3A。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResolutionLevel&gt; | Promise对象。返回远端设备推荐的分辨率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## getSupportedDecoders

```TypeScript
getSupportedDecoders(): Promise<Array<DecoderType>>
```

获取当前远端设备的解码方式。使用Promise异步回调。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-getSupportedDecoders(): Promise<Array<DecoderType>>--><!--Device-AVCastController-getSupportedDecoders(): Promise<Array<DecoderType>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DecoderType&gt;&gt; | Promise对象。返回远端设备所支持的解码能力列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## getSupportedHdrCapabilities

```TypeScript
getSupportedHdrCapabilities(): Promise<Array<hdrCapability.HDRFormat>>
```

获取当前的远端设备所支持的HDR能力。使用Promise异步回调。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-getSupportedHdrCapabilities(): Promise<Array<hdrCapability.HDRFormat>>--><!--Device-AVCastController-getSupportedHdrCapabilities(): Promise<Array<hdrCapability.HDRFormat>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;hdrCapability.HDRFormat&gt;&gt; | Promise对象。返回远端设备所支持的HDR能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## getSupportedPlaySpeeds

ArkTS-Dyn:
```TypeScript
getSupportedPlaySpeeds(): Promise<Array<number>>
```

ArkTS-Sta:
```TypeScript
getSupportedPlaySpeeds(): Promise<Array<double>>
```

获取当前的远端设备所支持倍速播放列表，仅支持使用cast+协议连接的设备。使用Promise异步回调。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-getSupportedPlaySpeeds(): Promise<Array<double>>--><!--Device-AVCastController-getSupportedPlaySpeeds(): Promise<Array<double>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;Array&lt;double&gt;&gt; | Promise对象。返回远端设备所支持的倍速播放列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## getValidCommands

```TypeScript
getValidCommands(callback: AsyncCallback<Array<AVCastControlCommandType>>): void
```

获取当前支持的命令。结果通过callback异步回调方式返回。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-AVCastController-getValidCommands(callback: AsyncCallback<Array<AVCastControlCommandType>>): void--><!--Device-AVCastController-getValidCommands(callback: AsyncCallback<Array<AVCastControlCommandType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;AVCastControlCommandType&gt;&gt; | 是 | 回调函数。返回当前支持的命令。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## getValidCommands

```TypeScript
getValidCommands(): Promise<Array<AVCastControlCommandType>>
```

获取当前支持的命令。结果通过Promise异步回调方式返回。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-AVCastController-getValidCommands(): Promise<Array<AVCastControlCommandType>>--><!--Device-AVCastController-getValidCommands(): Promise<Array<AVCastControlCommandType>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;AVCastControlCommandType&gt;&gt; | Promise对象，返回当前支持的命令。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## off('playbackStateChange')

```TypeScript
off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void
```

取消播放状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void--><!--Device-AVCastController-off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | 是 |  |
| callback | (state: AVPlaybackState) =&gt; void | 否 | 回调函数，参数state是变化后的播放状态。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off

```TypeScript
off(type: 'mediaItemChange'): void
```

取消设置投播当前播放媒体内容事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'mediaItemChange'): void--><!--Device-AVCastController-off(type: 'mediaItemChange'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mediaItemChange' | 是 | 取消对应的监听事件，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off

```TypeScript
off(type: 'playNext'): void
```

取消设置播放下一首资源事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'playNext'): void--><!--Device-AVCastController-off(type: 'playNext'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playNext' | 是 | 取消对应的监听事件，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off

```TypeScript
off(type: 'playPrevious'): void
```

取消设置播放上一首资源事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'playPrevious'): void--><!--Device-AVCastController-off(type: 'playPrevious'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playPrevious' | 是 | 取消对应的监听事件，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off('requestPlay')

```TypeScript
off(type: 'requestPlay', callback?: Callback<AVQueueItem>): void
```

取消设置请求播放事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-AVCastController-off(type: 'requestPlay', callback?: Callback<AVQueueItem>): void--><!--Device-AVCastController-off(type: 'requestPlay', callback?: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'requestPlay' | 是 | 取消对应的监听事件，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVQueueItem&gt; | 否 | 回调函数，参数AVQueueItem是当前正在播放的媒体内容。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off('endOfStream')

```TypeScript
off(type: 'endOfStream', callback?: Callback<void>): void
```

取消设置播放结束事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-AVCastController-off(type: 'endOfStream', callback?: Callback<void>): void--><!--Device-AVCastController-off(type: 'endOfStream', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 取消对应的监听事件，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off

```TypeScript
off(type: 'seekDone'): void
```

取消设置seek结束事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'seekDone'): void--><!--Device-AVCastController-off(type: 'seekDone'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'seekDone' | 是 | 取消对应的监听事件，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off('validCommandChange')

```TypeScript
off(type: 'validCommandChange', callback?: Callback<Array<AVCastControlCommandType>>)
```

取消会话有效命令变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-AVCastController-off(type: 'validCommandChange', callback?: Callback<Array<AVCastControlCommandType>>)--><!--Device-AVCastController-off(type: 'validCommandChange', callback?: Callback<Array<AVCastControlCommandType>>)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'validCommandChange' | 是 | 取消对应的监听事件，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;AVCastControlCommandType&gt;&gt; | 否 | 回调函数。参数commands是有效命令的集合。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## off

```TypeScript
off(type: 'videoSizeChange'): void
```

取消视频尺寸事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-AVCastController-off(type: 'videoSizeChange'): void--><!--Device-AVCastController-off(type: 'videoSizeChange'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当检测到会话的合法命令发生改变时，触发该事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

**示例：**

```TypeScript
aVCastController.off('videoSizeChange');
```

## off

```TypeScript
off(type: 'error'): void
```

取消播放的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'error'): void--><!--Device-AVCastController-off(type: 'error'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 错误事件回调类型，取消注册的事件：'error'。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [5400101](../../apis-media-kit/errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400104](../../apis-media-kit/errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-不支持的规格) | Unsupport format. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off('castControlGenericError')

```TypeScript
off(type: 'castControlGenericError', callback?: ErrorCallback): void
```

取消投播通用的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlGenericError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlGenericError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlGenericError' | 是 | 取消对应的监听事件，支持的事件是'castControlGenericError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

## off('castControlIoError')

```TypeScript
off(type: 'castControlIoError', callback?: ErrorCallback): void
```

取消投播输入/输出的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlIoError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlIoError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlIoError' | 是 | 取消对应的监听事件，支持的事件是'castControlIoError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

## off('castControlParsingError')

```TypeScript
off(type: 'castControlParsingError', callback?: ErrorCallback): void
```

取消投播解析的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlParsingError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlParsingError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlParsingError' | 是 | 取消对应的监听事件，支持的事件是'castControlParsingError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

## off('castControlDecodingError')

```TypeScript
off(type: 'castControlDecodingError', callback?: ErrorCallback): void
```

取消投播解码的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlDecodingError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlDecodingError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlDecodingError' | 是 | 取消对应的监听事件，支持的事件是'castControlDecodingError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

## off('castControlAudioRendererError')

```TypeScript
off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void
```

取消投播音频渲染器的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlAudioRendererError' | 是 | 取消对应的监听事件，支持的事件是'castControlAudioRendererError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

## off('castControlDrmError')

```TypeScript
off(type: 'castControlDrmError', callback?: ErrorCallback): void
```

取消投播drm的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlDrmError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlDrmError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlDrmError' | 是 | 取消对应的监听事件，支持的事件是'castControlDrmError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

## off('keyRequest')

```TypeScript
off(type: 'keyRequest', callback?: KeyRequestCallback): void
```

取消许可证请求事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'keyRequest', callback?: KeyRequestCallback): void--><!--Device-AVCastController-off(type: 'keyRequest', callback?: KeyRequestCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyRequest' | 是 | 取消对应的监听事件，支持的事件是\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## off('customDataChange')

```TypeScript
off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void
```

取消对自定义数据的监听。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void--><!--Device-AVCastController-off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'customDataChange' | 是 | 取消对应的监听事件，支持的事件是'customDataChange'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Record&lt;string, Object&gt;&gt; | 否 | 注册监听事件时的回调函数。该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offCastControlAudioRendererError

```TypeScript
offCastControlAudioRendererError(callback?: ErrorCallback): void
```

Unregister listeners for cast control audio renderer error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offCastControlAudioRendererError(callback?: ErrorCallback): void--><!--Device-AVCastController-offCastControlAudioRendererError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to listen for the cast control error event. |

## offCastControlDecodingError

```TypeScript
offCastControlDecodingError(callback?: ErrorCallback): void
```

Unregister listeners for cast control decoding error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offCastControlDecodingError(callback?: ErrorCallback): void--><!--Device-AVCastController-offCastControlDecodingError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to listen for the cast control error event. |

## offCastControlDrmError

```TypeScript
offCastControlDrmError(callback?: ErrorCallback): void
```

Unregister listeners for cast control drm error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offCastControlDrmError(callback?: ErrorCallback): void--><!--Device-AVCastController-offCastControlDrmError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to listen for the cast control error event. |

## offCastControlGenericError

```TypeScript
offCastControlGenericError(callback?: ErrorCallback): void
```

Unregister listeners for cast control generic error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offCastControlGenericError(callback?: ErrorCallback): void--><!--Device-AVCastController-offCastControlGenericError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to listen for the cast control error event. |

## offCastControlIoError

```TypeScript
offCastControlIoError(callback?: ErrorCallback): void
```

Unregister listeners for cast control input/output error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offCastControlIoError(callback?: ErrorCallback): void--><!--Device-AVCastController-offCastControlIoError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to listen for the cast control error event. |

## offCastControlParsingError

```TypeScript
offCastControlParsingError(callback?: ErrorCallback): void
```

Unregister listeners for cast control parsing error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offCastControlParsingError(callback?: ErrorCallback): void--><!--Device-AVCastController-offCastControlParsingError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to listen for the cast control error event. |

## offCustomDataChange

```TypeScript
offCustomDataChange(callback?: Callback<Record<string, Object>>): void
```

Unregister listener for custom data sent from remote device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offCustomDataChange(callback?: Callback<Record<string, Object>>): void--><!--Device-AVCastController-offCustomDataChange(callback?: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Record&lt;string, Object&gt;&gt; | 否 | Callback used to retrieve custom data. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offEndOfStream

```TypeScript
offEndOfStream(callback?: NoParamCallback): void
```

Unregister endOfStream state callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offEndOfStream(callback?: NoParamCallback): void--><!--Device-AVCastController-offEndOfStream(callback?: NoParamCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Used to handle 'endOfStream' command |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offError

```TypeScript
offError(): void
```

Unregister listens for playback error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offError(): void--><!--Device-AVCastController-offError(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../../apis-media-kit/errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400104](../../apis-media-kit/errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-不支持的规格) | Unsupport format. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offKeyRequest

```TypeScript
offKeyRequest(callback?: KeyRequestCallback): void
```

Unregister listener for drm key request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offKeyRequest(callback?: KeyRequestCallback): void--><!--Device-AVCastController-offKeyRequest(callback?: KeyRequestCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to request drm key. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offMediaItemChange

```TypeScript
offMediaItemChange(): void
```

Unregister listener for current media item playback events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offMediaItemChange(): void--><!--Device-AVCastController-offMediaItemChange(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offPlayNext

```TypeScript
offPlayNext(): void
```

Unregister playback command callback sent by remote side or media center. When canceling the callback, need to update the supported commands list.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offPlayNext(): void--><!--Device-AVCastController-offPlayNext(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offPlayPrevious

```TypeScript
offPlayPrevious(): void
```

Unregister playback command callback sent by remote side or media center. When canceling the callback, need to update the supported commands list.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offPlayPrevious(): void--><!--Device-AVCastController-offPlayPrevious(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offPlaybackStateChange

```TypeScript
offPlaybackStateChange(callback?: Callback<AVPlaybackState>): void
```

Unregister playback state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offPlaybackStateChange(callback?: Callback<AVPlaybackState>): void--><!--Device-AVCastController-offPlaybackStateChange(callback?: Callback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVPlaybackState&gt; | 否 | The callback used to handle playback state changed event.The callback function provides the \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offRequestPlay

```TypeScript
offRequestPlay(callback?: Callback<AVQueueItem>): void
```

Unregister requested playback command callback sent by remote side or media center.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offRequestPlay(callback?: Callback<AVQueueItem>): void--><!--Device-AVCastController-offRequestPlay(callback?: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVQueueItem&gt; | 否 | Used to handle 'requestPlay' command |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offSeekDone

```TypeScript
offSeekDone(): void
```

Unregister listens for playback events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offSeekDone(): void--><!--Device-AVCastController-offSeekDone(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## offValidCommandChange

```TypeScript
offValidCommandChange(callback?: Callback<Array<AVCastControlCommandType>>): void
```

Unregister the valid commands of the casted session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offValidCommandChange(callback?: Callback<Array<AVCastControlCommandType>>): void--><!--Device-AVCastController-offValidCommandChange(callback?: Callback<Array<AVCastControlCommandType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;AVCastControlCommandType&gt;&gt; | 否 | The callback used to handle the changes.The callback function provides an array of AVCastControlCommandType. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## offVideoSizeChange

```TypeScript
offVideoSizeChange(): void
```

Unregister listener for video size change event, used at remote side.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-offVideoSizeChange(): void--><!--Device-AVCastController-offVideoSizeChange(): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

**示例：**

```TypeScript
aVCastController.offVideoSizeChange();
```

## on('playbackStateChange')

```TypeScript
on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void
```

设置播放状态变化的监听事件。使用callback异步回调。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void--><!--Device-AVCastController-on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | 是 |  |
| filter | Array&lt;keyof AVPlaybackState&gt; \| 'all' | 是 | 'all'表示关注播放状态所有字段变化；Array&lt;keyof AVPlaybackState&gt;表示关注Array中的字段变化。 |
| callback | (state: AVPlaybackState) =&gt; void | 是 | 回调函数，参数state是变化后的播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('mediaItemChange')

```TypeScript
on(type: 'mediaItemChange', callback: Callback<AVQueueItem>): void
```

设置投播当前播放媒体内容的监听事件。使用callback异步回调。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'mediaItemChange', callback: Callback<AVQueueItem>): void--><!--Device-AVCastController-on(type: 'mediaItemChange', callback: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mediaItemChange' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当播放的媒体内容变化时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVQueueItem&gt; | 是 | 回调函数，参数AVQueueItem是当前正在播放的媒体内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('playNext')

```TypeScript
on(type: 'playNext', callback: Callback<void>): void
```

设置播放下一首资源的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'playNext', callback: Callback<void>): void--><!--Device-AVCastController-on(type: 'playNext', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playNext' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当播放下一首状态变化时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('playPrevious')

```TypeScript
on(type: 'playPrevious', callback: Callback<void>): void
```

设置播放上一首资源的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'playPrevious', callback: Callback<void>): void--><!--Device-AVCastController-on(type: 'playPrevious', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playPrevious' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当播放上一首状态变化时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('requestPlay')

```TypeScript
on(type: 'requestPlay', callback: Callback<AVQueueItem>): void
```

设置请求播放的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-AVCastController-on(type: 'requestPlay', callback: Callback<AVQueueItem>): void--><!--Device-AVCastController-on(type: 'requestPlay', callback: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'requestPlay' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当请求播放状态变化时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVQueueItem&gt; | 是 | 回调函数，参数AVQueueItem是当前正在播放的媒体内容。当监听事件注册成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('endOfStream')

```TypeScript
on(type: 'endOfStream', callback: Callback<void>): void
```

设置播放结束的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-AVCastController-on(type: 'endOfStream', callback: Callback<void>): void--><!--Device-AVCastController-on(type: 'endOfStream', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当资源播放结束时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当监听事件注册成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('seekDone')

```TypeScript
on(type: 'seekDone', callback: Callback<int>): void
```

设置seek结束的监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'seekDone', callback: Callback<int>): void--><!--Device-AVCastController-on(type: 'seekDone', callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'seekDone' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当seek结束时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | 回调函数，返回seek后播放的位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('validCommandChange')

```TypeScript
on(type: 'validCommandChange', callback: Callback<Array<AVCastControlCommandType>>)
```

会话支持的有效命令变化监听事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-AVCastController-on(type: 'validCommandChange', callback: Callback<Array<AVCastControlCommandType>>)--><!--Device-AVCastController-on(type: 'validCommandChange', callback: Callback<Array<AVCastControlCommandType>>)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'validCommandChange' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当检测到会话的合法命令发生改变时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;AVCastControlCommandType&gt;&gt; | 是 | 回调函数。参数commands是有效命令的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## on('videoSizeChange')

```TypeScript
on(type: 'videoSizeChange', callback: (width: int, height: int) => void): void
```

媒体控制器监听视频尺寸变化变化的事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-AVCastController-on(type: 'videoSizeChange', callback: (width: int, height: int) => void): void--><!--Device-AVCastController-on(type: 'videoSizeChange', callback: (width: int, height: int) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当检测到会话的合法命令发生改变时，触发该事件。 |
| callback | (width: int, height: int) =&gt; void | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

**示例：**

```TypeScript
aVCastController.on('videoSizeChange', (width: number, height: number) => {
  console.info(`width ：${width} `);
  console.info(`height：${height} `);
});
```

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听远端播放器的错误事件，该事件仅用于错误提示，不需要用户停止播控动作。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'error', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 错误事件回调类型，支持的事件：'error'，用户操作和系统都会触发此事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 错误事件回调方法：远端播放过程中发生的错误，会提供错误码ID和错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [5400101](../../apis-media-kit/errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400104](../../apis-media-kit/errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-不支持的规格) | Unsupport format. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('castControlGenericError')

```TypeScript
on(type: 'castControlGenericError', callback: ErrorCallback): void
```

监听投播通用错误事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlGenericError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlGenericError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlGenericError' | 是 | 错误事件回调类型，支持的事件：'castControlGenericError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 投播通用错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6611000](../errorcode-avsession.md#6611000-投播控制器出现未知错误) | The error code for cast control is unspecified. |
| [6611001](../errorcode-avsession.md#6611001-远端设备出现未知错误) | An unspecified error occurs in the remote player. |
| [6611002](../errorcode-avsession.md#6611002-加载位置超过投播视频的总进度) | The playback position falls behind the live window. |
| [6611003](../errorcode-avsession.md#6611003-投播控制器加载超时) | The process of cast control times out. |
| [6611004](../errorcode-avsession.md#6611004-运行时检查失败) | The runtime check failed. |
| [6611100](../errorcode-avsession.md#6611100-跨设备数据传输被锁定) | Cross-device data transmission is locked. |
| [6611101](../errorcode-avsession.md#6611101-不支持当前进度条模式) | The specified seek mode is not supported. |
| [6611102](../errorcode-avsession.md#6611102-非法seek目标) | The position to seek to is out of the range of the media asset or the specified seek mode is not supported. |
| [6611103](../errorcode-avsession.md#6611103-不支持当前播放模式) | The specified playback mode is not supported. |
| [6611104](../errorcode-avsession.md#6611104-不支持当前播放速度) | The specified playback speed is not supported. |
| [6611105](../errorcode-avsession.md#6611105-设备吊销) | The action failed because either the media source device or the media sink device has been revoked. |
| [6611106](../errorcode-avsession.md#6611106-传入非法参数) | The parameter is invalid, for example, the url is illegal to play. |
| [6611107](../errorcode-avsession.md#6611107-内存分配失败) | Allocation of memory failed. |
| [6611108](../errorcode-avsession.md#6611108-不允许进行当前操作) | Operation is not allowed. |

## on('castControlIoError')

```TypeScript
on(type: 'castControlIoError', callback: ErrorCallback): void
```

监听投播输入/输出的错误事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlIoError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlIoError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlIoError' | 是 | 错误事件回调类型，支持的事件：'castControlIoError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 投播输入/输出的错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6612000](../errorcode-avsession.md#6612000-未知的输入输出错误) | An unspecified input/output error occurs. |
| [6612001](../errorcode-avsession.md#6612001-网络连接失败) | Network connection failure. |
| [6612002](../errorcode-avsession.md#6612002-网络超时) | Network timeout. |
| [6612003](../errorcode-avsession.md#6612003-无效contenttypehttp头) | Invalid "Content-Type" HTTP header. |
| [6612004](../errorcode-avsession.md#6612004-http服务器返回异常的http响应状态码) | The HTTP server returns an unexpected HTTP response status code. |
| [6612005](../errorcode-avsession.md#6612005-文件不存在) | The file does not exist. |
| [6612006](../errorcode-avsession.md#6612006-缺少执行io操作的权限) | No permission is granted to perform the IO operation. |
| [6612007](../errorcode-avsession.md#6612007-网络安全配置不允许此操作) | Access to cleartext HTTP traffic is not allowed by the app's network security configuration. |
| [6612008](../errorcode-avsession.md#6612008-读取数据超出数据范围) | Reading data out of the data bound. |
| [6612100](../errorcode-avsession.md#6612100-缺少可播放的媒体资源) | The media does not contain any contents that can be played. |
| [6612101](../errorcode-avsession.md#6612101-媒体资源无法被读取) | The media cannot be read, for example, because of dust or scratches. |
| [6612102](../errorcode-avsession.md#6612102-资源正在使用) | This resource is already in use. |
| [6612103](../errorcode-avsession.md#6612103-内容使用有效期已过) | The content using the validity interval has expired. |
| [6612104](../errorcode-avsession.md#6612104-不允许使用请求的内容) | Using the requested content to play is not allowed. |
| [6612105](../errorcode-avsession.md#6612105-无法验证允许使用的内容) | The use of the allowed content cannot be verified. |
| [6612106](../errorcode-avsession.md#6612106-资源使用频繁) | The number of times this content has been used as requested has reached the maximum allowed number of uses. |
| [6612107](../errorcode-avsession.md#6612107-本端向远端发送资源包失败) | An error occurs when sending packet from source device to sink device. |

## on('castControlParsingError')

```TypeScript
on(type: 'castControlParsingError', callback: ErrorCallback): void
```

监听投播解析的错误事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlParsingError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlParsingError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlParsingError' | 是 | 错误事件回调类型，支持的事件：'castControlParsingError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 投播解析的错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6613000](../errorcode-avsession.md#6613000-未知解析错误) | Unspecified error related to content parsing. |
| [6613001](../errorcode-avsession.md#6613001-非法类型) | Parsing error associated with media container format bit streams. |
| [6613002](../errorcode-avsession.md#6613002-相关媒体清单的解析错误) | Parsing error associated with the media manifest. |
| [6613003](../errorcode-avsession.md#6613003-不支持该媒体格式) | An error occurs when attempting to extract a file with an unsupported media container format or an unsupported media container feature. |
| [6613004](../errorcode-avsession.md#6613004-媒体清单中不支持此功能) | Unsupported feature in the media manifest. |

## on('castControlDecodingError')

```TypeScript
on(type: 'castControlDecodingError', callback: ErrorCallback): void
```

监听投播解码的错误事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlDecodingError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlDecodingError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlDecodingError' | 是 | 错误事件回调类型，支持的事件：'castControlDecodingError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 投播解码的错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6614000](../errorcode-avsession.md#6614000-未知的解码错误) | Unspecified decoding error. |
| [6614001](../errorcode-avsession.md#6614001-解码器初始化失败) | Decoder initialization failed. |
| [6614002](../errorcode-avsession.md#6614002-解码器查询失败) | Decoder query failed. |
| [6614003](../errorcode-avsession.md#6614003-解码媒体样本时失败) | Decoding the media samples failed. |
| [6614004](../errorcode-avsession.md#6614004-所需解码的内容格式超出设备能力) | The format of the content to decode exceeds the capabilities of the device. |
| [6614005](../errorcode-avsession.md#6614005-解码不支持的内容格式) | The format of the content to decode is not supported. |

## on('castControlAudioRendererError')

```TypeScript
on(type: 'castControlAudioRendererError', callback: ErrorCallback): void
```

监听投播音频渲染器的错误事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlAudioRendererError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlAudioRendererError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlAudioRendererError' | 是 | 错误事件回调类型，支持的事件：'castControlAudioRendererError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 投播音频渲染器的错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6615000](../errorcode-avsession.md#6615000-音频渲染器相关的未知错误) | Unspecified errors related to the audio renderer. |
| [6615001](../errorcode-avsession.md#6615001-音频渲染器初始化异常) | Initializing the audio renderer failed. |
| [6615002](../errorcode-avsession.md#6615002-音频渲染器写数据异常) | The audio renderer fails to write data. |

## on('castControlDrmError')

```TypeScript
on(type: 'castControlDrmError', callback: ErrorCallback): void
```

监听投播drm的错误事件。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlDrmError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlDrmError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlDrmError' | 是 | 错误事件回调类型，支持的事件：'castControlDrmError'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 投播drm的错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6616000](../errorcode-avsession.md#6616000-drm相关的未知错误) | Unspecified error related to DRM. |
| [6616001](../errorcode-avsession.md#6616001-设备不支持所选的drm保护方案) | The chosen DRM protection scheme is not supported by the device. |
| [6616002](../errorcode-avsession.md#6616002-调配设备时出现故障) | Device provisioning failed. |
| [6616003](../errorcode-avsession.md#6616003-尝试播放不兼容的drm保护内容) | The DRM-protected content to play is incompatible. |
| [6616004](../errorcode-avsession.md#6616004-许可证获取失败) | Failed to obtain a license. |
| [6616005](../errorcode-avsession.md#6616005-许可证策略不允许的操作) | The operation is disallowed by the license policy. |
| [6616006](../errorcode-avsession.md#6616006-drm系统错误) | An error occurs in the DRM system. |
| [6616007](../errorcode-avsession.md#6616007-设备已吊销drm权限) | The device has revoked DRM privileges. |
| [6616008](../errorcode-avsession.md#6616008-已过期的drm许可证被加载到打开的drm会话中) | The DRM license being loaded into the open DRM session has expired. |
| [6616100](../errorcode-avsession.md#6616100-drm进程密钥响应错误) | An error occurs when the DRM processes the key response. |

## on('keyRequest')

```TypeScript
on(type: 'keyRequest', callback: KeyRequestCallback): void
```

在线DRM资源投播时，设置许可证请求的事件监听。 每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'keyRequest', callback: KeyRequestCallback): void--><!--Device-AVCastController-on(type: 'keyRequest', callback: KeyRequestCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyRequest' | 是 | 事件回调类型，支持事件\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_：当DRM资源播放需要许可证时，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调函数，媒体资源及许可证请求数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## on('customDataChange')

```TypeScript
on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void
```

注册从远端设备发送的自定义数据的监听器。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void--><!--Device-AVCastController-on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'customDataChange' | 是 | 事件回调类型，支持'customDataChange'事件。媒体提供方发送自定义数据时触发。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Record&lt;string, Object&gt;&gt; | 是 | 回调函数，用于接收自定义数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onCastControlAudioRendererError

```TypeScript
onCastControlAudioRendererError(callback: ErrorCallback): void
```

Register listeners for cast control audio renderer error error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onCastControlAudioRendererError(callback: ErrorCallback): void--><!--Device-AVCastController-onCastControlAudioRendererError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to listen for the cast control error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6615000](../errorcode-avsession.md#6615000-音频渲染器相关的未知错误) | Unspecified errors related to the audio renderer. |
| [6615001](../errorcode-avsession.md#6615001-音频渲染器初始化异常) | Initializing the audio renderer failed. |
| [6615002](../errorcode-avsession.md#6615002-音频渲染器写数据异常) | The audio renderer fails to write data. |

## onCastControlDecodingError

```TypeScript
onCastControlDecodingError(callback: ErrorCallback): void
```

Register listeners for cast control decoding error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onCastControlDecodingError(callback: ErrorCallback): void--><!--Device-AVCastController-onCastControlDecodingError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to listen for the cast control error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6614000](../errorcode-avsession.md#6614000-未知的解码错误) | Unspecified decoding error. |
| [6614001](../errorcode-avsession.md#6614001-解码器初始化失败) | Decoder initialization failed. |
| [6614002](../errorcode-avsession.md#6614002-解码器查询失败) | Decoder query failed. |
| [6614003](../errorcode-avsession.md#6614003-解码媒体样本时失败) | Decoding the media samples failed. |
| [6614004](../errorcode-avsession.md#6614004-所需解码的内容格式超出设备能力) | The format of the content to decode exceeds the capabilities of the device. |
| [6614005](../errorcode-avsession.md#6614005-解码不支持的内容格式) | The format of the content to decode is not supported. |

## onCastControlDrmError

```TypeScript
onCastControlDrmError(callback: ErrorCallback): void
```

Register listeners for cast control drm error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onCastControlDrmError(callback: ErrorCallback): void--><!--Device-AVCastController-onCastControlDrmError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to listen for the cast control error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6616000](../errorcode-avsession.md#6616000-drm相关的未知错误) | Unspecified error related to DRM. |
| [6616001](../errorcode-avsession.md#6616001-设备不支持所选的drm保护方案) | The chosen DRM protection scheme is not supported by the device. |
| [6616002](../errorcode-avsession.md#6616002-调配设备时出现故障) | Device provisioning failed. |
| [6616003](../errorcode-avsession.md#6616003-尝试播放不兼容的drm保护内容) | The DRM-protected content to play is incompatible. |
| [6616004](../errorcode-avsession.md#6616004-许可证获取失败) | Failed to obtain a license. |
| [6616005](../errorcode-avsession.md#6616005-许可证策略不允许的操作) | The operation is disallowed by the license policy. |
| [6616006](../errorcode-avsession.md#6616006-drm系统错误) | An error occurs in the DRM system. |
| [6616007](../errorcode-avsession.md#6616007-设备已吊销drm权限) | The device has revoked DRM privileges. |
| [6616008](../errorcode-avsession.md#6616008-已过期的drm许可证被加载到打开的drm会话中) | The DRM license being loaded into the open DRM session has expired. |
| [6616100](../errorcode-avsession.md#6616100-drm进程密钥响应错误) | An error occurs when the DRM processes the key response. |

## onCastControlGenericError

```TypeScript
onCastControlGenericError(callback: ErrorCallback): void
```

Register listeners for cast control generic error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onCastControlGenericError(callback: ErrorCallback): void--><!--Device-AVCastController-onCastControlGenericError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to listen for the cast control error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6611000](../errorcode-avsession.md#6611000-投播控制器出现未知错误) | The error code for cast control is unspecified. |
| [6611001](../errorcode-avsession.md#6611001-远端设备出现未知错误) | An unspecified error occurs in the remote player. |
| [6611002](../errorcode-avsession.md#6611002-加载位置超过投播视频的总进度) | The playback position falls behind the live window. |
| [6611003](../errorcode-avsession.md#6611003-投播控制器加载超时) | The process of cast control times out. |
| [6611004](../errorcode-avsession.md#6611004-运行时检查失败) | The runtime check failed. |
| [6611100](../errorcode-avsession.md#6611100-跨设备数据传输被锁定) | Cross-device data transmission is locked. |
| [6611101](../errorcode-avsession.md#6611101-不支持当前进度条模式) | The specified seek mode is not supported. |
| [6611102](../errorcode-avsession.md#6611102-非法seek目标) | The position to seek to is out of the range of the media asset or the specified seek mode is not supported. |
| [6611103](../errorcode-avsession.md#6611103-不支持当前播放模式) | The specified playback mode is not supported. |
| [6611104](../errorcode-avsession.md#6611104-不支持当前播放速度) | The specified playback speed is not supported. |
| [6611105](../errorcode-avsession.md#6611105-设备吊销) | The action failed because either the media source device or the media sink device has been revoked. |
| [6611106](../errorcode-avsession.md#6611106-传入非法参数) | The parameter is invalid, for example, the url is illegal to play. |
| [6611107](../errorcode-avsession.md#6611107-内存分配失败) | Allocation of memory failed. |
| [6611108](../errorcode-avsession.md#6611108-不允许进行当前操作) | Operation is not allowed. |

## onCastControlIoError

```TypeScript
onCastControlIoError(callback: ErrorCallback): void
```

Register listeners for cast control input/output error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onCastControlIoError(callback: ErrorCallback): void--><!--Device-AVCastController-onCastControlIoError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to listen for the cast control error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6612000](../errorcode-avsession.md#6612000-未知的输入输出错误) | An unspecified input/output error occurs. |
| [6612001](../errorcode-avsession.md#6612001-网络连接失败) | Network connection failure. |
| [6612002](../errorcode-avsession.md#6612002-网络超时) | Network timeout. |
| [6612003](../errorcode-avsession.md#6612003-无效contenttypehttp头) | Invalid "Content-Type" HTTP header. |
| [6612004](../errorcode-avsession.md#6612004-http服务器返回异常的http响应状态码) | The HTTP server returns an unexpected HTTP response status code. |
| [6612005](../errorcode-avsession.md#6612005-文件不存在) | The file does not exist. |
| [6612006](../errorcode-avsession.md#6612006-缺少执行io操作的权限) | No permission is granted to perform the IO operation. |
| [6612007](../errorcode-avsession.md#6612007-网络安全配置不允许此操作) | Access to cleartext HTTP traffic is not allowed by the app's network security configuration. |
| [6612008](../errorcode-avsession.md#6612008-读取数据超出数据范围) | Reading data out of the data bound. |
| [6612100](../errorcode-avsession.md#6612100-缺少可播放的媒体资源) | The media does not contain any contents that can be played. |
| [6612101](../errorcode-avsession.md#6612101-媒体资源无法被读取) | The media cannot be read, for example, because of dust or scratches. |
| [6612102](../errorcode-avsession.md#6612102-资源正在使用) | This resource is already in use. |
| [6612103](../errorcode-avsession.md#6612103-内容使用有效期已过) | The content using the validity interval has expired. |
| [6612104](../errorcode-avsession.md#6612104-不允许使用请求的内容) | Using the requested content to play is not allowed. |
| [6612105](../errorcode-avsession.md#6612105-无法验证允许使用的内容) | The use of the allowed content cannot be verified. |
| [6612106](../errorcode-avsession.md#6612106-资源使用频繁) | The number of times this content has been used as requested has reached the maximum allowed number of uses. |
| [6612107](../errorcode-avsession.md#6612107-本端向远端发送资源包失败) | An error occurs when sending packet from source device to sink device. |

## onCastControlParsingError

```TypeScript
onCastControlParsingError(callback: ErrorCallback): void
```

Register listeners for cast control parsing error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onCastControlParsingError(callback: ErrorCallback): void--><!--Device-AVCastController-onCastControlParsingError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to listen for the cast control error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6613000](../errorcode-avsession.md#6613000-未知解析错误) | Unspecified error related to content parsing. |
| [6613001](../errorcode-avsession.md#6613001-非法类型) | Parsing error associated with media container format bit streams. |
| [6613002](../errorcode-avsession.md#6613002-相关媒体清单的解析错误) | Parsing error associated with the media manifest. |
| [6613003](../errorcode-avsession.md#6613003-不支持该媒体格式) | An error occurs when attempting to extract a file with an unsupported media container format or an unsupported media container feature. |
| [6613004](../errorcode-avsession.md#6613004-媒体清单中不支持此功能) | Unsupported feature in the media manifest. |

## onCustomDataChange

```TypeScript
onCustomDataChange(callback: Callback<Record<string, Object>>): void
```

Register listener for custom data sent from remote device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onCustomDataChange(callback: Callback<Record<string, Object>>): void--><!--Device-AVCastController-onCustomDataChange(callback: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Record&lt;string, Object&gt;&gt; | 是 | Callback used to retrieve custom data. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onEndOfStream

```TypeScript
onEndOfStream(callback: NoParamCallback): void
```

Register endOfStream state callback. Application needs update the new media resource when receive these commands by using playItem.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onEndOfStream(callback: NoParamCallback): void--><!--Device-AVCastController-onEndOfStream(callback: NoParamCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Used to handle 'endOfStream' command |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

Register listeners for playback error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onError(callback: ErrorCallback): void--><!--Device-AVCastController-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to listen for the playback error event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400101](../../apis-media-kit/errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../../apis-media-kit/errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../../apis-media-kit/errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400104](../../apis-media-kit/errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../../apis-media-kit/errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../../apis-media-kit/errorcode-media.md#5400106-不支持的规格) | Unsupport format. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onKeyRequest

```TypeScript
onKeyRequest(callback: KeyRequestCallback): void
```

Register listener for drm key request.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onKeyRequest(callback: KeyRequestCallback): void--><!--Device-AVCastController-onKeyRequest(callback: KeyRequestCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to request drm key. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onMediaItemChange

```TypeScript
onMediaItemChange(callback: Callback<AVQueueItem>): void
```

Register listener for current media item playback events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onMediaItemChange(callback: Callback<AVQueueItem>): void--><!--Device-AVCastController-onMediaItemChange(callback: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVQueueItem&gt; | 是 | Callback used to listen for current item changed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onPlayNext

```TypeScript
onPlayNext(callback: NoParamCallback): void
```

Register playback command callback sent by remote side or media center. Application needs update the new media resource when receive these commands by using playItem.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onPlayNext(callback: NoParamCallback): void--><!--Device-AVCastController-onPlayNext(callback: NoParamCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Used to handle 'playNext' command |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onPlayPrevious

```TypeScript
onPlayPrevious(callback: NoParamCallback): void
```

Register playback command callback sent by remote side or media center. Application needs update the new media resource when receive these commands by using playItem.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onPlayPrevious(callback: NoParamCallback): void--><!--Device-AVCastController-onPlayPrevious(callback: NoParamCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Used to handle 'playPrevious' command |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onPlaybackStateChange

```TypeScript
onPlaybackStateChange(filter: Array<string>, callback: Callback<AVPlaybackState>): void
```

Register playback state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onPlaybackStateChange(filter: Array<string>, callback: Callback<AVPlaybackState>): void--><!--Device-AVCastController-onPlaybackStateChange(filter: Array<string>, callback: Callback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | Array&lt;string&gt; | 是 | The properties of \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ that you cared about |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVPlaybackState&gt; | 是 | The callback used to handle playback state changed event.The callback function provides the \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onPlaybackStateChangeAll

```TypeScript
onPlaybackStateChangeAll(callback: Callback<AVPlaybackState>): void
```

Register playback state changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onPlaybackStateChangeAll(callback: Callback<AVPlaybackState>): void--><!--Device-AVCastController-onPlaybackStateChangeAll(callback: Callback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVPlaybackState&gt; | 是 | The callback used to handle playback state changed event.The callback function provides the \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ parameter. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onRequestPlay

```TypeScript
onRequestPlay(callback: Callback<AVQueueItem>): void
```

Register requested playback command callback sent by remote side or media center. The AVQueueItem may include the requested assetId, starting position and other configurations.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onRequestPlay(callback: Callback<AVQueueItem>): void--><!--Device-AVCastController-onRequestPlay(callback: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;AVQueueItem&gt; | 是 | Used to handle 'requestPlay' command |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onSeekDone

```TypeScript
onSeekDone(callback: Callback<int>): void
```

Register listens for playback events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onSeekDone(callback: Callback<int>): void--><!--Device-AVCastController-onSeekDone(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | Callback used to listen for the playback seekDone event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## onValidCommandChange

```TypeScript
onValidCommandChange(callback: Callback<Array<AVCastControlCommandType>>): void
```

Register the valid commands of the casted session changed callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onValidCommandChange(callback: Callback<Array<AVCastControlCommandType>>): void--><!--Device-AVCastController-onValidCommandChange(callback: Callback<Array<AVCastControlCommandType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;AVCastControlCommandType&gt;&gt; | 是 | The callback used to handle the changes.The callback function provides an array of AVCastControlCommandType. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

## onVideoSizeChange

```TypeScript
onVideoSizeChange(callback: VideoSizeEvent): void
```

Register listener for video size change event, used at remote side.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVCastController-onVideoSizeChange(callback: VideoSizeEvent): void--><!--Device-AVCastController-onVideoSizeChange(callback: VideoSizeEvent): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to return video size. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

**示例：**

```TypeScript
aVCastController.onVideoSizeChange((width: int, height: int) => {
  console.info(`width ：${width} `);
  console.info(`height：${height} `);
});
```

## prepare

```TypeScript
prepare(item: AVQueueItem, callback: AsyncCallback<void>): void
```

准备播放媒体资源，即进行播放资源的加载和缓冲。结果通过callback异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-AVCastController-prepare(item: AVQueueItem, callback: AsyncCallback<void>): void--><!--Device-AVCastController-prepare(item: AVQueueItem, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 播放列表中单项的相关属性。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

## prepare

```TypeScript
prepare(item: AVQueueItem): Promise<void>
```

准备播放媒体资源，即进行播放资源的加载和缓冲。结果通过Promise异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-prepare(item: AVQueueItem): Promise<void>--><!--Device-AVCastController-prepare(item: AVQueueItem): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 播放列表中单项的相关属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当命令发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

## processMediaKeyResponse

```TypeScript
processMediaKeyResponse(assetId: string, response: Uint8Array): Promise<void>
```

在线DRM资源投播时，处理许可证响应。结果通过Promise异步回调方式返回。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-processMediaKeyResponse(assetId: string, response: Uint8Array): Promise<void>--><!--Device-AVCastController-processMediaKeyResponse(assetId: string, response: Uint8Array): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetId | string | 是 | 媒体ID。 |
| response | Uint8Array | 是 | 许可证响应。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，当处理许可证响应成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

销毁当前controller，结果通过callback异步回调方式返回。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-AVCastController-release(callback: AsyncCallback<void>): void--><!--Device-AVCastController-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当命令执行成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## release

```TypeScript
release(): Promise<void>
```

销毁当前controller。结果通过Promise异步回调方式返回。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-release(): Promise<void>--><!--Device-AVCastController-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，controller销毁成功，无结果返回，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## sendControlCommand

```TypeScript
sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback<void>): void
```

通过会话控制器发送命令到其对应的会话。结果通过callback异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-AVCastController-sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback<void>): void--><!--Device-AVCastController-sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 会话的相关命令和命令相关参数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

## sendControlCommand

```TypeScript
sendControlCommand(command: AVCastControlCommand): Promise<void>
```

通过控制器发送命令到其对应的会话。结果通过Promise异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-sendControlCommand(command: AVCastControlCommand): Promise<void>--><!--Device-AVCastController-sendControlCommand(command: AVCastControlCommand): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 会话的相关命令和命令相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当命令发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

## sendCustomData

```TypeScript
sendCustomData(data: Record<string, Object>): Promise<void>
```

发送私有数据到远端设备。使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-sendCustomData(data: Record<string, Object>): Promise<void>--><!--Device-AVCastController-sendCustomData(data: Record<string, Object>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Record&lt;string, Object&gt; | 是 | 应用程序填充的自定义数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

## start

```TypeScript
start(item: AVQueueItem, callback: AsyncCallback<void>): void
```

启动播放某个媒体资源。结果通过callback异步回调方式返回。 > **说明：** > > 在音视频投播场景下，当应用程序顺序调用 > [prepare]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和start接口，且 > assetId不变时，如果prepare已经传入有效的mediaUri或fdSrc，则start接口将复用prepare阶段的完整的AVMediaDescription对象信息。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-AVCastController-start(item: AVQueueItem, callback: AsyncCallback<void>): void--><!--Device-AVCastController-start(item: AVQueueItem, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 播放列表中单项的相关属性。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

## start

```TypeScript
start(item: AVQueueItem): Promise<void>
```

启动播放某个媒体资源。结果通过Promise异步回调方式返回。 > **说明：** > > 在音视频投播场景下，当应用程序顺序调用 > [prepare]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和start接口，且 > assetId不变时，如果prepare已经传入有效的mediaUri或fdSrc，则start接口将复用prepare阶段的完整的AVMediaDescription对象信息。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-start(item: AVQueueItem): Promise<void>--><!--Device-AVCastController-start(item: AVQueueItem): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 播放列表中单项的相关属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当命令发送成功，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

## update

```TypeScript
update(item: AVQueueItem): Promise<void>
```

更新投播媒体信息

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVCastController-update(item: AVQueueItem): Promise<void>--><!--Device-AVCastController-update(item: AVQueueItem): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 媒体信息item |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 通过promise回调成功 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

