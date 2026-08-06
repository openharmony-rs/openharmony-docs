# VideoAttribute

用于播放视频文件并控制其播放状态的组件。

**继承/实现关系：** VideoAttribute extends [CommonMethod](../../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface VideoAttribute extends CommonMethod--><!--Device-unnamed-export declare interface VideoAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## analyzerConfig

```TypeScript
default analyzerConfig(config: ImageAnalyzerConfig | undefined): this
```

设置AI分析识别类型，包括主体识别、文字识别和对象查找等功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default analyzerConfig(config: ImageAnalyzerConfig | undefined): this--><!--Device-VideoAttribute-default analyzerConfig(config: ImageAnalyzerConfig | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 设置AI分析识别类型。取值为undefined时，与不设置表现一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## attributeModifier

```TypeScript
default attributeModifier(modifier: AttributeModifier<VideoAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

设置组件的动态属性。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default attributeModifier(modifier: AttributeModifier<VideoAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-VideoAttribute-default attributeModifier(modifier: AttributeModifier<VideoAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| AttributeModifier&lt;CommonMethod&gt; \| undefined | 是 | 动态设置Video组件的属性。取值为undefined时，按当前组件的属性方法默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## autoPlay

```TypeScript
default autoPlay(value: boolean | undefined): this
```

设置视频是否自动播放。 true：开启自动播放；false：关闭自动播放。 默认值：false，取值为undefined时，按默认值处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default autoPlay(value: boolean | undefined): this--><!--Device-VideoAttribute-default autoPlay(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 是否自动播放。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## controls

```TypeScript
default controls(value: boolean | undefined): this
```

设置控制视频播放的控制栏是否显示。 true：控制栏显示；false：控制栏不显示。 默认值：true，取值为undefined时，按默认值处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default controls(value: boolean | undefined): this--><!--Device-VideoAttribute-default controls(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 控制视频播放的控制栏是否显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableAnalyzer

```TypeScript
default enableAnalyzer(enable: boolean | undefined): this
```

设置组件支持AI分析，当前支持主体识别、文字识别和对象查找等功能。 使能后，视频播放暂停时自动进入分析状态，开始分析当前画面帧， 视频继续播放后自动退出分析状态。 不能和overlay属性同时使用，两者同时设置时overlay中CustomBuilder属性将失效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default enableAnalyzer(enable: boolean | undefined): this--><!--Device-VideoAttribute-default enableAnalyzer(enable: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 | 是否启用AI分析功能。true：开启AI分析功能；false：关闭AI分析功能。默认值：false，取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableShortcutKey

```TypeScript
default enableShortcutKey(enabled: boolean | undefined): this
```

设置组件支持快捷键响应。 目前支持在组件获焦后响应空格键播放/暂停、上下方向键调整视频音量、 左右方向键快进/快退。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default enableShortcutKey(enabled: boolean | undefined): this--><!--Device-VideoAttribute-default enableShortcutKey(enabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | 是否启用快捷键响应。true：开启快捷键响应；false：关闭快捷键响应。默认值：false，取值为undefined时，按默认值处理。enabled设置为false且Video组件的控制栏显示时，仍然可以通过左右方向键控制进度条快进或快退。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## loop

```TypeScript
default loop(value: boolean | undefined): this
```

设置是否单个视频循环播放。 true：开启循环播放；false：关闭循环播放。 默认值：false，取值为undefined时，按默认值处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default loop(value: boolean | undefined): this--><!--Device-VideoAttribute-default loop(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 是否单个视频循环播放。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## muted

```TypeScript
default muted(value: boolean | undefined): this
```

设置视频是否静音。 true：开启静音；false：关闭静音。 默认值：false，取值为undefined时，按默认值处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default muted(value: boolean | undefined): this--><!--Device-VideoAttribute-default muted(value: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean \| undefined | 是 | 视频是否静音。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## objectFit

```TypeScript
default objectFit(value: ImageFit | undefined): this
```

设置视频的填充模式。 默认值：Cover。 约束：不支持ImageFit类型中的枚举值MATRIX，若设置，则作用效果与Cover一致。 异常值：若设置异常值undefined、null，或不在ImageFit枚举范围内的值， 作用效果均与Cover一致。取值为undefined时，按默认值处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default objectFit(value: ImageFit | undefined): this--><!--Device-VideoAttribute-default objectFit(value: ImageFit | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 视频填充模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onError

```TypeScript
default onError(event: VoidCallback | ErrorCallback | undefined): this
```

播放失败时触发该事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onError(event: VoidCallback | ErrorCallback | undefined): this--><!--Device-VideoAttribute-default onError(event: VoidCallback | ErrorCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ErrorCallback \| undefined | 是 | 视频播放失败时的回调函数。其中ErrorCallback类型入参的回调函数用于接收异常信息，回调返回的错误码详细介绍请参见Video组件错误码和Media错误码。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onFinish

```TypeScript
default onFinish(event: VoidCallback | undefined): this
```

播放结束时触发该事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onFinish(event: VoidCallback | undefined): this--><!--Device-VideoAttribute-default onFinish(event: VoidCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 视频播放结束的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onFullscreenChange

```TypeScript
default onFullscreenChange(callback: Callback<FullscreenInfo> | undefined): this
```

在全屏播放与非全屏播放状态之间切换时触发该事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onFullscreenChange(callback: Callback<FullscreenInfo> | undefined): this--><!--Device-VideoAttribute-default onFullscreenChange(callback: Callback<FullscreenInfo> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | 在全屏播放与非全屏播放状态之间切换时的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onPause

```TypeScript
default onPause(event: VoidCallback | undefined): this
```

暂停时触发该事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onPause(event: VoidCallback | undefined): this--><!--Device-VideoAttribute-default onPause(event: VoidCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 视频暂停的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onPrepared

```TypeScript
default onPrepared(callback: Callback<PreparedInfo> | undefined): this
```

视频准备完成时触发该事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onPrepared(callback: Callback<PreparedInfo> | undefined): this--><!--Device-VideoAttribute-default onPrepared(callback: Callback<PreparedInfo> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | 视频准备完成时的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onSeeked

```TypeScript
default onSeeked(callback: Callback<PlaybackInfo> | undefined): this
```

操作进度条完成后，上报播放时间信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onSeeked(callback: Callback<PlaybackInfo> | undefined): this--><!--Device-VideoAttribute-default onSeeked(callback: Callback<PlaybackInfo> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | 操作进度条完成后的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onSeeking

```TypeScript
default onSeeking(callback: Callback<PlaybackInfo> | undefined): this
```

操作进度条过程时上报时间信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onSeeking(callback: Callback<PlaybackInfo> | undefined): this--><!--Device-VideoAttribute-default onSeeking(callback: Callback<PlaybackInfo> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | 操作进度条过程时的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onStart

```TypeScript
default onStart(event: VoidCallback | undefined): this
```

播放时触发该事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onStart(event: VoidCallback | undefined): this--><!--Device-VideoAttribute-default onStart(event: VoidCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 视频播放的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onStop

```TypeScript
default onStop(event: VoidCallback | undefined): this
```

播放停止时触发该事件（当stop()方法被调用后触发）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onStop(event: VoidCallback | undefined): this--><!--Device-VideoAttribute-default onStop(event: VoidCallback | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 视频播放停止时的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onUpdate

```TypeScript
default onUpdate(callback: Callback<PlaybackInfo> | undefined): this
```

播放进度变化时触发该事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default onUpdate(callback: Callback<PlaybackInfo> | undefined): this--><!--Device-VideoAttribute-default onUpdate(callback: Callback<PlaybackInfo> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; \| undefined | 是 | 播放进度变化时的回调函数。取值为undefined时，不使用回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setVideoOptions

```TypeScript
default setVideoOptions(value: VideoOptions): this
```

设置Video选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default setVideoOptions(value: VideoOptions): this--><!--Device-VideoAttribute-default setVideoOptions(value: VideoOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Video constructor options |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | Returns the instance of the VideoAttribute. |

