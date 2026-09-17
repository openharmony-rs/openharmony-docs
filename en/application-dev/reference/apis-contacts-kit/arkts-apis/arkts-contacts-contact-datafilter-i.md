# DataFilter

Defines the contact data filter item.

**Since:** 15

**System capability:** SystemCapability.Applications.Contacts

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## field

```TypeScript
field: DataField
```

Contact data field.

**Type:** [DataField](arkts-contacts-contact-datafield-e.md)

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Applications.Contacts

## options

```TypeScript
options: Array<FilterOptions>
```

Contact filtering parameter. Multiple filter options in the array are ORed. The maximum length of the array is 3.

**Type:** Array&lt;[FilterOptions](arkts-contacts-contact-filteroptions-i.md)&gt;

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Applications.Contacts
