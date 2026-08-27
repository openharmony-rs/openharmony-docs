# OnContentScrollCallback

```TypeScript
declare type OnContentScrollCallback = (totalOffsetX: number, totalOffsetY: number) => void
```

文本内容滚动时，触发该回调。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| totalOffsetX | number | 是 | 文本左上角横坐标相较于整个内容输入区左上角横坐标的偏移量。单位：px。 |
| totalOffsetY | number | 是 | 文本左上角纵坐标相较于整个内容输入区左上角纵坐标的偏移量。单位：px。 |
