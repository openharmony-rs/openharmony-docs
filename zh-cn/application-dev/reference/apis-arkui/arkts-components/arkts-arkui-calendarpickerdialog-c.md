# CalendarPickerDialog

点击日期弹出日历选择器弹窗，可在弹窗内选择日期。

**起始版本：** 10

<!--Device-unnamed-declare class CalendarPickerDialog--><!--Device-unnamed-declare class CalendarPickerDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## show

```TypeScript
static show(options?: CalendarDialogOptions): void
```

定义日历选择器弹窗。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CalendarPickerDialog-static show(options?: CalendarDialogOptions): void--><!--Device-CalendarPickerDialog-static show(options?: CalendarDialogOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CalendarDialogOptions](arkts-arkui-calendardialogoptions-i.md) | 否 | 配置日历选择器弹窗参数。参数缺省时无法弹出弹窗。 |

