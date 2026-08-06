# VideoController

一个VideoController对象可以控制一个或多个Video。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class VideoController--><!--Device-unnamed-export declare class VideoController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

VideoController的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoController-constructor()--><!--Device-VideoController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## exitFullscreen

```TypeScript
exitFullscreen(): void
```

退出全屏播放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoController-exitFullscreen(): void--><!--Device-VideoController-exitFullscreen(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause(): void
```

暂停播放，显示当前帧，再次播放时从当前位置继续播放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoController-pause(): void--><!--Device-VideoController-pause(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## requestFullscreen

```TypeScript
requestFullscreen(value: boolean): void
```

请求全屏播放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoController-requestFullscreen(value: boolean): void--><!--Device-VideoController-requestFullscreen(value: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否全屏（填充满应用窗口）播放。true：请求全屏播放；false：不请求全屏播放。默认值：false |

## reset

```TypeScript
reset(): void
```

Video组件重置AVPlayer。显示当前帧，再次播放时从头开始播放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoController-reset(): void--><!--Device-VideoController-reset(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setCurrentTime

```TypeScript
setCurrentTime(value: double, seekMode?: SeekMode): void
```

指定视频播放的进度位置，并指定跳转模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoController-setCurrentTime(value: double, seekMode?: SeekMode): void--><!--Device-VideoController-setCurrentTime(value: double, seekMode?: SeekMode): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | 视频播放进度位置，单位：秒。 |
| seekMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 跳转模式。 |

## start

```TypeScript
start(): void
```

开始播放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoController-start(): void--><!--Device-VideoController-start(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stop

```TypeScript
stop(): void
```

停止播放，显示当前帧，再次播放时从头开始播放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoController-stop(): void--><!--Device-VideoController-stop(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

