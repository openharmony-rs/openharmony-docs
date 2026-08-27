# TimeOptions

TimeOptions定义时间选择器的选项。继承于[CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)。

> **说明：**
> 
> 若设置了start或end参数且为有效值，loop参数将不生效，具体请参考[CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)的参数说明。

**继承/实现关系：** TimeOptions extends [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

## format

```TypeScript
format?: TimeFormat
```

定义时间选择器的格式。默认值：TimeFormat.HOUR_MINUTE

**类型：** [TimeFormat](arkts-arkui-arkui-advanced-datepickercomponent-timeformat-e.md)

**默认值：** TimeFormat.HOUR_MINUTE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useMilitaryTime

```TypeScript
useMilitaryTime?: boolean
```

指定是否使用24小时制显示时间。  
- true：时间以24小时制展示，适用于国际化应用、需要精确时间表达的专业场景（如医疗、交通、军事等）。  
- false：时间以12小时制展示，适用于面向普通用户的日常应用场景，更符合用户的日常阅读习惯。  
默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
