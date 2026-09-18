# ReactiveComponentContent

ReactiveComponentContent is inherited from [Content](../../../reference/apis-arkui/js-apis-arkui-Content.md#content-1) and is a container component used to dynamically bear and reuse UI content. It uses the @Builder function to build the UI and uses [ReactiveBuilderNode](arkts-arkui-buildernode-reactivebuildernode-c.md) to generate and manage the component tree. The core value of this component is to provide complete lifecycle management for dynamic content so that it can be integrated into the ArkUI component reuse system. This component is especially suitable for scenarios that require high- performance rendering, such as long lists.

**Inheritance/Implementation:** ReactiveComponentContent extends [Content](arkts-arkui-content-c.md)

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(uiContext: UIContext, builder: WrappedBuilder<T>, config: BuildOptions, ...args: T)
```

Constructor of ReactiveComponentContent.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uiContext | [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) | Yes | UI context required for creating a node. |
| builder | WrappedBuilder&lt;T&gt; | Yes | Encapsulates the WrappedBuilder object of the @Builder function with parameters. |
| config | [BuildOptions](arkts-arkui-buildernode-buildoptions-i.md) | Yes | Configures the build behavior of the builder. All attributes in BuildOptions are optional. The default value is the corresponding default value in BuildOptions. |
| args | T | Yes | Parameters of the builder function encapsulated in the **WrappedBuilder** object. Transfers external data to the WrappedBuilder&lt;T & gt and build functions specified in the constructor. Multiple input parameters are supported. The default value is **undefined**. |

**Examples**

```TypeScript
This example demonstrates how to use the ReactiveComponentContent constructor to dynamically create UI components containing responsive content, implementing nested calls of builder functions and flexible transfer of function parameters.
```

## dispose

```TypeScript
dispose(): void
```

Immediately releases the reference relationship between this **ReactiveComponentContent** object and its [entity node](../../../ui/arkts-user-defined-node.md#basic-concepts). For details about the scenarios involving **ReactiveComponentContent** unbinding, see [Canceling the Reference to the Entity Node](../../../ui/arkts-user-defined-arktsNode-builderNode.md#canceling-the-reference-to-the-entity-node).

> **NOTE:** 
> 
> After calling **dispose**, the **ReactiveComponentContent** object cancels its reference to the backend entity
> node. If the frontend object **ReactiveComponentContent** cannot be released, memory leaks may occur. To avoid
> this, be sure to call **dispose** on the **ReactiveComponentContent** object when you no longer need it. This
> reduces the complexity of reference relationships and lowers the risk of memory leaks.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
The following example shows how to use the dispose API to correctly release the ReactiveComponentContent object and manage the node lifecycle.
```

## flushState

```TypeScript
flushState(): void
```

Updates **ReactiveComponentContent**. If the bound parameters used in the **builder** function encapsulated by the [WrappedBuilder](../../../ui/state-management/arkts-wrapBuilder.md) object in **ReactiveComponentContent** are class instances decorated by the V1 decorator (such as @Observed), you need to manually call this API to update data after the data of this class changes. If the bound parameters are class instances decorated by the V2 decorator (such as @ObservedV2), the data can be automatically updated without manual calling.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
This example demonstrates how to use the flushState API in ReactiveComponentContent. By comparing the data update mechanisms of classes decorated by V2 decorators (such as @ObservedV2) and classes decorated by V1 decorators (such as @Observed), this example illustrates the state update strategies under different responsive approaches.
```

## inheritFreezeOptions

```TypeScript
inheritFreezeOptions(enabled: boolean): void
```

Sets whether the current **ReactiveComponentContent** object inherits the freeze policy configured by [ComponentOptions](../arkts-components/arkts-arkui-componentoptions-i.md) from its parent component's custom components. When inheritance is disabled (set to **false**), the **ReactiveComponentContent** object's freeze policy is set to **false**, which means its associated node remains unfrozen even in an inactive state.

> **NOTE:** 
> 
> When **inheritFreezeOptions** is set to **true** for a **ReactiveComponentContent** object, and its parent
> component is a custom component, **BuilderNode**, **ComponentContent**, **ReactiveBuilderNode**, or
> **ReactiveComponentContent**, it will inherit the parent component's freeze policy. If the child component is a
> custom component, its freeze policy is not transferred to the child component.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether the **ReactiveComponentContent** object inherits the freeze policy from its parent component's custom components.<br>The value **true** means to inherit the freeze policy from the parent component's custom components, and **false** means the opposite. |

**Examples**

```TypeScript
This example demonstrates how to set the inheritance state of ReactiveComponentContent to true, inheriting the freeze policy from the parent component's custom components. The component freezes when inactive and unfreezes and updates cached data when switching to the active state.
```

## isDisposed

```TypeScript
isDisposed(): boolean
```

Checks whether this **ReactiveComponentContent** object has released its reference to its backend entity node. Frontend nodes maintain references to corresponding backend entity nodes. After a node calls the **dispose** API to release this reference, subsequent API calls may cause crashes or return default values. This API facilitates validation of node validity prior to operations, thereby mitigating risks in scenarios where calls after disposal are required.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the reference to the backend node is released.<br>The value **true** means that the reference to backend node is released, and **false** means the opposite. |

**Examples**

```TypeScript
This example demonstrates how to use the isDisposed API to check whether the ReactiveComponentContent object's reference to the backend node is released, providing a complete implementation solution for node status security detection.
```

## isTransferred

```TypeScript
isTransferred(): boolean
```

Returns a flag indicating whether the current ReactiveComponentContent was obtained through dynamic-static conversion, includes conversions in both directions: dynamic-to-static and static-to-dynamic.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the ReactiveComponentContent was converted between dynamic and static states, otherwise, returns false. |

## recycle

```TypeScript
recycle(): void
```

Recycles the custom component in ReactiveComponentContent. Component recycling is part of the component reuse mechanism. For details, see [@Reusable Decorator: Reusing V1 Components](../../../ui/state-management/arkts-reusable.md). Since API version 26.0.0, custom components in **ReactiveComponentContent** support V2 component reuse. For details, see [@ReusableV2 Decorator: Reusing Components](../../../ui/state-management/arkts-new-reusableV2.md).

**ReactiveComponentContent** completes the reuse event transfer between internal and external custom components through [reuse](arkts-arkui-componentcontent-c.md#reuse) and **recycle**. For specific usage scenarios, see [Implementing Node Reuse with the BuilderNode reuse and recycle APIs](../../../ui/arkts-user-defined-arktsNode-builderNode.md#implementing-node-reuse-with-the-buildernode-reuse-and-recycle-apis).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
A high-performance long list that contains multi-layer component reuse is implemented. ReactiveComponentContent dynamically manages Builder content and automatically reclaims and reuses components when the list scrolls.
```

```TypeScript


Since API version 26.0.0, custom components in ReactiveComponentContent support V2 component reuse.
```

## reuse

```TypeScript
reuse(param?: Object): void
```

Triggers component reuse for custom components under this **ReactiveComponentContent**. For details about component reuse, see [@Reusable Decorator: Reusing V1 Components](../../../ui/state-management/arkts-reusable.md). For details about the scenarios involving **ReactiveComponentContent** unbinding, see [Canceling the Reference to the Entity Node](../../../ui/arkts-user-defined-arktsNode-builderNode.md#canceling-the-reference-to-the-entity-node). Since API version 26.0.0, custom components in **ReactiveComponentContent** support V2 component reuse. For details, see [@ReusableV2 Decorator: Reusing Components](../../../ui/state-management/arkts-new-reusableV2.md).

**ReactiveComponentContent** completes the reuse event transfer between internal and external custom components through **reuse** and [recycle](arkts-arkui-componentcontent-c.md#recycle). For specific usage scenarios, see [Implementing Node Reuse with the BuilderNode reuse and recycle APIs](../../../ui/arkts-user-defined-arktsNode-builderNode.md#implementing-node-reuse-with-the-buildernode-reuse-and-recycle-apis).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | Object | No | Parameter used to reuse [ReactiveComponentContent](arkts-arkui-componentcontent-reactivecomponentcontent-c.md). This parameter is directly used for reusing all top-level custom components in **ReactiveComponentContent**. It should contain the content required by the constructor parameters of each custom component. Otherwise, undefined behavior may occur. Calling this method synchronously triggers the [aboutToReuse](../../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#abouttoreuse10) lifecycle callback of internal custom components, with this parameter as the callback input. The default value is undefined. In this case, the custom component in ReactiveComponentContent directly uses the data source during construction. |

**Examples**

```TypeScript
For details, see the example in [recycle](#recycle).
```

## updateConfiguration

```TypeScript
updateConfiguration(): void
```

Transfers a system environment change event and triggers full update of a node. This event can be used to notify the object of the update. Whether the system environment used by the object is updated depends on the current system environment change of the application. For details about system environment changes, see [@ohos.app.ability.Configuration (Environment Variables)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-configuration-configuration-i.md).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
The following example shows how to use the updateConfiguration API to respond to system environment configuration changes and dynamically update the UI node constructed by ReactiveComponentContent.
```
