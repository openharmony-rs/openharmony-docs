# AVScreenCaptureRecorder

屏幕录制管理类，用于进行屏幕录制。在调用AVScreenCaptureRecorder的方法前，需要先通过[createAVScreenCaptureRecorder()](arkts-media-media-createavscreencapturerecorder-f.md#createavscreencapturerecorder-1)创建一个AVScreenCaptureRecorder实例。

> **说明：**  
>  
> - 本Interface首批接口从API version 12开始支持。

**起始版本：** 12

<!--Device-unnamed-interface AVScreenCaptureRecorder--><!--Device-unnamed-interface AVScreenCaptureRecorder-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## excludePickerWindows

```TypeScript
excludePickerWindows(excludedWindows: Array<number>): Promise<void>
```

设置在Picker中隐藏的窗口列表，在下一次显示Picker时生效。使用Promise异步回调。

**起始版本：** 22

<!--Device-AVScreenCaptureRecorder-excludePickerWindows(excludedWindows: Array<int>): Promise<void>--><!--Device-AVScreenCaptureRecorder-excludePickerWindows(excludedWindows: Array<int>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| excludedWindows | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 需要在Picker中隐藏的窗口列表，窗口属性获取方法可以参考[getWindowProperties](../../../../reference/apis-arkui/arkts-apis-window-Window.md#getwindowproperties9)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## init

```TypeScript
init(config: AVScreenCaptureRecordConfig): Promise<void>
```

进行录屏初始化，设置录屏参数。使用Promise异步回调。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-init(config: AVScreenCaptureRecordConfig): Promise<void>--><!--Device-AVScreenCaptureRecorder-init(config: AVScreenCaptureRecordConfig): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AVScreenCaptureRecordConfig](arkts-media-multimedia-media-avscreencapturerecordconfig-i.md) | 是 | 配置屏幕录制的相关参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types. 3. Parameter verification failed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: Callback<AVScreenCaptureStateCode>): void
```

取消订阅状态切换回调事件。用户可以指定填入状态切换的回调方法来取消订阅。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-off(type: 'stateChange', callback?: Callback<AVScreenCaptureStateCode>): void--><!--Device-AVScreenCaptureRecorder-off(type: 'stateChange', callback?: Callback<AVScreenCaptureStateCode>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 状态切换事件回调类型，支持的事件：'stateChange'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AVScreenCaptureStateCode> | 否 | 状态切换事件回调方法，[AVScreenCaptureStateCode](@ohos.multimedia.media:media.AVScreenCaptureStateCode)表示切换到的状态，不填此参数则会取消最后一次订阅事件。 |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

取消订阅错误回调事件。用户可以指定填入错误回调方法来取消订阅。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-off(type: 'error', callback?: ErrorCallback): void--><!--Device-AVScreenCaptureRecorder-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 状态切换事件回调类型，支持的事件：'error'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 否 | 录屏错误事件回调方法，不填此参数则会取消最后一次订阅事件。 |

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: Callback<AVScreenCaptureStateCode>): void
```

订阅录屏状态切换的事件，当状态发生的时候，会通过订阅的回调通知用户。用户只能订阅一个状态切换的回调方法，重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-on(type: 'stateChange', callback: Callback<AVScreenCaptureStateCode>): void--><!--Device-AVScreenCaptureRecorder-on(type: 'stateChange', callback: Callback<AVScreenCaptureStateCode>): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'stateChange' | 是 | 状态切换事件回调类型，支持的事件：'stateChange'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<AVScreenCaptureStateCode> | 是 | 状态切换事件回调方法，[AVScreenCaptureStateCode](@ohos.multimedia.media:media.AVScreenCaptureStateCode)表示切换到的状态。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

订阅AVScreenCaptureRecorder的错误事件，用户可以根据应用自身逻辑对错误事件进行处理。用户只能订阅一个错误事件的回调方法，重复订阅时，以最后一次订阅的回调接口为准。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-on(type: 'error', callback: ErrorCallback): void--><!--Device-AVScreenCaptureRecorder-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 错误事件回调类型，支持的事件：'error'。 |
| callback | [ErrorCallback](../../apis-arkui/arkts-components/arkts-arkui-errorcallback-t-sys.md) | 是 | 录屏错误事件回调方法。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by ErrorCallback. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by ErrorCallback. |

## pauseRecording

```TypeScript
pauseRecording(): Promise<void>
```

暂停录屏。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVScreenCaptureRecorder-pauseRecording(): Promise<void>--><!--Device-AVScreenCaptureRecorder-pauseRecording(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not be permitted. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## presentPicker

```TypeScript
presentPicker(): Promise<void>
```

录屏开始后，调用该接口再次弹出Picker，可动态更新录制源（窗口、屏幕）。使用Promise异步回调。

> **说明：**  
>  
> - 更新录制源过程中，原录制流程不中断。  
>  
> - 通过picker动态更新录制源后，按照新的录制源进行录制。

**起始版本：** 22

<!--Device-AVScreenCaptureRecorder-presentPicker(): Promise<void>--><!--Device-AVScreenCaptureRecorder-presentPicker(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## release

```TypeScript
release(): Promise<void>
```

释放录屏。使用Promise异步回调。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-release(): Promise<void>--><!--Device-AVScreenCaptureRecorder-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## resumeRecording

```TypeScript
resumeRecording(): Promise<void>
```

恢复录屏。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVScreenCaptureRecorder-resumeRecording(): Promise<void>--><!--Device-AVScreenCaptureRecorder-resumeRecording(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not be permitted. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## setMicEnabled

```TypeScript
setMicEnabled(enable: boolean): Promise<void>
```

设置麦克风开关。使用Promise异步回调。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-setMicEnabled(enable: boolean): Promise<void>--><!--Device-AVScreenCaptureRecorder-setMicEnabled(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 麦克风开关控制，true代表麦克风打开，false代表麦克风关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## setPickerMode

```TypeScript
setPickerMode(pickerMode: PickerMode): Promise<void>
```

设置Picker显示模式，在下一次显示Picker时生效。使用Promise异步回调。

**起始版本：** 22

<!--Device-AVScreenCaptureRecorder-setPickerMode(pickerMode: PickerMode): Promise<void>--><!--Device-AVScreenCaptureRecorder-setPickerMode(pickerMode: PickerMode): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pickerMode | [PickerMode](arkts-media-multimedia-media-pickermode-e.md) | 是 | 选择Picker模式。<br>定义了在Picker中显示的内容类型：<br>- SCREEN_ONLY：仅显示屏幕列表。<br>- WINDOW_ONLY：仅显示窗口列表。<br>- SCREEN_AND_WINDOW：同时显示屏幕列表和窗口列表（默认值）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400102](../errorcode-media.md#5400102-当前状态不支持此操作) | Operation not allowed. Return by promise. |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## skipPrivacyMode

```TypeScript
skipPrivacyMode(windowIDs: Array<number>): Promise<void>
```

录屏时，应用可对本应用的隐私窗口做安全豁免。使用Promise异步回调。

如录屏时，用户在本应用进行输入密码等操作，应用不会进行黑屏处理。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-skipPrivacyMode(windowIDs: Array<int>): Promise<void>--><!--Device-AVScreenCaptureRecorder-skipPrivacyMode(windowIDs: Array<int>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowIDs | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 需要豁免隐私的窗口列表，包括主窗口id和子窗口id，窗口属性获取方法可以参考[getWindowProperties](../../../../reference/apis-arkui/arkts-apis-window-Window.md#getwindowproperties9)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## startRecording

```TypeScript
startRecording(): Promise<void>
```

开始录屏，在使用前需要先调用[init](@ohos.multimedia.media:media.AVScreenCaptureRecorder.init)接口。使用Promise异步回调。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-startRecording(): Promise<void>--><!--Device-AVScreenCaptureRecorder-startRecording(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

## stopRecording

```TypeScript
stopRecording(): Promise<void>
```

结束录屏。使用Promise异步回调。

**起始版本：** 12

<!--Device-AVScreenCaptureRecorder-stopRecording(): Promise<void>--><!--Device-AVScreenCaptureRecorder-stopRecording(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [5400103](../errorcode-media.md#5400103-出现io错误) | IO error. Return by promise. |
| [5400105](../errorcode-media.md#5400105-播放服务死亡) | Service died. Return by promise. |

