# PersistenceV2

```TypeScript
export declare class PersistenceV2 extends AppStorageV2
```

Provides persistent storage for UI states. This API is inherited from [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md). It supports persisting application state data to disks and restoring data after application restart, making it suitable for scenarios where UI state data needs to be retained. For details about the UI usage, see [PersistenceV2: Persisting UI States](../../../ui/state-management/arkts-new-persistencev2.md).

**Inheritance/Implementation:** PersistenceV2 extends [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md)

**Since:** 12

<!--Device-unnamed-export declare class PersistenceV2 extends AppStorageV2--><!--Device-unnamed-export declare class PersistenceV2 extends AppStorageV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## globalConnect

```TypeScript
static globalConnect<T extends object>(
    type: ConnectOptions<T>
  ): T | undefined
```

Stores key-value pair data on the application disk. If the given key already exists in [PersistenceV2](../../../ui/state-management/arkts-new-persistencev2.md), the corresponding value is returned. Otherwise, a default value is constructed using the default value constructor and returned. If the object connected through **globalConnect** is an [\@ObservedV2](../../../ui/state-management/arkts-new-observedV2-and-trace.md) object, changes to its [\@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md) properties will trigger automatic refresh of the entire associated object, while changes to non-\@Trace properties will not be automatically persisted. To persist changes to non-\@Trace properties, call the [PersistenceV2.save](#save) API to manually store them.

> **NOTE:** 
> 
> 1. If no key is specified, the class name of the data returned by the default constructor **defaultCreator** is used as the key and stored in PersistenceV2.
> 
> 2. If the data has been stored in PersistenceV2, you can obtain the stored data without using the default constructor. Otherwise, you must specify a default constructor to avoid application exceptions.
> 
> 3. Ensure that the data types match the key. Matching different types of **globalConnect** data to the same key will result in an application exception.
> 
> 4. You are advised to use meaningful values for keys. The values can contain letters, digits, and underscores (_) and a maximum of 255 characters. Using invalid characters or empty characters will result in undefined behavior.
> 
> 5. When associating an [\@Observed](../../../ui/state-management/arkts-observed-and-objectlink.md) object,because the name property of this type is undefined, you need to specify a key or customize the name property.
> 
> 6. The storage path for data is application-level. If different modules use the same key and the same encryption partition for **globalConnect**, only one copy of the data will be stored in the application.
> 
> 7. If **globalConnect** is used with the same key but different encryption levels, the data will be stored with the encryption level of the first **globalConnect** call, and the data in PersistenceV2 will also be stored with the encryption level that uses the key first.
> 
> 8. Avoid using **connect** and **globalConnect** together because they have different data copy paths. If they must be used together, make sure the keys are unique to avoid application crashes.
> 
> 9. To enable EL5 encryption, configure the **ohos.permission.PROTECT_SCREEN_LOCK_DATA** field in the
> **module.json** file. For details, see
> [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PersistenceV2-static globalConnect<T extends object>(    type: ConnectOptions<T>  ): T | undefined--><!--Device-PersistenceV2-static globalConnect<T extends object>(    type: ConnectOptions<T>  ): T | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md)&lt;T&gt; | Yes | Configuration options of **globalConnect**, which include the specified type, key, default constructor, encryption level, and other configuration items. For details, see [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Returns the data if creation or acquisition is successful; otherwise, returns **undefined**. |

**Examples**

The following is the sample code for globalConnect to persist data of the Map type:

```TypeScript
import { PersistenceV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Page1 {
  // globalConnect supports the persistence of data of the Map type.
  @Local map: Map<number, number> = PersistenceV2.globalConnect({
    type: Map<number, number>, defaultCreator: () => new Map<number, number>()
  })!;
  output: string[] = [];

  // Start the application. When you access the application for the first time, the following information is displayed: restored Map.size=0, map.get(0)=undefined, map.get(1)=undefined, map.get(2)=undefined.
  // Stop the application. When you access the application for the second time, the following information is displayed: restored Map.size=1, map.get(0)=0, map.get(1)=undefined, map.get(2)=undefined.
  // Stop the application. When you access the application for the third time, the following information is displayed: restored Map.size=2, map.get(0)=0, map.get(1)=1, map.get(2)=undefined.
  // Stop the application. When you access the application for the fourth time, the following information is displayed: restored Map.size=3, map.get(0)=0, map.get(1)=1, map.get(2)=2.
  aboutToAppear(): void {
    const restoredMapSize = this.map.size;
    this.output.push(`restored Map.size=${restoredMapSize}, map.get(0)=${this.map.get(0)}, map.get(1)=${this.map.get(1)}, map.get(2)=${this.map.get(2)}`);
    this.map.set(restoredMapSize, restoredMapSize);
    // Manual persistence is required.
    PersistenceV2.save('Map');
  }

  build() {
    Column() {
      Row() {
        Text(this.output.join('\n\n'))
          .fontSize(24)
      }
    }
    .width('100%')
  }
}
```

<a id="globalconnect-1"></a>

## globalConnect

```TypeScript
static globalConnect<T extends CollectionType<S>, S extends object>(
    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>
  ): T | undefined
```

Stores key-value pair data on the application disk. Supports the persistence of the following collection types: [Array, Map, Set, collections.Array, collections.Map, and collections.Set](../../../ui/state-management/arkts-new-persistencev2.md#types-supported-by-globalconnect). Note that when persisting data of the **Array\&lt;ClassA&gt;** type, you need to call [makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved) to make the returned object observed. Multi-level nested sets are not supported. For example, **Array&lt;Array\<ClassA>&gt;** persistence is not supported.

> **NOTE:** 
> 
> 1. If no key is specified, the class name of the data returned by the default constructor **defaultCreator**is used as the key and stored in PersistenceV2.
> 
> 2. You are advised to use meaningful values for keys. The values can contain letters, digits, and underscores (_) and a maximum of 255 characters. Using invalid characters or empty characters will result in undefined behavior.
> 
> 3. Avoid using **connect** and **globalConnect** together because they have different data copy paths. If they must be used together, make sure the keys are unique to avoid application crashes.
> 
> For other general conditions, see the description of **globalConnect&lt;sup&gt;18+&lt;/sup&gt;**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-PersistenceV2-static globalConnect<T extends CollectionType<S>, S extends object>(    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>  ): T | undefined--><!--Device-PersistenceV2-static globalConnect<T extends CollectionType<S>, S extends object>(    type: ConnectOptionsCollections<T, S> | ConnectOptions<T>  ): T | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ConnectOptionsCollections](arkts-arkui-arkui-statemanagement-connectoptionscollections-c.md)&lt;T, S&gt; &#124; [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md)&lt;T&gt; | Yes | Passed **globalConnect** parameters. For details, see the description of **ConnectOptions** and **ConnectOptionsCollections**.<br>If **defaultSubCreator** is provided in **ConnectOptionsCollections**, **defaultCreator** must be provided. Otherwise, the persistence fails. The collection item type S must be the same as the return type of **defaultSubCreator**. If the return types are inconsistent, an error will be reported during compilation. |

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Returns the data if creation or acquisition is successful; otherwise, returns **undefined**. |

**Examples**

See [globalConnect](#globalconnect)

## notifyOnError

```TypeScript
static notifyOnError(callback: PersistenceErrorCallback | undefined): void
```

Registers a callback invoked when persistence fails.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PersistenceV2-static notifyOnError(callback: PersistenceErrorCallback | undefined): void--><!--Device-PersistenceV2-static notifyOnError(callback: PersistenceErrorCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) &#124; undefined | Yes | Callback called when persistence fails. The callback parameters include **key** (the key that caused the error), **reason** (the type of error cause, which can be **'quota'**, **'serialization'**, or **'unknown'**), **message** (detailed error information), and **oldValue** (optional, indicating the old data returned when deserialization fails). |

**Examples**

```TypeScript
// Called when persistence fails.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});
```

## save

```TypeScript
static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void
```

Persists the specified key-value pair data once.

> **NOTE:** 
> 
> Since changes to non-[\@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md) data do
> not trigger automatic persistence of [PersistenceV2](../../../ui/state-management/arkts-new-persistencev2.md),
> when non-\**@Trace** data changes and needs to be persisted, you can call this API to persist the data of the
> corresponding key.
> 
> It is useless to manually persist the keys that are not in the **connect** state in the memory.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PersistenceV2-static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void--><!--Device-PersistenceV2-static save<T>(keyOrType: string | TypeConstructorWithArgs<T>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOrType | string &#124; [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | Yes | Key to be persisted. If a type is specified, the key for persistence is the name of the type. |

**Examples**

```TypeScript
@ObservedV2
class SampleClass {
  @Trace value: number = 0;
}

// Assuming there is a key named key_as2 in PersistenceV2, the following will persist the data for this key-value pair.
PersistenceV2.save('key_as2');

// Assuming there is a key named SampleClass in PersistenceV2, the following will persist the data for this key-value pair.
PersistenceV2.save(SampleClass);

// Assuming there is no key named key_as1 in PersistenceV2, this operation is meaningless.
PersistenceV2.save('key_as1');
```
