# DatePickerComponent
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

DatePickerComponent组件用于选择日期（年月日）和时间（时分秒）。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 该组件接口仅可在Stage模型下使用。

**起始版本：** 26.0.0

## 导入模块

ArkTS-Dyn示例：

```ts
import { DatePickerComponent, DatePickerComponentOptions, DisplayMode, DateMode, TimeFormat, DatePickerComponentResult } from '@kit.ArkUI';
```

ArkTS-Sta示例：

```ts
import {
  DatePickerComponent,
  DatePickerComponentOptions,
  DisplayMode,
  DateMode,
  TimeFormat,
  DatePickerComponentResult,
  CommonOptions,
  DateOptions,
  TimeOptions
} from '@ohos.arkui.advanced.DatePickerComponent';
```

## 子组件

无

## DatePickerComponent

DatePickerComponent({ options: DatePickerComponentOptions })

定义日期时间选择器组件。

**装饰器类型：** @Component

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 必填 | 装饰器类型 | 说明 |
| ---- | ---- | ---- | ---------- | ---- |
| options | [DatePickerComponentOptions](#datepickercomponentoptions) | 是 | ArkTS-Dyn: @Prop<br>ArkTS-Sta: @PropRef | 定义日期时间选择器组件的选项。 |

## DatePickerComponentOptions

DatePickerComponentOptions定义日期时间选择器组件的选项。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| displayMode | [DisplayMode](#displaymode) | 否 | 是 | 选择器的显示模式。<br/>默认值：DisplayMode.DATE |
| dateOptions | [DateOptions](#dateoptions) | 否 | 是 | 日期选项。 |
| timeOptions | [TimeOptions](#timeoptions) | 否 | 是 | 时间选项。 |

## DisplayMode

DisplayMode枚举用于定义选择器的显示模式。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 值 | 说明 |
| ---- | -- | ---- |
| DATE | 0 | 仅显示日期。 |
| TIME | 1 | 仅显示时间。 |
| DATE_TIME | 2 | 同时显示日期和时间。 |

## DateMode

DateMode枚举用于定义日期选择器的模式。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 值 | 说明 |
| ---- | -- | ---- |
| DATE | 0 | 日期显示三列：年、月、日。 |
| YEAR_AND_MONTH | 1 | 日期显示两列：年、月。 |
| MONTH_AND_DAY | 2 | 定义以月和日显示日期的模式。在此模式下，当月份从12月变为1月时，年份不会增加；当月份从1月变为12月时，年份不会减少。年份保持当前设置的值不变。 |

## TimeFormat

TimeFormat枚举用于定义时间选择器的格式。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 值 | 说明 |
| ---- | -- | ---- |
| HOUR_MINUTE | 0 | 显示时、分。 |
| HOUR_MINUTE_SECOND | 1 | 显示时、分、秒。 |

## DatePickerComponentResult

DatePickerComponentResult定义日期时间选择器的选择结果。

> **说明：**
>
> 从API版本26.1.0开始，当[hideYear](#dateoptions)为true时，若用户选择“----”，year返回undefined；若选择具体年份，year为所选具体年份。农历模式下，若用户选择“----”，year同样返回undefined，返回的月、日为农历值；若选择具体年份，则依然返回对应年、月、日的公历值。当[hideYear](#dateoptions)为false时，年、月、日固定返回公历值。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| year | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 是 | 所选日期的年份。<br>当[hideYear](#dateoptions)为true且用户选择“----”时，year返回undefined；当选择具体年份时，值为所选具体年份。 |
| month | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 是 | 所选日期的月份索引，从0开始，0表示1月，11表示12月。 |
| day | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 是 | 所选日期的日。 |
| hour | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 是 | 所选时间的小时部分。 |
| minute | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 是 | 所选时间的分钟部分。 |
| second | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否 | 是 | 所选时间的秒部分。 |

## CommonOptions

CommonOptions定义日期时间选择器的通用选项。

>  **说明：**
>
> - Date的使用请参考[TimePickerOptions](ts-basic-components-timepicker.md#timepickeroptions对象说明)。
> - DatePickerComponent的字体字号在14vp至16vp范围内自适应变化，当组件宽度过窄时，可能出现文本显示截断的情况。
> - 参数缺省或者设置为undefined时，均保持默认值。
> - 在[DateOptions](#dateoptions)中设置start、end、selected时仅日期部分（年月日）设置生效，在[TimeOptions](#timeoptions)中设置start、end、selected时仅时间部分（时分秒）设置生效。
> - [extendSelected](#commonoptions)优先级高于[selected](#commonoptions)，从API版本26.1.0开始，当两者同时设置时，selected不生效。extendSelected支持传入[DatePickerComponentResult](#datepickercomponentresult)以回传上次选择结果，适用于跨组件重建恢复选择状态的场景（如页面跳转后恢复用户上次选择的日期时间）。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| start | Date | 否 | 是 | 选择器的起始日期或时间。<br/>默认值：Date(1970, 0, 1, 0, 0, 0)<br/>取值范围：\[Date(0, 0, 1, 0, 0, 0), Date(10000, 11, 31,23, 59, 59)] |
| end | Date | 否 | 是 | 选择器的结束日期或时间。<br/>默认值：Date(2100, 12, 31, 23, 59, 59)<br/>取值范围：\[Date(0, 0, 1, 0, 0, 0), Date(10000, 11, 31,23, 59, 59)] |
| selected | Date | 否 | 是 | 选中的日期。<br/>默认值为当前系统日期或时间。<br/>从API版本26.1.0开始，当与[extendSelected](#commonoptions)同时设置时，selected不生效。 |
| extendSelected |  Date \| [DatePickerComponentResult](#datepickercomponentresult) | 否 | 是 | 选中的日期或时间，设置后作为初始选中值显示。<br>**优先级高于[selected](#commonoptions)**：当两者同时设置时，selected不生效。<br>默认值为当前系统日期或时间。<br>**说明：**<br>从API版本26.1.0开始，新增该参数。该参数支持传入[DatePickerComponentResult](#datepickercomponentresult)，用于回传[onChange](#commonoptions)或[onScrollStop](#commonoptions)回调收到的选择结果以恢复上次选择状态：<br>- 传入Date时，行为与selected一致。<br>- 传入DatePickerComponentResult时，每个已设置字段生效，未设置字段取系统默认对应部分（字段级默认）。例如传入`{hour: 10, minute: 30}`（second未设置），时、分生效，秒取系统默认值。<br>- 当[hideYear](#dateoptions)为true且year为undefined时，年份列选中“----”，忽略year，仅采用month/day。<br>- 当传入的日期或时间为非法值时，回退到系统默认日期。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。<br>**ArkTS-Dyn起始版本：** 26.1.0<br>**ArkTS-Sta起始版本：** 26.1.0 |
| loop | boolean | 否 | 是 | 设置是否启用循环模式。<br/>- true：启用循环模式。<br/>- false：不启用循环模式。<br/>默认值：true |
| onChange | [Callback](ts-types.md#callback12)<[DatePickerComponentResult](#datepickercomponentresult)> | 否 | 是 | 选择日期或时间后触发该回调。 |
| onScrollStop | [Callback](ts-types.md#callback12)<[DatePickerComponentResult](#datepickercomponentresult)> | 否 | 是 | 选择器项被选中且滚动停止时触发该回调。 |
| enableHapticFeedback | boolean | 否 | 是 | 启用或禁用触控反馈。<br/>默认值：true<br/>- true：开启触控反馈。<br/>- false：不开启触控反馈。<br />**说明**：<br/>1. 设置为true后，其生效情况取决于系统的硬件是否支持。<br/>2. 开启触控反馈时，需要在工程的[module.json5](../../../quick-start/module-configuration-file.md)中配置requestPermissions字段以开启振动权限，配置如下：<br />"requestPermissions": [{"name": "ohos.permission.VIBRATE"}] |


**起始日期、结束日期和选中日期的异常情形说明：**

| 异常情形   | 对应结果  |
| -------- |  ------------------------------------------------------------ |
| 起始日期晚于结束日期，选中日期未设置。    | 起始日期、结束日期和选中日期都为默认值。 |
| 起始日期晚于结束日期，选中日期早于起始日期默认值。    | 起始日期、结束日期都为默认值，选中日期为起始日期默认值。  |
| 起始日期晚于结束日期，选中日期晚于结束日期默认值。    | 起始日期、结束日期都为默认值，选中日期为结束日期默认值。  |
| 起始日期晚于结束日期，选中日期在起始日期与结束日期默认值范围内。    | 起始日期、结束日期都为默认值，选中日期为设置的值。 |
| 选中日期早于起始日期。    | 选中日期为起始日期。  |
| 选中日期晚于结束日期。    | 选中日期为结束日期。  |
| 起始日期晚于当前系统日期，选中日期未设置。    | 选中日期为起始日期。  |
| 结束日期早于当前系统日期，选中日期未设置。    | 选中日期为结束日期。  |
| 日期格式不符合规范，如‘1999-13-32’。   | 取默认值。  |
| 起始日期或结束日期早于取值范围最小值。    | 起始日期或结束日期取起始日期默认值。 |
| 起始日期或结束日期晚于取值范围最大值。    | 起始日期或结束日期取结束日期默认值。 |
| 起始日期与结束日期同时早于取值范围最小值。 | 起始日期与结束日期取系统有效范围最早日期。 |
| 起始日期与结束日期同时晚于取值范围最大值。 | 起始日期与结束日期取系统有效范围最晚日期。 |

**起始时间和结束时间的异常情形说明：**

| 异常情形   | 对应结果  |
| -------- |  ------------------------------------------------------------ |
| 起始时间晚于结束时间。    | 起始时间、结束时间都为默认值。  |
| 选中时间早于起始时间。   | 选中时间为起始时间。  |
| 选中时间晚于结束时间。    | 选中时间为结束时间。  |
| 起始时间晚于当前系统时间，选中时间未设置。    | 选中时间为起始时间。 |
| 结束时间早于当前系统时间，选中时间未设置。    | 选中时间为结束时间。  |
| 时间格式不符合规范，如'01:61:61'。   | 取默认值。  |

## DateOptions

DateOptions定义日期选择器的选项。

继承于[CommonOptions](#commonoptions)。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| mode | [DateMode](#datemode) | 否 | 是 | 定义日期选择器的模式。<br/>默认值：DateMode.DATE |
| lunar | boolean | 否 | 是 | 指定是否显示农历。<br/>- true：显示为农历。<br/>- false：不显示为农历。<br/>默认值：false<br />**说明**：<br/>仅在简体中文和繁体中文语言环境下生效，其他语言环境下设置该属性无效果。 |
| hideYear | boolean | 否 | 是 | 是否启用“隐藏年份”选项。<br/>- true：在[end](#commonoptions)后面追加一个“----”选项。用户可以选择“----”表示不关心具体年份，适用于生日、纪念日等无需具体年份的场景。<br/>- false：不显示“----”选项。年份列仅展示[start](#commonoptions)和[end](#commonoptions)范围内的具体年份。<br/>默认值：false<br/>**说明：**<br/>1. 该属性仅在[displayMode](#datepickercomponentoptions)为DisplayMode.DATE或DisplayMode.DATE_TIME，且[mode](#dateoptions)为DateMode.DATE或DateMode.YEAR_AND_MONTH时生效。<br/>2. 该属性为true时，用户仍可滚动选择具体年份，“----”选项与具体年份可自由切换。<br/>3. 该属性支持运行时动态切换，属性值变化时年份列随之更新。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 26.1.0<br/>**ArkTS-Sta起始版本：** 26.1.0 |

## TimeOptions

TimeOptions定义时间选择器的选项。

继承于[CommonOptions](#commonoptions)。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| format | [TimeFormat](#timeformat) | 否 | 是 | 定义时间选择器的格式。<br/>默认值：TimeFormat.HOUR_MINUTE |
| useMilitaryTime | boolean | 否 | 是 | 指定是否使用24小时制显示时间。<br/>- true：时间以24小时制展示。<br/>- false：时间以12小时制展示。<br/>默认值：false |

## 示例

### 示例1（日期选择器）

该示例通过设置[DatePickerComponentOptions](#datepickercomponentoptions)中的displayMode为DisplayMode.DATE，实现日期选择器。

 从API版本26.0.0开始，新增[DatePickerComponentOptions](#datepickercomponentoptions)参数。

ArkTS-Dyn示例：

```ts
import { DatePickerComponent, DisplayMode, DateMode } from '@kit.ArkUI';

@Entry
@Component
struct DatePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            selected: new Date(),
            start: new Date('2020-01-01'),
            end: new Date('2030-12-31'),
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected date: ' + result.year + '-' + (result.month! + 1) + '-' + result.day);
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + result.year + '-' + (result.month! + 1) + '-' + result.day);
            }
          }
        }
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Component, Column } from '@kit.ArkUI';
import {
  DatePickerComponent,
  DatePickerComponentOptions,
  DisplayMode,
  DateMode,
  TimeFormat,
  DatePickerComponentResult,
  CommonOptions,
  DateOptions,
  TimeOptions
} from '@ohos.arkui.advanced.DatePickerComponent';

@Entry
@Component
struct DatePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            selected: new Date(),
            start: new Date('2020-01-01'),
            end: new Date('2030-12-31'),
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected date: ' + result.year + '-' + (result.month! + 1) + '-' + result.day);
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + result.year + '-' + (result.month! + 1) + '-' + result.day);
            }
          } as DateOptions
        } as DatePickerComponentOptions
      })
    }
  }
}
```

![date](figures/DatePickerComponent1.gif)

### 示例2（时间选择器）

该示例通过设置[DatePickerComponentOptions](#datepickercomponentoptions)中的displayMode为DisplayMode.TIME，实现时间选择器。

 从API版本26.0.0开始，新增[DatePickerComponentOptions](#datepickercomponentoptions)参数。

ArkTS-Dyn示例：

```ts
import { DatePickerComponent, DisplayMode, TimeFormat } from '@kit.ArkUI';

@Entry
@Component
struct TimePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.TIME,
          timeOptions: {
            format: TimeFormat.HOUR_MINUTE,
            useMilitaryTime: true,
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected time: ' + result.hour + ':' + result.minute);
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + result.hour + ':' + result.minute);
            }
          }
        }
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Component, Column } from '@kit.ArkUI';
import {
  DatePickerComponent,
  DatePickerComponentOptions,
  DisplayMode,
  DateMode,
  TimeFormat,
  DatePickerComponentResult,
  CommonOptions,
  DateOptions,
  TimeOptions
} from '@ohos.arkui.advanced.DatePickerComponent';

@Entry
@Component
struct TimePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.TIME,
          timeOptions: {
            format: TimeFormat.HOUR_MINUTE,
            useMilitaryTime: true,
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected time: ' + result.hour + ':' + result.minute);
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + result.hour + ':' + result.minute);
            }
          } as TimeOptions
        } as DatePickerComponentOptions
      })
    }
  }
}
```

![time](figures/DatePickerComponent2.gif)

### 示例3（日期时间选择器）

该示例通过设置[DatePickerComponentOptions](#datepickercomponentoptions)中的displayMode为DisplayMode.DATE_TIME，同时选择日期和时间。

 从API版本26.0.0开始，新增[DatePickerComponentOptions](#datepickercomponentoptions)参数。

ArkTS-Dyn示例：

```ts
import { DatePickerComponent, DisplayMode, DateMode, TimeFormat } from '@kit.ArkUI';

@Entry
@Component
struct DateTimePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE_TIME,
          dateOptions: {
            mode: DateMode.DATE,
            lunar: false,
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected: ' + JSON.stringify(result));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + JSON.stringify(result));
            }
          },
          timeOptions: {
            format: TimeFormat.HOUR_MINUTE_SECOND,
            useMilitaryTime: false,
            onChange: (result) => {
              console.info('Selected: ' + JSON.stringify(result));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + JSON.stringify(result));
            }
          }
        }
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Component, Column } from '@kit.ArkUI';
import {
  DatePickerComponent,
  DatePickerComponentOptions,
  DisplayMode,
  DateMode,
  TimeFormat,
  DatePickerComponentResult,
  CommonOptions,
  DateOptions,
  TimeOptions
} from '@ohos.arkui.advanced.DatePickerComponent';

@Entry
@Component
struct DateTimePickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE_TIME,
          dateOptions: {
            mode: DateMode.DATE,
            lunar: false,
            enableHapticFeedback: true,
            onChange: (result) => {
              console.info('Selected: ' + JSON.stringify(result));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + JSON.stringify(result));
            }
          } as DateOptions,
          timeOptions: {
            format: TimeFormat.HOUR_MINUTE_SECOND,
            useMilitaryTime: false,
            onChange: (result) => {
              console.info('Selected: ' + JSON.stringify(result));
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: ' + JSON.stringify(result));
            }
          } as TimeOptions
        } as DatePickerComponentOptions
      })
    }
  }
}
```

![datetime](figures/DatePickerComponent3.gif)

### 示例4（关闭循环模式）

该示例通过设置[DateOptions](#dateoptions)中的loop为false，关闭选择器的循环滚动模式。

从API版本26.0.0开始，新增[DateOptions](#dateoptions)参数。

ArkTS-Dyn示例：

```ts
import { DatePickerComponent, DisplayMode, DateMode } from '@kit.ArkUI';

@Entry
@Component
struct NoLoopPickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            selected: new Date(),
            start: new Date('2020-01-01'),
            end: new Date('2030-12-31'),
            loop: false,
            onChange: (result) => {
              console.info('Selected date: ' + result.year + '-' + (result.month! + 1) + '-' + result.day);
            }
          }
        }
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Component, Column } from '@kit.ArkUI';
import {
  DatePickerComponent,
  DatePickerComponentOptions,
  DisplayMode,
  DateMode,
  TimeFormat,
  DatePickerComponentResult,
  CommonOptions,
  DateOptions,
  TimeOptions
} from '@ohos.arkui.advanced.DatePickerComponent';

@Entry
@Component
struct NoLoopPickerExample {
  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            selected: new Date(),
            start: new Date('2020-01-01'),
            end: new Date('2030-12-31'),
            loop: false,
            onChange: (result) => {
              console.info('Selected date: ' + result.year + '-' + (result.month! + 1) + '-' + result.day);
            }
          } as DateOptions
        } as DatePickerComponentOptions
      })
    }
  }
}
```

![loop](figures/DatePickerComponent4.gif)

### 示例5（隐藏年份选项与回传结果）

该示例通过[DateOptions](#dateoptions)中的hideYear参数启用“----”选项，并通过[CommonOptions](#commonoptions)中的extendSelected参数回传上次选择结果（含“----”选择）以恢复选择状态。

从API版本26.1.0开始，[DateOptions](#dateoptions)新增hideYear参数，[CommonOptions](#commonoptions)新增extendSelected参数。

ArkTS-Dyn示例：

```ts
import { DatePickerComponent, DisplayMode, DateMode, DatePickerComponentResult } from '@kit.ArkUI';

@Entry
@Component
struct HideYearAndExtendSelectedExample {
  // 保存上次选择结果，用于回传
  @State lastResult: DatePickerComponentResult = { year: undefined, month: 10, day: 20 };

  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            start: new Date('2020-01-01'),
            end: new Date('2030-12-31'),
            hideYear: true,
            // extendSelected优先于selected；传入上次结果恢复选择状态
            extendSelected: this.lastResult,
            onChange: (result) => {
              this.lastResult = result
              console.info('Selected: year=' + (result.year ?? '----') +
                ', month=' + (result.month ?? 0) + ', day=' + (result.day ?? 0))
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: year=' + (result.year ?? '----') +
                ', month=' + (result.month ?? 0) + ', day=' + (result.day ?? 0))
            }
          }
        }
      })
    }
  }
}
```

ArkTS-Sta示例：

```ts
import { Entry, Component, Column } from '@kit.ArkUI';
import { State } from '@ohos.arkui.stateManagement';
import {
  DatePickerComponent,
  DatePickerComponentOptions,
  DisplayMode,
  DateMode,
  TimeFormat,
  DatePickerComponentResult,
  CommonOptions,
  DateOptions,
  TimeOptions
} from '@ohos.arkui.advanced.DatePickerComponent';

@Entry
@Component
struct HideYearAndExtendSelectedExample {
  // 保存上次选择结果，用于回传
  @State lastResult: DatePickerComponentResult = { year: undefined, month: 10, day: 20 } as DatePickerComponentResult;

  build() {
    Column() {
      DatePickerComponent({
        options: {
          displayMode: DisplayMode.DATE,
          dateOptions: {
            mode: DateMode.DATE,
            start: new Date('2020-01-01'),
            end: new Date('2030-12-31'),
            hideYear: true,
            // extendSelected优先于selected；传入上次结果恢复选择状态
            extendSelected: this.lastResult,
            onChange: (result) => {
              this.lastResult = result
              console.info('Selected: year=' + (result.year == undefined ? '----' : result.year) +
                ', month=' + result.month! + ', day=' + result.day!)
            },
            onScrollStop: (result) => {
              console.info('Scroll stop: year=' + (result.year == undefined ? '----' : result.year) +
                ', month=' + result.month! + ', day=' + result.day!)
            }
          } as DateOptions
        } as DatePickerComponentOptions
      })
    }
  }
}
```

![hideyear](figures/datepickercomponenthideyear.gif)
