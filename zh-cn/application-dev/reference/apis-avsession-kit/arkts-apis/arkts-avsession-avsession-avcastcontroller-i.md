# AVCastController

在投播建立后，调用[avSession.getAVCastController](arkts-avsession-avsession-getavcastcontroller-f-sys.md#getavcastcontroller-1)后，返回会话控制器实例。控制器可查看会话ID，并可完成对会话发送命令及事件，获取会话元数据，播放状态信息等操作。

> **说明：**  
>  
> - 本Interface首批接口从API version 10开始支持。

**起始版本：** 10

<!--Device-avSession-interface AVCastController--><!--Device-avSession-interface AVCastController-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

<a id="getavplaybackstate"></a>
## getAVPlaybackState

```TypeScript
getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void
```

获取当前的远端播放状态。结果通过callback异步回调方式返回。

**起始版本：** 10

<!--Device-AVCastController-getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void--><!--Device-AVCastController-getAVPlaybackState(callback: AsyncCallback<AVPlaybackState>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AVPlaybackState&gt; | 是 | 回调函数，返回远端播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="getavplaybackstate-1"></a>
## getAVPlaybackState

```TypeScript
getAVPlaybackState(): Promise<AVPlaybackState>
```

获取当前的远端播放状态。结果通过Promise异步回调方式返回。

**起始版本：** 10

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

<a id="getcurrentitem"></a>
## getCurrentItem

```TypeScript
getCurrentItem(callback: AsyncCallback<AVQueueItem>): void
```

获取当前投播的资源信息。结果通过callback异步回调方式返回。

**起始版本：** 10

<!--Device-AVCastController-getCurrentItem(callback: AsyncCallback<AVQueueItem>): void--><!--Device-AVCastController-getCurrentItem(callback: AsyncCallback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;AVQueueItem&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="getcurrentitem-1"></a>
## getCurrentItem

```TypeScript
getCurrentItem(): Promise<AVQueueItem>
```

获取当前投播的资源信息。结果通过Promise异步回调方式返回。

**起始版本：** 10

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

<a id="getrecommendedresolutionlevel"></a>
## getRecommendedResolutionLevel

```TypeScript
getRecommendedResolutionLevel(decoderType: DecoderType): Promise<ResolutionLevel>
```

通过传递解码方式，获取推荐的分辨率。使用Promise异步回调。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-getRecommendedResolutionLevel(decoderType: DecoderType): Promise<ResolutionLevel>--><!--Device-AVCastController-getRecommendedResolutionLevel(decoderType: DecoderType): Promise<ResolutionLevel>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| decoderType | [DecoderType](arkts-avsession-avsession-decodertype-e.md) | 是 | 设备所支持的解码格式。<br>设备所支持的解码格式包括：<br>'OH_AVCODEC_MIMETYPE_VIDEO_AVC'：VIDEO AVC，<br>'OH_AVCODEC_MIMETYPE_VIDEO_HEVC'：VIDEO HEVC，<br>'OH_AVCODEC_MIMETYPE_AUDIO_VIVID'：AUDIO AV3A。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResolutionLevel&gt; | Promise对象。返回远端设备推荐的分辨率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="getsupporteddecoders"></a>
## getSupportedDecoders

```TypeScript
getSupportedDecoders(): Promise<Array<DecoderType>>
```

获取当前远端设备的解码方式。使用Promise异步回调。

**起始版本：** 19

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

<a id="getsupportedhdrcapabilities"></a>
## getSupportedHdrCapabilities

```TypeScript
getSupportedHdrCapabilities(): Promise<Array<hdrCapability.HDRFormat>>
```

获取当前的远端设备所支持的HDR能力。使用Promise异步回调。

**起始版本：** 19

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

<a id="getsupportedplayspeeds"></a>
## getSupportedPlaySpeeds

```TypeScript
getSupportedPlaySpeeds(): Promise<Array<number>>
```

获取当前的远端设备所支持倍速播放列表，仅支持使用cast+协议连接的设备。使用Promise异步回调。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-getSupportedPlaySpeeds(): Promise<Array<double>>--><!--Device-AVCastController-getSupportedPlaySpeeds(): Promise<Array<double>>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise对象。返回远端设备所支持的倍速播放列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="getvalidcommands"></a>
## getValidCommands

```TypeScript
getValidCommands(callback: AsyncCallback<Array<AVCastControlCommandType>>): void
```

获取当前支持的命令。结果通过callback异步回调方式返回。

**起始版本：** 11

<!--Device-AVCastController-getValidCommands(callback: AsyncCallback<Array<AVCastControlCommandType>>): void--><!--Device-AVCastController-getValidCommands(callback: AsyncCallback<Array<AVCastControlCommandType>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;AVCastControlCommandType&gt;&gt; | 是 | 回调函数。返回当前支持的命令。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

<a id="getvalidcommands-1"></a>
## getValidCommands

```TypeScript
getValidCommands(): Promise<Array<AVCastControlCommandType>>
```

获取当前支持的命令。结果通过Promise异步回调方式返回。

**起始版本：** 11

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

<a id="off"></a>
## off('playbackStateChange')

```TypeScript
off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void
```

取消播放状态变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void--><!--Device-AVCastController-off(type: 'playbackStateChange', callback?: (state: AVPlaybackState) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | 是 |  |
| callback | (state: AVPlaybackState) =&gt; void | 否 | 回调函数，参数state是变化后的播放状态。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="off-1"></a>
## off

```TypeScript
off(type: 'mediaItemChange'): void
```

取消设置投播当前播放媒体内容事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'mediaItemChange'): void--><!--Device-AVCastController-off(type: 'mediaItemChange'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mediaItemChange' | 是 | 取消对应的监听事件，支持事件`'mediaItemChange'`。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="off-2"></a>
## off

```TypeScript
off(type: 'playNext'): void
```

取消设置播放下一首资源事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'playNext'): void--><!--Device-AVCastController-off(type: 'playNext'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playNext' | 是 | 取消对应的监听事件，支持事件`'playNext'`。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="off-3"></a>
## off

```TypeScript
off(type: 'playPrevious'): void
```

取消设置播放上一首资源事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'playPrevious'): void--><!--Device-AVCastController-off(type: 'playPrevious'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playPrevious' | 是 | 取消对应的监听事件，支持事件`'playPrevious'`。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="off-4"></a>
## off('requestPlay')

```TypeScript
off(type: 'requestPlay', callback?: Callback<AVQueueItem>): void
```

取消设置请求播放事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

<!--Device-AVCastController-off(type: 'requestPlay', callback?: Callback<AVQueueItem>): void--><!--Device-AVCastController-off(type: 'requestPlay', callback?: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'requestPlay' | 是 | 取消对应的监听事件，支持事件`'requestPlay'`。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AVQueueItem&gt; | 否 | 回调函数，参数AVQueueItem是当前正在播放的媒体内容。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="off-5"></a>
## off('endOfStream')

```TypeScript
off(type: 'endOfStream', callback?: Callback<void>): void
```

取消设置播放结束事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

<!--Device-AVCastController-off(type: 'endOfStream', callback?: Callback<void>): void--><!--Device-AVCastController-off(type: 'endOfStream', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 取消对应的监听事件，支持事件`'endOfStream'`。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="off-6"></a>
## off

```TypeScript
off(type: 'seekDone'): void
```

取消设置seek结束事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'seekDone'): void--><!--Device-AVCastController-off(type: 'seekDone'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'seekDone' | 是 | 取消对应的监听事件，支持事件`'seekDone'`。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="off-7"></a>
## off('validCommandChange')

```TypeScript
off(type: 'validCommandChange', callback?: Callback<Array<AVCastControlCommandType>>)
```

取消会话有效命令变化事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 11

<!--Device-AVCastController-off(type: 'validCommandChange', callback?: Callback<Array<AVCastControlCommandType>>)--><!--Device-AVCastController-off(type: 'validCommandChange', callback?: Callback<Array<AVCastControlCommandType>>)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'validCommandChange' | 是 | 取消对应的监听事件，支持事件`'validCommandChange'`。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;AVCastControlCommandType&gt;&gt; | 否 | 回调函数。参数commands是有效命令的集合。<br>该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

<a id="off-8"></a>
## off

```TypeScript
off(type: 'videoSizeChange'): void
```

取消视频尺寸事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 12

<!--Device-AVCastController-off(type: 'videoSizeChange'): void--><!--Device-AVCastController-off(type: 'videoSizeChange'): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | 是 | 事件回调类型，支持事件`'videoSizeChange'`：当检测到会话的合法命令发生改变时，触发该事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

**示例：**

```TypeScript
avCastController.off('videoSizeChange');

```

<a id="off-9"></a>
## off

```TypeScript
off(type: 'error'): void
```

取消播放的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 10

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

<a id="off-10"></a>
## off('castControlGenericError')

```TypeScript
off(type: 'castControlGenericError', callback?: ErrorCallback): void
```

取消投播通用的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlGenericError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlGenericError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlGenericError' | 是 | 取消对应的监听事件，支持的事件是'castControlGenericError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

<a id="off-11"></a>
## off('castControlIoError')

```TypeScript
off(type: 'castControlIoError', callback?: ErrorCallback): void
```

取消投播输入/输出的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlIoError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlIoError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlIoError' | 是 | 取消对应的监听事件，支持的事件是'castControlIoError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

<a id="off-12"></a>
## off('castControlParsingError')

```TypeScript
off(type: 'castControlParsingError', callback?: ErrorCallback): void
```

取消投播解析的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlParsingError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlParsingError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlParsingError' | 是 | 取消对应的监听事件，支持的事件是'castControlParsingError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

<a id="off-13"></a>
## off('castControlDecodingError')

```TypeScript
off(type: 'castControlDecodingError', callback?: ErrorCallback): void
```

取消投播解码的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlDecodingError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlDecodingError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlDecodingError' | 是 | 取消对应的监听事件，支持的事件是'castControlDecodingError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

<a id="off-14"></a>
## off('castControlAudioRendererError')

```TypeScript
off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void
```

取消投播音频渲染器的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlAudioRendererError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlAudioRendererError' | 是 | 取消对应的监听事件，支持的事件是'castControlAudioRendererError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

<a id="off-15"></a>
## off('castControlDrmError')

```TypeScript
off(type: 'castControlDrmError', callback?: ErrorCallback): void
```

取消投播drm的错误事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'castControlDrmError', callback?: ErrorCallback): void--><!--Device-AVCastController-off(type: 'castControlDrmError', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlDrmError' | 是 | 取消对应的监听事件，支持的事件是'castControlDrmError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

<a id="off-16"></a>
## off('keyRequest')

```TypeScript
off(type: 'keyRequest', callback?: KeyRequestCallback): void
```

取消许可证请求事件监听。指定callback，可取消对应监听；未指定callback，取消所有事件监听。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'keyRequest', callback?: KeyRequestCallback): void--><!--Device-AVCastController-off(type: 'keyRequest', callback?: KeyRequestCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyRequest' | 是 | 取消对应的监听事件，支持的事件是`'keyRequest'`。 |
| callback | [KeyRequestCallback](arkts-avsession-avsession-keyrequestcallback-t.md) | 否 | 回调函数。当监听事件取消成功，err为undefined，否则返回错误对象。该参数为可选参数，若不填写该参数，则认为取消所有相关会话的事件监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="off-17"></a>
## off('customDataChange')

```TypeScript
off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void
```

取消对自定义数据的监听。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void--><!--Device-AVCastController-off(type: 'customDataChange', callback?: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'customDataChange' | 是 | 取消对应的监听事件，支持的事件是'customDataChange'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Record&lt;string, Object&gt;&gt; | 否 | 注册监听事件时的回调函数。该参数为可选参数，若不填写该参数，则认为取消会话所有与此事件相关的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on"></a>
## on('playbackStateChange')

```TypeScript
on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void
```

设置播放状态变化的监听事件。使用callback异步回调。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void--><!--Device-AVCastController-on(type: 'playbackStateChange', filter: Array<keyof AVPlaybackState> | 'all', callback: (state: AVPlaybackState) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playbackStateChange' | 是 |  |
| filter | Array&lt;keyof AVPlaybackState&gt; \| 'all' | 是 | 'all'表示关注播放状态所有字段变化；Array<keyof AVPlaybackState>表示关注Array中的字段变化。 |
| callback | (state: AVPlaybackState) =&gt; void | 是 | 回调函数，参数state是变化后的播放状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on-1"></a>
## on('mediaItemChange')

```TypeScript
on(type: 'mediaItemChange', callback: Callback<AVQueueItem>): void
```

设置投播当前播放媒体内容的监听事件。使用callback异步回调。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'mediaItemChange', callback: Callback<AVQueueItem>): void--><!--Device-AVCastController-on(type: 'mediaItemChange', callback: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'mediaItemChange' | 是 | 事件回调类型，支持事件`'mediaItemChange'`：当播放的媒体内容变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AVQueueItem&gt; | 是 | 回调函数，参数AVQueueItem是当前正在播放的媒体内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on-2"></a>
## on('playNext')

```TypeScript
on(type: 'playNext', callback: Callback<void>): void
```

设置播放下一首资源的监听事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'playNext', callback: Callback<void>): void--><!--Device-AVCastController-on(type: 'playNext', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playNext' | 是 | 事件回调类型，支持事件`'playNext'`：当播放下一首状态变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on-3"></a>
## on('playPrevious')

```TypeScript
on(type: 'playPrevious', callback: Callback<void>): void
```

设置播放上一首资源的监听事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'playPrevious', callback: Callback<void>): void--><!--Device-AVCastController-on(type: 'playPrevious', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'playPrevious' | 是 | 事件回调类型，支持事件`'playPrevious'`：当播放上一首状态变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on-4"></a>
## on('requestPlay')

```TypeScript
on(type: 'requestPlay', callback: Callback<AVQueueItem>): void
```

设置请求播放的监听事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

<!--Device-AVCastController-on(type: 'requestPlay', callback: Callback<AVQueueItem>): void--><!--Device-AVCastController-on(type: 'requestPlay', callback: Callback<AVQueueItem>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'requestPlay' | 是 | 事件回调类型，支持事件`'requestPlay'`：当请求播放状态变化时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AVQueueItem&gt; | 是 | 回调函数，参数AVQueueItem是当前正在播放的媒体内容。当监听事件注册成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on-5"></a>
## on('endOfStream')

```TypeScript
on(type: 'endOfStream', callback: Callback<void>): void
```

设置播放结束的监听事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

<!--Device-AVCastController-on(type: 'endOfStream', callback: Callback<void>): void--><!--Device-AVCastController-on(type: 'endOfStream', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'endOfStream' | 是 | 事件回调类型，支持事件`'endOfStream'`：当资源播放结束时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 回调函数。当监听事件注册成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on-6"></a>
## on('seekDone')

```TypeScript
on(type: 'seekDone', callback: Callback<number>): void
```

设置seek结束的监听事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'seekDone', callback: Callback<int>): void--><!--Device-AVCastController-on(type: 'seekDone', callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'seekDone' | 是 | 事件回调类型，支持事件`'seekDone'`：当seek结束时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;number&gt; | 是 | 回调函数，返回seek后播放的位置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on-7"></a>
## on('validCommandChange')

```TypeScript
on(type: 'validCommandChange', callback: Callback<Array<AVCastControlCommandType>>)
```

会话支持的有效命令变化监听事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 11

<!--Device-AVCastController-on(type: 'validCommandChange', callback: Callback<Array<AVCastControlCommandType>>)--><!--Device-AVCastController-on(type: 'validCommandChange', callback: Callback<Array<AVCastControlCommandType>>)-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'validCommandChange' | 是 | 事件回调类型，支持事件`'validCommandChange'`：当检测到会话的合法命令发生改变时，触发该事件。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;AVCastControlCommandType&gt;&gt; | 是 | 回调函数。参数commands是有效命令的集合。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |
| [6600103](../errorcode-avsession.md#6600103-会话控制器不存在) | The session controller does not exist. |

<a id="on-8"></a>
## on('videoSizeChange')

```TypeScript
on(type: 'videoSizeChange', callback: (width: number, height: number) => void): void
```

媒体控制器监听视频尺寸变化变化的事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 12

<!--Device-AVCastController-on(type: 'videoSizeChange', callback: (width: int, height: int) => void): void--><!--Device-AVCastController-on(type: 'videoSizeChange', callback: (width: int, height: int) => void): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'videoSizeChange' | 是 | 事件回调类型，支持事件`'videoSizeChange'`：当检测到会话的合法命令发生改变时，触发该事件。 |
| callback | (width: number, height: number) =&gt; void | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

**示例：**

```TypeScript
avCastController.on('videoSizeChange', (width: number, height: number) => {
  console.info(`width ：${width} `);
  console.info(`height：${height} `);
});

```

<a id="on-9"></a>
## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听远端播放器的错误事件，该事件仅用于错误提示，不需要用户停止播控动作。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'error', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 错误事件回调类型，支持的事件：'error'，用户操作和系统都会触发此事件。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 错误事件回调方法：远端播放过程中发生的错误，会提供错误码ID和错误信息。 |

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

<a id="on-10"></a>
## on('castControlGenericError')

```TypeScript
on(type: 'castControlGenericError', callback: ErrorCallback): void
```

监听投播通用错误事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlGenericError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlGenericError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlGenericError' | 是 | 错误事件回调类型，支持的事件：'castControlGenericError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 投播通用错误事件回调方法。 |

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

<a id="on-11"></a>
## on('castControlIoError')

```TypeScript
on(type: 'castControlIoError', callback: ErrorCallback): void
```

监听投播输入/输出的错误事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlIoError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlIoError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlIoError' | 是 | 错误事件回调类型，支持的事件：'castControlIoError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 投播输入/输出的错误事件回调方法。 |

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

<a id="on-12"></a>
## on('castControlParsingError')

```TypeScript
on(type: 'castControlParsingError', callback: ErrorCallback): void
```

监听投播解析的错误事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlParsingError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlParsingError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlParsingError' | 是 | 错误事件回调类型，支持的事件：'castControlParsingError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 投播解析的错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6613000](../errorcode-avsession.md#6613000-未知解析错误) | Unspecified error related to content parsing. |
| [6613001](../errorcode-avsession.md#6613001-非法类型) | Parsing error associated with media container format bit streams. |
| [6613002](../errorcode-avsession.md#6613002-相关媒体清单的解析错误) | Parsing error associated with the media manifest. |
| [6613003](../errorcode-avsession.md#6613003-不支持该媒体格式) | An error occurs when attempting to extract a file with an unsupported media container format or an unsupported media container feature. |
| [6613004](../errorcode-avsession.md#6613004-媒体清单中不支持此功能) | Unsupported feature in the media manifest. |

<a id="on-13"></a>
## on('castControlDecodingError')

```TypeScript
on(type: 'castControlDecodingError', callback: ErrorCallback): void
```

监听投播解码的错误事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlDecodingError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlDecodingError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlDecodingError' | 是 | 错误事件回调类型，支持的事件：'castControlDecodingError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 投播解码的错误事件回调方法。 |

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

<a id="on-14"></a>
## on('castControlAudioRendererError')

```TypeScript
on(type: 'castControlAudioRendererError', callback: ErrorCallback): void
```

监听投播音频渲染器的错误事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlAudioRendererError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlAudioRendererError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlAudioRendererError' | 是 | 错误事件回调类型，支持的事件：'castControlAudioRendererError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 投播音频渲染器的错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter check failed. 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [6615000](../errorcode-avsession.md#6615000-音频渲染器相关的未知错误) | Unspecified errors related to the audio renderer. |
| [6615001](../errorcode-avsession.md#6615001-音频渲染器初始化异常) | Initializing the audio renderer failed. |
| [6615002](../errorcode-avsession.md#6615002-音频渲染器写数据异常) | The audio renderer fails to write data. |

<a id="on-15"></a>
## on('castControlDrmError')

```TypeScript
on(type: 'castControlDrmError', callback: ErrorCallback): void
```

监听投播drm的错误事件。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 13

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'castControlDrmError', callback: ErrorCallback): void--><!--Device-AVCastController-on(type: 'castControlDrmError', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'castControlDrmError' | 是 | 错误事件回调类型，支持的事件：'castControlDrmError'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 投播drm的错误事件回调方法。 |

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
| [6616100](../errorcode-avsession.md#6616100-drm进程秘钥响应错误) | An error occurs when the DRM processes the key response. |

<a id="on-16"></a>
## on('keyRequest')

```TypeScript
on(type: 'keyRequest', callback: KeyRequestCallback): void
```

在线DRM资源投播时，设置许可证请求的事件监听。

每个指令支持注册多个回调，如果需要只执行最新监听，需要先注销旧的监听，否则新旧监听都会触发回调。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'keyRequest', callback: KeyRequestCallback): void--><!--Device-AVCastController-on(type: 'keyRequest', callback: KeyRequestCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyRequest' | 是 | 事件回调类型，支持事件`'keyRequest'`：当DRM资源播放需要许可证时，触发该事件。 |
| callback | [KeyRequestCallback](arkts-avsession-avsession-keyrequestcallback-t.md) | 是 | 回调函数，媒体资源及许可证请求数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="on-17"></a>
## on('customDataChange')

```TypeScript
on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void
```

注册从远端设备发送的自定义数据的监听器。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void--><!--Device-AVCastController-on(type: 'customDataChange', callback: Callback<Record<string, Object>>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'customDataChange' | 是 | 事件回调类型，支持'customDataChange'事件。媒体提供方发送自定义数据时触发。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Record&lt;string, Object&gt;&gt; | 是 | 回调函数，用于接收自定义数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |

<a id="prepare"></a>
## prepare

```TypeScript
prepare(item: AVQueueItem, callback: AsyncCallback<void>): void
```

准备播放媒体资源，即进行播放资源的加载和缓冲。结果通过callback异步回调方式返回。

**起始版本：** 10

<!--Device-AVCastController-prepare(item: AVQueueItem, callback: AsyncCallback<void>): void--><!--Device-AVCastController-prepare(item: AVQueueItem, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | 是 | 播放列表中单项的相关属性。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

<a id="prepare-1"></a>
## prepare

```TypeScript
prepare(item: AVQueueItem): Promise<void>
```

准备播放媒体资源，即进行播放资源的加载和缓冲。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-prepare(item: AVQueueItem): Promise<void>--><!--Device-AVCastController-prepare(item: AVQueueItem): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | 是 | 播放列表中单项的相关属性。 |

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

<a id="processmediakeyresponse"></a>
## processMediaKeyResponse

```TypeScript
processMediaKeyResponse(assetId: string, response: Uint8Array): Promise<void>
```

在线DRM资源投播时，处理许可证响应。结果通过Promise异步回调方式返回。

**起始版本：** 12

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

<a id="release"></a>
## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

销毁当前controller，结果通过callback异步回调方式返回。

**起始版本：** 11

<!--Device-AVCastController-release(callback: AsyncCallback<void>): void--><!--Device-AVCastController-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当命令执行成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception. |

<a id="release-1"></a>
## release

```TypeScript
release(): Promise<void>
```

销毁当前controller。结果通过Promise异步回调方式返回。

**起始版本：** 11

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

<a id="sendcontrolcommand"></a>
## sendControlCommand

```TypeScript
sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback<void>): void
```

通过会话控制器发送命令到其对应的会话。结果通过callback异步回调方式返回。

**起始版本：** 10

<!--Device-AVCastController-sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback<void>): void--><!--Device-AVCastController-sendControlCommand(command: AVCastControlCommand, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [AVCastControlCommand](arkts-avsession-avsession-avcastcontrolcommand-i.md) | 是 | 会话的相关命令和命令相关参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600105](../errorcode-avsession.md#6600105-无效会话命令) | Invalid session command |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

<a id="sendcontrolcommand-1"></a>
## sendControlCommand

```TypeScript
sendControlCommand(command: AVCastControlCommand): Promise<void>
```

通过控制器发送命令到其对应的会话。结果通过Promise异步回调方式返回。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-sendControlCommand(command: AVCastControlCommand): Promise<void>--><!--Device-AVCastController-sendControlCommand(command: AVCastControlCommand): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| command | [AVCastControlCommand](arkts-avsession-avsession-avcastcontrolcommand-i.md) | 是 | 会话的相关命令和命令相关参数。 |

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

<a id="sendcustomdata"></a>
## sendCustomData

```TypeScript
sendCustomData(data: Record<string, Object>): Promise<void>
```

发送私有数据到远端设备。使用Promise异步回调。

**起始版本：** 20

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

<a id="start"></a>
## start

```TypeScript
start(item: AVQueueItem, callback: AsyncCallback<void>): void
```

启动播放某个媒体资源。结果通过callback异步回调方式返回。

> **说明：**  
>  
> 在音视频投播场景下，当应用程序顺序调用  
> [prepare](arkts-avsession-avsession-avcastcontroller-i.md#prepare-1)和start接口，且  
> assetId不变时，如果prepare已经传入有效的mediaUri或fdSrc，则start接口将复用prepare阶段的完整的AVMediaDescription对象信息。

**起始版本：** 10

<!--Device-AVCastController-start(item: AVQueueItem, callback: AsyncCallback<void>): void--><!--Device-AVCastController-start(item: AVQueueItem, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | 是 | 播放列表中单项的相关属性。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

<a id="start-1"></a>
## start

```TypeScript
start(item: AVQueueItem): Promise<void>
```

启动播放某个媒体资源。结果通过Promise异步回调方式返回。

> **说明：**  
>  
> 在音视频投播场景下，当应用程序顺序调用  
> [prepare](arkts-avsession-avsession-avcastcontroller-i.md#prepare-1)和start接口，且  
> assetId不变时，如果prepare已经传入有效的mediaUri或fdSrc，则start接口将复用prepare阶段的完整的AVMediaDescription对象信息。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVCastController-start(item: AVQueueItem): Promise<void>--><!--Device-AVCastController-start(item: AVQueueItem): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | 是 | 播放列表中单项的相关属性。 |

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

<a id="update"></a>
## update

```TypeScript
update(item: AVQueueItem): Promise<void>
```

更新投播媒体信息

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVCastController-update(item: AVQueueItem): Promise<void>--><!--Device-AVCastController-update(item: AVQueueItem): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | [AVQueueItem](arkts-avsession-avsession-avqueueitem-i.md) | 是 | 媒体信息item |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 通过promise回调成功 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600109](../errorcode-avsession.md#6600109-远端会话不存在) | The remote connection is not established |

