# AccessibilityOptions

```TypeScript
declare interface AccessibilityOptions
```

Defines the struct of AccessibilityOptions.

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## accessibilityPreferred

```TypeScript
accessibilityPreferred?: boolean
```

If **accessibilityPreferred** is set to **true**, the accessibility text of this child node is prioritized during depth-first traversal of each child node.

If **accessibilityText** is empty, the component's **Text** is used. The concatenated text is set for the parent node whose **accessibilityText** and **text** are both empty.

If **accessibilityPreferred** is set to **false**, this feature is disabled.

Default value: **false**

**Type:** boolean

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## actionControllerId

```TypeScript
actionControllerId?: string
```

[Unique ID](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id) of the target child component. After a container component with [accessibilityGroup](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup-1) enabled performs accessibility grouping, any triggered accessibility control operation is forwarded to the child component of the specified ID. This aggregates click events during screen reading and eliminates the need to focus on child components individually. **NOTE:** If multiple child components of the same type exist in the grouped component, the first matching child component found under the grouped component in the component tree acts as the controller component. Currently, only accessibility click actions are supported. If this API is configured together with **actionControllerRoleType**, the component with a matching ID is prioritized. Specific types in cross-process embedded components are not supported, such as widgets and **EmbeddedUIExtension**. Default value: no specified component.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## actionControllerRoleType

```TypeScript
actionControllerRoleType?: AccessibilityRoleType
```

Type of the target child component. After a container component with [accessibilityGroup](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup-1) enabled performs accessibility grouping, any triggered accessibility control operation is forwarded to the child component of the specified type. This aggregates click events during screen reading and eliminates the need to focus on child components individually.

**NOTE:** 

If multiple child components of the same type exist in the grouped component, the first matching child component found under the grouped component in the component tree acts as the controller component.

Currently, only accessibility click actions are supported.

Specific types in cross-process embedded components are not supported, such as widgets and **EmbeddedUIExtension**.

Default value: no specified component

**Type:** [AccessibilityRoleType](../arkts-components/arkts-arkui-common-comp-accessibilityroletype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stateControllerId

```TypeScript
stateControllerId?: string
```

[Unique ID](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#id) of the target child component. After a container component with [accessibilityGroup](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup-1) enabled performs accessibility grouping, the selection state and state announcement text of the child component of the specified ID are used as the state and announcement text of the grouped component. This aggregates state announcements during screen reading and eliminates the need to focus on child components individually. **NOTE:** If multiple child components of the same type exist in the grouped component, the first matching child component found under the grouped component in the component tree acts as the controller component. If this API is configured together with **stateControllerRoleType**, the component with a matching ID is prioritized. Specific types in cross-process embedded components are not supported, such as widgets and **EmbeddedUIExtension**. Default value: no specified component.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stateControllerRoleType

```TypeScript
stateControllerRoleType?: AccessibilityRoleType
```

Type of the target child component. After a container component with [accessibilityGroup](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup-1) enabled performs accessibility grouping, the selection state and state announcement text of the child component of the specified type are used as the state and announcement text of the grouped component. This aggregates state announcements during screen reading and eliminates the need to focus on child components individually.

**NOTE:** 

If multiple child components of the same type exist in the grouped component, the first matching child component found under the grouped component in the component tree acts as the controller component.

Specific types in cross-process embedded components are not supported, such as widgets and **EmbeddedUIExtension**.

Default value: no specified component

**Type:** [AccessibilityRoleType](../arkts-components/arkts-arkui-common-comp-accessibilityroletype-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
