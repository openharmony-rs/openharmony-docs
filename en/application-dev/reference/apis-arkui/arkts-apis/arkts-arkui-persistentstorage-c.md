# PersistentStorage

```TypeScript
declare class PersistentStorage
```

For details about how to use PersistentStorage on the UI, see [PersistentStorage: Persisting Application State](../../../ui/state-management/arkts-persiststorage.md).

> **NOTE:** 

> Since API version 12, PersistentStorage supports **null** and **undefined**.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DeleteProp

```TypeScript
static DeleteProp(key: string): void
```

Performs the reverse operation of [PersistProp](#persistprop). Specifically, this API deletes the property corresponding to the specified key from [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md). Subsequent operations on [AppStorage](../../../ui/state-management/arkts-appstorage.md) do not affect data in PersistentStorage.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [deleteProp](#deleteprop)

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Property name in PersistentStorage. |

**Examples**

```TypeScript
PersistentStorage.DeleteProp('highScore');
```

## deleteProp

```TypeScript
static deleteProp(key: string): void
```

Performs the reverse operation of [persistProp](#persistprop). Specifically, this API deletes the property corresponding to the specified **key** from [PersistentStorage](../../../ui/state-management/arkts-persiststorage.md). Subsequent operations on [AppStorage](../../../ui/state-management/arkts-appstorage.md) do not affect data in PersistentStorage. This operation removes the corresponding key from the persistence file. To persist the property again, you can call the [persistProp](#persistprop) API.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Property name in PersistentStorage. |

**Examples**

```TypeScript
PersistentStorage.deleteProp('highScore');
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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Returns an array of all persisted property names. |

**Examples**

```TypeScript
let keys: Array<string> = PersistentStorage.Keys();
```

## keys

```TypeScript
static keys(): Array<string>
```

Returns an array of all persisted property names.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Returns an array of all persisted property names. |

**Examples**

```TypeScript
let keys: Array<string> = PersistentStorage.keys();
```

## PersistProp

```TypeScript
static PersistProp<T>(key: string, defaultValue: T): void
```

Persists the property corresponding to **key** from [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a file. This API is usually called before access to AppStorage.

The order for determining the type and value of a property is as follows:

1. If the property with the specified key is found in the
[PersistentStorage](../../../ui/state-management/arkts-persiststorage.md) file, the corresponding property is created in AppStorage and initialized with the value found in PersistentStorage.

2. If the property with the specified key is not found in the PersistentStorage file, AppStorage is searched for
the property. If the property is found, it is persisted.

3. If no matching property is found in AppStorage, it is created in AppStorage, initialized with the value of  
**defaultValue**, and persisted.

According to the preceding initialization process, if the property exists in AppStorage, its value will be used, overriding the value in the PersistentStorage file. Because AppStorage stores data in the memory, the property value becomes nonpersistent.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [persistProp](#persistprop)

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Property name. |
| defaultValue | T | Yes | Default value used for initialization if the specified **key** is not found in PersistentStorage and AppStorage. The value cannot be **null** or **undefined**. |

**Examples**

```TypeScript
PersistentStorage.PersistProp('highScore', '0');
```

## persistProp

```TypeScript
static persistProp<T>(key: string, defaultValue: T): void
```

Persists the property corresponding to **key** from [AppStorage](../../../ui/state-management/arkts-appstorage.md) to a file. This API is usually called before access to AppStorage.

The order for determining the type and value of a property is as follows:

1. If the property with the specified key is found in the
[PersistentStorage](../../../ui/state-management/arkts-persiststorage.md) file, the corresponding property is created in AppStorage and initialized with the value found in PersistentStorage.

2. If the property with the specified key is not found in the PersistentStorage file, AppStorage is searched for
the property. If the property is found, it is persisted.

3. If no matching property is found in AppStorage, it is created in AppStorage, initialized with the value of  
**defaultValue**, and persisted.

According to the preceding initialization process, if the property exists in AppStorage, its value will be used, overriding the value in the PersistentStorage file. Because AppStorage stores data in the memory, the property value becomes nonpersistent.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Property name. |
| defaultValue | T | Yes | Default value used for initialization if the specified **key** is not found in PersistentStorage and AppStorage. Since API version 12, the value can be **null** or **undefined**. |

**Examples**

For details about how to use persistProp, see [Accessing a PersistentStorage-Initialized Property from AppStorage](../../../ui/state-management/arkts-persiststorage.md#accessing-a-persistentstorage-initialized-property-from-appstorage).

## PersistProps

```TypeScript
static PersistProps(
    properties: {
      key: string;
      defaultValue: any;
    }[],
  ): void
```

Persists multiple properties. This API is similar to [PersistProp](#persistprop), but allows multiple properties to be persisted at once, making it suitable for initializing during application startup.

**Since:** 7

**Deprecated since:** 10

**Substitutes:** [PersistProps](#persistprops)

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| properties | {       key: string;       defaultValue: any;     }[] | Yes | Array of properties to persist.<br>**key**: property name. <br>**defaultValue**: default value. The rule is the same as that for **PersistProp**. |

**Examples**

```TypeScript
PersistentStorage.PersistProps([{ key: 'highScore', defaultValue: '0' }, { key: 'weightScore', defaultValue: '1' }]);
```

## persistProps

```TypeScript
static persistProps(props: PersistPropsOptions[]): void
```

Persists multiple properties. This API is similar to [persistProp](#persistprop), but allows multiple properties to be persisted at once, making it suitable for initializing during application startup.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| props | [PersistPropsOptions](arkts-arkui-persistpropsoptions-i.md)[] | Yes | Array of properties to persist. |

**Examples**

```TypeScript
PersistentStorage.persistProps([{ key: 'highScore', defaultValue: '0' }, { key: 'weightScore', defaultValue: '1' }]);
```
