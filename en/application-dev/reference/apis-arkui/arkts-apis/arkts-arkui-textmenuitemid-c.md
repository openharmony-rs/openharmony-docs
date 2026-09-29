# TextMenuItemId

```TypeScript
declare class TextMenuItemId
```

Defines the unique identifier for a custom menu item. It is used to identify menu items. The IDs for built-in menu items are listed in the table below.

**Since:** 12

<!--Device-unnamed-declare class TextMenuItemId--><!--Device-unnamed-declare class TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## equals

```TypeScript
equals(id: TextMenuItemId): boolean
```

Checks whether this **TextMenuItemId** object is the same as another **TextMenuItemId** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItemId-equals(id: TextMenuItemId): boolean--><!--Device-TextMenuItemId-equals(id: TextMenuItemId): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) | Yes | TextMenuItemId object to compare. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether two TextMenuItemId values are equal.<br>The value **true** indicates that they are equal, and **false** indicates that they are not equal. |

## of

```TypeScript
static of(id: ResourceStr): TextMenuItemId
```

Creates a **TextMenuItemId** object based on **id**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItemId-static of(id: ResourceStr): TextMenuItemId--><!--Device-TextMenuItemId-static of(id: ResourceStr): TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Menu item identifier, used to create a TextMenuItemId object to identify the menu option. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) | Menu item identifier object created based on the passed-in ID, used to identify a menu option. |

## address

```TypeScript
static readonly address: TextMenuItemId
```

Navigate, a first-level menu item. Provides a jump service for the selected address and opens the map application.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextMenuItemId-static readonly address: TextMenuItemId--><!--Device-TextMenuItemId-static readonly address: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AI_WRITER

```TypeScript
static readonly AI_WRITER: TextMenuItemId
```

<!--RP1--><!--RP1End-->Polishes, summarizes, and formats the selected text, a first-level menu item. This menu item depends on the large model capability; otherwise, it does not take effect.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

<!--Device-TextMenuItemId-static readonly AI_WRITER: TextMenuItemId--><!--Device-TextMenuItemId-static readonly AI_WRITER: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## askAI

```TypeScript
static readonly askAI: TextMenuItemId
```

<!--RP2--><!--RP2End-->Provides AI query capability for the selected text, a first-level menu item. This menu item depends on the large model capability; otherwise, it does not take effect.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextMenuItemId-static readonly askAI: TextMenuItemId--><!--Device-TextMenuItemId-static readonly askAI: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoFill

```TypeScript
static readonly autoFill: TextMenuItemId
```

Auto fill, a first-level menu item. Tapping it expands the second-level menu item "Password vault". It is supported only by [Search](../arkts-components/arkts-arkui-search-comp.md), [TextInput](../arkts-components/arkts-arkui-textinput-comp.md), [TextArea](../arkts-components/arkts-arkui-textarea-comp.md), or [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md).

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextMenuItemId-static readonly autoFill: TextMenuItemId--><!--Device-TextMenuItemId-static readonly autoFill: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CAMERA_INPUT

```TypeScript
static readonly CAMERA_INPUT: TextMenuItemId
```

Camera input, a first-level menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItemId-static readonly CAMERA_INPUT: TextMenuItemId--><!--Device-TextMenuItemId-static readonly CAMERA_INPUT: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COLLABORATION_SERVICE

```TypeScript
static readonly COLLABORATION_SERVICE: TextMenuItemId
```

Collaboration service, a first-level menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItemId-static readonly COLLABORATION_SERVICE: TextMenuItemId--><!--Device-TextMenuItemId-static readonly COLLABORATION_SERVICE: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COPY

```TypeScript
static readonly COPY: TextMenuItemId
```

Default copy, a first-level menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItemId-static readonly COPY: TextMenuItemId--><!--Device-TextMenuItemId-static readonly COPY: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CUT

```TypeScript
static readonly CUT: TextMenuItemId
```

Default cut, a first-level menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItemId-static readonly CUT: TextMenuItemId--><!--Device-TextMenuItemId-static readonly CUT: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dateTime

```TypeScript
static readonly dateTime: TextMenuItemId
```

New schedule, a first-level menu item. Provides a jump service for the selected date and time and opens the new schedule page.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextMenuItemId-static readonly dateTime: TextMenuItemId--><!--Device-TextMenuItemId-static readonly dateTime: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## email

```TypeScript
static readonly email: TextMenuItemId
```

New email, a first-level menu item. Provides a jump service for the selected email address and opens the email application.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextMenuItemId-static readonly email: TextMenuItemId--><!--Device-TextMenuItemId-static readonly email: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## passwordVault

```TypeScript
static readonly passwordVault: TextMenuItemId
```

Password vault, a second-level menu item. Tapping this menu item opens the password vault application, which provides the capability of auto-filling account and password. It is supported only by [Search](../arkts-components/arkts-arkui-search-comp.md), [TextInput](../arkts-components/arkts-arkui-textinput-comp.md), [TextArea](../arkts-components/arkts-arkui-textarea-comp.md), or [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md).

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextMenuItemId-static readonly passwordVault: TextMenuItemId--><!--Device-TextMenuItemId-static readonly passwordVault: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PASTE

```TypeScript
static readonly PASTE: TextMenuItemId
```

Default paste, a first-level menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItemId-static readonly PASTE: TextMenuItemId--><!--Device-TextMenuItemId-static readonly PASTE: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## phoneNumber

```TypeScript
static readonly phoneNumber: TextMenuItemId
```

Call, a first-level menu item. Provides a jump service for the selected phone number and opens the dialing page.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextMenuItemId-static readonly phoneNumber: TextMenuItemId--><!--Device-TextMenuItemId-static readonly phoneNumber: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SEARCH

```TypeScript
static readonly SEARCH: TextMenuItemId
```

Search, a first-level menu item. Provides search service for the selected text and opens the browser to search the selected text content.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMenuItemId-static readonly SEARCH: TextMenuItemId--><!--Device-TextMenuItemId-static readonly SEARCH: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELECT_ALL

```TypeScript
static readonly SELECT_ALL: TextMenuItemId
```

Default select all, a first-level menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextMenuItemId-static readonly SELECT_ALL: TextMenuItemId--><!--Device-TextMenuItemId-static readonly SELECT_ALL: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SHARE

```TypeScript
static readonly SHARE: TextMenuItemId
```

Share, a first-level menu item. Provides share service for the selected text and opens the share window to share the selected text content.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMenuItemId-static readonly SHARE: TextMenuItemId--><!--Device-TextMenuItemId-static readonly SHARE: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE

```TypeScript
static readonly TRANSLATE: TextMenuItemId
```

Translation, a first-level menu item. Provides translation service for the selected text.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-TextMenuItemId-static readonly TRANSLATE: TextMenuItemId--><!--Device-TextMenuItemId-static readonly TRANSLATE: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## url

```TypeScript
static readonly url: TextMenuItemId
```

Open link, a first-level menu item. Provides a jump service for the selected URL and opens the browser to search or the application page.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-TextMenuItemId-static readonly url: TextMenuItemId--><!--Device-TextMenuItemId-static readonly url: TextMenuItemId-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
