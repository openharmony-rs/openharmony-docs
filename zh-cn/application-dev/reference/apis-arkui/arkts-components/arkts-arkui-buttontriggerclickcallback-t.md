# ButtonTriggerClickCallback

```TypeScript
declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void
```

定义ButtonConfiguration中使用的回调类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void--><!--Device-unnamed-declare type ButtonTriggerClickCallback = (xPos: number, yPos: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| xPos | number | 是 | 点击位置x的坐标。<br/>单位：vp |
| yPos | number | 是 | 点击位置y的坐标。<br/>单位：vp |

