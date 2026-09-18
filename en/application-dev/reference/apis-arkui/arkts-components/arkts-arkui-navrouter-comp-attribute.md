# NavRouter properties/events

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** NavRouterAttribute extends CommonMethod<NavRouterAttribute>

**Since:** 9

**Deprecated since:** 13

**Substitutes:** NavPathStack and navDestination

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mode

```TypeScript
mode(mode: NavRouteMode)
```

Sets the route mode used for redirecting the user from the **NavRouter** component to the specified navigation destination page.

> **NOTE:** 

**Since:** 10

**Deprecated since:** 13

**Substitutes:** LaunchMode

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [NavRouteMode](arkts-arkui-navroutemode-e.md) | Yes | Route mode used for redirection.<br>Default value: **NavRouteMode.PUSH_WITH_RECREATE** |

## onStateChange

```TypeScript
onStateChange(callback: (isActivated: boolean) => void)
```

Called when the component activation status changes. **onStateChange(true)** is called when the **NavRouter** component is activated and its **NavDestination** child component is loaded. **onStateChange(false)** is called when the **NavDestination** child component is not displayed.

> **NOTE:** 

**Since:** 9

**Deprecated since:** 13

**Substitutes:** [onShown](arkts-arkui-navdestination-comp-attribute.md#onshown)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (isActivated: boolean) =&gt; void | Yes | Component activation status. The value **true** means that component is activated, and **false** means the opposite. |
