# Navigator properties/events

```TypeScript
declare class NavigatorAttribute extends CommonMethod<NavigatorAttribute>
```

Declare navigator properties.

**Inheritance/Implementation:** NavigatorAttribute extends CommonMethod&lt;NavigatorAttribute&gt;

**Since:** 7

**Deprecated since:** 13

**Substitutes:** [Navigation](arkts-arkui-navigation-comp.md)

<!--Device-unnamed-declare class NavigatorAttribute extends CommonMethod<NavigatorAttribute>--><!--Device-unnamed-declare class NavigatorAttribute extends CommonMethod<NavigatorAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## active

```TypeScript
active(value: boolean)
```

Sets whether the **Navigator** component is activated. If the component is activated, the corresponding navigation takes effect.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** [Navigation](arkts-arkui-navigation-comp.md)

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigatorAttribute-active(value: boolean): NavigatorAttribute--><!--Device-NavigatorAttribute-active(value: boolean): NavigatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the **Navigator** component is activated. The value **true** means that the component is activated, and **false** means the opposite. |

## params

```TypeScript
params(value: object)
```

Sets the data that needs to be passed to the target page during redirection.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** [param](arkts-arkui-navigation-comp-navpathinfo-c.md#param)

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigatorAttribute-params(value: object): NavigatorAttribute--><!--Device-NavigatorAttribute-params(value: object): NavigatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | object | Yes | Data that needs to be passed to the target page during redirection. You can use [router.getParams()](../arkts-apis/arkts-arkui-router-getparams-f.md) to obtain the data on the target page. |

## target

```TypeScript
target(value: string)
```

Sets the path of the target page to be redirected to. The target page must be added to the **main_pages.json** file.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** [Navigation](arkts-arkui-navigation-comp.md)

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigatorAttribute-target(value: string): NavigatorAttribute--><!--Device-NavigatorAttribute-target(value: string): NavigatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Path of the target page to be redirected to. |

## type

```TypeScript
type(value: NavigationType)
```

Sets the navigation type.

**Since:** 7

**Deprecated since:** 13

**Substitutes:** [Navigation](arkts-arkui-navigation-comp.md)

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-NavigatorAttribute-type(value: NavigationType): NavigatorAttribute--><!--Device-NavigatorAttribute-type(value: NavigationType): NavigatorAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NavigationType](arkts-arkui-navigator-comp-navigationtype-e.md) | Yes | Navigation type.<br>Default value: **NavigationType.Push** |
