# TimeOptions

TimeOptions定义时间选择器的选项。

继承于[CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)。

**继承/实现关系：** TimeOptions extends [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class TimeOptions extends CommonOptions--><!--Device-unnamed-export declare class TimeOptions extends CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DisplayMode, TimeFormat, DatePickerComponent, DateMode, DatePickerComponentOptions, DatePickerComponentResult } from '@kit.ArkUI';
```

## format

```TypeScript
format?: TimeFormat
```

定义时间选择器的格式。

默认值：TimeFormat.HOUR_MINUTE

**类型：** TimeFormat

**默认值：** TimeFormat.HOUR_MINUTE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TimeOptions-format?: TimeFormat--><!--Device-TimeOptions-format?: TimeFormat-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## useMilitaryTime

```TypeScript
useMilitaryTime?: boolean
```

指定是否使用24小时制显示时间。

- true：时间以24小时制展示。  
- false：时间以12小时制展示。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TimeOptions-useMilitaryTime?: boolean--><!--Device-TimeOptions-useMilitaryTime?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

