# FrameCallback

Class FrameCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class FrameCallback--><!--Device-unnamed-export declare abstract class FrameCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## onFrame

```TypeScript
onFrame(frameTimeInNano: long): void
```

Call when a new display frame is being rendered.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameCallback-onFrame(frameTimeInNano: long): void--><!--Device-FrameCallback-onFrame(frameTimeInNano: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| frameTimeInNano | long | 是 | The frame time in nanoseconds. |

## onIdle

```TypeScript
onIdle(timeLeftInNano: long): void
```

在下一帧空闲时回调。如果没有下一帧，会自动请求一帧。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameCallback-onIdle(timeLeftInNano: long): void--><!--Device-FrameCallback-onIdle(timeLeftInNano: long): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeLeftInNano | long | 是 | The remaining time from the deadline for this frame. |

