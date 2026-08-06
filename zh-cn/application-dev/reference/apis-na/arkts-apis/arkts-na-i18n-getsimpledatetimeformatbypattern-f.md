# getSimpleDateTimeFormatByPattern

## getSimpleDateTimeFormatByPattern

```TypeScript
export function getSimpleDateTimeFormatByPattern(pattern: string, locale?: Intl.Locale): SimpleDateTimeFormat
```

通过模式字符串获取SimpleDateTimeFormat对象。与[getSimpleDateTimeFormatBySkeleton]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接 口获取的对象在格式化后显示差异请参考[SimpleDateTimeFormat.format]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的示例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getSimpleDateTimeFormatByPattern(pattern: string, locale?: Intl.Locale): SimpleDateTimeFormat--><!--Device-i18n-export function getSimpleDateTimeFormatByPattern(pattern: string, locale?: Intl.Locale): SimpleDateTimeFormat-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pattern | string | 是 | 合法的模式字符串，支持\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中Field Patterns值的自由组合。同时，pattern支持传入自定义文本，文本内容以\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_标识。 |
| locale | Intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | SimpleDateTimeFormat对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../../apis-localization-kit/errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

