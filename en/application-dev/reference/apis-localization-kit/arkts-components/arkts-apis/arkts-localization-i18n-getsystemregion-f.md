# getSystemRegion

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## getSystemRegion

```TypeScript
export function getSystemRegion(): string
```

Obtains the system region.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getSystemRegion](arkts-localization-i18n-system-c.md#getsystemregion)

**System capability:** SystemCapability.Global.I18n

**Return value:**

| Type | Description |
| --- | --- |
| string | System region ID. |

**Examples**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

let region: string = i18n.getSystemRegion();
```
