# UpdateTransitionCallback

```TypeScript
export type UpdateTransitionCallback = (progress: double) => void
```

交互转场动画进度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type UpdateTransitionCallback = (progress: double) => void--><!--Device-unnamed-export type UpdateTransitionCallback = (progress: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| progress | double | 是 | 设置交互转场动画进度百分比。 取值范围：[0,1]  |

