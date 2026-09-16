# MenuOnAppearCallback

```TypeScript
declare type MenuOnAppearCallback = (start: number, end: number) => void
```

自定义选择菜单弹出时触发的回调事件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | 选中内容的起始位置。 |
| end | number | 是 | 选中内容的终止位置，选中范围为[start, end)，结束位置对应的内容不包含在内。 |
