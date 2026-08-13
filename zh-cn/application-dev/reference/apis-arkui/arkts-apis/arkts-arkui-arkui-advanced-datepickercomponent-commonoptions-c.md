# CommonOptions

CommonOptions定义日期时间选择器的通用选项。 > **说明：** > > - Date构造函数参数顺序为：年、月索引（0-11）、日、时、分、秒。注意：年份参数需大于99或小于0以避免1900年代映射。 > > - Date的使用请参考TimePickerOptions，需要注意的是，当需要设置1-99的年份日期时， > 不可使用new Date(1, 0, 1)写法，因为JavaScript的new Date(year, month, day)构造函数对1-99的年份有特殊处理，会自动加上1900， > 即变为1901年，因此此时推荐使用new Date('0001-01-01')写法。 > > - DatePickerComponent的文本字号根据显示的总列数变化，当列数大于等于6列时，字号为14vp，其他情况下为16vp，当组件宽度过窄时，可能出现文本 > 显示截断的情况。 > > - 参数缺省或者设置为undefined时，均保持默认值。 > > - 在[DateOptions](arkts-arkui-arkui-advanced-datepickercomponent-dateoptions-c.md#DateOptions)中设置start、end、selected时仅日期部分（年月日）设置生效， > 在[TimeOptions](arkts-arkui-arkui-advanced-datepickercomponent-timeoptions-c.md#TimeOptions)中设置start、end、selected时仅时间部分（时分秒）设置生效。系统会根据配置的displayMode和对应的 > Options类型，自动过滤Date对象的相应部分并应用约束。 > **说明：** > > - onChange在用户选择日期或时间时触发，用于响应用户的选择操作。 > > - onScrollStop在滚动完全停止后触发，无论值是否变化都会返回当前选中项。 > > - 两者可根据需要同时使用或单独使用：onChange用于即时响应用户选择，onScrollStop用于获取滚动停止后的稳定结果。 > **起始日期、结束日期和选中日期的异常情形说明：** > > - 起始日期晚于结束日期，选中日期未设置：起始日期、结束日期和选中日期都为默认值。 > - 起始日期晚于结束日期，选中日期早于起始日期默认值：起始日期、结束日期都为默认值，选中日期为起始日期默认值。 > - 起始日期晚于结束日期，选中日期晚于结束日期默认值：起始日期、结束日期都为默认值，选中日期为结束日期默认值。 > - 起始日期晚于结束日期，选中日期在起始日期与结束日期默认值范围内：起始日期、结束日期都为默认值，选中日期为设置的值。 > - 选中日期早于起始日期：选中日期为起始日期。 > - 选中日期晚于结束日期：选中日期为结束日期。 > - 起始日期晚于当前系统日期，选中日期未设置：选中日期为起始日期。 > - 结束日期早于当前系统日期，选中日期未设置：选中日期为结束日期。 > - Date对象构造参数不符合规范或无效，如年份、月份、日期等参数超出有效范围，或传入无效字符串导致Invalid Date：取默认值。 > - 起始日期或结束日期早于取值范围最小值：起始日期或结束日期取起始日期默认值。 > - 起始日期或结束日期晚于取值范围最大值：起始日期或结束日期取结束日期默认值。 > - 起始日期与结束日期同时早于取值范围最小值：起始日期与结束日期取系统有效范围最早日期。 > - 起始日期与结束日期同时晚于取值范围最大值：起始日期与结束日期取系统有效范围最晚日期。 > **起始时间和结束时间的异常情形说明：** > > - 起始时间晚于结束时间：起始时间、结束时间都为默认值。 > - 选中时间早于起始时间：选中时间为起始时间。 > - 选中时间晚于结束时间：选中时间为结束时间。 > - 起始时间晚于当前系统时间，选中时间未设置：选中时间为起始时间。 > - 结束时间早于当前系统时间，选中时间未设置：选中时间为结束时间。 > - Date对象构造参数不符合规范或无效，如小时、分钟、秒等参数超出有效范围，或传入无效字符串导致Invalid Date：取默认值。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class CommonOptions--><!--Device-unnamed-export declare class CommonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHapticFeedback

```TypeScript
enableHapticFeedback?: boolean
```

设置是否启用触控反馈。 默认值：true - true：启用触控反馈，适用于需要增强用户交互体验的场景，如游戏、乐器类应用等。 - false：不启用触控反馈，适用于不需要触觉反馈或需要节省设备资源的场景。 > **说明：** > > 1. 设置为true后，其生效情况取决于系统的硬件是否支持。 > 2. 启用触控反馈时，需要在工程的[module.json5](../../../quick-start/module-configuration-file.md)中配置 > requestPermissions字段以开启振动权限，配置如下： > > "requestPermissions": [{"name": "ohos.permission.VIBRATE"}]

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-enableHapticFeedback?: boolean--><!--Device-CommonOptions-enableHapticFeedback?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: Date
```

选择器的结束日期或时间。 > 默认值：Date('2100-12-31T23:59:59') > 取值范围：[Date('0001-01-01T00:00:00'), Date('9999-12-31T23:59:59')] > **说明：** > > 设置了end且为有效值的场景下，loop不生效。

**类型：** Date

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-end?: Date--><!--Device-CommonOptions-end?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: boolean
```

设置是否启用循环模式。 - true：启用循环模式，支持滚动到边界时继续循环选择。 - false：不启用循环模式，滚动到边界时停止。 > 默认值：true > **使用场景：** > > 循环模式适用于需要连续滚动选择的场景，如快速浏览年月；非循环模式适用于需要明确边界范围的场景。 > **说明：** > > 设置了[start](#CommonOptions)或[end](#CommonOptions)且为有效值的场景下，本参数不生效。

**类型：** boolean

**默认值：** true

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-loop?: boolean--><!--Device-CommonOptions-loop?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onChange

```TypeScript
onChange?: Callback<DatePickerComponentResult>
```

选择日期或时间后触发该回调。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-onChange?: Callback<DatePickerComponentResult>--><!--Device-CommonOptions-onChange?: Callback<DatePickerComponentResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onScrollStop

```TypeScript
onScrollStop?: Callback<DatePickerComponentResult>
```

选择器项被选中且滚动停止时触发该回调。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DatePickerComponentResult](arkts-arkui-arkui-advanced-datepickercomponent-datepickercomponentresult-c.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-onScrollStop?: Callback<DatePickerComponentResult>--><!--Device-CommonOptions-onScrollStop?: Callback<DatePickerComponentResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selected

```TypeScript
selected?: Date
```

选中的日期或时间，设置后作为初始选中值显示。 > 默认值为当前系统日期或时间。 > **说明：** > > 在DateMode.MONTH_AND_DAY模式下，仅month和day字段参与选择；年份取selected指定值，未指定时取当前系统年份，滚动过程中保持不变。

**类型：** Date

**默认值：** current system date or time

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-selected?: Date--><!--Device-CommonOptions-selected?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: Date
```

选择器的起始日期或时间。 > 默认值：Date('1970-01-01T00:00:00') > 取值范围：[Date('0001-01-01T00:00:00'), Date('9999-12-31T23:59:59')] > **说明：** > > 设置了start且为有效值的场景下，loop不生效。

**类型：** Date

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CommonOptions-start?: Date--><!--Device-CommonOptions-start?: Date-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

