# Video

Video组件用于播放视频文件并控制其播放状态，支持播放、暂停、进度控制、倍速播放、全屏切换等功能。

> **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > <br> > > Video组件只提供简单的视频播放功能，无法支撑复杂的视频播控场景。复杂开发场景推荐使用[AVPlayer](../../apis-media-kit/arkts-apis/arkts-media-media-avplayer-i.md)播控API和 > XComponent组件开发。 > <br> > > Video组件在使用[expandSafeArea](arkts-arkui-commonmethod-c.md#expandsafearea)扩展安全区域时，组件视频显示内容区域不支持扩展。

## 权限列表

使用网络视频时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。

## 子组件

不支持子组件。

## Video

```TypeScript
Video(value: VideoOptions)
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [VideoOptions](arkts-arkui-videooptions-i.md) | 是 | 视频信息。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [FullscreenInfo](arkts-arkui-fullscreeninfo-i.md) | 用于描述当前视频是否进入全屏播放状态。 |
| [PlaybackInfo](arkts-arkui-playbackinfo-i.md) | 用于描述当前视频播放的进度。 |
| [PosterOptions](arkts-arkui-posteroptions-i.md) | 用于描述当前视频是否配置首帧送显。 |
| [PreparedInfo](arkts-arkui-preparedinfo-i.md) | 用于描述当前视频的时长。 |
| [VideoOptions](arkts-arkui-videooptions-i.md) | 定义Video的具体配置参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PlaybackSpeed](arkts-arkui-playbackspeed-e.md) | 视频播放倍速选项。 |
| [SeekMode](arkts-arkui-seekmode-e.md) | 视频跳转模式选项。 |

## 示例

```TypeScript
### 示例1（视频播放基础用法）

基础用法包括：控制栏、预览图、自动播放、播放速度、响应快捷键（从API version 15开始，支持通过[enableShortcutKey](arkts-arkui-video-comp-attribute.md#enableshortcutkey)设置组件开启快捷键响应）、控制器（开始播放、暂停播放、停止播放、重置视频播放器、跳转等）、首帧送显（从API version 18开始，支持通过[posterOptions](#posteroptions18对象说明)设置视频播放的首帧送显选项。从API version 21开始，posterOptions支持通过[PosterOptions](#posteroptions18对象说明)的contentTransitionEffect参数来设置当前视频的预览图内容变化时的转场动效。）以及一些状态回调方法。


```

```TypeScript
### 示例2（图像分析功能）

通过enableAnalyzer属性开启图像AI分析。
```

```TypeScript
### 示例3（播放拖入的视频）

以下示例展示了如何使Video组件能够播放拖入的视频。
```

```TypeScript
### 示例4（视频填充模式）

通过objectFit属性设置视频填充模式。


```

```TypeScript
### 示例5（onError事件上报错误码）

从API version 20开始，支持通过[onError](#onerror)获取错误信息，该示例以传入不存在的视频资源路径为例。


```

```TypeScript
### 示例6（使用attributeModifier动态设置Video组件的属性及方法）

以下示例展示了如何使用attributeModifier动态设置Video组件的enableAnalyzer、analyzerConfig属性和onStart、onPause、onFinish、onError、onStop、onPrepared、onSeeking、onSeeked、onUpdate、onFullscreenChange方法。


```

```TypeScript
### 示例7（VideoControllerAsync用法）

本示例展示VideoControllerAsync的[start](#start-1)、[pause](#pause-1)、[stop](#stop-1)、[reset](#reset)接口用法，通过Promise异步回调获取命令执行状态。

从API版本26.0.0开始，新增VideoControllerAsync控制器及[start](#start-1)、[pause](#pause-1)、[stop](#stop-1)、[reset](#reset)接口。
```
