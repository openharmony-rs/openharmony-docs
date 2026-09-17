# EntityInfoItem

Defines a list of entities.

**Since:** 11

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

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## end

```TypeScript
end: number
```

End position of the entity the input string.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n

## type

```TypeScript
type: string
```

Entity type. The value can be **phone_number** or **date**. **phone_number** indicates that the entity is a phone number, and **date** indicates that the entity is a date.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.I18n
