# Video属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** VideoAttribute extends [CommonMethod<VideoAttribute>](CommonMethod<VideoAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class VideoAttribute extends CommonMethod<VideoAttribute>--><!--Device-unnamed-declare class VideoAttribute extends CommonMethod<VideoAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="analyzerconfig"></a>
## analyzerConfig

```TypeScript
analyzerConfig(config: ImageAnalyzerConfig)
```

设置AI分析识别类型，包括主体识别、文字识别和对象查找等功能，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-analyzerConfig(config: ImageAnalyzerConfig): VideoAttribute--><!--Device-VideoAttribute-analyzerConfig(config: ImageAnalyzerConfig): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ImageAnalyzerConfig](../arkts-apis/arkts-arkui-imageanalyzerconfig-i.md) | 是 | 设置AI分析识别类型。 |

<a id="autoplay"></a>
## autoPlay

```TypeScript
autoPlay(value: boolean)
```

设置视频是否自动播放，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-autoPlay(value: boolean): VideoAttribute--><!--Device-VideoAttribute-autoPlay(value: boolean): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否自动播放。<br/>true：开启自动播放；false：关闭自动播放。<br/>默认值：false |

<a id="controls"></a>
## controls

```TypeScript
controls(value: boolean)
```

设置控制视频播放的控制栏是否显示，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-controls(value: boolean): VideoAttribute--><!--Device-VideoAttribute-controls(value: boolean): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 控制视频播放的控制栏是否显示。<br/>true：控制栏显示；false：控制栏不显示。<br/>默认值：true |

<a id="enableanalyzer"></a>
## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

使能后，视频播放暂停时自动进入分析状态，开始分析当前画面帧，视频继续播放后自动退出分析状态。

不能和[overlay](arkts-arkui-commonmethod-c.md#overlay-1)属性同时使用，两者同时设置时[overlay](arkts-arkui-commonmethod-c.md#overlay-1)中[CustomBuilder](docroot://reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8)属性将失效。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-enableAnalyzer(enable: boolean): VideoAttribute--><!--Device-VideoAttribute-enableAnalyzer(enable: boolean): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否启用AI分析功能。<br/>true：开启AI分析功能；false：关闭AI分析功能。<br/>默认值：false |

<a id="enableshortcutkey"></a>
## enableShortcutKey

```TypeScript
enableShortcutKey(enabled: boolean)
```

设置组件支持快捷键响应，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

目前支持在组件获焦后响应空格键播放/暂停、上下方向键调整视频音量、左右方向键快进/快退。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-enableShortcutKey(enabled: boolean): VideoAttribute--><!--Device-VideoAttribute-enableShortcutKey(enabled: boolean): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否启用快捷键响应。<br/>true：开启快捷键响应；false：关闭快捷键响应。<br/>默认值：false<br/>**说明：**<br/>enabled设置为false且Video组件的控制栏显示时，仍然可以通过左右方向键控制进度条快进或快退。 |

<a id="loop"></a>
## loop

```TypeScript
loop(value: boolean)
```

设置是否单个视频循环播放，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 6

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-loop(value: boolean): VideoAttribute--><!--Device-VideoAttribute-loop(value: boolean): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否单个视频循环播放。<br/>true：开启循环播放；false：关闭循环播放。<br/>默认值：false |

<a id="muted"></a>
## muted

```TypeScript
muted(value: boolean)
```

设置视频是否静音，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-muted(value: boolean): VideoAttribute--><!--Device-VideoAttribute-muted(value: boolean): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 视频是否静音。<br/>true：开启静音；false：关闭静音。<br/>默认值：false |

<a id="objectfit"></a>
## objectFit

```TypeScript
objectFit(value: ImageFit)
```

设置视频的填充模式，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-objectFit(value: ImageFit): VideoAttribute--><!--Device-VideoAttribute-objectFit(value: ImageFit): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md) | 是 | 视频填充模式。<br/>默认值：Cover<br/>约束：不支持ImageFit类型中的枚举值MATRIX，若设置，则作用效果与Cover一致。<br/>异常值：若设置异常值undefined、null，或不在[ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md)枚举范围内的值，作用效果均与Cover一致。 |

<a id="onerror"></a>
## onError

```TypeScript
onError(event: VoidCallback | import('../api/@ohos.base').ErrorCallback)
```

播放失败时触发该事件，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onError(event: VoidCallback | import('../api/@ohos.base').ErrorCallback): VideoAttribute--><!--Device-VideoAttribute-onError(event: VoidCallback | import('../api/@ohos.base').ErrorCallback): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) \| import('../api/@ohos.base').ErrorCallback | 是 | 视频播放失败时的回调函数。其中[ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md)类型入参的回调函数用于接收异常信息，回调返回的错误码详细介绍请参见[Video组件错误码](docroot://reference/apis-arkui/errorcode-video.md)和[Media错误码](docroot://reference/apis-media-kit/errorcode-media.md)。<br>**起始版本：** 20 |

<a id="onfinish"></a>
## onFinish

```TypeScript
onFinish(event: VoidCallback)
```

播放结束时触发该事件，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onFinish(event: VoidCallback): VideoAttribute--><!--Device-VideoAttribute-onFinish(event: VoidCallback): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 视频播放结束的回调函数。<br>**起始版本：** 18 |

<a id="onfullscreenchange"></a>
## onFullscreenChange

```TypeScript
onFullscreenChange(callback: Callback<FullscreenInfo>)
```

在全屏播放与非全屏播放状态之间切换时触发该事件，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onFullscreenChange(callback: Callback<FullscreenInfo>): VideoAttribute--><!--Device-VideoAttribute-onFullscreenChange(callback: Callback<FullscreenInfo>): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;FullscreenInfo&gt; | 是 | 在全屏播放与非全屏播放状态之间切换时的回调函数。<br>**起始版本：** 18 |

<a id="onpause"></a>
## onPause

```TypeScript
onPause(event: VoidCallback)
```

暂停时触发该事件，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onPause(event: VoidCallback): VideoAttribute--><!--Device-VideoAttribute-onPause(event: VoidCallback): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 视频暂停的回调函数。<br>**起始版本：** 18 |

<a id="onprepared"></a>
## onPrepared

```TypeScript
onPrepared(callback: Callback<PreparedInfo>)
```

视频准备完成时触发该事件，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onPrepared(callback: Callback<PreparedInfo>): VideoAttribute--><!--Device-VideoAttribute-onPrepared(callback: Callback<PreparedInfo>): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;PreparedInfo&gt; | 是 | 视频准备完成时的回调函数。<br>**起始版本：** 18 |

<a id="onseeked"></a>
## onSeeked

```TypeScript
onSeeked(callback: Callback<PlaybackInfo>)
```

操作进度条完成后，上报播放时间信息，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onSeeked(callback: Callback<PlaybackInfo>): VideoAttribute--><!--Device-VideoAttribute-onSeeked(callback: Callback<PlaybackInfo>): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;PlaybackInfo&gt; | 是 | 操作进度条完成后的回调函数。<br>**起始版本：** 18 |

<a id="onseeking"></a>
## onSeeking

```TypeScript
onSeeking(callback: Callback<PlaybackInfo>)
```

操作进度条过程时上报时间信息，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onSeeking(callback: Callback<PlaybackInfo>): VideoAttribute--><!--Device-VideoAttribute-onSeeking(callback: Callback<PlaybackInfo>): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;PlaybackInfo&gt; | 是 | 操作进度条过程时的回调函数。<br>**起始版本：** 18 |

<a id="onstart"></a>
## onStart

```TypeScript
onStart(event: VoidCallback)
```

播放时触发该事件，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onStart(event: VoidCallback): VideoAttribute--><!--Device-VideoAttribute-onStart(event: VoidCallback): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | 视频播放的回调函数。<br>**起始版本：** 18 |

<a id="onstop"></a>
## onStop

```TypeScript
onStop(event: Callback<void>)
```

播放停止时触发该事件(当stop()方法被调用后触发)，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onStop(event: Callback<void>): VideoAttribute--><!--Device-VideoAttribute-onStop(event: Callback<void>): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 视频播放停止时的回调函数。 |

<a id="onupdate"></a>
## onUpdate

```TypeScript
onUpdate(callback: Callback<PlaybackInfo>)
```

播放进度变化时触发该事件，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoAttribute-onUpdate(callback: Callback<PlaybackInfo>): VideoAttribute--><!--Device-VideoAttribute-onUpdate(callback: Callback<PlaybackInfo>): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;PlaybackInfo&gt; | 是 | 播放进度变化时的回调函数。<br>**起始版本：** 18 |

