# UnitInfo

```TypeScript
export interface UnitInfo
```

Defines the measurement unit information.

**Since:** 8

<!--Device-i18n-export interface UnitInfo--><!--Device-i18n-export interface UnitInfo-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## measureSystem

```TypeScript
measureSystem: string
```

Measurement system. The value can be **SI**, **US**, or **UK**.

**Type:** string

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-UnitInfo-measureSystem: string--><!--Device-UnitInfo-measureSystem: string-End-->

**System capability:** SystemCapability.Global.I18n

## unit

```TypeScript
unit: string
```

Name of the measurement unit, for example, **meter**, **inch**, or **cup**.

**Type:** string

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-UnitInfo-unit: string--><!--Device-UnitInfo-unit: string-End-->

**System capability:** SystemCapability.Global.I18n
