# PersistenceV2

```TypeScript
export declare class PersistenceV2 extends AppStorageV2
```

Inherits from [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md). For details, see [PersistenceV2: Persisting Application State](../../../ui/state-management/arkts-new-persistencev2.md).

**Inheritance/Implementation:** PersistenceV2 extends [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md)

**Since:** 12

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

Stores key-value pair data on the application disk. If the given key already exists in [PersistenceV2](../../../ui/state-management/arkts-new-persistencev2.md), the corresponding value is returned. Otherwise, a default value is constructed using the default value constructor and returned. If **globalConnect** is used for an [\@ObservedV2](../../../ui/state-management/arkts-new-observedV2-and-trace.md) decorated object, changes to the object's [\@Trace](../../../ui/state-management/arkts-new-observedV2-and-trace.md) properties will trigger automatic refresh of the associated object, while changes to non-@Trace properties will not. If necessary, the [PersistenceV2.save](#save) API can be called to store the data manually.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md)&lt;T&gt; | Yes | Connection settings. |

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

Stores key-value pair data on the application disk. Supports the persistence of the following collection types: [Array, Map, Set, Date, collections.Array, collections.Map, and collections.Set](../../../ui/state-management/arkts-new-persistencev2.md#types-supported-by-globalconnect). Note that when persisting data of the **Array\&lt;ClassA&gt;** type, you need to call [makeObserved](arkts-arkui-arkui-statemanagement-uiutils-c.md#makeobserved) to make the returned object observed. Multi-level nested sets are not supported. For example, **Array&lt;Array\<ClassA>&gt;** persistence is not supported.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

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

Called when persistence fails.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) &#124; undefined | Yes | Callback called when persistence fails. |

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

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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
