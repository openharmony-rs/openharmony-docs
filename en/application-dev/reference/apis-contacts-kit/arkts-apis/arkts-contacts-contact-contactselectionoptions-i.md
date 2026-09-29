# ContactSelectionOptions

```TypeScript
interface ContactSelectionOptions
```

Defines the Contact selection options, which specifies whether one contact or multiple contacts can be selected.

**Since:** 10

<!--Device-contact-interface ContactSelectionOptions--><!--Device-contact-interface ContactSelectionOptions-End-->

**System capability:** SystemCapability.Applications.Contacts

## Modules to Import

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## filter

```TypeScript
filter?: ContactSelectionFilter
```

Contact selection filter. This API can be used in atomic services since API version 15.

**Type:** [ContactSelectionFilter](arkts-contacts-contact-contactselectionfilter-i.md)

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ContactSelectionOptions-filter?: ContactSelectionFilter--><!--Device-ContactSelectionOptions-filter?: ContactSelectionFilter-End-->

**System capability:** SystemCapability.Applications.Contacts

## isAutoDismissOnNavigation

```TypeScript
isAutoDismissOnNavigation?: boolean
```

Whether to allow automatic dismissal of the picker when the page that launched it undergoes a route change. The value true means the picker is allowed to be dismissed automatically, and false means the picker is not allowed to be dismissed automatically.

The default value is false.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ContactSelectionOptions-isAutoDismissOnNavigation?: boolean--><!--Device-ContactSelectionOptions-isAutoDismissOnNavigation?: boolean-End-->

**System capability:** SystemCapability.Applications.Contacts

## isDisplayedByName

```TypeScript
isDisplayedByName?: boolean
```

Whether to display contacts by name. The value **true** indicates that contacts are displayed by name, and the value **false** indicates that contacts are displayed by number. The default value is **false**. This API can be used in atomic services since API version 15.

**Type:** boolean

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ContactSelectionOptions-isDisplayedByName?: boolean--><!--Device-ContactSelectionOptions-isDisplayedByName?: boolean-End-->

**System capability:** SystemCapability.Applications.Contacts

## isMultiSelect

```TypeScript
isMultiSelect?: boolean
```

Whether multiple contacts can be selected. The value **true** indicates that multiple contacts can be selected, and the value **false** indicates that only one contact can be selected. The default value is **false**.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ContactSelectionOptions-isMultiSelect?: boolean--><!--Device-ContactSelectionOptions-isMultiSelect?: boolean-End-->

**System capability:** SystemCapability.Applications.Contacts

## maxSelectable

```TypeScript
maxSelectable?: number
```

Maximum number of contacts. The default value is **10000**. If the value exceeds the maximum number, the default value is used. This API can be used in atomic services since API version 15.

**Type:** number

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-ContactSelectionOptions-maxSelectable?: number--><!--Device-ContactSelectionOptions-maxSelectable?: number-End-->

**System capability:** SystemCapability.Applications.Contacts
