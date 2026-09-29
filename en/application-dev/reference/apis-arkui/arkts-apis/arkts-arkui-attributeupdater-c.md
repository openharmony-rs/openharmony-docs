# AttributeUpdater

```TypeScript
export declare class AttributeUpdater<T, C = Initializer<T>> implements AttributeModifier<T>
```

Sets attributes directly to a component to trigger UI re-renders, without marking them as state variables. This is applicable to scenarios where component attributes need to be dynamically updated without defining state variables, such as dynamically modifying component constructor parameters or avoiding defining state variables for one-time attribute updates.

**Inheritance/Implementation:** AttributeUpdater implements AttributeModifier<T>

**Since:** 12

<!--Device-unnamed-export declare class AttributeUpdater<T, C = Initializer<T>> implements AttributeModifier<T>--><!--Device-unnamed-export declare class AttributeUpdater<T, C = Initializer<T>> implements AttributeModifier<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## applyNormalAttribute

```TypeScript
applyNormalAttribute?(instance: T): void
```

Defines the normal-state attribute update function, which is triggered when **AttributeUpdater** subsequently updates attributes. It is not recommended to use both **AttributeUpdater** and an attribute method to set the same attribute on the same component, as this can easily cause confusion. When **AttributeUpdater** is used together with an attribute method, the one that is used later takes effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeUpdater-applyNormalAttribute?(instance: T): void--><!--Device-AttributeUpdater-applyNormalAttribute?(instance: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | Attribute class instance of the component. You can call the attribute method of this instance to set or update the normal-state attributes of the component, for example, **ButtonAttribute** of the **Button** component and **TextAttribute** of the **Text** component. |

## initializeModifier

```TypeScript
initializeModifier(instance: T): void
```

Provides the style when **AttributeUpdater** initially sets attributes to a component. It is not recommended to use both **AttributeUpdater** and an attribute method to set the same attribute on the same component, as this can easily cause confusion. When **AttributeUpdater** is used together with an attribute method, the one that is used later takes effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeUpdater-initializeModifier(instance: T): void--><!--Device-AttributeUpdater-initializeModifier(instance: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | Attribute class instance of the component. You can call the attribute method of this instance to initially set the style attribute to the component, such as **ButtonAttribute** of the **Button** component and **TextAttribute** of the **Text** component. |

## onComponentChanged

```TypeScript
onComponentChanged(component: T): void
```

Invoked to notify the application when multiple components are bound to the same custom **AttributeUpdater** object and the bound component changes. Note that one **AttributeUpdater** object can be associated with only one component at a time. Otherwise, the set attributes will take effect on only one component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeUpdater-onComponentChanged(component: T): void--><!--Device-AttributeUpdater-onComponentChanged(component: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| component | T | Yes | Attribute class instance of the component. You can call the attribute method of this instance to set the attribute to the component after changing, for example, **ButtonAttribute** of the **Button** component and **TextAttribute** of the **Text** component. |

## attribute

```TypeScript
get attribute(): T | undefined
```

Obtains the attribute class instance corresponding to the component in **AttributeUpdater**. The instance can then be used to directly update attributes. The binding relationship between the component and **AttributeUpdater** must first be established through the component's **attributeModifier** attribute method before the attribute class instance can be obtained. It is not recommended to use both **AttributeUpdater** and an attribute method to set the same attribute on the same component. When **AttributeUpdater** is used together with an attribute method, the one that is used later takes effect.

**Type:** T

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeUpdater-get attribute(): T | undefined--><!--Device-AttributeUpdater-get attribute(): T | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## updateConstructorParams

```TypeScript
updateConstructorParams: C
```

**C** indicates the constructor type of the component, for example, **TextInterface** of the **Text** component and **ImageInterface** of the **Image** component. The type is used to change the constructor input parameters of the component. The component must first be bound to **AttributeUpdater** through the component's **attributeModifier** attribute method before use. Currently, only the **Button**, **Image**, **Text**, **Span**, **SymbolSpan**, and **ImageSpan** components are supported. Ensure the type matching of **T** and **C** before use; otherwise, it may cause functionality issues.

**Type:** C

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AttributeUpdater-updateConstructorParams: C--><!--Device-AttributeUpdater-updateConstructorParams: C-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
