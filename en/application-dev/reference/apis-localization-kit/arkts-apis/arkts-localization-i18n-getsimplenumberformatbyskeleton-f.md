# getSimpleNumberFormatBySkeleton

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getSimpleNumberFormatBySkeleton

```TypeScript
export function getSimpleNumberFormatBySkeleton(skeleton: string, locale?: Intl.Locale): SimpleNumberFormat
```

Obtains a **SimpleNumberFormat** object based on the specified skeleton.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| skeleton | string | Yes | Valid skeleton. For details about the supported characters and their meanings, see [Number Skeletons](https://unicode-org.github.io/icu/userguide/format_parse/numbers/skeletons.html#number-skeletons). |
| locale | [Intl.Locale](arkts-localization-intl-locale-c.md) | No | **Locale** object. The default value is the current system locale. |

**Return value:**

| Type | Description |
| --- | --- |
| [SimpleNumberFormat](arkts-localization-i18n-simplenumberformat-c.md) | **SimpleNumberFormat** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [8900001](../errorcode-i18n.md#8900001-parameter-verification-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n } from '@kit.LocalizationKit';

try {
  let locale: Intl.Locale = new Intl.Locale('zh-Hans-CN');
  let formatter: i18n.SimpleNumberFormat = i18n.getSimpleNumberFormatBySkeleton('%', locale);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call SimpleDateTimeFormat.getSimpleNumberFormatBySkeleton failed, error code: ${err.code}, message: ${err.message}.`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { i18n, intl } from '@kit.LocalizationKit';

try {
  let locale: intl.Locale = new intl.Locale('zh-Hans-CN');
  let formatter: i18n.SimpleNumberFormat = i18n.getSimpleNumberFormatBySkeleton('%', locale);
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`call SimpleDateTimeFormat.getSimpleNumberFormatBySkeleton failed, error code: ${err.code}, message: ${err.message}.`);
}
```


## getSimpleNumberFormatBySkeleton

```TypeScript
export function getSimpleNumberFormatBySkeleton(skeleton: string, locale?: intl.Locale): SimpleNumberFormat
```

Obtains a **SimpleNumberFormat** object based on the specified skeleton.

**Since:** 18

**Deprecated since:** 20

**Substitutes:** [getSimpleNumberFormatBySkeleton](arkts-localization-i18n-getsimplenumberformatbyskeleton-f.md)(skeleton: string, locale?: Intl.Locale)

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| skeleton | string | Yes | Valid skeleton. For details about the supported characters and their meanings, see [Number Skeletons](https://unicode-org.github.io/icu/userguide/format_parse/numbers/skeletons.html#number-skeletons). |
| locale | [intl.Locale](arkts-localization-intl-locale-c.md) | No | **Locale** object. The default value is the current system locale. |

**Return value:**

| Type | Description |
| --- | --- |
| [SimpleNumberFormat](arkts-localization-i18n-simplenumberformat-c.md) | **SimpleNumberFormat** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [890001](../errorcode-i18n.md#890001-parameter-error) | Invalid parameter. Possible causes: Parameter verification failed. |

**Examples**

See [getSimpleNumberFormatBySkeleton](#getsimplenumberformatbyskeleton)
