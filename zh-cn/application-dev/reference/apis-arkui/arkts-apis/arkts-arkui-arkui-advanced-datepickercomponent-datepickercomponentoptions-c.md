# DatePickerComponentOptions

DatePickerComponentOptions定义日期时间选择器组件的选项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## dateOptions

```TypeScript
dateOptions?: DateOptions
```

日期选项。

**类型：** [DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## displayMode

```TypeScript
displayMode?: DisplayMode
```

选择器的显示模式。

> 默认值：DisplayMode.DATE

> **说明：**
> 
> - DATE：仅显示日期，使用dateOptions，适用于只需要用户选择日期的场景，如生日选择、日程日期设置等。
> - TIME：仅显示时间，使用timeOptions，适用于只需要用户选择时间的场景，如闹钟设置、提醒时间设置等。
> - DATE_TIME：同时显示日期和时间，dateOptions与timeOptions同时生效，适用于需要用户同时选择日期和时间的场景，如日程安排、会议时间设
> 置等。

**类型：** [DisplayMode](arkts-arkui-arkui-advanced-datepickercomponent-displaymode-e.md)

**默认值：** DisplayMode.DATE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeOptions

```TypeScript
timeOptions?: TimeOptions
```

时间选项。

**类型：** [TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
