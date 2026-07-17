# State Management with Application-Level Variables

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin0206-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=79e4597a11fe0470e85a7a6ec526decbb0cbcff4 translatedAt=2026-07-15T07:47:29.881Z pushedAt=2026-07-16T08:21:59.553Z -->

The state management module provides data storage, persistent data management, UIAbility data storage, and environment state query required by applications. [AppStorage](#appstorage) is the global UI state storage center bound to applications, [LocalStorage](#localstorage9) provides page-level UI state storage, [PersistentStorage](#persistentstorage) enables state variable persistence, and [Environment](#environment) offers the capability to read system environment variables and write their values to AppStorage.

For details about the development guides, see [AppStorage: Storing Application-wide UI State](../../../ui/state-management/arkts-appstorage.md), [LocalStorage: Storing Page-Level UI State](../../../ui/state-management/arkts-localstorage.md), [PersistentStorage: Persisting UI State](../../../ui/state-management/arkts-persiststorage.md), and [Environment: Querying the Device Environment](../../../ui/state-management/arkts-environment.md).

>**NOTE**
>
>The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

T and S in this topic represent the types as described below.

| Type  | Description                                    |
| ---- | -------------------------------------- |
| T    | Class, number, boolean, string, and arrays of these types. |
| S    | number, boolean, string.                 |

## AppStorage

AppStorage is the global UI state storage center bound to applications. It is created by the UI framework at application startup, which is used to store UI state data in runtime memory, and implement application-level global state sharing. For details about how to use it on the UI, see [AppStorage: Storing Application-wide UI State](../../../ui/state-management/arkts-appstorage.md).

> **NOTE**
>
> Since API version 12, AppStorage supports [Map](../../../ui/state-management/arkts-appstorage.md#decorating-variables-of-the-map-type), [Set](../../../ui/state-management/arkts-appstorage.md#decorating-variables-of-the-set-type), [Date](../../../ui/state-management/arkts-appstorage.md#decorating-variables-of-the-date-type) types, as well as **null**, **undefined**, and [union types](../../../ui/state-management/arkts-appstorage.md#using-union-types-in-appstorage).

### ref<sup>12+</sup>

static ref\<T\>(propName: string): AbstractProperty\<T\>&nbsp;\|&nbsp;undefined

Returns a reference to the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** does not exist, this API returns **undefined**.

This API is basically the same as [link](#link10), except that it does not require manual release of the returned variable of the [AbstractProperty&lt;T&gt;](#abstractpropertyt12) type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description              |
| -------- | ------ | ---- | ---------------------- |
| propName | string | Yes  | Property name in AppStorage.|

**Return value**

| Type                                  | Description                                                        |
| -------------------------------------- | ------------------------------------------------------------ |
| [AbstractProperty&lt;T&gt;](#abstractpropertyt12) \| undefined | Reference to the property corresponding to **propName** in AppStorage, or **undefined** if the corresponding **propName** does not exist in AppStorage. |

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let refToPropA1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
let refToPropA2: AbstractProperty<number> | undefined = AppStorage.ref('PropA'); // refToPropA2.get() == 47
refToPropA1?.set(48); // Synchronously modify AppStorage: refToPropA1.get() == refToPropA2.get() == 48.
```

### setAndRef<sup>12+</sup>

static setAndRef&lt;T&gt;(propName: string, defaultValue: T): AbstractProperty&lt;T&gt;

Similar to the [ref](#ref12) API, returns a reference to the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given property does not exist, this API creates and initializes the property in AppStorage using **defaultValue** and returns its reference.

This API is basically the same as [setAndLink](#setandlink10), except that it does not require manual release of the returned variable of the [AbstractProperty&lt;T&gt;](#abstractpropertyt12) type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | Yes  | Property name in AppStorage.                                      |
| defaultValue | T      | Yes  | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. The value can be **null** or **undefined**.|

**Return value**

| Type                     | Description                                                        |
| ------------------------- | ------------------------------------------------------------ |
| [AbstractProperty&lt;T&gt;](#abstractpropertyt12) | Instance of **AbstractProperty&lt;T&gt;**, which is a reference to the property corresponding to **propName** in AppStorage. |

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> = AppStorage.setAndRef('PropB', 49); // Create PropB with the default value 49.
let ref2: AbstractProperty<number> = AppStorage.setAndRef('PropA', 50); // PropA already exists with the value 47.
```

### link<sup>10+</sup>

static link&lt;T&gt;(propName: string): SubscribedAbstractProperty&lt;T&gt;

Establishes a two-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, the two-way bound data of the corresponding property in AppStorage is returned. Unlike the one-way data binding of [prop](#prop10), modifications through **link** are synchronized back to AppStorage, and AppStorage synchronizes the changes to all data and custom components bound to this **propName**.

If the given property does not exist in AppStorage, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type                               | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | Two-way bound data of the specified property in AppStorage, or **undefined** if the property does not exist.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = AppStorage.link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // Two-way synchronization: linkToPropA1.get() == linkToPropA2.get() == 48.
```

### setAndLink<sup>10+</sup>

static setAndLink&lt;T&gt;(propName: string, defaultValue: T): SubscribedAbstractProperty&lt;T&gt;

Similar to the [link](#link10) API, establishes a two-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given property exists in AppStorage, this API returns the two-way bound data for the property. If the given property does not exist, this API creates and initializes the property in AppStorage using **defaultValue** and returns its two-way bound data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | Yes  | Property name in AppStorage.                                      |
| defaultValue | T | Yes | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. Since API version 12, **defaultValue** can be **null** or **undefined**.|

**Return value**

| Type                                 | Description                                      |
| ----------------------------------- | ---------------------------------------- |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | Instance of **SubscribedAbstractProperty&lt;T&gt;**, which is the two-way bound data of the property corresponding to **propName** in AppStorage.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let link1: SubscribedAbstractProperty<number> = AppStorage.setAndLink('PropB', 49); // Create PropB with the default value 49.
let link2: SubscribedAbstractProperty<number> = AppStorage.setAndLink('PropA', 50); // PropA already exists with the value 47.
```

### prop<sup>10+</sup>

static prop&lt;T&gt;(propName: string): SubscribedAbstractProperty&lt;T&gt;

Establishes a one-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, the one-way bound data of the corresponding property in AppStorage is returned. If **propName** does not exist in AppStorage, **undefined** is returned. Modifications to the one-way bound data are not synchronized back to AppStorage.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type                               | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | One-way bound data of the specified property in AppStorage, or **undefined** if the property does not exist.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let prop1: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
let prop2: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
prop1.set(1); // One-way synchronization: prop1.get() returns 1, while prop2.get() returns 47.
```

### setAndProp<sup>10+</sup>

static setAndProp&lt;T&gt;(propName: string, defaultValue: T): SubscribedAbstractProperty&lt;T&gt;

Similar to the [prop](#prop10) API, establishes a one-way data binding with the property corresponding to propName in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, the one-way bound data of the corresponding property is returned. If the given **propName** does not exist, this API creates and initializes the property corresponding to **propName** in AppStorage using **defaultValue** and returns its one-way bound data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | Yes  | Property name in AppStorage.                                      |
| defaultValue | T | Yes | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. Since API version 12, **defaultValue** can be **null** or **undefined**.|

**Return value**

| Type                                 | Description                                     |
| ----------------------------------- | --------------------------------------- |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | Instance of **SubscribedAbstractProperty&lt;T&gt;**, which is the one-way bound data of the property corresponding to **propName** in AppStorage. |

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let prop: SubscribedAbstractProperty<number> = AppStorage.setAndProp('PropB', 49); // PropA -> 47, PropB -> 49
```

### has<sup>10+</sup>

static has(propName: string): boolean

Checks whether the property corresponding to **propName** exists in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type     | Description                                      |
| ------- | ---------------------------------------- |
| boolean | Returns **true** if the property exists in AppStorage; returns **false** otherwise.|

**Example**

```ts
AppStorage.has('simpleProp');
```

### get<sup>10+</sup>

static get&lt;T&gt;(propName: string): T \| undefined

Obtains the value of the property corresponding to **propName** from [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the property does not exist, this API returns **undefined**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type                    | Description                                                       |
| ------------------------ | ----------------------------------------------------------- |
| T&nbsp;\|&nbsp;undefined | Value of the property corresponding to **propName** in AppStorage, or **undefined** if it does not exist. |

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let value: number = AppStorage.get('PropA') as number; // 47
```

### set<sup>10+</sup>

static set&lt;T&gt;(propName: string, newValue: T): boolean

Sets the value of the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the value of **newValue** is the same as the current value of the property, no assignment is performed, and the state variable does not instruct the UI to update the value of the property. Unlike [setOrCreate](#setorcreate10), **set** takes effect only when **propName** already exists, and returns **false** if **propName** does not exist.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description                  |
| -------- | ------ | ---- | ---------------------- |
| propName | string | Yes   | Property name in AppStorage.      |
| newValue | T | Yes | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **false** if the property corresponding to **propName** does not exist in AppStorage or if the assignment fails. Returns **true** if the assignment is successful.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 48);
let res: boolean = AppStorage.set('PropA', 47); // true
let res1: boolean = AppStorage.set('PropB', 47); // false
```

### setOrCreate<sup>10+</sup>

static setOrCreate&lt;T&gt;(propName: string, newValue: T): void

Sets the value of the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a new value, if the property exists and the new value is different from the current value. If the new value is the same as the current value of the property, no assignment is performed, and the state variable does not instruct the UI to update the value of the property.

If **propName** does not exist, this API creates it with the value of **newValue**. This **setOrCreate** API can create only one AppStorage key-value pair each time. To create multiple key-value pairs, call this API multiple times.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description                  |
| -------- | ------ | ---- | ---------------------- |
| propName | string | Yes   | Property name in AppStorage.      |
| newValue | T | Yes | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Example**

```ts
AppStorage.setOrCreate('simpleProp', 121);
```

### delete<sup>10+</sup>

static delete(propName: string): boolean

Deletes the property corresponding to **propName** from [AppStorage](../../../ui/state-management/arkts-appstorage.md).

The deletion is only successful if the property has no subscribers. If there is a subscriber, the deletion fails and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

The property subscribers include the following:

1. Variables decorated by [@StorageLink](../../../ui/state-management/arkts-appstorage.md#storagelink) and [@StorageProp](../../../ui/state-management/arkts-appstorage.md#storageprop).

2. Instances of [SubscribedAbstractProperty](#subscribedabstractproperty) returned by [link](#link10), [prop](#prop10), [setAndLink](#setandlink10), or [setAndProp](#setandprop10)

To delete these subscribers:

1. Remove the custom component containing \@StorageLink or \@StorageProp. For details, see [Custom Component Deletion](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#custom-component-deletion).

2. Call the [aboutToBeDeleted](#abouttobedeleted10) API on instances of **SubscribedAbstractProperty** returned by **link**, **prop**, **setAndLink**, or **setAndProp**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type     | Description                                      |
| ------- | ---------------------------------------- |
| boolean | Returns **true** if the operation is successful; returns **false** if the operation fails.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
AppStorage.link<number>('PropA');
let res: boolean = AppStorage.delete('PropA'); // false: PropA still has subscribers.

AppStorage.setOrCreate('PropB', 48);
let res1: boolean = AppStorage.delete('PropB'); // true: PropB is successfully deleted from AppStorage.
```

### keys<sup>10+</sup>

static keys(): IterableIterator&lt;string&gt;

Obtains all property names in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                            | Description                |
| ------------------------------ | ------------------ |
| IterableIterator&lt;string&gt; | All property names in AppStorage.|

**Example**

```ts
AppStorage.setOrCreate('PropB', 48);
let keys: IterableIterator<string> = AppStorage.keys();
```

### clear<sup>10+</sup>

static clear(): boolean

Deletes all properties from [AppStorage](../../../ui/state-management/arkts-appstorage.md). The deletion is only successful if none of the properties in AppStorage have any subscribers. If there are subscribers, this API does not take effect and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

For details about the subscriber, see [delete](#delete10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the properties in AppStorage have no subscribers and the deletion is successful; returns **false** if there are still subscribers.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let res: boolean = AppStorage.clear(); // true: There are no subscribers.
```

### size<sup>10+</sup>

static size(): number

Obtains the number of properties in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                 |
| ------ | ------------------- |
| number | Number of properties in AppStorage. |

**Example**

```ts
AppStorage.setOrCreate('PropB', 48);
let res: number = AppStorage.size(); // 1
```

### Link<sup>(deprecated)</sup>

static Link(propName: string): any

Establishes a two-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given property exists in AppStorage, the two-way bound data of the property in AppStorage is returned.

Any update of the data is synchronized back to AppStorage, which then synchronizes the update to all data and custom components bound to the property.

If the given property does not exist in AppStorage, **undefined** is returned.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [link](#link10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type                            | Description                                                        |
| -------------------------------- | ------------------------------------------------------------ |
| any | Two-way bound data of the specified property in AppStorage, or **undefined** if the property does not exist.|

**Example**

```ts
AppStorage.SetOrCreate('PropA', 47);
let linkToPropA1: SubscribedAbstractProperty<number> = AppStorage.Link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = AppStorage.Link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // Two-way synchronization: linkToPropA1.get() == linkToPropA2.get() == 48
```

### SetAndLink<sup>(deprecated)</sup>

static SetAndLink&lt;T&gt;(propName: string, defaultValue: T): SubscribedAbstractProperty&lt;T&gt;

Similar to the [Link](#linkdeprecated) API, establishes a two-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given property exists in AppStorage, this API returns the two-way bound data for the property. If the given property does not exist, this API creates and initializes the property in AppStorage using **defaultValue** and returns its two-way bound data. The value of **defaultValue** must be of the **T** type and cannot be **null** or **undefined**.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [setAndLink](#setandlink10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | Yes  | Property name in AppStorage.                                      |
| defaultValue | T      | Yes   | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. The value cannot be **null** or **undefined**. |

**Return value**

| Type                                 | Description                                      |
| ----------------------------------- | ---------------------------------------- |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | Instance of **SubscribedAbstractProperty&lt;T&gt;**, which is the two-way bound data of the property corresponding to **propName** in AppStorage. |

**Example**

```ts
AppStorage.SetOrCreate('PropA', 47);
let link1: SubscribedAbstractProperty<number> = AppStorage.SetAndLink('PropB', 49); // Create PropB with the default value 49.
let link2: SubscribedAbstractProperty<number> = AppStorage.SetAndLink('PropA', 50); // PropA already exists with the value 47.
```

### Prop<sup>(deprecated)</sup>

static Prop(propName: string): any

Establishes a one-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, the one-way bound data of the corresponding property in AppStorage is returned. If the given **propName** does not exist in AppStorage, **undefined** is returned. Modifications to the one-way bound data are not synchronized back to AppStorage.

> **NOTE**
>
> **Prop** supports only the **S** type (number, boolean, string).
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [prop](#prop10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type                            | Description                                                        |
| -------------------------------- | ------------------------------------------------------------ |
| any | One-way bound data of the specified property in AppStorage, or **undefined** if the property does not exist.|

**Example**

```ts
AppStorage.SetOrCreate('PropA', 47);
let prop1: SubscribedAbstractProperty<number> = AppStorage.Prop('PropA');
let prop2: SubscribedAbstractProperty<number> = AppStorage.Prop('PropA');
prop1.set(1); // One-way synchronization: prop1.get() returns 1, while prop2.get() returns 47.
```

### SetAndProp<sup>(deprecated)</sup>

static SetAndProp&lt;S&gt;(propName: string, defaultValue: S): SubscribedAbstractProperty&lt;S&gt;

Similar to the [Prop](#propdeprecated) API, establishes a one-way data binding with the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the given **propName** exists in AppStorage, this API returns the one-way bound data of the corresponding property. If the given **propName** does not exist, this API creates and initializes the property corresponding to **propName** in AppStorage using **defaultValue** and returns its one-way bound data. The value of **defaultValue** must be of the **S** type and cannot be **null** or **undefined**.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [setAndProp](#setandprop10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | Yes  | Property name in AppStorage.                                      |
| defaultValue | S      | Yes  | Default value used to initialize the property corresponding to **propName** in AppStorage if **propName** does not exist. The value cannot be **null** or **undefined**.|

**Return value**

| Type                                 | Description                                     |
| ----------------------------------- | --------------------------------------- |
| [SubscribedAbstractProperty&lt;S&gt;](#subscribedabstractproperty) | Instance of **SubscribedAbstractProperty&lt;S&gt;**, which is the one-way bound data of the property corresponding to **propName** in AppStorage. |

**Example**

```ts
AppStorage.SetOrCreate('PropA', 47);
let prop: SubscribedAbstractProperty<number> = AppStorage.SetAndProp('PropB', 49); // PropA -> 47, PropB -> 49
```

### Has<sup>(deprecated)</sup>

static Has(propName: string): boolean

Checks whether the property corresponding to **propName** exists in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [has](#has10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type     | Description                                      |
| ------- | ---------------------------------------- |
| boolean | Returns **true** if the property exists in AppStorage; returns **false** otherwise.|

**Example**

```ts
AppStorage.Has('simpleProp');
```

### Get<sup>(deprecated)</sup>

static Get&lt;T&gt;(propName: string): T \| undefined

Obtains the value of the property corresponding to **propName** from [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the property does not exist, this API returns **undefined**.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [get](#get10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type                    | Description                                                        |
| ------------------------ | ------------------------------------------------------------ |
| T&nbsp;\|&nbsp;undefined | Value of the property corresponding to **propName** in AppStorage, or **undefined** if it does not exist.|

**Example**

```ts
AppStorage.SetOrCreate('PropA', 47);
let value: number = AppStorage.Get('PropA') as number; // 47
```

### Set<sup>(deprecated)</sup>

static Set&lt;T&gt;(propName: string, newValue: T): boolean

Sets the value of the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the value of **newValue** is the same as the current value of the property corresponding to **propName**, no assignment is performed, and the state variable does not instruct the UI to update the value of the property. Unlike [SetOrCreate](#setorcreatedeprecated), **Set** takes effect only when **propName** already exists, and returns **false** if **propName** does not exist. Since API version 12, **newValue** can be **null** or **undefined**.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [set](#set10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                       |
| -------- | ------ | ---- | ------------------------------- |
| propName | string | Yes  | Property name in AppStorage.         |
| newValue | T | Yes | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **false** if the property corresponding to **propName** does not exist in AppStorage. Returns **true** if the operation is successful.|

**Example**

```ts
AppStorage.SetOrCreate('PropA', 48);
let res: boolean = AppStorage.Set('PropA', 47); // true
let res1: boolean = AppStorage.Set('PropB', 47); // false
```

### SetOrCreate<sup>(deprecated)</sup>

static SetOrCreate&lt;T&gt;(propName: string, newValue: T): void

Sets the value of the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a new value, if **propName** exists and the value of **newValue** is different from the value of the property corresponding to **propName**. If the new value is the same as the current value of the property, no assignment is performed, and the state variable does not instruct the UI to update the value of the property. If **propName** does not exist, this API creates it with the value of **newValue**. Since API version 12, **newValue** can be **null** or **undefined**.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [setOrCreate](#setorcreate10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                       |
| -------- | ------ | ---- | ------------------------------- |
| propName | string | Yes  | Property name in AppStorage.         |
| newValue | T      | Yes   | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**.|

**Example**

```ts
AppStorage.SetOrCreate('simpleProp', 121);
```

### Delete<sup>(deprecated)</sup>

static Delete(propName: string): boolean

Deletes the property corresponding to **propName** from [AppStorage](../../../ui/state-management/arkts-appstorage.md).

The deletion is only successful if the property has no subscribers. If there is a subscriber, the deletion fails and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

Subscribers include properties bound using [Link](#linkdeprecated) and [Prop](#propdeprecated) APIs, as well as those decorated with [@StorageLink](../../../ui/state-management/arkts-appstorage.md#storagelink) and [@StorageProp](../../../ui/state-management/arkts-appstorage.md#storageprop). This means that if there is still an **\@StorageLink('propName')**/**\@StorageProp('propName')** decorated variable or a **SubscribedAbstractProperty** instance in a synchronization with the property, the property cannot be deleted from AppStorage.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [delete](#delete10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type     | Description                                      |
| ------- | ---------------------------------------- |
| boolean | Returns **true** if the operation is successful; returns **false** if the operation fails.|

**Example**

```ts
AppStorage.SetOrCreate('PropA', 47);
AppStorage.Link('PropA');
let res: boolean = AppStorage.Delete('PropA'); // false: PropA still has subscribers.

AppStorage.SetOrCreate('PropB', 48);
let res1: boolean = AppStorage.Delete('PropB'); // true: PropB is successfully deleted from AppStorage.
```

### Keys<sup>(deprecated)</sup>

static Keys(): IterableIterator&lt;string&gt;

Obtains all property names in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [keys](#keys10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                            | Description                |
| ------------------------------ | ------------------ |
| IterableIterator&lt;string&gt; | All property names in AppStorage.|

**Example**

```ts
AppStorage.SetOrCreate('PropB', 48);
let keys: IterableIterator<string> = AppStorage.Keys();
```

### staticClear<sup>(deprecated)</sup>

static staticClear(): boolean

Deletes all properties from [AppStorage](../../../ui/state-management/arkts-appstorage.md). The deletion is only successful if none of the properties in AppStorage have any subscribers. If there are subscribers, this API does not take effect and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned. For details about the subscriber, see [delete](#delete10).

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [clear](#clear10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type     | Description                               |
| ------- | --------------------------------- |
| boolean | Result of deleting all properties from AppStorage. Returns **true** if the operation is successful; returns **false** otherwise. |

**Example**

```ts
let clearResult = AppStorage.staticClear();
```

### Clear<sup>(deprecated)</sup>

static Clear(): boolean

Deletes all properties from [AppStorage](../../../ui/state-management/arkts-appstorage.md). The deletion is only successful if none of the properties in AppStorage have any subscribers. If there are subscribers, this API does not take effect and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

For details about the subscriber, see [delete](#delete10).

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [clear](#clear10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```typescript
AppStorage.SetOrCreate('PropA', 47);
let res: boolean = AppStorage.Clear(); // true: There are no subscribers.
```

### IsMutable<sup>(deprecated)</sup>

static IsMutable(propName: string): boolean

Checks whether the property corresponding to **propName** in [AppStorage](../../../ui/state-management/arkts-appstorage.md) is mutable.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. There is no substitute API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description            |
| -------- | ------ | ---- | ---------------- |
| propName | string | Yes   | Property name in AppStorage.|

**Return value**

| Type     | Description                              |
| ------- | -------------------------------- |
| boolean | Whether the property corresponding to **propName** is mutable. Currently, this return value is always **true**.|

**Example**

```ts
AppStorage.SetOrCreate('PropA', 47);
let res: boolean = AppStorage.IsMutable('PropA');
```

### Size<sup>(deprecated)</sup>

static Size(): number

Obtains the number of properties in [AppStorage](../../../ui/state-management/arkts-appstorage.md).

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [size](#size10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type    | Description                 |
| ------ | ------------------- |
| number | Number of properties in AppStorage. |

**Example**

```ts
AppStorage.SetOrCreate('PropB', 48);
let res: number = AppStorage.Size(); // 1
```

## LocalStorage<sup>9+</sup>

A page-level UI state storage. The parameters received through the [@Entry](../../apis-arkui/arkui-ts/ts-universal-entry.md#entry) decorator can share the same **LocalStorage** instance within a page. For details about how to use it on the UI, see [LocalStorage: Storing Page-Level UI State](../../../ui/state-management/arkts-localstorage.md).

> **NOTE**
> 
> Since API version 12, LocalStorage supports [Map](../../../ui/state-management/arkts-localstorage.md#decorating-variables-of-the-map-type), [Set](../../../ui/state-management/arkts-localstorage.md#decorating-variables-of-the-set-type), [Date](../../../ui/state-management/arkts-localstorage.md#decorating-variables-of-the-date-type) types, as well as **null**, **undefined**, and [union types](../../../ui/state-management/arkts-localstorage.md#using-union-types-in-localstorage).

### constructor<sup>9+</sup>

constructor(initializingProperties?: Object)

Creates a [LocalStorage](../../../ui/state-management/arkts-localstorage.md) instance and initializes it using the property names and values returned by **Object.keys(initializingProperties)**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name                   | Type    | Mandatory  | Description                                    |
| ---------------------- | ------ | ---- | ---------------------------------------- |
| initializingProperties | Object | No | Properties and values used to initialize the **LocalStorage** instance. This parameter is passed when property data is preset during creation. Its keys serve as property names in **LocalStorage**, and values are the initial values of the corresponding properties. **initializingProperties** cannot be set to **undefined**. If not passed, the default value is an empty object, indicating **LocalStorage** contains no preset properties. |

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
```

### getShared<sup>(deprecated)</sup>

static getShared(): LocalStorage

Obtains the [LocalStorage](../../../ui/state-management/arkts-localstorage.md) instance shared across the current stage.

> **NOTE**
> 
> This API is supported since API version 10 and deprecated since API version 18. You are advised to use [getSharedLocalStorage](../arkts-apis-uicontext-uicontext.md#getsharedlocalstorage12) in [UIContext](../arkts-apis-uicontext-uicontext.md) instead.
>
> Since API version 12, you can use [getSharedLocalStorage](../arkts-apis-uicontext-uicontext.md#getsharedlocalstorage12) in [UIContext](../arkts-apis-uicontext-uicontext.md) to specify the **LocalStorage** instance in the UI execution context.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                            | Description               |
| ------------------------------ | ----------------- |
| [LocalStorage](#localstorage9) | **LocalStorage** instance shared across the current stage. |

### has<sup>9+</sup>

has(propName: string): boolean

Checks whether the property corresponding to **propName** exists in [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description              |
| -------- | ------ | ---- | ------------------ |
| propName | string | Yes   | Property name in LocalStorage.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the property exists in LocalStorage; returns **false** otherwise.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
storage.has('PropA'); // true
```

### get<sup>9+</sup>

get&lt;T&gt;(propName: string): T \| undefined

Obtains the value of the property corresponding to **propName** from [LocalStorage](../../../ui/state-management/arkts-localstorage.md). If **propName** does not exist, **undefined** is returned.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description              |
| -------- | ------ | ---- | ------------------ |
| propName | string | Yes   | Property name in LocalStorage.|

**Return value**

| Type                    | Description                                                        |
| ------------------------ | ------------------------------------------------------------ |
| T&nbsp;\|&nbsp;undefined | Value of the property corresponding to **propName** in LocalStorage, or **undefined** if it does not exist.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let value: number = storage.get('PropA') as number; // 47
```

### set<sup>9+</sup>

set&lt;T&gt;(propName: string, newValue: T): boolean

Sets the value of the property corresponding to **propName** in [LocalStorage](../../../ui/state-management/arkts-localstorage.md). If the value of **newValue** is the same as the current value of the property corresponding to **propName**, no assignment is performed and the state variable does not instruct the UI to update the value of the property. Unlike [setOrCreate](#setorcreate9), **set** takes effect only when **propName** already exists, and returns **false** if **propName** does not exist.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description                   |
| -------- | ------ | ---- | ----------------------- |
| propName | string | Yes   | Property name in LocalStorage.     |
| newValue | T | Yes | New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **false** if the property corresponding to **propName** does not exist in LocalStorage. Returns **true** if the operation is successful.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: boolean = storage.set('PropA', 47); // true
let res1: boolean = storage.set('PropB', 47); // false
```

### setOrCreate<sup>9+</sup>

setOrCreate&lt;T&gt;(propName: string, newValue: T): boolean

Sets the value of the property corresponding to **propName** in [LocalStorage](../../../ui/state-management/arkts-localstorage.md) to a new value, if the property exists and the new value is different from the current value. If the new value is the same as the current value of the property, no assignment is performed, and the state variable does not instruct the UI to update the value of the property.

If **propName** does not exist, this API creates it with the value of **newValue**. This **setOrCreate** API can create only one LocalStorage key-value pair each time. To create multiple key-value pairs, call this API multiple times.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description                   |
| -------- | ------ | ---- | ----------------------- |
| propName | string | Yes   | Property name in LocalStorage.     |
| newValue | T | Yes| New value of the property corresponding to **propName**. Since API version 12, the value can be **null** or **undefined**. |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the property corresponding to **propName** exists and its value is updated to the value of **newValue**, or if **propName** is created with the value of **newValue**.<br>Before API version 12, **false** is returned when the value of **newValue** is **null** or **undefined**. |

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: boolean = storage.setOrCreate('PropA', 121); // true
let res1: boolean = storage.setOrCreate('PropB', 111); // true
let res2: boolean = storage.setOrCreate('PropB', null); // true (returns true since API version 12, and returns false in API version 11 and earlier)
```

### ref<sup>12+</sup>

ref\<T\>(propName: string): AbstractProperty\<T\>&nbsp;\|&nbsp;undefined

Returns a reference to the property corresponding to **propName** in [LocalStorage](../../../ui/state-management/arkts-localstorage.md). If the provided **propName** does not exist, this API returns **undefined**.

This API is basically the same as [link](#link9), except that it does not require manual release of the returned variable of the [AbstractProperty&lt;T&gt;](#abstractpropertyt12) type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                |
| -------- | ------ | ---- | ------------------------ |
| propName | string | Yes  | Property name in LocalStorage.|

**Return value**

| Type                                  | Description                                                        |
| -------------------------------------- | ------------------------------------------------------------ |
| [AbstractProperty&lt;T&gt;](#abstractpropertyt12) \| undefined | Reference to the property corresponding to **propName** in LocalStorage. If the corresponding **propName** does not exist in LocalStorage, **undefined** is returned. |

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let refToPropA1: AbstractProperty<number> | undefined = storage.ref('PropA');
let refToPropA2: AbstractProperty<number> | undefined = storage.ref('PropA'); // refToPropA2.get() == 47
refToPropA1?.set(48); // refToPropA1.get() == refToPropA2.get() == 48
```

### setAndRef<sup>12+</sup>

setAndRef&lt;T&gt;(propName: string, defaultValue: T): AbstractProperty&lt;T&gt;

Similar to the [ref](#ref12-1) API, returns a reference to the property corresponding to **propName** in [LocalStorage](../../../ui/state-management/arkts-localstorage.md). If the given property does not exist, this API creates and initializes the property in LocalStorage using **defaultValue** and returns its reference.

This API is basically the same as [setAndLink](#setandlink9), except that it does not require manual release of the returned variable of the [AbstractProperty&lt;T&gt;](#abstractpropertyt12) type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | Yes  | Property name in LocalStorage.                                    |
| defaultValue | T      | Yes  | Default value used to initialize the property corresponding to **propName** in LocalStorage if **propName** does not exist. The value can be **null** or **undefined**.|

**Return value**

| Type                     | Description                                                        |
| ------------------------- | ------------------------------------------------------------ |
| [AbstractProperty&lt;T&gt;](#abstractpropertyt12) | Instance of **AbstractProperty&lt;T&gt;**, which is a reference to the property corresponding to **propName** in LocalStorage. |

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let ref1: AbstractProperty<number> = storage.setAndRef('PropB', 49); // Create PropB with the default value 49.
let ref2: AbstractProperty<number> = storage.setAndRef('PropA', 50); // PropA already exists with the value 47.
```

### link<sup>9+</sup>

link&lt;T&gt;(propName: string): SubscribedAbstractProperty&lt;T&gt;

Establishes a two-way data binding with the property corresponding to **propName** in [LocalStorage](../../../ui/state-management/arkts-localstorage.md). If the given **propName** exists in LocalStorage, the two-way bound data of the corresponding property in LocalStorage is returned. Unlike the one-way data binding of [prop](#prop9), **link** establishes a two-way data binding, where modifications are synchronized back to LocalStorage, and LocalStorage synchronizes the changes to all data and custom components bound to this **propName**.

If the given property does not exist in LocalStorage, **undefined** is returned.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description              |
| -------- | ------ | ---- | ------------------ |
| propName | string | Yes   | Property name in LocalStorage.|

**Return value**

| Type                               | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | Returns the **SubscribedAbstractProperty&lt;T&gt;** instance if the given property exists in LocalStorage; returns **undefined** otherwise.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let linkToPropA1: SubscribedAbstractProperty<number> = storage.link('PropA');
let linkToPropA2: SubscribedAbstractProperty<number> = storage.link('PropA'); // linkToPropA2.get() == 47
linkToPropA1.set(48); // Two-way synchronization: linkToPropA1.get() == linkToPropA2.get() == 48
```

### setAndLink<sup>9+</sup>

setAndLink&lt;T&gt;(propName: string, defaultValue: T): SubscribedAbstractProperty&lt;T&gt;

Similar to the [link](#link9) API, establishes a two-way data binding with the property corresponding to **propName** in [LocalStorage](../../../ui/state-management/arkts-localstorage.md). If the given property exists in LocalStorage, this API returns the two-way bound data for the property. If the given property does not exist, this API creates and initializes the property in LocalStorage using **defaultValue** and returns its two-way bound data.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | Yes  | Property name in LocalStorage.                                    |
| defaultValue | T | Yes | Default value used to initialize the property corresponding to **propName** in LocalStorage if **propName** does not exist. Since API version 12, **defaultValue** can be **null** or **undefined**. |

**Return value**

| Type                               | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;T&gt;](#subscribedabstractproperty) | Instance of **SubscribedAbstractProperty&lt;T&gt;** and two-way bound data of the given property in LocalStorage.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let link1: SubscribedAbstractProperty<number> = storage.setAndLink('PropB', 49); // Create PropB with the default value 49.
let link2: SubscribedAbstractProperty<number> = storage.setAndLink('PropA', 50); // PropA already exists with the value 47.
```

### prop<sup>9+</sup>

prop&lt;S&gt;(propName: string): SubscribedAbstractProperty&lt;S&gt;

Establishes a one-way data binding with the property corresponding to propName in [LocalStorage](../../../ui/state-management/arkts-localstorage.md). If the given **propName** exists in LocalStorage, the one-way bound data of the corresponding property in LocalStorage is returned. If **propName** does not exist in LocalStorage, **undefined** is returned. Modifications to the one-way bound data are not synchronized back to LocalStorage.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description              |
| -------- | ------ | ---- | ------------------ |
| propName | string | Yes   | Property name in LocalStorage.|

**Return value**

| Type                               | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;S&gt;](#subscribedabstractproperty) | Instance of **SubscribedAbstractProperty&lt;S&gt;**, which is the one-way bound data of the property corresponding to **propName** in LocalStorage. If the corresponding **propName** does not exist in LocalStorage, **undefined** is returned. |

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let prop1: SubscribedAbstractProperty<number> = storage.prop('PropA');
let prop2: SubscribedAbstractProperty<number> = storage.prop('PropA');
prop1.set(1); // One-way synchronization: prop1.get() returns 1, while prop2.get() returns 47.
```

### setAndProp<sup>9+</sup>

setAndProp&lt;S&gt;(propName: string, defaultValue: S): SubscribedAbstractProperty&lt;S&gt;

Similar to the [prop](#prop9) API, establishes a one-way data binding with the property corresponding to propName in [LocalStorage](../../../ui/state-management/arkts-localstorage.md). If the given **propName** exists in LocalStorage, the one-way bound data of the corresponding property is returned. If the given **propName** does not exist, this API creates and initializes the property corresponding to **propName** in LocalStorage using **defaultValue** and returns its one-way bound data.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| propName     | string | Yes  | Property name in LocalStorage.                                    |
| defaultValue | S | Yes | Default value used to initialize the property corresponding to **propName** in LocalStorage if **propName** does not exist in LocalStorage. Since API version 12, **defaultValue** can be **null** or **undefined**. |

**Return value**

| Type                               | Description                                                        |
| ----------------------------------- | ------------------------------------------------------------ |
| [SubscribedAbstractProperty&lt;S&gt;](#subscribedabstractproperty) | Instance of **SubscribedAbstractProperty&lt;S&gt;**, which is the one-way bound data of the property corresponding to **propName** in LocalStorage. |

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let prop: SubscribedAbstractProperty<number> = storage.setAndProp('PropB', 49); // PropA -> 47, PropB -> 49
```

### delete<sup>9+</sup>

delete(propName: string): boolean

Deletes the property corresponding to **propName** from [LocalStorage](../../../ui/state-management/arkts-localstorage.md). The deletion is only successful if the property has no subscribers. If there is a subscriber, the deletion fails and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

The property subscribers include the following:

1. Variables decorated by [@LocalStorageLink](../../../ui/state-management/arkts-localstorage.md#localstoragelink) and [@LocalStorageProp](../../../ui/state-management/arkts-localstorage.md#localstorageprop).

2. Instances of [SubscribedAbstractProperty](#subscribedabstractproperty) returned by [link](#link9), [prop](#prop9), [setAndLink](#setandlink9), or [setAndProp](#setandprop9)

To delete these subscribers:

1. Remove the custom component containing \@LocalStorageLink or \@LocalStorageProp. For details, see [Custom Component Deletion](../../../ui/state-management/arkts-page-custom-components-lifecycle.md#custom-component-deletion).

2. Call the [aboutToBeDeleted](#abouttobedeleted10) API on instances of **SubscribedAbstractProperty** returned by **link**, **prop**, **setAndLink**, or **setAndProp**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type    | Mandatory  | Description              |
| -------- | ------ | ---- | ------------------ |
| propName | string | Yes   | Property name in LocalStorage.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the operation is successful; returns **false** if the operation fails.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
storage.link<number>('PropA');
let res: boolean = storage.delete('PropA'); // false: PropA still has subscribers.
let res1: boolean = storage.delete('PropB'); // false: PropB does not exist in LocalStorage.
storage.setOrCreate('PropB', 48);
let res2: boolean = storage.delete('PropB'); // true: PropB is successfully deleted from LocalStorage.
```

### keys<sup>9+</sup>

keys(): IterableIterator&lt;string&gt;

Obtains all property names in [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                            | Description                  |
| ------------------------------ | -------------------- |
| IterableIterator&lt;string&gt; | All property names in LocalStorage.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let keys: IterableIterator<string> = storage.keys();
```

### size<sup>9+</sup>

size(): number

Obtains the number of properties in [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type  | Description                        |
| ------ | ---------------------------- |
| number | Number of properties in LocalStorage.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: number = storage.size(); // 1
```

### clear<sup>9+</sup>

clear(): boolean

Deletes all properties from [LocalStorage](../../../ui/state-management/arkts-localstorage.md). The deletion is only successful if none of the properties in LocalStorage have any subscribers. If there are subscribers, this API does not take effect and **false** is returned. If there are no subscribers, the deletion is successful and **true** is returned.

For details about the subscriber, see [delete](#delete9).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise.|

**Example**

```ts
let initialData: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(initialData);
let res: boolean = storage.clear(); // true: There are no subscribers.
```

### GetShared<sup>(deprecated)</sup>

static GetShared(): LocalStorage

Obtains the [LocalStorage](../../../ui/state-management/arkts-localstorage.md) instance shared across the current stage.

> **NOTE**
> 
> This API is supported since API version 9 and deprecated since API version 10. You are advised to use [getSharedLocalStorage](../arkts-apis-uicontext-uicontext.md#getsharedlocalstorage12) in [UIContext](../arkts-apis-uicontext-uicontext.md) instead.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                            | Description               |
| ------------------------------ | ----------------- |
| [LocalStorage](#localstorage9) | **LocalStorage** instance shared across the current stage. |

**Example**

```ts
let storage: LocalStorage = LocalStorage.GetShared();
```

## AbstractProperty\<T\><sup>12+</sup>

A reference to a property in AppStorage or LocalStorage. It provides the capabilities to read and modify referenced property data and query property names. Unlike **SubscribedAbstractProperty**, an **AbstractProperty** instance does not need to be manually released.

> **NOTE**
>
> Since API version 12, AppStorage and LocalStorage support the **Map**, **Set**, and **Date** types, as well as **null**, **undefined**, and union types.

### get<sup>12+</sup>

get(): T

Reads data of the referenced property from [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type| Description                                       |
| ---- | ------------------------------------------- |
| T    | Data of the referenced property in AppStorage or LocalStorage.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
ref1?.get(); // ref1.get()=47
```

### set<sup>12+</sup>

set(newValue: T): void

Updates the data of the referenced property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). The value of **newValue** must be of the **T** type and can be **null** or **undefined**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type| Mandatory| Description                             |
| -------- | ---- | ---- | ------------------------------------- |
| newValue | T    | Yes   | New value of the property referenced in AppStorage/LocalStorage. The value can be **null** or **undefined**. |

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
ref1?.set(1); // ref1.get()=1
let mapValue: Map<string, number> = new Map([['1', 0]]);
let ref2 = AppStorage.setAndRef('MapA', mapValue);
ref2.set(mapValue);
let setValue: Set<string> = new Set(['1']);
let ref3 = AppStorage.setAndRef('SetB', setValue);
ref3.set(setValue);
let dateValue: Date = new Date('2024');
let ref4 = AppStorage.setAndRef('DateC', dateValue);
ref4.set(dateValue);
ref2.set(null);
ref3.set(undefined);
```

### info<sup>12+</sup>

info(): string

Reads the property name of the referenced property from [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type  | Description                                         |
| ------ | --------------------------------------------- |
| string | Property name of the referenced property in AppStorage or LocalStorage.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let ref1: AbstractProperty<number> | undefined = AppStorage.ref('PropA');
ref1?.info(); // ref1.info()='PropA'
```

## SubscribedAbstractProperty

An object of a one-way or two-way synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). It is used to establish a data synchronization relationship with a property in AppStorage or LocalStorage. A **SubscribedAbstractProperty** instance needs to be manually released through the [aboutToBeDeleted](#abouttobedeleted10) API to cancel the synchronization relationship and invalidate the instance.

> **NOTE**
> 
> Since API version 12, AppStorage and LocalStorage support the **Map**, **Set**, and **Date** types, as well as **null**, **undefined**, and union types.

### get<sup>9+</sup>

abstract get(): T

Reads the data of the synchronized property from [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type  | Description                             |
| ---- | ------------------------------- |
| T    | Data of the synchronized property in AppStorage or LocalStorage.|

**Example**

```ts
AppStorage.setOrCreate('PropA', 47); 
let prop1: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');    
prop1.get(); // prop1.get()=47
```

### set<sup>9+</sup>

abstract set(newValue: T): void

Sets the data of the synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). The value of **newValue** must be of the **T** type. Since API version 12, it can be **null** or **undefined**.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type| Mandatory| Description                                                 |
| -------- | ---- | ---- | --------------------------------------------------------- |
| newValue | T | Yes | New value of the synchronized property in AppStorage or LocalStorage. Since API version 12, the value can be **null** or **undefined**. |

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let prop1: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
prop1.set(1); // prop1.get()=1
// Since API version 12, the Map, Set, and Date types, as well as null, undefined, and union types are supported.
let mapValue: Map<string, number> = new Map([['1', 0]]);
let prop2 = AppStorage.setAndProp('MapA', mapValue);
prop2.set(mapValue);
let setValue: Set<string> = new Set(['1']);
let prop3 = AppStorage.setAndProp('SetB', setValue);
prop3.set(setValue);
let dateValue: Date = new Date('2024');
let prop4 = AppStorage.setAndProp('DateC', dateValue);
prop4.set(dateValue);
prop2.set(null);
prop3.set(undefined);
```

### aboutToBeDeleted<sup>10+</sup>

abstract aboutToBeDeleted(): void

Cancels the one-way or two-way synchronization relationship between the [SubscribedAbstractProperty](#subscribedabstractproperty) instance and [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md), and invalidates the **SubscribedAbstractProperty** instance. That is, after **aboutToBeDeleted** is called, [set](#set9-1) or [get](#get9-1) can no longer be called using the **SubscribedAbstractProperty** instance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
AppStorage.setOrCreate('PropA', 47);
let link = AppStorage.setAndLink('PropB', 49); // PropA -> 47, PropB -> 49
link.aboutToBeDeleted();
```

### info<sup>10+</sup>

info(): string

Returns the name of the synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|Type  |Description    |
|---------|-------------|
| string | Name of the property synchronized in AppStorage or LocalStorage. |

**Example**

```ts
AppStorage.setOrCreate('PropA', 47); 
let prop1: SubscribedAbstractProperty<number> = AppStorage.prop('PropA');
prop1.info(); // prop1.info() = 'PropA'
```

## PersistPropsOptions<sup>10+</sup>

Defines a key-value pair object used to specify persistent properties and their default values, passed as a parameter to [persistProps](#persistprops10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                                 | Read-Only                           | Optional| Description                                                    |
| ------------ | ------------------------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| key          | string                                | No                               | No  | Property name.                                                     |
| defaultValue | number \| string \| boolean \| Object | No | No | Default value used for initialization if the specified **key** is not found in PersistentStorage or AppStorage. Since API version 12, **defaultValue** can be **null** or **undefined**. |

## PersistentStorage

Provides the persistent storage capability for UI states. It persists selected AppStorage properties to a file and restores these property values from the file and writes them to AppStorage when applications restart. For details about how to use it on the UI, see [PersistentStorage: Persisting Application State](../../../ui/state-management/arkts-persiststorage.md).

> **NOTE**
>
> Since API version 12, PersistentStorage supports **null** and **undefined**.

### persistProp<sup>10+</sup>

static persistProp&lt;T&gt;(key: string, defaultValue: T): void

Persists the property corresponding to **key** from [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a file. This API is usually called before access to AppStorage.

The order for determining the type and value of a property is as follows:

1. If the property corresponding to **key** exists in the [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md) file, the corresponding key is created in AppStorage and initialized with the property value found in PersistentStorage.

2. If the property with the specified key is not found in the PersistentStorage file, AppStorage is searched for the property. If the property is found, it is persisted.

3. If no matching property is found in AppStorage, it is created in AppStorage, initialized with the value of **defaultValue**, and persisted.

According to the preceding initialization process, if the property exists in AppStorage, its value will overwrite the value in the PersistentStorage file. Since AppStorage stores data in memory, this operation causes the data in the persistent file to be overwritten by the in-memory data, making the persistent data meaningless.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| key          | string | Yes  | Property name.                                                     |
| defaultValue | T      | Yes  | Default value used for initialization if the specified **key** is not found in PersistentStorage or AppStorage. Since API version 12, the value can be **null** or **undefined**. |

**Example**

For details about how to use **persistProp**, see [Accessing a PersistentStorage-Initialized Property from AppStorage](../../../ui/state-management/arkts-persiststorage.md#accessing-a-persistentstorage-initialized-property-from-appstorage).

### deleteProp<sup>10+</sup>

static deleteProp(key: string): void

Performs the reverse operation of [persistProp](#persistprop10). It deletes the property corresponding to **key** from [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md), after which subsequent operations on [AppStorage](../../../ui/state-management/arkts-appstorage.md) no longer affect PersistentStorage. To persist the property again, call the [persistProp](#persistprop10) API again.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type    | Mandatory  | Description                   |
| ---- | ------ | ---- | ----------------------- |
| key  | string | Yes   | Property name in PersistentStorage.|

**Example**

```ts
PersistentStorage.deleteProp('highScore');
```

### persistProps<sup>10+</sup>

static persistProps(props: PersistPropsOptions[]): void

Persists multiple properties. This API is similar to [persistProp](#persistprop10), but allows multiple properties to be persisted at once, making it suitable for initializing during application startup. This API is usually called before access to AppStorage.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name       | Type                                      | Mandatory  | Description                                    |
| ---------- | ---------------------------------------- | ---- | ---------------------------------------- |
| props | [PersistPropsOptions](#persistpropsoptions10)[] | Yes | Array of properties to persist, where each item contains a property name and a default value. |

**Example**

```ts
PersistentStorage.persistProps([{ key: 'highScore', defaultValue: '0' }, { key: 'weightScore', defaultValue: '1' }]);
```

### keys<sup>10+</sup>

static keys(): Array&lt;string&gt;

Returns an array of all persisted property names.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type               | Description                              |
| ------------------- | ---------------------------------- |
| Array&lt;string&gt; | Returns an array of all persisted property names.|

**Example**

```ts
let keys: Array<string> = PersistentStorage.keys();
```

### PersistProp<sup>(deprecated)</sup>

static PersistProp&lt;T&gt;(key: string, defaultValue: T): void

Persists the property corresponding to **key** in [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a file. This API is usually called before access to AppStorage.

The order for determining the type and value of a property is as follows:

1. If the property corresponding to **key** exists in the [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md) file, the corresponding key is created in AppStorage and initialized with the property value found in PersistentStorage.

2. If the property with the specified key is not found in the PersistentStorage file, AppStorage is searched for the property. If the property is found, it is persisted.

3. If no matching property is found in AppStorage, it is created in AppStorage, initialized with the value of **defaultValue**, and persisted.

According to the preceding initialization process, if the property exists in AppStorage, its value will overwrite the value in the PersistentStorage file. Since AppStorage stores data in memory, this operation causes the data in the persistent file to be overwritten by the in-memory data, making the persistent data meaningless.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [persistProp](#persistprop10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type  | Mandatory| Description                                                    |
| ------------ | ------ | ---- | ------------------------------------------------------------ |
| key          | string | Yes  | Property name.                                                     |
| defaultValue | T      | Yes  | Default value used for initialization if the specified **key** is not found in PersistentStorage or AppStorage. The default value cannot be **null** or **undefined**. |

**Example**

```ts
PersistentStorage.PersistProp('highScore', '0');
```

### DeleteProp<sup>(deprecated)</sup>

static DeleteProp(key: string): void

Performs the reverse operation of [PersistProp](#persistpropdeprecated). It deletes the property corresponding to **key** from [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md), after which subsequent operations on [AppStorage](../../../ui/state-management/arkts-appstorage.md) no longer affect PersistentStorage. To persist the property again, call the [PersistProp](#persistpropdeprecated) API again.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [deleteProp](#deleteprop10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type    | Mandatory  | Description                   |
| ---- | ------ | ---- | ----------------------- |
| key  | string | Yes   | Property name in PersistentStorage.|

**Example**

```ts
PersistentStorage.DeleteProp('highScore');
```

### PersistProps<sup>(deprecated)</sup>

static PersistProps(properties: {key: string; defaultValue: any;}[]): void

Persists multiple properties. This API is similar to [PersistProp](#persistpropdeprecated), but allows multiple properties to be persisted at once, making it suitable for initializing during application startup. This API should be called before access to AppStorage.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [persistProps](#persistprops10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                              | Mandatory| Description                                                    |
| ---------- | ---------------------------------- | ---- | ------------------------------------------------------------ |
| properties | {key: string; defaultValue: any}[] | Yes | Array of properties to persist, where **key** indicates the property name and **defaultValue** indicates the default value. The rules are the same as those of **PersistProp**. |

**Example**

```ts
PersistentStorage.PersistProps([{ key: 'highScore', defaultValue: '0' }, { key: 'weightScore', defaultValue: '1' }]);
```

### Keys<sup>(deprecated)</sup>

static Keys(): Array&lt;string&gt;

Returns an array of all persisted property names.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [keys](#keys10-1) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type               | Description                              |
| ------------------- | ---------------------------------- |
| Array&lt;string&gt; | Returns an array of all persisted property names.|

**Example**

```ts
let keys: Array<string> = PersistentStorage.Keys();
```

## EnvPropsOptions<sup>10+</sup>

Defines a key-value pair object used to specify environment variable names and their default values, passed as a parameter to [envProps](#envprops10).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type                       | Read-Only            | Optional| Description                                                    |
| ------------ | --------------------------- | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| key          | string                      | No                    | No | Environment variable name. For details about the value range, see [Built-in Environment Variables](#built-in-environment-variables).|
| defaultValue | number \| string \| boolean | No| No | Default value used if the value of the specified environment variable key is not found in AppStorage.|

## Environment

Provides the capability to query device environment states. It can inject system environment variables (such as the dark/light mode, language, font scale, and layout direction) into AppStorage, enabling applications to perceive and respond to device environment changes. For details about how to use it on the UI, see [Environment: Device Environment Query](../../../ui/state-management/arkts-environment.md).

### envProp<sup>10+</sup>

static envProp&lt;S&gt;(key: string, value: S): boolean

Stores the built-in environment variable key of [Environment](../../../ui/state-management/arkts-environment.md) into [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the value of the environment variable key is not found in AppStorage, the default value is used and stored in AppStorage. If the value is successfully stored, **true** is returned. If the value of the environment variable key already exists in AppStorage, **false** is returned.

If **envProp** is not called, reading environment variables directly from AppStorage will fail to obtain the corresponding environment variable values. You are advised to call this API at application startup.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                    |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| key    | string | Yes  | Environment variable name. For details about the value range, see [Built-in Environment Variables](#built-in-environment-variables).|
| value  | S      | Yes  | Default value used if the value of the environment variable key is not found in AppStorage.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **false** if the property corresponding to the key exists in AppStorage; creates a property with the key and the default value and returns **true** otherwise.|

**Example**

For details about how to use **envProp**, see [Accessing Environment Parameters from the UI](../../../ui/state-management/arkts-environment.md#accessing-environment-parameters-from-the-ui).

### envProps<sup>10+</sup>

static envProps(props: EnvPropsOptions[]): void

Works in a way similar to the [envProp](#envprop10) API, with the difference that it allows for initialization of multiple properties in batches. If **envProps** is not called, reading environment variables directly from AppStorage will fail to obtain the corresponding environment variable values. You are advised to call this API at application startup to store system environment variables in batches into [AppStorage](../../../ui/state-management/arkts-appstorage.md).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                         | Mandatory| Description                            |
| ------ | --------------------------------------------- | ---- | ------------------------------------ |
| props  | [EnvPropsOptions](#envpropsoptions10)[] | Yes  | Array of key-value pairs consisting of system environment variables and default values.|

**Example**

```ts
Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);
```

### keys<sup>10+</sup>

static keys(): Array&lt;string&gt;

Returns the property key array of environment variables.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                 | Description         |
| ------------------- | ----------- |
| Array&lt;string&gt; | Array of property keys of environment variables. |

**Example**

```ts
Environment.envProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);

let keys: Array<string> = Environment.keys(); // keys contains accessibilityEnabled, languageCode, and prop.
```

### EnvProp<sup>(deprecated)</sup>

static EnvProp&lt;S&gt;(key: string, value: S): boolean

Stores the built-in environment variable key of [Environment](../../../ui/state-management/arkts-environment.md) into [AppStorage](../../../ui/state-management/arkts-appstorage.md). If the value of the environment variable key is not found in AppStorage, the default value is used and stored in AppStorage. If the value is successfully stored, **true** is returned. If the value of the environment variable key already exists in AppStorage, **false** is returned.

If **EnvProp** is not called, reading environment variables directly from AppStorage will fail to obtain the corresponding environment variable values. You are advised to call this API at application startup.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [envProp](#envprop10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                    |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| key    | string | Yes  | Environment variable name. For details about the value range, see [Built-in Environment Variables](#built-in-environment-variables).|
| value  | S      | Yes   | Default value used if the value of the environment variable key is not found in AppStorage. |

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **false** if the property corresponding to the key exists in AppStorage; creates a property with the key and the default value and returns **true** otherwise.|

**Example**

```ts
Environment.EnvProp('accessibilityEnabled', 'default');
```

### EnvProps<sup>(deprecated)</sup>

static EnvProps(props: {key: string; defaultValue: any;}[]): void

Works in a way similar to the [EnvProp](#envpropdeprecated) API, with the difference that it allows for initialization of multiple properties in batches. If **EnvProps** is not called, reading environment variables directly from AppStorage will fail to obtain the corresponding environment variable values. You are advised to call this API at application startup to store system environment variables in batches into [AppStorage](../../../ui/state-management/arkts-appstorage.md).

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [envProps](#envprops10) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                             | Mandatory| Description                            |
| ------ | ------------------------------------------------- | ---- | ------------------------------------ |
| props  | {key:&nbsp;string; &nbsp;defaultValue:&nbsp;any}[] | Yes  | Array of key-value pairs consisting of system environment variables and default values.|

**Example**

```ts
Environment.EnvProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);
```

### Keys<sup>(deprecated)</sup>

static Keys(): Array&lt;string&gt;

Returns the property key array of environment variables.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [keys](#keys10-2) instead.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                 | Description         |
| ------------------- | ----------- |
| Array&lt;string&gt; | Array of property keys of environment variables. |

**Example**

```ts
Environment.EnvProps([{ key: 'accessibilityEnabled', defaultValue: 'default' }, {
  key: 'languageCode',
  defaultValue: 'en'
}, { key: 'prop', defaultValue: 'hhhh' }]);

let keys: Array<string> = Environment.Keys(); // keys contains accessibilityEnabled, languageCode, and prop.
```

## Built-in Environment Variables

| key                  | Type           | Description                                                        |
| -------------------- | --------------- | ------------------------------------------------------------ |
| accessibilityEnabled | string          | Whether to enable accessibility. If there is no value of **accessibilityEnabled** in the environment variables, the default value passed through APIs such as **envProp** and **envProps** is added to AppStorage.|
| colorMode            | [ColorMode](./ts-state-management-environment-variables.md#colormode)       | Color mode. The options are as follows:<br>-&nbsp;**ColorMode.LIGHT**: light mode.<br>-&nbsp;**ColorMode.DARK**: dark mode. |
| fontScale            | number          | Font scale.                                              |
| fontWeightScale      | number          | Font weight ratio.                                                  |
| layoutDirection      | [LayoutDirection](./ts-state-management-environment-variables.md#layoutdirection) | Layout direction. The options are as follows:<br>-&nbsp;**LayoutDirection.LTR**: left to right;<br>-&nbsp;**LayoutDirection.RTL**: right to left;<br>-&nbsp;**LayoutDirection.Auto**: follows the system settings. |
| languageCode         | string          | Current system language, which is in lowercase letters, for example, **zh**.                            |