# MenuCallback

```TypeScript
declare type MenuCallback = (start: number, end: number) => void
```

自定义选择菜单显示或隐藏时触发的回调事件。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type MenuCallback = (start: number, end: number) => void--><!--Device-unnamed-declare type MenuCallback = (start: number, end: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 选中内容的起始位置。 |
| end | number | 是 | 选中内容的终止位置。 |

