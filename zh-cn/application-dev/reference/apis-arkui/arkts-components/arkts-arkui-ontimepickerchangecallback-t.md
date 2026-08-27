# OnTimePickerChangeCallback

```TypeScript
declare type OnTimePickerChangeCallback = (result: TimePickerResult) => void
```

选择时间时触发该事件。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [TimePickerResult](arkts-arkui-timepickerresult-i.md) | 是 | 选中的时间结果，hour取值0-23，与展示制式无关。 |
