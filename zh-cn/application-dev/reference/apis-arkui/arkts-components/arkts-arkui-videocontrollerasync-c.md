# VideoControllerAsync

VideoControllerAsync是VideoController的异步版本，可以通过Promise获取部分播控命令的结果。不支持同时控制多个Video。

> **说明：**
> 
> VideoControllerAsync提供命令执行结果。与VideoController相比，[start](arkts-arkui-videocontroller-c.md#start)、
> [pause](arkts-arkui-videocontroller-c.md#pause)、[stop](arkts-arkui-videocontroller-c.md#stop)、[reset](#reset)等播
> 放控制命令为异步执行，请求后立即返回不阻塞当前线程，可通过Promise的then和catch方法处理命令执行结果。

## 导入对象

```ts
let controllerAsync: VideoControllerAsync = new VideoControllerAsync();
```

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

VideoControllerAsync的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## exitFullscreen

```TypeScript
exitFullscreen()
```

退出全屏播放。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause(): Promise<void>
```

暂停播放视频，显示当前帧，再次播放时从当前位置继续播放。使用Promise异步回调。只能在正在播放的状态下调用，其他情况下调用pause()方法会失败。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

## requestFullscreen

```TypeScript
requestFullscreen(value: boolean)
```

请求全屏播放。未通过该接口设置时，默认不请求全屏播放。

> **说明：**
> 
> Video组件自带的全屏功能仅将视频内容设为全屏，显示默认控制器，无法显示自定义标题或控制器。如需其他功能，用户需自行实现全屏功能。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否全屏（填充满应用窗口）播放。 true：请求全屏播放；false：不请求全屏播放。 |

## reset

```TypeScript
reset(): Promise<void>
```

重置视频播放器。显示当前帧，再次播放时从头开始播放。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

## setCurrentTime

```TypeScript
setCurrentTime(value: number, seekMode?: SeekMode)
```

指定视频播放的进度位置，可以指定跳转模式。

> **说明：**
> 
> 如需从视频内的某一时间点开始播放，应关闭自动播放，在视频准备完成后先跳转再播放。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 视频播放进度位置。 取值范围：[0, [duration](arkts-arkui-preparedinfo-i.md)] 当设置value大于duration时，进度跳转至最后；当设置value小于0时，不会进行进度跳转。 单位：s |
| seekMode | [SeekMode](arkts-arkui-seekmode-e.md) | 否 | 跳转模式。 异常值undefined、null、NaN和Infinity按PreviousKeyframe处理。 默认值：PreviousKeyframe |

## start

```TypeScript
start(): Promise<void>
```

开始播放视频。使用Promise异步回调。视频准备完成前（未收到[onPrepared](arkts-arkui-video-attribute.md#onprepared)回调）调用start()方法会失败。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

## stop

```TypeScript
stop(): Promise<void>
```

停止播放视频，显示当前帧，再次播放时从头开始播放。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |
