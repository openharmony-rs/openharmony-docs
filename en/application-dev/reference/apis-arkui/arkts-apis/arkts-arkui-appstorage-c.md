# AppStorage

```TypeScript
declare class AppStorage
```

AppStorage is the global UI state storage center bound to applications. It is created by the UI framework at application startup, which is used to store UI state data in runtime memory, and implement application-level global state sharing. For details about how to use it on the UI, see [AppStorage: Storing Application-wide UI State](../../../ui/state-management/arkts-appstorage.md).

> **NOTE:** 

> Since API version 12, AppStorage supports
> [Map](../../../ui/state-management/arkts-appstorage.md#decorating-variables-of-the-map-type),
> [Set](../../../ui/state-management/arkts-appstorage.md#decorating-variables-of-the-set-type),
> [Date](../../../ui/state-management/arkts-appstorage.md#decorating-variables-of-the-date-type) types,
> as well as **null**, **undefined**, and
> [union types](../../../ui/state-management/arkts-appstorage.md#using-union-types-in-appstorage).

**Since:** 7

<!--Device-unnamed-declare class AppStorage--><!--Device-unnamed-declare class AppStorage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## clear

```TypeScript
static clear(): boolean
```

Deletes all properties from [AppStorage](../../../ui/state-management/arkts-appstorage.md). The deletion is only successful if none of the properties in AppStorage have any subscribers. If there are subscribers, this API does not take effect and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

For details about the subscriber, see [delete](#delete).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static clear(): boolean--><!--Device-AppStorage-static clear(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the properties in AppStorage have no subscribers and the deletion is successful; returns **false** if there are still subscribers. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let res: boolean = AppStorage.clear(); // true: There are no subscribers.
```

## delete

```TypeScript
static delete(propName: string): boolean
```

Deletes the property corresponding to **propName** from [AppStorage](../../../ui/state-management/arkts-appstorage.md).

The deletion is only successful if the property has no subscribers. If there is a subscriber, the deletion fails and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

The property subscribers include the following:

1. Variables decorated by [\@StorageLink](../../../ui/state-management/arkts-appstorage.md#storagelink) and
[\@StorageProp](../../../ui/state-management/arkts-appstorage.md#storageprop)

2. Instances of [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) returned by
[link](#link), [prop](#prop), [setAndLink](#setandlink), or [setAndProp](#setandprop)

To delete these subscribers:

1. Remove the custom component containing \@StorageLink or \@StorageProp. For details, see
[Custom Component Deletion](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#custom-component-deletion).

2. Call the [aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted) API on instances of  
**SubscribedAbstractProperty** returned by **link**, **prop**, **setAndLink**, or **setAndProp**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static delete(propName: string): boolean--><!--Device-AppStorage-static delete(propName: string): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** if the operation fails. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
AppStorage.link<number>('PropA');
let res: boolean = AppStorage.delete('PropA'); // false: PropA still has subscribers.

AppStorage.setOrCreate('PropB', 48);
let res1: boolean = AppStorage.delete('PropB'); // true: PropB is successfully deleted from AppStorage.
```

## get

```TypeScript
static get<T>(propName: string): T | undefined
```

Obtains the value of the property corresponding to **propName** from [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the property does not exist, this API returns **undefined**.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static get<T>(propName: string): T | undefined--><!--Device-AppStorage-static get<T>(propName: string): T | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Value of the property corresponding to **propName** in AppStorage, or **undefined** if it does not exist. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let value: number = AppStorage.get('PropA') as number; // 47
```

## has

```TypeScript
static has(propName: string): boolean
```

Checks whether the property corresponding to **propName** exists in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static has(propName: string): boolean--><!--Device-AppStorage-static has(propName: string): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the property exists in AppStorage; returns **false** otherwise. |

**Examples**

```TypeScript
AppStorage.has('simpleProp');
```

## keys

```TypeScript
static keys(): IterableIterator<string>
```

Obtains all property names in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static keys(): IterableIterator<string>--><!--Device-AppStorage-static keys(): IterableIterator<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;string&gt; | All property names in AppStorage. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropB', 48);
let keys: IterableIterator<string> = AppStorage.keys();
```

## link

```TypeScript
static link<T>(propName: string): SubscribedAbstractProperty<T>
```

Establishes a two-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, the two-way bound data of the corresponding property in AppStorage is returned. Unlike the one-way data binding of [prop](#prop), modifications through **link** are synchronized back to AppStorage, and AppStorage synchronizes the changes to all data and custom components bound to this **propName**.

If the given property does not exist in AppStorage, **undefined** is returned.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static link<T>(propName: string): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static link<T>(propName: string): SubscribedAbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | Two-way bound data of the specified property in AppStorage, or **undefined** if the property does not exist. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = AppStorage.link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // Two-way synchronization: linkToPropA1.get() == linkToPropA2.get() == 48.
```

## prop

```TypeScript
static prop<T>(propName: string): SubscribedAbstractProperty<T>
```

Establishes a one-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, the one-way bound data of the corresponding property in AppStorage is returned. If **propName** does not exist in AppStorage, **undefined** is returned. Modifications to the one-way bound data are not synchronized back to AppStorage.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static prop<T>(propName: string): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static prop<T>(propName: string): SubscribedAbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | One-way bound data of the specified property in AppStorage, or **undefined** if the property does not exist. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let prop1: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
let prop2: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
prop1.set(1); // One-way synchronization: prop1.get() returns 1, while prop2.get() returns 47.
```

## ref

```TypeScript
static ref<T>(propName: string): AbstractProperty<T> | undefined
```

Returns a reference to the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** does not exist, this API returns **undefined**.

This API is basically the same as [link](#link), except that it does not require manual release of the returned variable of the [AbstractProperty&lt;T&gt;](arkts-arkui-abstractproperty-i.md) type.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AppStorage-static ref<T>(propName: string): AbstractProperty<T> | undefined--><!--Device-AppStorage-static ref<T>(propName: string): AbstractProperty<T> | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; &#124; undefined | Reference to the property corresponding to **propName** in AppStorage, or **undefined** if the corresponding **propName** does not exist in AppStorage. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let refToPropA1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
let refToPropA2: AbstractProperty<number> | undefined = AppStorage.ref('PropA'); // refToPropA2.get() == 47
refToPropA1?.set(48); // Synchronously modify AppStorage: refToPropA1.get() == refToPropA2.get() == 48.
```

## set

```TypeScript
static set<T>(propName: string, newValue: T): boolean
```

Sets the value of the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the value of **newValue** is the same as the current value of the property, no assignment is performed, and the state variable does not instruct the UI to update the value of the property. Unlike [setOrCreate](#setorcreate), **set** takes effect only when **propName** already exists, and returns **false** if **propName** does not exist.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static set<T>(propName: string, newValue: T): boolean--><!--Device-AppStorage-static set<T>(propName: string, newValue: T): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| newValue | T | Yes | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **false** if the property corresponding to **propName** does not exist in AppStorage or if the assignment fails. Returns **true** if the assignment is successful. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 48);
let res: boolean = AppStorage.set('PropA', 47); // true
let res1: boolean = AppStorage.set('PropB', 47); // false
```

## setAndLink

```TypeScript
static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

Similar to the [link](#link) API, establishes a two-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given property exists in AppStorage, this API returns the two-way bound data for the property. If the given property does not exist, this API creates and initializes the property in AppStorage using **defaultValue** and returns its two- way bound data.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static setAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| defaultValue | T | Yes | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. Since API version 12, **defaultValue** can be **null** or **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | Instance of SubscribedAbstractProperty&lt;T&gt;, which is the two-way bound data of the property corresponding to **propName** in AppStorage. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let link1: SubscribedAbstractProperty<number> = AppStorage.setAndLink('PropB', 49); // Create PropB with the default value 49.
let link2: SubscribedAbstractProperty<number> = AppStorage.setAndLink('PropA', 50); // PropA already exists with the value 47.
```

## setAndProp

```TypeScript
static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

Similar to the [prop](#prop) API, establishes a one-way data binding with the property corresponding to propName in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, the one-way bound data of the corresponding property is returned. If the given **propName** does not exist, this API creates and initializes the property corresponding to **propName** in AppStorage using **defaultValue** and returns its one-way bound data.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static setAndProp<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| defaultValue | T | Yes | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. Since API version 12, **defaultValue** can be **null** or **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | Instance of SubscribedAbstractProperty&lt;T&gt;, which is the one-way bound data of the property corresponding to **propName** in AppStorage. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let prop: SubscribedAbstractProperty<number> = AppStorage.setAndProp('PropB', 49); // PropA -> 47, PropB -> 49
```

## setAndRef

```TypeScript
static setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>
```

Similar to the [ref](#ref) API, returns a reference to the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given property does not exist, this API creates and initializes the property in AppStorage using **defaultValue** and returns its reference.

This API is basically the same as [setAndLink](#setandlink), except that it does not require manual release of the returned variable of the[AbstractProperty](arkts-arkui-abstractproperty-i.md) type.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AppStorage-static setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>--><!--Device-AppStorage-static setAndRef<T>(propName: string, defaultValue: T): AbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| defaultValue | T | Yes | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. The value can be **null** or **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md)&lt;T&gt; | Instance of **AbstractProperty&lt;T&gt;**, which is a reference to the property corresponding to **propName** in AppStorage. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> = AppStorage.setAndRef('PropB', 49); // Create PropB with the default value 49.
let ref2: AbstractProperty<number> = AppStorage.setAndRef('PropA', 50); // PropA already exists with the value 47.
```

## setOrCreate

```TypeScript
static setOrCreate<T>(propName: string, newValue: T): void
```

Sets the value of the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a new value, if the property exists and the new value is different from the current value. If the new value is the same as the current value of the property, no assignment is performed, and the state variable does not instruct the UI to update the value of the property.

If **propName** does not exist, this API creates it with the value of **newValue**. This **setOrCreate** API can create only one AppStorage key-value pair each time. To create multiple key-value pairs, call this API multiple times.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static setOrCreate<T>(propName: string, newValue: T): void--><!--Device-AppStorage-static setOrCreate<T>(propName: string, newValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| newValue | T | Yes | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Examples**

```TypeScript
AppStorage.setOrCreate('simpleProp', 121);
```

## size

```TypeScript
static size(): number
```

Obtains the number of properties in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AppStorage-static size(): number--><!--Device-AppStorage-static size(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of properties in AppStorage. |

**Examples**

```TypeScript
AppStorage.setOrCreate('PropB', 48);
let res: number = AppStorage.size(); // 1
```

## Clear

```TypeScript
static Clear(): boolean
```

Deletes all properties from [AppStorage](../../../ui/state-management/arkts-appstorage.md). The deletion is only successful if none of the properties in AppStorage have any subscribers. If there are subscribers, this API does not take effect and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

For details about the subscriber, see [delete](#delete).

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [clear](#clear)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Clear(): boolean--><!--Device-AppStorage-static Clear(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let res: boolean = AppStorage.Clear(); // true: There are no subscribers.
```

## Delete

```TypeScript
static Delete(propName: string): boolean
```

Deletes the property corresponding to **propName** from [AppStorage](../../../ui/state-management/arkts-appstorage.md).

The deletion is only successful if the property has no subscribers. If there is a subscriber, the deletion fails and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

Subscribers include properties bound using [Link](#link) and [Prop](#prop) APIs, as well as those decorated with [@StorageLink](../../../ui/state-management/arkts-appstorage.md#storagelink) and [@StorageProp](../../../ui/state-management/arkts-appstorage.md#storageprop). This means that if there is still an **\@StorageLink('propName') / \@StorageProp('propName')** decorated variable or a **SubscribedAbstractProperty** instance in a synchronization with the property, the property cannot be deleted from AppStorage.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [delete](#delete)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Delete(propName: string): boolean--><!--Device-AppStorage-static Delete(propName: string): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** if the operation fails. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
AppStorage.Link('PropA');
let res: boolean = AppStorage.Delete('PropA'); // false: PropA still has subscribers.

AppStorage.SetOrCreate('PropB', 48);
let res1: boolean = AppStorage.Delete('PropB'); // true: PropB is successfully deleted from AppStorage.
```

## Get

```TypeScript
static Get<T>(propName: string): T | undefined
```

Obtains the value of the property corresponding to **propName** from [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the property does not exist, this API returns **undefined**.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [get](#get)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Get<T>(propName: string): T | undefined--><!--Device-AppStorage-static Get<T>(propName: string): T | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Value of the property corresponding to **propName** in AppStorage, or **undefined** if it does not exist. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let value: number = AppStorage.Get('PropA') as number; // 47
```

## Has

```TypeScript
static Has(propName: string): boolean
```

Checks whether the property corresponding to **propName** exists in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [has](#has)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Has(propName: string): boolean--><!--Device-AppStorage-static Has(propName: string): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the property exists in AppStorage; returns **false** otherwise. |

**Examples**

```TypeScript
AppStorage.Has('simpleProp');
```

## IsMutable

```TypeScript
static IsMutable(propName: string): boolean
```

Checks whether the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md) is mutable.

**Since:** 7

**Deprecated since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static IsMutable(propName: string): boolean--><!--Device-AppStorage-static IsMutable(propName: string): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the property corresponding to **propName** is mutable. Currently, this return value is always **true**. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let res: boolean = AppStorage.IsMutable('PropA');
```

## Keys

```TypeScript
static Keys(): IterableIterator<string>
```

Obtains all property names in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [keys](#keys)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Keys(): IterableIterator<string>--><!--Device-AppStorage-static Keys(): IterableIterator<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;string&gt; | All property names in AppStorage. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropB', 48);
let keys: IterableIterator<string> = AppStorage.Keys();
```

## Link

```TypeScript
static Link(propName: string): any
```

Establishes a two-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given property exists in AppStorage, the two-way bound data of the property in AppStorage is returned.

Any update of the data is synchronized back to AppStorage, which then synchronizes the update to all data and custom components bound to the property.

If the given property does not exist in AppStorage, **undefined** is returned.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [link](#link)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Link(propName: string): any--><!--Device-AppStorage-static Link(propName: string): any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| any | Two-way bound data of the specified property in AppStorage, or **undefined** if the property does not exist. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.Link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = AppStorage.Link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // Two-way synchronization: linkToPropA1.get() == linkToPropA2.get() == 48
```

## Prop

```TypeScript
static Prop(propName: string): any
```

Establishes a one-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, the one-way bound data of the corresponding property in AppStorage is returned. If the given **propName** does not exist in AppStorage, **undefined** is returned. Modifications to the one-way bound data are not synchronized back to AppStorage.

> **NOTE:** 

> **Prop** supports only the **S** type (number, boolean, string).

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [prop](#prop)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Prop(propName: string): any--><!--Device-AppStorage-static Prop(propName: string): any-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |

**Return value:**

| Type | Description |
| --- | --- |
| any | One-way bound data of the specified property in AppStorage, or **undefined** if the property does not exist. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let prop1: SubscribedAbstractProperty<number> = AppStorage.Prop('PropA');
let prop2: SubscribedAbstractProperty<number> = AppStorage.Prop('PropA');
prop1.set(1); // One-way synchronization: prop1.get() returns 1, while prop2.get() returns 47.
```

## Set

```TypeScript
static Set<T>(propName: string, newValue: T): boolean
```

Sets the value of the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the value of **newValue** is the same as the current value of the property corresponding to **propName**, no assignment is performed, and the state variable does not instruct the UI to update the value of the property. Unlike [SetOrCreate](#setorcreate), **Set** takes effect only when **propName** already exists, and returns **false** if **propName** does not exist. Since API version 12, **newValue** can be **null** or **undefined**.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [set](#set)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Set<T>(propName: string, newValue: T): boolean--><!--Device-AppStorage-static Set<T>(propName: string, newValue: T): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| newValue | T | Yes | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **false** if the property corresponding to **propName** does not exist in AppStorage. Returns **true** if the operation is successful. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 48);
let res: boolean = AppStorage.Set('PropA', 47); // true
let res1: boolean = AppStorage.Set('PropB', 47); // false
```

## SetAndLink

```TypeScript
static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>
```

Similar to the [Link](#link) API, establishes a two-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given property exists in AppStorage, this API returns the two-way bound data for the property. If the given property does not exist, this API creates and initializes the property in AppStorage using **defaultValue** and returns its two- way bound data. The value of **defaultValue** must be of the **T** type and cannot be **null** or **undefined**.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [setAndLink](#setandlink)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>--><!--Device-AppStorage-static SetAndLink<T>(propName: string, defaultValue: T): SubscribedAbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| defaultValue | T | Yes | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. The value cannot be **null** or **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | Instance of SubscribedAbstractProperty&lt;T&gt;, which is the two-way bound data of the property corresponding to **propName** in AppStorage. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let link1: SubscribedAbstractProperty<number> = AppStorage.SetAndLink('PropB', 49); // Create PropB with the default value 49.
let link2: SubscribedAbstractProperty<number> = AppStorage.SetAndLink('PropA', 50); // PropA already exists with the value 47.
```

## SetAndProp

```TypeScript
static SetAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>
```

Similar to the [Prop](#prop) API, establishes a one-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, this API returns the one-way bound data of the corresponding property. If the given **propName** does not exist, this API creates and initializes the property corresponding to **propName** in AppStorage using **defaultValue** and returns its one-way bound data. The value of **defaultValue** must be of the **S** type and cannot be **null** or **undefined**.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [setAndProp](#setandprop)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static SetAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>--><!--Device-AppStorage-static SetAndProp<S>(propName: string, defaultValue: S): SubscribedAbstractProperty<S>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| defaultValue | S | Yes | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. The value cannot be **null** or **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;S&gt; | Instance of SubscribedAbstractProperty&lt;S&gt;, which is the one-way bound data of the property corresponding to **propName** in AppStorage. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropA', 47);
let prop: SubscribedAbstractProperty<number> = AppStorage.SetAndProp('PropB', 49); // PropA -> 47, PropB -> 49
```

## SetOrCreate

```TypeScript
static SetOrCreate<T>(propName: string, newValue: T): void
```

Sets the value of the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a new value, if **propName** exists and the value of **newValue** is different from the value of the property corresponding to **propName**. If the new value is the same as the current value of the property, no assignment is performed, and the state variable does not instruct the UI to update the value of the property. If **propName** does not exist, this API creates it with the value of **newValue**. Since API version 12, **newValue** can be **null** or **undefined**.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [setOrCreate](#setorcreate)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static SetOrCreate<T>(propName: string, newValue: T): void--><!--Device-AppStorage-static SetOrCreate<T>(propName: string, newValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name in AppStorage. |
| newValue | T | Yes | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('simpleProp', 121);
```

## Size

```TypeScript
static Size(): number
```

Obtains the number of properties in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [size](#size)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static Size(): number--><!--Device-AppStorage-static Size(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of properties in AppStorage. |

**Examples**

```TypeScript
AppStorage.SetOrCreate('PropB', 48);
let res: number = AppStorage.Size(); // 1
```

## staticClear

```TypeScript
static staticClear(): boolean
```

Deletes all properties from [AppStorage](../../../ui/state-management/arkts-appstorage.md). The deletion is only successful if none of the properties in AppStorage have any subscribers. If there are subscribers, this API does not take effect and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned. For details about the subscriber, see [delete](#delete).

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [Clear](#clear)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-AppStorage-static staticClear(): boolean--><!--Device-AppStorage-static staticClear(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Result of deleting all properties from AppStorage. Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let clearResult = AppStorage.staticClear();
```
