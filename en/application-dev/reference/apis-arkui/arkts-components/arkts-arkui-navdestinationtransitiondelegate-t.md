# NavDestinationTransitionDelegate

```TypeScript
declare type NavDestinationTransitionDelegate =
    (operation: NavigationOperation, isEnter: boolean) => Array<NavDestinationTransition> | undefined
```

Defines the delegate function for custom transition animations of the **NavDestination** component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| operation | [NavigationOperation](arkts-arkui-navigationoperation-e.md) | Yes | Type of navigation operation for the current page transition. |
| isEnter | boolean | Yes | Whether the current page is an entry page.<br>**true**: The current page is an entry page.<br>**false**: The current page is not an entry page. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[NavDestinationTransition](arkts-arkui-navdestinationtransition-i.md)&gt; &#124; undefined | Array of custom animations for the **NavDestination** page. If **undefined** is returned, the default system animation is used. |
