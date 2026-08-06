# OnContentScrollCallback

```TypeScript
export type OnContentScrollCallback = (totalOffsetX: double, totalOffsetY: double) => void
```

文本内容滚动回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnContentScrollCallback = (totalOffsetX: double, totalOffsetY: double) => void--><!--Device-unnamed-export type OnContentScrollCallback = (totalOffsetX: double, totalOffsetY: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| totalOffsetX | double | 是 | 文本在内容区的横坐标偏移，单位px。  |
| totalOffsetY | double | 是 | 文本在内容区的纵坐标偏移，单位px。  |

