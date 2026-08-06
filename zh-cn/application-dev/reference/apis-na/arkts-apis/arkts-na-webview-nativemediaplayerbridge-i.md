# NativeMediaPlayerBridge

\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ 回调函数的返回值类型。接管网页媒体的播放器和ArkWeb内核之间的一个接口类。 ArkWeb内核通过该接口类的实例对象来控制应用创建的用来接管网页媒体的播放器。 > **说明：** > > - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。 > > - 本Interface首批接口从API version 12开始支持。 > > - 示例效果请以真机运行为准。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-webview-interface NativeMediaPlayerBridge--><!--Device-webview-interface NativeMediaPlayerBridge-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## enterFullscreen

```TypeScript
enterFullscreen: ZeroParamFn<>
```

播放器进入全屏。

**类型：** ZeroParamFn&lt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-enterFullscreen: ZeroParamFn<>--><!--Device-NativeMediaPlayerBridge-enterFullscreen: ZeroParamFn<>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## exitFullscreen

```TypeScript
exitFullscreen: ZeroParamFn<>
```

播放器退出全屏。

**类型：** ZeroParamFn&lt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-exitFullscreen: ZeroParamFn<>--><!--Device-NativeMediaPlayerBridge-exitFullscreen: ZeroParamFn<>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## pause

```TypeScript
pause: ZeroParamFn<>
```

暂停播放。

**类型：** ZeroParamFn&lt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-pause: ZeroParamFn<>--><!--Device-NativeMediaPlayerBridge-pause: ZeroParamFn<>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## play

```TypeScript
play: ZeroParamFn<>
```

播放视频。

**类型：** ZeroParamFn&lt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-play: ZeroParamFn<>--><!--Device-NativeMediaPlayerBridge-play: ZeroParamFn<>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## release

```TypeScript
release: ZeroParamFn<>
```

销毁播放器。

**类型：** ZeroParamFn&lt;&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-release: ZeroParamFn<>--><!--Device-NativeMediaPlayerBridge-release: ZeroParamFn<>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## resumePlayer

```TypeScript
resumePlayer?: ResumePlayerFn
```

通知应用销毁应用内播放器，并保存应用内播放器的状态信息。

**类型：** ResumePlayerFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-resumePlayer?: ResumePlayerFn--><!--Device-NativeMediaPlayerBridge-resumePlayer?: ResumePlayerFn-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## seek

```TypeScript
seek: OneParamFn<double>
```

播放跳转到某个时间点。

**类型：** OneParamFn&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-seek: OneParamFn<double>--><!--Device-NativeMediaPlayerBridge-seek: OneParamFn<double>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## setMuted

```TypeScript
setMuted: OneParamFn<boolean>
```

设置静音状态。

**类型：** OneParamFn&lt;boolean&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-setMuted: OneParamFn<boolean>--><!--Device-NativeMediaPlayerBridge-setMuted: OneParamFn<boolean>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## setPlaybackRate

```TypeScript
setPlaybackRate: OneParamFn<double>
```

设置播放速度。

**类型：** OneParamFn&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-setPlaybackRate: OneParamFn<double>--><!--Device-NativeMediaPlayerBridge-setPlaybackRate: OneParamFn<double>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## setVolume

```TypeScript
setVolume: OneParamFn<double>
```

设置播放器音量值。

**类型：** OneParamFn&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-setVolume: OneParamFn<double>--><!--Device-NativeMediaPlayerBridge-setVolume: OneParamFn<double>-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## suspendPlayer

```TypeScript
suspendPlayer?: SuspendPlayerFn
```

通知应用销毁应用内播放器，并保存应用内播放器的状态信息。

**类型：** SuspendPlayerFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-suspendPlayer?: SuspendPlayerFn--><!--Device-NativeMediaPlayerBridge-suspendPlayer?: SuspendPlayerFn-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## updateRect

```TypeScript
updateRect: UpdateRectFn
```

更新surface位置信息。

**类型：** UpdateRectFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-NativeMediaPlayerBridge-updateRect: UpdateRectFn--><!--Device-NativeMediaPlayerBridge-updateRect: UpdateRectFn-End-->

**系统能力：** SystemCapability.Web.Webview.Core

