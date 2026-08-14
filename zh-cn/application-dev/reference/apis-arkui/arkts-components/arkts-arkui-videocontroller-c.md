# VideoController

一个VideoController对象可以控制一个或多个Video。

## 导入对象 ```ts let controller: VideoController = new VideoController(); ```

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare class VideoController--><!--Device-unnamed-declare class VideoController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

VideoController的构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-constructor()--><!--Device-VideoController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## exitFullscreen

```TypeScript
exitFullscreen()
```

退出全屏播放。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-exitFullscreen()--><!--Device-VideoController-exitFullscreen()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause()
```

暂停播放，显示当前帧，再次播放时从当前位置继续播放。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-pause()--><!--Device-VideoController-pause()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## requestFullscreen

```TypeScript
requestFullscreen(value: boolean)
```

请求全屏播放。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-requestFullscreen(value: boolean)--><!--Device-VideoController-requestFullscreen(value: boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否全屏（填充满应用窗口）播放。 &lt;br&gt;true：请求全屏播放；false：不请求全屏播放。 &lt;br&gt;默认值：false |

## reset

```TypeScript
reset(): void
```

重置视频播放器。显示当前帧，再次播放时从头开始播放。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-reset(): void--><!--Device-VideoController-reset(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setCurrentTime

```TypeScript
setCurrentTime(value: number)
```

指定视频播放的进度位置。 > **说明：** > > 如需从视频内的某一时间点开始播放，应关闭自动播放，在视频准备完成后先跳转再播放。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-setCurrentTime(value: number)--><!--Device-VideoController-setCurrentTime(value: number)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 视频播放进度位置。 &lt;br&gt;取值范围：[0, [duration](arkts-arkui-preparedinfo-i.md#PreparedInfo)] &lt;br&gt;当设置value大于duration时，进度跳转至最后；当设置value小于0时，不会进行进度跳转。 &lt;br&gt;单位：s &lt;br&gt;从API version 8开始，支持设置视频的跳转模式，详见 [setCurrentTime&lt;sup&gt;8+&lt;/sup&gt;](#setCurrentTime)。 |

## setCurrentTime

```TypeScript
setCurrentTime(value: number, seekMode: SeekMode)
```

指定视频播放的进度位置，并指定跳转模式。 > **说明：** > > 如需从视频内的某一时间点开始播放，应关闭自动播放，在视频准备完成后先跳转再播放。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-setCurrentTime(value: number, seekMode: SeekMode)--><!--Device-VideoController-setCurrentTime(value: number, seekMode: SeekMode)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 视频播放进度位置。 &lt;br&gt;取值范围：[0, [duration](arkts-arkui-preparedinfo-i.md#PreparedInfo)] &lt;br&gt;当设置value大于duration时，进度跳转至最后；当设置value小于0时，不会进行进度跳转。 &lt;br&gt;单位：s |
| seekMode | [SeekMode](arkts-arkui-seekmode-e.md) | 是 | 跳转模式。 &lt;br&gt;异常值undefined、null、NaN和Infinity按PreviousKeyframe处理。 |

## start

```TypeScript
start()
```

开始播放。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-start()--><!--Device-VideoController-start()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stop

```TypeScript
stop()
```

停止播放，显示当前帧，再次播放时从头开始播放。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VideoController-stop()--><!--Device-VideoController-stop()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

