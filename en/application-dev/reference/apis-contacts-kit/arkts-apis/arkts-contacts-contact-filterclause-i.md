# FilterClause

Defines the contact filter criteria. Multiple filter criteria are ORed. If the parameter is an array, the array can contain a maximum of three elements.

**Since:** 15

**System capability:** SystemCapability.Applications.Contacts

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## dataItem

```TypeScript
dataItem?: DataFilter
```

Contact data filter item.

**Type:** [DataFilter](arkts-contacts-contact-datafilter-i.md)

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Applications.Contacts

## focusModeList

```TypeScript
focusModeList?: Array<FilterOptions>
```

Focus mode list.

**Type:** Array&lt;[FilterOptions](arkts-contacts-contact-filteroptions-i.md)&gt;

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Applications.Contacts

## id

```TypeScript
id?: Array<FilterOptions>
```

Contact ID.

**Type:** Array&lt;[FilterOptions](arkts-contacts-contact-filteroptions-i.md)&gt;

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Applications.Contacts

## name

```TypeScript
name?: Array<FilterOptions>
```

Contact name.

**Type:** Array&lt;[FilterOptions](arkts-contacts-contact-filteroptions-i.md)&gt;

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Applications.Contacts
