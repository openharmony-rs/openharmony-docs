# SubscribedAbstractProperty

```TypeScript
declare abstract class SubscribedAbstractProperty<T>
```

Represents a synchronized property from [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## aboutToBeDeleted

```TypeScript
abstract aboutToBeDeleted(): void
```

Cancels the synchronization relationship between the [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) instance and [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md), whether it is a one-way or two-way binding. After **aboutToBeDeleted** is called, the **SubscribedAbstractProperty** instance is invalidated, meaning it can no longer be used to call the [set](arkts-arkui-localstorage-c.md#set) or [get](arkts-arkui-localstorage-c.md#get) API.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| T | Data of the synchronized property in AppStorage or LocalStorage. |

## info

```TypeScript
info(): string
```

Property name.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Property name. |

## set

```TypeScript
abstract set(newValue: T): void
```

Sets the data of the synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). The value of **newValue** must be of the **T** type. Since API version 12, it can be **null** or **undefined**.

> **NOTE:** 

> Since API version 12, AppStorage and LocalStorage support the Map, Set, Date types, as well as **null**,
> **undefined**, and union types.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newValue | T | Yes | Data to set. Since API version 12, the value can be **null** or **undefined**. |
