# NativeMediaPlayerBridge

NativeMediaPlayerBridge 是[CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的返回值类 型，是接管网页媒体的播放器和 ArkWeb 内核之间的一个接口类。ArkWeb 内核通过该接口类的实例对象控制应用创建的用于接管网页媒体的播放器。该接口允许应用使用自定义的媒体播放器接管网页中的媒体内容播放，同时，该接口还支持播放 器的挂起和恢复机制。

**起始版本：** 12

<!--Device-webview-interface NativeMediaPlayerBridge--><!--Device-webview-interface NativeMediaPlayerBridge-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## enterFullscreen

```TypeScript
enterFullscreen(): void
```

使播放器进入全屏。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-enterFullscreen(): void--><!--Device-NativeMediaPlayerBridge-enterFullscreen(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## exitFullscreen

```TypeScript
exitFullscreen(): void
```

使播放器退出全屏。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-exitFullscreen(): void--><!--Device-NativeMediaPlayerBridge-exitFullscreen(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## pause

```TypeScript
pause(): void
```

暂停播放。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-pause(): void--><!--Device-NativeMediaPlayerBridge-pause(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## play

```TypeScript
play(): void
```

播放媒体。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-play(): void--><!--Device-NativeMediaPlayerBridge-play(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## release

```TypeScript
release(): void
```

销毁播放器。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-release(): void--><!--Device-NativeMediaPlayerBridge-release(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## resumePlayer

```TypeScript
resumePlayer?(): void
```

通知应用重建播放器，并恢复播放器的状态信息。仅与 suspendPlayer 成对出现。

**起始版本：** 12

<!--Device-NativeMediaPlayerBridge-resumePlayer?(): void--><!--Device-NativeMediaPlayerBridge-resumePlayer?(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## seek

```TypeScript
seek(targetTime: number): void
```

跳转播放进度到指定时间点。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-seek(targetTime: number): void--><!--Device-NativeMediaPlayerBridge-seek(targetTime: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetTime | number | 是 | 播放跳转到的时间点，从媒体开始播放时计算。 <br>单位：秒。 |

## setMuted

```TypeScript
setMuted(muted: boolean): void
```

设置静音状态。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-setMuted(muted: boolean): void--><!--Device-NativeMediaPlayerBridge-setMuted(muted: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| muted | boolean | 是 | 是否静音。 <br>true表示静音，false表示未静音。 |

## setPlaybackRate

```TypeScript
setPlaybackRate(playbackRate: number): void
```

设置播放速率。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-setPlaybackRate(playbackRate: number): void--><!--Device-NativeMediaPlayerBridge-setPlaybackRate(playbackRate: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| playbackRate | number | 是 | 播放速率。 <br>取值范围：[0, 10.0]，其中1表示原速播放。超出取值范围时，按边界值自动修正。 |

## setVolume

```TypeScript
setVolume(volume: number): void
```

设置播放器音量值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-setVolume(volume: number): void--><!--Device-NativeMediaPlayerBridge-setVolume(volume: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 播放器的音量。 <br>取值范围：[0, 1.0]，其中0表示静音，1.0表示最大音量。超出取值范围时，按边界值自动修正。 |

## suspendPlayer

```TypeScript
suspendPlayer?(type: SuspendType): void
```

通知应用销毁播放器，并保存播放器的状态信息。仅与 resumePlayer 成对出现。

**起始版本：** 12

<!--Device-NativeMediaPlayerBridge-suspendPlayer?(type: SuspendType): void--><!--Device-NativeMediaPlayerBridge-suspendPlayer?(type: SuspendType): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SuspendType](arkts-arkweb-webview-suspendtype-e.md) | 是 | 播放器挂起类型，用于指定播放器挂起的方式。不同 SuspendType 取值对应不同的挂起场景。 |

## updateRect

```TypeScript
updateRect(x: number, y: number, width: number, height: number): void
```

向应用通知 surface 位置信息。当网页布局变化、页面滚动或播放区域发生改变时由 ArkWeb 内核回调此方法，应用需据此更新原生播放器渲染表面的位置和大小。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerBridge-updateRect(x: number, y: number, width: number, height: number): void--><!--Device-NativeMediaPlayerBridge-updateRect(x: number, y: number, width: number, height: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | number | 是 | surface相对于Web组件的x坐标信息。 <br>单位：px。 |
| y | number | 是 | surface相对于Web组件的y坐标信息。 <br>单位：px。 |
| width | number | 是 | surface的宽度。 <br>单位：px。 |
| height | number | 是 | surface的高度。 <br>单位：px。 |

