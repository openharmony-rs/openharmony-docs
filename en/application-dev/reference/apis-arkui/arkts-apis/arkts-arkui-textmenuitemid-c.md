# TextMenuItemId

```TypeScript
declare class TextMenuItemId
```

Defines the unique identifier for a custom menu item. It is used to identify menu items. The IDs for built-in menu items are listed in the table below.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## equals

```TypeScript
equals(id: TextMenuItemId): boolean
```

Checks whether this **TextMenuItemId** object is the same as another **TextMenuItemId** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) | Yes | ID of the **TextMenuItemId** object to compare. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the two **TextMenuItemId** objects are the same.<br>**true** if the objects are equal; **false** otherwise. |

## of

```TypeScript
static of(id: ResourceStr): TextMenuItemId
```

Creates a **TextMenuItemId** object based on **id**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | [ResourceStr](arkts-arkui-resourcestr-t.md) | Yes | Menu ID. |

**Return value:**

| Type | Description |
| --- | --- |
| [TextMenuItemId](arkts-arkui-textmenuitemid-c.md) | **TextMenuItemId** object. |

## address

```TypeScript
static readonly address: TextMenuItemId
```

ID for the navigation menu item. It is a level-1 menu item. This menu item provides the redirection service for the selected address, launching the map app.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AI_WRITER

```TypeScript
static readonly AI_WRITER: TextMenuItemId
```

&lt;!--RP1--&gt;&lt;!--RP1End--&gt;ID for the menu item involving text enhancement features, such as polishing, summary extraction, and formatting, for selected text. It is a level-1 menu item. This menu item requires the large language model. If no large language model is available, this menu item does not take effect.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 13

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## askAI

```TypeScript
static readonly askAI: TextMenuItemId
```

&lt;!--RP2--&gt;&lt;!--RP2End--&gt;ID for the AI assistant menu item, which provides AI query capabilities for the selected text. It is a level-1 menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoFill

```TypeScript
static readonly autoFill: TextMenuItemId
```

ID for the autofill menu item. It is a level-1 menu item. When a menu item is tapped, the secondary menu item **Password Vault** is displayed. This menu item is supported exclusively for the Search, TextInput, TextArea, and RichEditor components.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CAMERA_INPUT

```TypeScript
static readonly CAMERA_INPUT: TextMenuItemId
```

ID for the camera input menu item. It is a level-1 menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COLLABORATION_SERVICE

```TypeScript
static readonly COLLABORATION_SERVICE: TextMenuItemId
```

ID for the collaboration service menu item. It is a level-1 menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COPY

```TypeScript
static readonly COPY: TextMenuItemId
```

ID for the default copy menu item. It is a level-1 menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CUT

```TypeScript
static readonly CUT: TextMenuItemId
```

ID for the default cut menu item. It is a level-1 menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dateTime

```TypeScript
static readonly dateTime: TextMenuItemId
```

ID for the event creation menu item. It is a level-1 menu item. This menu item provides the redirection service for the selected date and time, launching the page for creating a calendar event.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## email

```TypeScript
static readonly email: TextMenuItemId
```

ID for the email menu item. It is a level-1 menu item. This menu item provides the redirection service for the selected email address, launching the email app.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## passwordVault

```TypeScript
static readonly passwordVault: TextMenuItemId
```

ID for the password vault menu item. It is a level-2 menu item. Tapping this menu item launches the password vault app, which supports automatic username and password filling. The menu item is supported only for [Search](../arkts-components/arkts-arkui-search-comp.md#search), [TextInput](../arkts-components/arkts-arkui-textinput-comp.md#text_input), [TextArea](../arkts-components/arkts-arkui-textarea-comp.md#text_area), and [RichEditor](../arkts-components/arkts-arkui-richeditor-comp.md#rich_editor).

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PASTE

```TypeScript
static readonly PASTE: TextMenuItemId
```

ID for the default paste menu item. It is a level-1 menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## phoneNumber

```TypeScript
static readonly phoneNumber: TextMenuItemId
```

ID for the phone call menu item. It is a level-1 menu item. This menu item provides the redirection service for the selected phone number, launching the phone dialer page.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SEARCH

```TypeScript
static readonly SEARCH: TextMenuItemId
```

ID for the search menu item. It is a level-1 menu item. This menu item launches a browser to search for the selected text.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SELECT_ALL

```TypeScript
static readonly SELECT_ALL: TextMenuItemId
```

ID for the default select-all menu item. It is a level-1 menu item.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SHARE

```TypeScript
static readonly SHARE: TextMenuItemId
```

ID for the share menu item. It is a level-1 menu item. This menu item launches a window for sharing the selected text.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE

```TypeScript
static readonly TRANSLATE: TextMenuItemId
```

ID for the translate menu item. It is a level-1 menu item. The translation service is provided for the selected text.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## url

```TypeScript
static readonly url: TextMenuItemId
```

ID for the URL menu item. It is a level-1 menu item. This menu item provides the redirection service for the selected URL, launching a browser search or app page.

**Type:** [TextMenuItemId](arkts-arkui-textmenuitemid-c.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
