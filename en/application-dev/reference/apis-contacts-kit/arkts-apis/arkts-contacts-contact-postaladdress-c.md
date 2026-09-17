# PostalAddress

Defines a contact's postal address.

**Since:** 7

**System capability:** SystemCapability.Applications.ContactsData

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## ADDR_HOME

```TypeScript
static readonly ADDR_HOME: 1
```

Home address, the default value is **1**.

**Type:** 1

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## ADDR_OTHER

```TypeScript
static readonly ADDR_OTHER: 3
```

Other addresses, the default value is **3**.

**Type:** 3

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## ADDR_WORK

```TypeScript
static readonly ADDR_WORK: 2
```

Work address, the default value is **2**.

**Type:** 2

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## city

```TypeScript
city?: string
```

City where the contact is located.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## country

```TypeScript
country?: string
```

Country/Region where the contact is located.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## CUSTOM_LABEL

```TypeScript
static readonly CUSTOM_LABEL: 0
```

Custom postal address type, the default value is **0**.

**Type:** 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## INVALID_LABEL_ID

```TypeScript
static readonly INVALID_LABEL_ID: -1
```

Invalid address type, the default value is **-1**.

**Type:** -1

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## labelId

```TypeScript
labelId?: number
```

Postal address type.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## labelName

```TypeScript
labelName?: string
```

Name of the Postal address type.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## neighborhood

```TypeScript
neighborhood?: string
```

Neighbor of the contact.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## pobox

```TypeScript
pobox?: string
```

Email of the contact.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## postalAddress

```TypeScript
postalAddress: string
```

Postal address of the contact.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## postcode

```TypeScript
postcode?: string
```

Postal code of the region where the contact is located.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## region

```TypeScript
region?: string
```

Area where the contact is located.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData

## street

```TypeScript
street?: string
```

Street where the contact resides.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Applications.ContactsData
