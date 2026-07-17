# set24HourClock

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## set24HourClock

```TypeScript
export function set24HourClock(option: boolean): boolean
```

修改系统时间的24小时制设置。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [set24HourClock](arkts-localization-i18n-system-c-sys.md#set24hourclock-1)

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-i18n-export function set24HourClock(option: boolean): boolean--><!--Device-i18n-export function set24HourClock(option: boolean): boolean-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | boolean | 是 | true表示开启系统24小时制开关，false表示关闭系统24小时制开关。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示修改成功，false表示修改失败。 |

