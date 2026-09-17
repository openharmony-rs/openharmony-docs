# ListItem

The ListItem component displays specific items in the list. It must be used together with List.

> **NOTE** > > - This component is supported since API version 7. Updates will be marked with a superscript to indicate > their earliest API version. > > - The parent of this component can only be List or ListItemGroup. > > - When this component is used with LazyForEach, its child components are created when it is created. > When this component is used with if/else or ForEach, or when the parent component is List or ListItemGroup, > its child components are created when it is laid out.

## Child Components

This component can contain a single child component.

## ListItem

```TypeScript
ListItem(value?: ListItemOptions)
```

Creates a ListItem component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ListItemOptions](arkts-arkui-listitemoptions-i.md) | No |  |

## ListItem

```TypeScript
ListItem(value?: string)
```

Creates a ListItem component.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** listItem/ListItemInterface

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ListItemOptions](arkts-arkui-listitemoptions-i.md) | Defines ListItem component configuration options. |
| [SwipeActionItem](arkts-arkui-swipeactionitem-i.md) | Describes the swipe action item. For a list in vertical layout, it refers to the delete option displayed on the left (or right) of the list item when the list item is swiped right (or left). |
| [SwipeActionOptions](arkts-arkui-swipeactionoptions-i.md) | The top layer of the @builder function corresponding to start and end must be a single component. Otherwise, undefined behavior occurs. If the top layer of the @builder function is a statement such as if/else or ForEach, ensure that these statements can generate a single component. |

### Enums

| Name | Description |
| --- | --- |
| [EditMode](arkts-arkui-editmode-e.md) | Enumerates the edit modes of list items. |
| [ListItemStyle](arkts-arkui-listitemstyle-e.md) | Enumerates the card styles of the List component. |
| [ListItemSwipeActionDirection](arkts-arkui-listitemswipeactiondirection-e.md) | Enumerates the swipe action menu display directions for ListItem components. |
| [Sticky](arkts-arkui-sticky-e.md) | Enumerates the sticky effects for list items. |
| [SwipeActionState](arkts-arkui-swipeactionstate-e.md) | Enumerates swipe states of list items. |
| [SwipeEdgeEffect](arkts-arkui-swipeedgeeffect-e.md) | Enumerates the edge effects. |

## Examples

```TypeScript
### Example 1: Creating a List Item

This example demonstrates the basic usage of creating a list item.


```

```TypeScript
### Example 2: Setting the Swipe Action Item

This example shows how to set the swipe action item for a list item using swipeAction.


```

```TypeScript
### Example 3: Applying a Card-style Effect

This example illustrates the card-style effect of the ListItem component.


```

```TypeScript
### Example 4: Setting the Swipe Action Item Using ComponentContent

This example demonstrates how to set the action items displayed during swipe operations in ListItem using ComponentContent.


```

```TypeScript
### Example 5: Managing the Swipe Action Menu Through ListItemSwipeActionManager

This example demonstrates how to manage the swipe action menu of a list item using [ListItemSwipeActionManager](arkts-arkui-listitemswipeactionmanager-c.md), available since API version 21.
```
