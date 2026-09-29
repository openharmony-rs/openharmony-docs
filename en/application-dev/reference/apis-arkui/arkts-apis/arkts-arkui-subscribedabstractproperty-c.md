# SubscribedAbstractProperty

```TypeScript
declare abstract class SubscribedAbstractProperty<T>
```

An object of a one-way or two-way synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). It is used to establish a data synchronization relationship with a property in AppStorage or LocalStorage. A **SubscribedAbstractProperty** instance needs to be manually released through the [aboutToBeDeleted](#abouttobedeleted) API to cancel the synchronization relationship and invalidate the instance.

> **NOTE:** 

> Since API version 12, AppStorage and LocalStorage support the **Map**, **Set**, and **Date** types, as well as
> **null**, **undefined**, and union types.

**Since:** 9

<!--Device-unnamed-declare abstract class SubscribedAbstractProperty<T>--><!--Device-unnamed-declare abstract class SubscribedAbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToBeDeleted

```TypeScript
abstract aboutToBeDeleted(): void
```

Cancels the one-way or two-way synchronization relationship between the [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) instance and [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md), and invalidates the **SubscribedAbstractProperty** instance. That is, after **aboutToBeDeleted** is called, [set](#set) or [get](#get) can no longer be called using the **SubscribedAbstractProperty** instance.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubscribedAbstractProperty-abstract aboutToBeDeleted(): void--><!--Device-SubscribedAbstractProperty-abstract aboutToBeDeleted(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## get

```TypeScript
abstract get(): T
```

Reads the data of the synchronized property from [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SubscribedAbstractProperty-abstract get(): T--><!--Device-SubscribedAbstractProperty-abstract get(): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| T | Data of the synchronized property in AppStorage or LocalStorage. |

## info

```TypeScript
info(): string
```

Returns the name of the synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SubscribedAbstractProperty-info(): string--><!--Device-SubscribedAbstractProperty-info(): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Name of the property synchronized in AppStorage or LocalStorage. |

## set

```TypeScript
abstract set(newValue: T): void
```

Sets the data of the synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). The value of **newValue** must be of the **T** type. Since API version 12, it can be **null** or **undefined**.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-SubscribedAbstractProperty-abstract set(newValue: T): void--><!--Device-SubscribedAbstractProperty-abstract set(newValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newValue | T | Yes | New value of the synchronized property in AppStorage or LocalStorage. Since API version 12, the value can be **null** or **undefined**. |
