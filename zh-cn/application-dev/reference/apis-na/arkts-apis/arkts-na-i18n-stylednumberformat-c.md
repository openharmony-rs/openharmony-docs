# StyledNumberFormat

提供富文本数字格式化的能力。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-i18n-export class StyledNumberFormat--><!--Device-i18n-export class StyledNumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

## constructor

```TypeScript
constructor(numberFormat: Intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)
```

创建需要富文本显示的数字格式化的对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-StyledNumberFormat-constructor(numberFormat: Intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)--><!--Device-StyledNumberFormat-constructor(numberFormat: Intl.NumberFormat | SimpleNumberFormat, options?: StyledNumberFormatOptions)-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| numberFormat | Intl.NumberFormat \| [SimpleNumberFormat](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-simplenumberformat-c.md) | 是 | 用于格式化数字的对象。 |
| options | [StyledNumberFormatOptions](../../apis-localization-kit/arkts-apis/arkts-localization-i18n-stylednumberformatoptions-i.md) | 否 | 指定数字格式化对象的配置项。默认值：默认的文本样式。 |

## format

```TypeScript
format(value: double): StyledString
```

使用数字格式化对象对数字进行格式化，返回富文本对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-StyledNumberFormat-format(value: double): StyledString--><!--Device-StyledNumberFormat-format(value: double): StyledString-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | 需要格式化的数字。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](../../apis-arkui/arkts-apis/arkts-arkui-styledstring-styledstring-c.md) | 格式化后的富文本对象。 |

