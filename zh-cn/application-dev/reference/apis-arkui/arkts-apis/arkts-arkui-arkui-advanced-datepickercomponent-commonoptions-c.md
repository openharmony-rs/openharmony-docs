# CommonOptions

CommonOptions定义日期时间选择器的通用选项。

> **说明：**  
>  
> - Date的使用请参考  
> [TimePickerOptions](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-timepicker.md#timepickeroptions)。  
>  
> - DatePickerComponent的文本字号根据显示的总列数变化，当列数大于等于6列时，字号为14vp，其他情况下为16vp，当组件宽度过窄时，  
> 可能出现文本显示截断的情况。  
>  
> - 参数缺省或者设置为undefined时，均保持默认值。  
>  
> - 在[DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md)中设置start、end、selected时仅日期部分（年月日）设置生效，  
> 在[TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md)中设置start、end、selected时仅时间部分（时分秒）设置生效。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class CommonOptions--><!--Device-unnamed-export declare class CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { DisplayMode, TimeFormat, DatePickerComponent, DateMode, DatePickerComponentOptions, DatePickerComponentResult } from '@kit.ArkUI';
```

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

启用或禁用触控反馈。

默认值：true

- true：开启触控反馈。  
- false：不开启触控反馈。

**说明**：

1. 设置为true后，其生效情况取决于系统的硬件是否支持。2. 开启触控反馈时，需要在工程的[module.json5](docroot://quick-start/module-configuration-file.md)中配置requestPermissions字段以开启振动权限，配置如下：

"requestPermissions": [{"name": "ohos.permission.VIBRATE"}]

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-enableHapticFeedback?: boolean--><!--Device-CommonOptions-enableHapticFeedback?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

选择器的结束日期或时间。

默认值：Date(2100, 12, 31, 23, 59, 59)

取值范围：[Date(0, 0, 1, 0, 0, 0), Date(10000, 11, 31,23, 59, 59)]

**说明：**

设置了end且为有效值的场景下，loop不生效。

**类型：** Date

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-end?: Date--><!--Device-CommonOptions-end?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: boolean
```

设置是否启用循环模式。

- true：启用循环模式。  
- false：不启用循环模式。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-loop?: boolean--><!--Device-CommonOptions-loop?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<DatePickerComponentResult>
```

选择日期或时间后触发该回调。

**类型：** Callback&lt;DatePickerComponentResult&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-onChange?: Callback<DatePickerComponentResult>--><!--Device-CommonOptions-onChange?: Callback<DatePickerComponentResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onScrollStop

```TypeScript
onScrollStop?: Callback<DatePickerComponentResult>
```

选择器项被选中且滚动停止时触发该回调。

**类型：** Callback&lt;DatePickerComponentResult&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-onScrollStop?: Callback<DatePickerComponentResult>--><!--Device-CommonOptions-onScrollStop?: Callback<DatePickerComponentResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

选中的日期。默认值为当前系统日期或时间。

**类型：** Date

**默认值：** current system date or time

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-selected?: Date--><!--Device-CommonOptions-selected?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

选择器的起始日期或时间。

默认值：Date(1970, 0, 1, 0, 0, 0)

取值范围：[Date(0, 0, 1, 0, 0, 0), Date(10000, 11, 31,23, 59, 59)]

**说明：**

设置了start且为有效值的场景下，loop不生效。

**类型：** Date

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-start?: Date--><!--Device-CommonOptions-start?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

