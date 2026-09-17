# getInstance

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getInstance

```TypeScript
export function getInstance(locale?:string): IndexUtil
```

Creates an **IndexUtil** object.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | No | [System locale](../../../internationalization/i18n-locale-culture.md#how-it-works), which consists of the language, script, and country/region. The default value is the current system locale. |

**Return value:**

| Type | Description |
| --- | --- |
| [IndexUtil](arkts-localization-i18n-indexutil-c.md) | **IndexUtil** object created based on the specified locale ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
```
