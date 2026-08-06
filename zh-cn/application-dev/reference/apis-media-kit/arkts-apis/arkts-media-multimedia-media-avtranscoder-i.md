# AVTranscoder

视频转码管理类，用于视频转码。在调用AVTranscoder的方法前，需要先通过 [createAVTranscoder()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_构建一个AVTranscoder实例。 视频转码demo可参考：\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > **说明：** > > - 本Interface首批接口从API version 12开始支持。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-interface AVTranscoder--><!--Device-unnamed-interface AVTranscoder-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## addWatermark

ArkTS-Dyn:
```TypeScript
addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<number>
```

ArkTS-Sta:
```TypeScript
addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<int>
```

add a watermark for the AVTranscoder. This API uses a promise to return the result. App can add up to 5 watermarks. This API can be called only before the prepared state.

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVTranscoder-addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<int>--><!--Device-AVTranscoder-addWatermark(watermark: image.PixelMap, config: WatermarkConfiguration): Promise<int>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| watermark | image.PixelMap | 是 | : Watermark image. |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | : Configuration of the watermark. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | Promise that returns the watermark id. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [5400108](../errorcode-media.md#5400108-参数超过取值范围) | The parameter check failed, parameter value out of range. |

## cancel

```TypeScript
cancel(): Promise<void>
```

取消视频转码。使用Promise异步回调。 需要在[prepare()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、[start()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [pause()]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_或[resume()]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_事件成功触发后，才能调用cancel方法。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-cancel(): Promise<void>--><!--Device-AVTranscoder-cancel(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## off('complete')

```TypeScript
off(type:'complete', callback?: Callback<void>):void
```

取消注册转码完成事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-off(type:'complete', callback?: Callback<void>):void--><!--Device-AVTranscoder-off(type:'complete', callback?: Callback<void>):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' | 是 | 转码完成事件回调类型，支持的事件：'complete'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 完成事件回调方法。 |

## off('error')

```TypeScript
off(type:'error', callback?: ErrorCallback):void
```

取消注册转码错误事件，取消后不再接收到AVTranscoder的错误事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-off(type:'error', callback?: ErrorCallback):void--><!--Device-AVTranscoder-off(type:'error', callback?: ErrorCallback):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 转码错误事件回调类型'error'。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- 'error'：转码过程中发生错误，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 错误事件回调方法。 |

## off('progressUpdate')

```TypeScript
off(type:'progressUpdate', callback?: Callback<int>):void
```

取消注册转码进度更新事件。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-off(type:'progressUpdate', callback?: Callback<int>):void--><!--Device-AVTranscoder-off(type:'progressUpdate', callback?: Callback<int>):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'progressUpdate' | 是 | 进度更新事件回调类型，支持的事件：'progressUpdate'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 否 | 已注册的进度更新事件回调。由于当前回调注册时，仅会保留最后一次注册的回调，建议此参数缺省。 |

## offComplete

```TypeScript
offComplete(callback?: Callback<void>):void
```

Unsubscribes from the event indicating that transcoding is complete. This event can be triggered by both user operations and the system.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVTranscoder-offComplete(callback?: Callback<void>):void--><!--Device-AVTranscoder-offComplete(callback?: Callback<void>):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | Callback that has been registered to listen for transcoding completion events. |

## offError

```TypeScript
offError(callback?: ErrorCallback):void
```

Unsubscribes from AVTranscoder errors. After the unsubscription, your application can no longer receive AVTranscoder errors. This event is triggered when an error occurs during transcoding.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVTranscoder-offError(callback?: ErrorCallback):void--><!--Device-AVTranscoder-offError(callback?: ErrorCallback):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback that has been registered to listen for AVTranscoder errors. |

## offProgressUpdate

```TypeScript
offProgressUpdate(callback?: Callback<int>):void
```

Unsubscribes from transcoding progress updates. This event can be triggered by both user operations and the system.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVTranscoder-offProgressUpdate(callback?: Callback<int>):void--><!--Device-AVTranscoder-offProgressUpdate(callback?: Callback<int>):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 否 | Called that has been registered to listen for progress updates.You are advised to use the default value because only the last registered callback is retained in the current allback mechanism. |

## on('complete')

```TypeScript
on(type:'complete', callback: Callback<void>):void
```

注册转码完成事件，并通过注册的回调方法通知开发者。开发者只能注册一个进度更新事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。使用callback异步回调。 当AVTranscoder上报complete事件时，当前转码操作已完成，开发者需要通过[release()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_退出转码操作。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-on(type:'complete', callback: Callback<void>):void--><!--Device-AVTranscoder-on(type:'complete', callback: Callback<void>):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'complete' | 是 | 完成事件回调类型，支持的事件：'complete'，在转码过程中系统会自动触发此事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数，返回完成事件回调方法。 |

## on('error')

```TypeScript
on(type:'error', callback: ErrorCallback):void
```

注册AVTranscoder的错误事件，该事件仅用于错误提示。如果AVTranscoder上报error事件，开发者需要通过[release()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_退出转码操作 。使用callback异步回调。 开发者只能订阅一个错误事件的回调方法，当开发者重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-on(type:'error', callback: ErrorCallback):void--><!--Device-AVTranscoder-on(type:'error', callback: ErrorCallback):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 转码错误事件回调类型'error'。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_- 'error'：录制过程中发生错误，触发该事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 转码错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. |

## on('progressUpdate')

```TypeScript
on(type:'progressUpdate', callback: Callback<int>):void
```

注册转码进度更新事件，并通过注册的回调方法通知开发者。开发者只能注册一个进度更新事件的回调方法，当开发者重复注册时，以最后一次注册的回调接口为准。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-on(type:'progressUpdate', callback: Callback<int>):void--><!--Device-AVTranscoder-on(type:'progressUpdate', callback: Callback<int>):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'progressUpdate' | 是 | 进度更新事件回调类型，支持的事件：'progressUpdate'，在转码过程中系统会自动触发此事件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | 回调函数，返回进度更新事件，函数中的参数number，表示当前转码进度。 |

## onComplete

```TypeScript
onComplete(callback: Callback<void>):void
```

Subscribes to the event indicating that transcoding is complete. An application can subscribe to only one transcoding completion event. When the application initiates multiple subscriptions to this event, the last subscription is applied. When this event is reported, the current transcoding operation is complete. You need to call [release()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ to exit the transcoding.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVTranscoder-onComplete(callback: Callback<void>):void--><!--Device-AVTranscoder-onComplete(callback: Callback<void>):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | Callback that has been registered to listen for transcoding completion events. |

## onError

```TypeScript
onError(callback: ErrorCallback):void
```

Subscribes to AVTranscoder errors. If this event is reported, call [release()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ to exit the transcoding. An application can subscribe to only one AVTranscoder error event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVTranscoder-onError(callback: ErrorCallback):void--><!--Device-AVTranscoder-onError(callback: ErrorCallback):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback invoked when the event is triggered. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [5400101](../errorcode-media.md#5400101-内存分配失败) | No memory. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | I/O error. |
| [5400104](../errorcode-media.md#5400104-操作超时) | Time out. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. |

## onProgressUpdate

```TypeScript
onProgressUpdate(callback: Callback<int>):void
```

Subscribes to transcoding progress updates. An application can subscribe to only one transcoding progress update event. When the application initiates multiple subscriptions to this event, the last subscription is applied.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-AVTranscoder-onProgressUpdate(callback: Callback<int>):void--><!--Device-AVTranscoder-onProgressUpdate(callback: Callback<int>):void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; | 是 | Callback invoked when the event is triggered.**progress** is a number that indicates the current transcoding progress, in percentage. |

## pause

```TypeScript
pause(): Promise<void>
```

暂停视频转码。使用Promise异步回调。 需要[start()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_事件成功触发后，才能调用pause方法，可以通过调用[resume()]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接 口来恢复转码。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-pause(): Promise<void>--><!--Device-AVTranscoder-pause(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## prepare

```TypeScript
prepare(config: AVTranscoderConfig): Promise<void>
```

进行视频转码的参数设置。使用Promise异步回调。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-prepare(config: AVTranscoderConfig): Promise<void>--><!--Device-AVTranscoder-prepare(config: AVTranscoderConfig): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 配置视频转码的相关参数。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_COMMENT\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Return by promise. |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |
| [5400106](../errorcode-media.md#5400106-不支持的规格) | Unsupported format. Returned by promise. |

## release

```TypeScript
release(): Promise<void>
```

释放视频转码资源。使用Promise异步回调。 释放视频转码资源之后，该AVTranscoder实例不能再进行任何操作。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-release(): Promise<void>--><!--Device-AVTranscoder-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## resume

```TypeScript
resume(): Promise<void>
```

恢复视频转码。使用Promise异步回调。 需要在[pause()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_事件成功触发后，才能调用resume方法。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-resume(): Promise<void>--><!--Device-AVTranscoder-resume(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## start

```TypeScript
start(): Promise<void>
```

开始视频转码。使用Promise异步回调。 需要[prepare()]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_事件成功触发后，才能调用start方法。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-start(): Promise<void>--><!--Device-AVTranscoder-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## fdDst

```TypeScript
fdDst: int
```

目标媒体文件描述，通过该属性设置数据输出。在创建AVTranscoder实例后，必须设置fdSrc和fdDst属性。 **说明：** - 将资源句柄（fd）传递给AVTranscoder实例之后，请不要通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个AVPlayer/AVMetadataExtractor/AVImageGenerator /AVTranscoder。 - 同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致视频转码数据获取异常。

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-fdDst: int--><!--Device-AVTranscoder-fdDst: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

## fdSrc

```TypeScript
fdSrc: AVFileDescriptor
```

源媒体文件描述，通过该属性设置数据源。 **使用示例**： 假设一个连续存储的媒体文件，地址偏移：0，字节长度：100。其文件描述为AVFileDescriptor{ fd = 资源句柄; offset = 0; length = 100; }。 **说明：** - 将资源句柄（fd）传递给AVTranscoder实例之后，请不要通过该资源句柄做其他读写操作，包括但不限于将同一个资源句柄传递给多个AVPlayer/AVMetadataExtractor/AVImageGenerator /AVTranscoder。 - 同一时间通过同一个资源句柄读写文件时存在竞争关系，将导致视频转码数据获取异常。

**类型：** AVFileDescriptor

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-AVTranscoder-fdSrc: AVFileDescriptor--><!--Device-AVTranscoder-fdSrc: AVFileDescriptor-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVTranscoder

