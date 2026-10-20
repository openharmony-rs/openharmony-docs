# Currency

```TypeScript
export class Currency
```

Provides currency management capabilities, such as obtaining ISO 4217 currency codes.

**Since:** 26.2.0

<!--Device-i18n-export class Currency--><!--Device-i18n-export class Currency-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getISO4217Code

```TypeScript
getISO4217Code(): string
```

Obtains currency ISO 4217 code of this **Currency** object.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-Currency-getISO4217Code(): string--><!--Device-Currency-getISO4217Code(): string-End-->

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | ISO 4217 three-letter currency code. For example, the default currency of the US is USD. The default currency of China is CNY. |
