# ButtonTriggerClickCallback

```TypeScript
export type ButtonTriggerClickCallback = (xPos: double, yPos: double) => void
```

定义ButtonConfiguration中使用的回调类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ButtonTriggerClickCallback = (xPos: double, yPos: double) => void--><!--Device-unnamed-export type ButtonTriggerClickCallback = (xPos: double, yPos: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xPos | double | 是 | 点击位置x的坐标。<br/>单位：vp |
| yPos | double | 是 | 点击位置y的坐标。<br/>单位：vp |

