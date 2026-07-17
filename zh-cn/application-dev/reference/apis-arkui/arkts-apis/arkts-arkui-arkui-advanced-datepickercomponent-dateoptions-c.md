# DateOptions

DateOptions定义日期选择器的选项。

继承于[CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)。

**继承/实现关系：** DateOptions extends [CommonOptions](arkts-arkui-arkui-advanced-datepickercomponent-commonoptions-c.md)

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class DateOptions extends CommonOptions--><!--Device-unnamed-export declare class DateOptions extends CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DisplayMode, TimeFormat, DatePickerComponent, DateMode, DatePickerComponentOptions, DatePickerComponentResult } from '@kit.ArkUI';
```

## lunar

```TypeScript
lunar?: boolean
```

指定是否显示为农历。

- true：显示为农历。  
- false：不显示为农历。

默认值：false

**说明**：

仅在简体中文和繁体中文语言环境下生效，其他语言环境下设置该属性无效果。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DateOptions-lunar?: boolean--><!--Device-DateOptions-lunar?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode?: DateMode
```

定义日期选择器的模式。

默认值：DateMode.DATE

**类型：** DateMode

**默认值：** DateMode.DATE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DateOptions-mode?: DateMode--><!--Device-DateOptions-mode?: DateMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

