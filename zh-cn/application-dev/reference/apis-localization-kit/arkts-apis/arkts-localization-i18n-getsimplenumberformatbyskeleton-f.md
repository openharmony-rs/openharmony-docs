# getSimpleNumberFormatBySkeleton

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getSimpleNumberFormatBySkeleton

```TypeScript
export function getSimpleNumberFormatBySkeleton(skeleton: string, locale?: Intl.Locale): SimpleNumberFormat
```

通过框架字符串获取SimpleNumberFormat对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getSimpleNumberFormatBySkeleton(skeleton: string, locale?: Intl.Locale): SimpleNumberFormat--><!--Device-i18n-export function getSimpleNumberFormatBySkeleton(skeleton: string, locale?: Intl.Locale): SimpleNumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| skeleton | string | 是 | 合法的框架字符串，支持的字符及含义请参考[Number Skeletons](https://unicode-org.github.io/icu/userguide/format_parse/numbers/skeletons.html#number-skeletons)。 |
| locale | Intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleNumberFormat](arkts-localization-i18n-simplenumberformat-c.md) | SimpleNumberFormat对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |


## getSimpleNumberFormatBySkeleton

```TypeScript
export function getSimpleNumberFormatBySkeleton(skeleton: string, locale?: intl.Locale): SimpleNumberFormat
```

通过框架字符串获取SimpleNumberFormat对象。

**起始版本：** 18

**废弃版本：** 20

**替代接口：** getSimpleNumberFormatBySkeleton(skeleton:

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-i18n-export function getSimpleNumberFormatBySkeleton(skeleton: string, locale?: intl.Locale): SimpleNumberFormat--><!--Device-i18n-export function getSimpleNumberFormatBySkeleton(skeleton: string, locale?: intl.Locale): SimpleNumberFormat-End-->

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| skeleton | string | 是 | 合法的框架字符串，支持的字符及含义请参考[Number Skeletons](https://unicode-org.github.io/icu/userguide/format_parse/numbers/skeletons.html#number-skeletons)。 |
| locale | intl.Locale | 否 | 区域对象。默认值：系统区域对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimpleNumberFormat](arkts-localization-i18n-simplenumberformat-c.md) | SimpleNumberFormat对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [890001](../errorcode-i18n.md#890001-参数校验错误) | Invalid parameter. Possible causes: Parameter verification failed. |

