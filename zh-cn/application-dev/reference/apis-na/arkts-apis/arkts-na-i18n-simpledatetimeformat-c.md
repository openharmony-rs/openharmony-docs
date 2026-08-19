# SimpleDateTimeFormat

提供时间日期格式化的能力。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-i18n-export class SimpleDateTimeFormat--><!--Device-i18n-export class SimpleDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
```

## format

```TypeScript
format(date: Date): string
```

对时间日期进行格式化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SimpleDateTimeFormat-format(date: Date): string--><!--Device-SimpleDateTimeFormat-format(date: Date): string-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | Date | 是 | 时间日期。 <br>**说明：** <br>月份从0开始计数，0表示一月。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 格式化后的时间日期字符串。 |

