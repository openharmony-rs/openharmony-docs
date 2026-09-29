# EntityInfoItem

```TypeScript
export interface EntityInfoItem
```

Defines a list of entities.

**Since:** 11

<!--Device-i18n-export interface EntityInfoItem--><!--Device-i18n-export interface EntityInfoItem-End-->

**System capability:** SystemCapability.Global.I18n

## Modules to Import

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## begin

```TypeScript
begin: number
```

Start position of the entity in the input string.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-EntityInfoItem-begin: int--><!--Device-EntityInfoItem-begin: int-End-->

**System capability:** SystemCapability.Global.I18n

## end

```TypeScript
end: number
```

End position of the entity the input string.

**Type:** number

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-EntityInfoItem-end: int--><!--Device-EntityInfoItem-end: int-End-->

**System capability:** SystemCapability.Global.I18n

## type

```TypeScript
type: string
```

Entity type. The value can be **phone_number** or **date**. **phone_number** indicates that the entity is a phone number, and **date** indicates that the entity is a date.

**Type:** string

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-EntityInfoItem-type: string--><!--Device-EntityInfoItem-type: string-End-->

**System capability:** SystemCapability.Global.I18n
