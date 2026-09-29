# PersistentStorage

```TypeScript
declare class PersistentStorage
```

Provides the persistent storage capability for UI states. It persists selected AppStorage properties to a file and restores these property values from the file and writes them to AppStorage when applications restart. For details about how to use it on the UI, see [PersistentStorage: Persisting Application State](../../../ui/state-management/arkts-persiststorage.md).

> **NOTE:** 

> Since API version 12, PersistentStorage supports **null** and **undefined**.

**Since:** 7

<!--Device-unnamed-declare class PersistentStorage--><!--Device-unnamed-declare class PersistentStorage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## deleteProp

```TypeScript
static deleteProp(key: string): void
```

Performs the reverse operation of [persistProp](#persistprop). It deletes the property corresponding to **key** from [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md), after which subsequent operations on [AppStorage](../../../ui/state-management/arkts-appstorage.md) no longer affect PersistentStorage. To persist the property again, call the [persistProp](#persistprop) API again.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PersistentStorage-static deleteProp(key: string): void--><!--Device-PersistentStorage-static deleteProp(key: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Property name in PersistentStorage. |

**Examples**

```TypeScript
PersistentStorage.deleteProp('highScore');
```

## keys

```TypeScript
static keys(): Array<string>
```

Returns an array of all persisted property names.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PersistentStorage-static keys(): Array<string>--><!--Device-PersistentStorage-static keys(): Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Returns an array of all persisted property names. |

**Examples**

```TypeScript
let keys: Array<string> = PersistentStorage.keys();
```

## persistProp

```TypeScript
static persistProp<T>(key: string, defaultValue: T): void
```

Persists the property corresponding to **key** from [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a file. This API is usually called before access to AppStorage.

The order for determining the type and value of a property is as follows:

1. If the property corresponding to **key** exists in the
[PersistentStorage](../../../ui/state-management/arkts-persiststorage.md) file, the corresponding key is created in AppStorage and initialized with the property value found in PersistentStorage.
2. If the property with the specified key is not found in the PersistentStorage file, AppStorage is searched for
the property. If the property is found, it is persisted.
3. If no matching property is found in AppStorage, it is created in AppStorage, initialized with the value of  
**defaultValue**, and persisted.

According to the preceding initialization process, if the property exists in AppStorage, its value will overwrite the value in the PersistentStorage file. Since AppStorage stores data in memory, this operation causes the data in the persistent file to be overwritten by the in-memory data, making the persistent data meaningless.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PersistentStorage-static persistProp<T>(key: string, defaultValue: T): void--><!--Device-PersistentStorage-static persistProp<T>(key: string, defaultValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Property name. |
| defaultValue | T | Yes | Default value used for initialization if the specified **key** is not found in PersistentStorage or AppStorage. Since API version 12, the value can be **null** or **undefined**. |

**Examples**

For details about how to use persistProp, see [Accessing a PersistentStorage-Initialized Property from AppStorage](../../../ui/state-management/arkts-persiststorage.md#accessing-a-persistentstorage-initialized-property-from-appstorage).

## persistProps

```TypeScript
static persistProps(props: PersistPropsOptions[]): void
```

Persists multiple properties. This API is similar to [persistProp](#persistprop), but allows multiple properties to be persisted at once, making it suitable for initializing during application startup. This API is usually called before access to AppStorage.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-PersistentStorage-static persistProps(props: PersistPropsOptions[]): void--><!--Device-PersistentStorage-static persistProps(props: PersistPropsOptions[]): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| props | [PersistPropsOptions](arkts-arkui-persistpropsoptions-i.md)[] | Yes | Array of properties to persist, where each item contains a property name and a default value. |

**Examples**

```TypeScript
PersistentStorage.persistProps([{ key: 'highScore', defaultValue: '0' }, { key: 'weightScore', defaultValue: '1' }]);
```

## DeleteProp

```TypeScript
static DeleteProp(key: string): void
```

Performs the reverse operation of [PersistProp](#persistprop). It deletes the property corresponding to **key** from [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md), after which subsequent operations on [AppStorage](../../../ui/state-management/arkts-appstorage.md) no longer affect PersistentStorage. To persist the property again, call the [PersistProp](#persistprop) API again.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [deleteProp](#deleteprop)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PersistentStorage-static DeleteProp(key: string): void--><!--Device-PersistentStorage-static DeleteProp(key: string): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Property name in PersistentStorage. |

**Examples**

```TypeScript
PersistentStorage.DeleteProp('highScore');
```

## Keys

```TypeScript
static Keys(): Array<string>
```

Returns an array of all persisted property names.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [keys](#keys)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PersistentStorage-static Keys(): Array<string>--><!--Device-PersistentStorage-static Keys(): Array<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Returns an array of all persisted property names. |

**Examples**

```TypeScript
let keys: Array<string> = PersistentStorage.Keys();
```

## PersistProp

```TypeScript
static PersistProp<T>(key: string, defaultValue: T): void
```

Persists the property corresponding to **key** in [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a file. This API is usually called before access to AppStorage.

The order for determining the type and value of a property is as follows:

1. If the property corresponding to **key** exists in the
[PersistentStorage](../../../ui/state-management/arkts-persiststorage.md) file, the corresponding key is created in AppStorage and initialized with the property value found in PersistentStorage.
2. If the property with the specified key is not found in the PersistentStorage file, AppStorage is searched for
the property. If the property is found, it is persisted.
3. If no matching property is found in AppStorage, it is created in AppStorage, initialized with the value of  
**defaultValue**, and persisted.

According to the preceding initialization process, if the property exists in AppStorage, its value will overwrite the value in the PersistentStorage file. Since AppStorage stores data in memory, this operation causes the data in the persistent file to be overwritten by the in-memory data, making the persistent data meaningless.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [persistProp](#persistprop)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PersistentStorage-static PersistProp<T>(key: string, defaultValue: T): void--><!--Device-PersistentStorage-static PersistProp<T>(key: string, defaultValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Property name. |
| defaultValue | T | Yes | Default value used for initialization if the specified **key** is not found in PersistentStorage or AppStorage. The default value cannot be **null** or **undefined**. |

**Examples**

```TypeScript
PersistentStorage.PersistProp('highScore', '0');
```

## PersistProps

```TypeScript
static PersistProps(
    properties: {
      key: string;
      defaultValue: any;
    }[],
  ): void
```

Persists multiple properties. This API is similar to [PersistProp](#persistprop), but allows multiple properties to be persisted at once, making it suitable for initializing during application startup. This API should be called before access to AppStorage.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [PersistProps](#persistprops)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-PersistentStorage-static PersistProps(    properties: {      key: string;      defaultValue: any;    }[],  ): void--><!--Device-PersistentStorage-static PersistProps(    properties: {      key: string;      defaultValue: any;    }[],  ): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| properties | {       key: string;       defaultValue: any;     }[] | Yes | Array of properties to persist, where **key** indicates the property name and **defaultValue** indicates the default value. The rules are the same as those of **PersistProp**. |

**Examples**

```TypeScript
PersistentStorage.PersistProps([{ key: 'highScore', defaultValue: '0' }, { key: 'weightScore', defaultValue: '1' }]);
```
