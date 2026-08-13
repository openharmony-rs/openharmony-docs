# AnimationController

动画控制器对象。包含控制动画播放、停止、恢复、暂停和状态查询等方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface AnimationController--><!--Device-unnamed-export interface AnimationController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getStatus

```TypeScript
getStatus(): AnimationStatus
```

获取当前动图播放的状态。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimationController-getStatus(): AnimationStatus--><!--Device-AnimationController-getStatus(): AnimationStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AnimationStatus | 动图的播放状态。包含4种状态：初始态、播放态、暂停态、停止态。 |

## pause

```TypeScript
pause(): void
```

暂停动图的播放，保持在当前帧。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimationController-pause(): void--><!--Device-AnimationController-pause(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## resume

```TypeScript
resume(): void
```

在当前帧恢复播放动图。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimationController-resume(): void--><!--Device-AnimationController-resume(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start(): void
```

从首帧开始播放。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimationController-start(): void--><!--Device-AnimationController-start(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stop

```TypeScript
stop(): void
```

停止动图的播放并回到首帧。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimationController-stop(): void--><!--Device-AnimationController-stop(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

