# AppStorageV2

For details about how to use AppStorageV2, see [AppStorageV2: Storing Application-wide UI State](../../../ui/state-management/arkts-new-appstoragev2.md).

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## connect

```TypeScript
static connect<T extends object>(
    type: TypeConstructorWithArgs<T>,
    keyOrDefaultCreator?: string | StorageDefaultCreator<T>,
    defaultCreator?: StorageDefaultCreator<T>
  ): T | undefined
```

Stores key-value pair data in the application memory. If the given key already exists in [AppStorageV2](../../../ui/state-management/arkts-new-appstoragev2.md), the corresponding value is returned. Otherwise, a default value is constructed using the default value constructor and returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | Yes | Type. If no key is specified, the name of the type is used as the key. |
| keyOrDefaultCreator | string &#124; [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md)&lt;T&gt; | No | Key, or constructor for obtaining the default value. The default value is **undefined**. |
| defaultCreator | [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md)&lt;T&gt; | No | Constructor for obtaining the default value. The default value is **undefined**. |

**Return value:**

| Type | Description |
| --- | --- |
| T &#124; undefined | Returns data if the creation or data acquisition from AppStorageV2 is successful; returns **undefined** otherwise. |

**Examples**

```TypeScript
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2
class SampleClass {
  @Trace value: number = 0;
}

// Store the key-value pair with the key SampleClass and the value as a new object of SampleClass() in memory, and assign it to sampleData1.
const sampleData1: SampleClass | undefined = AppStorageV2.connect(SampleClass, () => new SampleClass());

// Store the key-value pair with the key key_as2 and the value as a new object of SampleClass() in memory, and assign it to sampleData2.
const sampleData2: SampleClass = AppStorageV2.connect(SampleClass, 'key_as2', () => new SampleClass())!;

// As the key SampleClass already exists in AppStorageV2, the value of the key SampleClass is returned to sampleData3.
const sampleData3: SampleClass = AppStorageV2.connect(SampleClass) as SampleClass;
```

## keys

```TypeScript
static keys(): Array<string>
```

Obtains all keys in [AppStorageV2](../../../ui/state-management/arkts-new-appstoragev2.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | All keys stored in AppStorageV2. |

**Examples**

```TypeScript
// Assuming there are two keys (key_as1 and key_as2) in AppStorageV2, the following will return an array containing these keys and assign it to keys.
const keys: Array<string> = AppStorageV2.keys();
```

## remove

```TypeScript
static remove<T>(keyOrType: string | TypeConstructorWithArgs<T>): void
```

Removes the specified key-value pair from [AppStorageV2](../../../ui/state-management/arkts-new-appstoragev2.md). If the specified key does not exist in AppStorageV2, the removal will fail.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyOrType | string &#124; [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md)&lt;T&gt; | Yes | Key to be removed. If a type is specified, the key to be removed is the name of that type. |

**Examples**

```TypeScript
// Assuming that there is a key named key_as2 in AppStorageV2, the following will remove the corresponding key-value pair from AppStorageV2.
AppStorageV2.remove('key_as2');

// Assuming that there is a key named SampleClass in AppStorageV2, the following will remove the corresponding key-value pair from AppStorageV2.
AppStorageV2.remove(SampleClass);

// Assuming there is no key named key_as1 in AppStorageV2, the following will result in a warning.
AppStorageV2.remove('key_as1');
```
