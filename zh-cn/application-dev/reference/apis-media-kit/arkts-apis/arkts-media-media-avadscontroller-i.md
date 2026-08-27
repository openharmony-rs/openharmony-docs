# AVAdsController

广告内容控制接口

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## addAdsMediaSource

```TypeScript
addAdsMediaSource(src: MediaSource, start: number): Promise<string>
```

向广告控制器添加广告媒体源，指定广告在主媒体资源播放进度中的插入位置。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [MediaSource](arkts-media-media-mediasource-i.md) | 是 | 要插入到主内容中播放的媒体源。 |
| start | number | 是 | 广告媒体源在主媒体资源播放进度中的插入位置，从主媒体资源开始播放时计算。 Unit: 单位为毫秒（ms）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象，返回添加到广告控制器中的媒体源ID，removeAdsMediaSource接口可用该ID移除对应的广告源。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | Insert a media asset whose start value exceeds the value of the main content. |

## disableAllAdsMediaSource

```TypeScript
disableAllAdsMediaSource(): void
```

禁用当前会话中剩余的广告内容播放，后续尚未播放的广告将不再播放。例如，当用户购买了免广告权益或通过内容审核机制判定不应展示广告时，可调用此接口禁用后续所有广告。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## offAdsEventListenerLoadingError

```TypeScript
offAdsEventListenerLoadingError(callback?: OnAdsEventLoadingErrorHandle): void
```

取消注册广告内容加载失败时的事件处理函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAdsEventLoadingErrorHandle](arkts-media-media-onadseventloadingerrorhandle-t.md) | 否 | 广告内容加载失败的处理函数。 传入指定回调时，仅取消订阅该回调；不传入该参数时，默认取消订阅该事件的所有回调函数。 |

## offAdsListenerAdsCompleted

```TypeScript
offAdsListenerAdsCompleted(callback?: Callback<string>): void
```

取消注册广告内容播放完成时触发的事件处理函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 否 | 广告播放完成的处理函数。 传入指定回调时，仅取消订阅该回调；不传入该参数时默认取消订阅该事件的所有回调函数。 |

## offAdsListenerAdsSkipped

```TypeScript
offAdsListenerAdsSkipped(callback?: Callback<string>): void
```

取消注册广告被跳过时触发的事件处理函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 否 | 广告跳过的处理函数。 传入指定回调时，仅取消订阅该回调；不传入该参数时，默认取消订阅该事件的所有回调函数。 |

## offAdsListenerAdsStarted

```TypeScript
offAdsListenerAdsStarted(callback?: OnAdsEventAdsStartedHandle): void
```

取消注册新广告内容播放时触发的事件处理函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAdsEventAdsStartedHandle](arkts-media-media-onadseventadsstartedhandle-t.md) | 否 | 广告内容开始播放时的处理函数。 常用于从主内容播放界面切换到广告播放界面的场景。 传入指定回调时，仅取消订阅该回调；不传入该参数时，默认取消订阅该事件的所有回调函数。 |

## onAdsEventListenerLoadingError

```TypeScript
onAdsEventListenerLoadingError(callback: OnAdsEventLoadingErrorHandle): void
```

注册广告内容加载失败时的事件处理函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAdsEventLoadingErrorHandle](arkts-media-media-onadseventloadingerrorhandle-t.md) | 是 | 广告内容加载失败的处理函数。 由使用方实现。 第一个参数用于传递广告ID，第二个参数用于传递失败原因。 |

## onAdsListenerAdsCompleted

```TypeScript
onAdsListenerAdsCompleted(callback: Callback<string>): void
```

注册广告内容播放完成时触发的事件处理函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 广告播放完成的处理函数。常用于恢复主内容播放。参数为播放完成的广告ID。 |

## onAdsListenerAdsSkipped

```TypeScript
onAdsListenerAdsSkipped(callback: Callback<string>): void
```

注册广告被跳过时触发的事件处理函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 广告跳过的处理函数。常用于恢复主内容播放。参数为被跳过的广告ID。 |

## onAdsListenerAdsStarted

```TypeScript
onAdsListenerAdsStarted(callback: OnAdsEventAdsStartedHandle): void
```

注册新广告内容播放时触发的事件处理函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnAdsEventAdsStartedHandle](arkts-media-media-onadseventadsstartedhandle-t.md) | 是 | 广告内容开始播放时的处理函数。 常用于从主内容播放界面切换到广告播放界面的场景。 第一个参数表示正在播放的广告ID，第二个参数表示广告的时长，单位为毫秒（ms）。 |

## release

```TypeScript
release(): void
```

释放AVAdsController对象。释放后已注册的回调将不再触发，应在AVPlayer释放前调用此方法释放广告控制器。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**示例**

```TypeScript
audioPlayer.release();
audioPlayer = undefined;
```

```TypeScript
audioRecorder.on('release', () => {    // 设置'release'事件回调。
  console.info('audio recorder release called');
});
audioRecorder.release();
audioRecorder = undefined;
```

## removeAdsMediaSource

```TypeScript
removeAdsMediaSource(id: string): void
```

移除广告控制器中指定的广告媒体源。如果该广告正在播放，则等广告播放完后再移除。例如，当广告内容失效或用户购买免广告权益后，可调用此接口移除已添加的广告。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 广告媒体源ID，由addAdsMediaSource接口返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | If the specified ID is not in the AdsController. |

## skipCurrentAdsMediaSource

```TypeScript
skipCurrentAdsMediaSource(): void
```

跳过当前正在播放的广告内容。跳过后将立即恢复主内容的播放，并触发onAdsListenerAdsSkipped的回调。例如，当用户点击播放器上的“跳过广告”按钮时，可调用此接口跳过当前广告并继续播放主内容。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer
