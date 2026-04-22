# Interface (NativeMediaPlayerBridge)
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhangyao75477-->
<!--Designer: @qiu-gongkai-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

[CreateNativeMediaPlayerCallback](./arkts-apis-webview-t.md#createnativemediaplayercallback12)回调函数的返回值类型。接管网页媒体的播放器和ArkWeb内核之间的一个接口类。

ArkWeb内核通过该接口类的实例对象来控制应用创建的用来接管网页媒体的播放器。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本Interface首批接口从API version 12开始支持。
>
> - 示例效果请以真机运行为准。

## 属性

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Sta起始版本：** 23

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

| 名称         | 类型   | 只读 | 可选 | 说明                                                         |
| ------------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| updateRect | [UpdateRectFn](#updaterectfn23) | 否   | 否   | 更新surface位置信息。|
| play | [ZeroParamFn\<>](#zeroparamfn23) | 否   | 否   | 播放视频。|
| pause | [ZeroParamFn\<>](#zeroparamfn23) | 否   | 否   | 暂停播放。|
| seek | [OneParamFn\<double>](#oneparamfn23) | 否   | 否   | 播放跳转到某个时间点。|
| setVolume | [OneParamFn\<double>](#oneparamfn23) | 否   | 否   | 设置播放器音量值。|
| setMuted | [OneParamFn\<boolean>](#oneparamfn23) | 否   | 否   | 设置静音状态。|
| setPlaybackRate | [OneParamFn\<double>](#oneparamfn23) | 否   | 否   | 设置播放速度。|
| release | [ZeroParamFn\<>](#zeroparamfn23) | 否   | 否   | 销毁播放器。|
| enterFullscreen | [ZeroParamFn\<>](#zeroparamfn23) | 否   | 否   | 播放器进入全屏。|
| exitFullscreen | [ZeroParamFn\<>](#zeroparamfn23) | 否   | 否   | 播放器退出全屏。|
| resumePlayer | [ResumePlayerFn](#resumeplayerfn23) | 否   | 是   | 通知应用销毁应用内播放器，并保存应用内播放器的状态信息。|
| suspendPlayer | [SuspendPlayerFn](#suspendplayerfn23) | 否   | 是   | 通知应用销毁应用内播放器，并保存应用内播放器的状态信息。|

## updateRect<sup>12+</sup>

updateRect(x: number, y: number, width: number, height: number): void

更新surface位置信息。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
|x|number| 是 |surface相对于Web组件的x坐标信息。 |
|y|number| 是 |surface相对于Web组件的y坐标信息。 |
|width|number| 是 |surface的宽度。<br>单位：像素。 |
|height|number| 是 |surface的高度。<br>单位：像素。 |

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## play<sup>12+</sup>

play(): void

播放视频。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## pause<sup>12+</sup>

pause(): void

暂停播放。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## seek<sup>12+</sup>

seek(targetTime: number): void

播放跳转到某个时间点。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| targetTime | number | 是 | 播放跳转到的时间点。<br>单位：秒。 |

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## setVolume<sup>12+</sup>

setVolume(volume: number): void

设置播放器音量值。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| volume | number | 是 | 播放器的音量。<br>取值范围：[0, 1.0]，其中0表示静音，1.0表示最大音量。 |

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## setMuted<sup>12+</sup>

setMuted(muted: boolean): void

设置静音状态。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| muted | boolean | 是 | 是否静音。<br>true表示静音，false表示未静音。 |

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## setPlaybackRate<sup>12+</sup>

setPlaybackRate(playbackRate: number): void

设置播放速率。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| playbackRate | number | 是 | 播放速率。<br>取值范围：[0, 10.0]，其中1表示原速播放。 |

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## release<sup>12+</sup>

release(): void

销毁播放器。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## enterFullscreen<sup>12+</sup>

enterFullscreen(): void

播放器进入全屏。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## exitFullscreen<sup>12+</sup>

exitFullscreen(): void

播放器退出全屏。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## resumePlayer<sup>12+</sup>

resumePlayer?(): void

通知应用重建应用内播放器，并恢复应用内播放器的状态信息。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## suspendPlayer<sup>12+</sup>

suspendPlayer?(type: SuspendType): void

通知应用销毁应用内播放器，并保存应用内播放器的状态信息。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| type | [SuspendType](./arkts-apis-webview-e.md#suspendtype12) | 是 | 播放器挂起类型。|

**示例：**

完整示例代码参考[onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12)。

## UpdateRectFn<sup>23+</sup>

type UpdateRectFn = (x: double, y: double, width: double, height: double) => void

更新surface位置信息。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| x | double | 是 | surface 相对于 Web 组件的 x 坐标信息。 |
| y | double | 是 | surface 相对于 Web 组件的 y 坐标信息。 |
| width  | double | 是 | surface 的宽度。<br>单位：px。 |
| height | double | 是 | surface 的高度。<br>单位：px。 |

## ZeroParamFn<sup>23+</sup>

type ZeroParamFn<V=void> = () => V

无参函数。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Sta起始版本：** 23

## OneParamFn<sup>23+</sup>

type OneParamFn<T,V=void> = (param: T) => V

带有一个参数的函数。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Sta起始版本：** 23

## ResumePlayerFn<sup>23+</sup>

type ResumePlayerFn = () => void

通知应用重建应用内播放器，并恢复应用内播放器的状态信息。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Sta起始版本：** 23

## SuspendPlayerFn<sup>23+</sup>

type SuspendPlayerFn = (type: SuspendType) => void

通知应用销毁应用内播放器，并保存应用内播放器的状态信息。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.Web.Webview.Core

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| type | [SuspendType](./arkts-apis-webview-e.md#suspendtype12) | 是 | 播放器挂起类型。|

