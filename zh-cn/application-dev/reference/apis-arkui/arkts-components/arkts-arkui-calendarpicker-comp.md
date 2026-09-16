# CalendarPicker

日历选择器组件，提供下拉日历弹窗，用户可快速选择日期。适用于需要用户选择具体日期的场景，如预订系统、日程安排、日期筛选等，提供直观的日历视图，提升用户日期输入体验。

> **说明：** > > - 该组件从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > - 该组件从API版本26.0.0开始支持WithTheme。

>

## 子组件 > > 无

## CalendarPicker

```TypeScript
CalendarPicker(options?: CalendarOptions)
```

日历选择器。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CalendarOptions](arkts-arkui-calendaroptions-i.md) | 否 | 配置日历选择器组件的参数。未设置该参数时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [CalendarDialogOptions](arkts-arkui-calendardialogoptions-i.md) | 日历选择器弹窗选项。 |
| [CalendarOptions](arkts-arkui-calendaroptions-i.md) | 日历选择器组件的参数说明。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CalendarAlign](arkts-arkui-calendaralign-e.md) | 对齐方式类型。 |

## 示例

```TypeScript
### 示例1（设置下拉日历弹窗）

该示例通过calendarPicker实现了日历选择器组件，提供下拉日历弹窗。


```

```TypeScript
### 示例2（设置开始日期和结束日期）

该示例通过start和end设置日历选择器的开始日期和结束日期。

从API version 18开始，[CalendarOptions](#calendaroptions对象说明)中新增了start、end属性。


```

```TypeScript
### 示例3（设置日历选择器在系统当前日期时，保持高亮显示和禁用日期区间）

该示例通过markToday设置日历选择器在系统当前日期时，开启保持高亮显示，同时，通过disabledDateRange设置日历选择器的禁用日期区间。

从API version 19开始，新增了[markToday](#marktoday19)接口，[CalendarOptions](#calendaroptions对象说明)中新增了disabledDateRange属性。
```
