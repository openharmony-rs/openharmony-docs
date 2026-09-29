# AbstractProperty

```TypeScript
declare interface AbstractProperty<T>
```

A reference to a property in AppStorage or LocalStorage. It provides the capabilities to read and modify referenced property data and query property names. Unlike **SubscribedAbstractProperty**, an **AbstractProperty** instance does not need to be manually released.

> **NOTE:** 

> Since API version 12, AppStorage and LocalStorage support the **Map**, **Set**, and **Date** types, as well as
> **null**, **undefined**, and union types.

**Since:** 12

<!--Device-unnamed-declare interface AbstractProperty<T>--><!--Device-unnamed-declare interface AbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## get

```TypeScript
get(): T
```

Reads data of the referenced property from [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AbstractProperty-get(): T--><!--Device-AbstractProperty-get(): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| T | Data of the referenced property in AppStorage or LocalStorage. |

## info

```TypeScript
info(): string
```

Reads the property name of the referenced property from [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AbstractProperty-info(): string--><!--Device-AbstractProperty-info(): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| string | Property name of the referenced property in AppStorage or LocalStorage. |

## set

```TypeScript
set(newValue: T): void
```

Updates the data of the referenced property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). The value of **newValue** must be of the **T** type and can be **null** or **undefined**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AbstractProperty-set(newValue: T): void--><!--Device-AbstractProperty-set(newValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newValue | T | Yes | New value of the property referenced in AppStorage/LocalStorage. The value can be **null** or **undefined**. |
