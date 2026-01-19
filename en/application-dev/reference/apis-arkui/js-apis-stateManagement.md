# @ohos.arkui.StateManagement (State Management)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926; @liwenzhen3; @zzq212050299-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

The state management module provides data storage, persistent data management, UIAbility data storage, and environment state and tools required by applications.

>**NOTE**
>
>The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.


T and S in this topic represent the types as described below.


| Type  | Description                                    |
| ---- | -------------------------------------- |
| T    | Class, number, boolean, string, and arrays of these types.|
| S    | number, boolean, string.                |


## Modules to Import

```ts
import { AppStorageV2, PersistenceV2, UIUtils } from '@kit.ArkUI';
```

## AppStorageV2

For details about how to use AppStorageV2, see [AppStorageV2: Storing Application-wide UI State](../../ui/state-management/arkts-new-appstoragev2.md).

### connect

static&nbsp;connect\<T extends object\>( <br>
  &nbsp;&nbsp;&nbsp;&nbsp;type:&nbsp;TypeConstructorWithArgs\<T\>, <br>
  &nbsp;&nbsp;&nbsp;&nbsp;keyOrDefaultCreator?:&nbsp;string&nbsp;|&nbsp;StorageDefaultCreator\<T\>, <br>
  &nbsp;&nbsp;&nbsp;&nbsp;defaultCreator?:&nbsp;StorageDefaultCreator\<T\> <br>
):&nbsp;T&nbsp;|&nbsp;undefined

Stores key-value pair data in the application memory. If the given key already exists in [AppStorageV2](../../ui/state-management/arkts-new-appstoragev2.md), the corresponding value is returned. Otherwise, a default value is constructed using the default value constructor and returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description              |
| -------- | ------ | ---- | ---------------------- |
| type | [TypeConstructorWithArgs\<T\>](#typeconstructorwithargst) | Yes  | Type. If no key is specified, the name of the type is used as the key.|
| keyOrDefaultCreator | string&nbsp;\|&nbsp;[StorageDefaultCreator\<T\>](#storagedefaultcreatort) | No  | Key, or constructor for obtaining the default value.|
| defaultCreator | StorageDefaultCreator\<T\> | No  | Constructor for obtaining the default value.|

>**NOTE**
>
>1. The second parameter is used when **key** is not specified, and the third parameter is used otherwise (including when the second parameter is invalid).
>
>2. If the data has been stored in AppStorageV2, you can obtain the stored data without using the default constructor. If the data has not been stored, you must specify a default constructor; otherwise, an application exception will be thrown.
>
>3. Ensure that the data types match the key. Matching different types of **connect** data to the same key will result in an application exception.
>
>4. You are advised to use meaningful values for the key, with a length not exceeding 255 characters. The behavior of using illegal characters or empty characters is undefined.

**Return value**

| Type                                  | Description                                                        |
| -------------------------------------- | ------------------------------------------------------------ |
| T \| undefined | Returns data if the creation or data acquisition from AppStorageV2 is successful; returns **undefined** otherwise.|

**Example**

```ts
import { AppStorageV2 } from '@kit.ArkUI';

@ObservedV2
class SampleClass {
  @Trace p: number = 0;
}

// Store the key-value pair with the key SampleClass and the value as a new instance of SampleClass() in memory, and assign it to variable as1.
const as1: SampleClass | undefined = AppStorageV2.connect(SampleClass, () => new SampleClass());

// Store the key-value pair with the key key_as2 and the value as a new instance of SampleClass() in memory, and assign it to variable as2.
const as2: SampleClass = AppStorageV2.connect(SampleClass, 'key_as2', () => new SampleClass())!;

// As the key SampleClass already exists in AppStorageV2, the value associated with the key is returned to variable as3.
const as3: SampleClass = AppStorageV2.connect(SampleClass) as SampleClass;
```

### remove

static&nbsp;remove\<T\>(keyOrType:&nbsp;string&nbsp;|&nbsp;TypeConstructorWithArgs\<T\>):&nbsp;void

Removes the specified key-value pair from [AppStorageV2](../../ui/state-management/arkts-new-appstoragev2.md). If the specified key does not exist in AppStorageV2, the removal will fail.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description              |
| -------- | ------ | ---- | ---------------------- |
| keyOrType | string \| TypeConstructorWithArgs\<T\> | Yes  | Key to be removed. If a type is specified, the key to be removed is the name of that type.|

>**NOTE**
>
>If a key that does not exist in AppStorageV2 is deleted, a warning is reported.


**Example**

<!--code_no_check-->
```ts
// Assuming that there is a key named key_as2 in AppStorageV2, the following will remove the corresponding key-value pair from AppStorageV2.
AppStorageV2.remove('key_as2');

// Assuming that there is a key named SampleClass in AppStorageV2, the following will remove the corresponding key-value pair from AppStorageV2.
AppStorageV2.remove(SampleClass);

// Assuming there is no key named key_as1 in AppStorageV2, the following will result in a warning.
AppStorageV2.remove('key_as1');
```

### keys

static&nbsp;keys():&nbsp;Array\<string\>

Obtains all keys in [AppStorageV2](../../ui/state-management/arkts-new-appstoragev2.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                  | Description                                                        |
| -------------------------------------- | ------------------------------------------------------------ |
| Array\<string\> | All keys stored in AppStorageV2.|

>**NOTE**
>
>The order of the keys in the Array is not sequential and does not correspond to the order in which the keys were inserted into AppStorageV2.

**Example**

```ts
// Assuming there are two keys (key_as1 and key_as2) in AppStorageV2, the following will return an array containing these keys and assign it to keys.
const keys: Array<string> = AppStorageV2.keys();
```



## PersistenceV2

Inherits from [AppStorageV2](#appstoragev2). For details, see [PersistenceV2: Persisting Application State](../../ui/state-management/arkts-new-persistencev2.md).

### globalConnect<sup>18+</sup>

static globalConnect\<T extends object\>(type: ConnectOptions\<T\>): T | undefined

Stores key-value pair data on the application disk. If the given key already exists in [PersistenceV2](../../ui/state-management/arkts-new-persistencev2.md), the corresponding value is returned. Otherwise, a default value is constructed using the default value constructor and returned. If **globalConnect** is used for an @ObservedV2 decorated object, changes to the object's @Trace properties will trigger automatic refresh of the associated object, while changes to non-@Trace properties will not. If necessary, the **PersistenceV2.save** API can be called to store the data manually.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  |Type  |Mandatory  | Description                                                     |
| ------------- | ------------|-------------------|-------------------------- |
| type    |[ConnectOptions\<T\>](#connectoptions18)    |Yes |Connection settings.|

**Return value**

|Type  |Description                |
|----------|-----------------------------------|
|T \| undefined    |Returns the data if creation or acquisition is successful; otherwise, returns **undefined**.   |

> **NOTE**
>
> 1. The second parameter is used when **key** is not specified, and the third parameter is used otherwise (including when the second parameter is invalid).
>
> 2. If the data has been stored in **PersistenceV2**, you can obtain the stored data without using the default constructor. Otherwise, you must specify a default constructor to avoid application exceptions.
>
> 3. Ensure that the data types match the key. Matching different types of **globalConnect** data to the same key will result in an application exception.
>
> 4. You are advised to use meaningful values for keys. The values can contain letters, digits, and underscores (_) and a maximum of 255 characters. Using invalid characters or null characters will result in undefined behavior.
>
> 5. When matching the key with an [\@Observed](../../ui/state-management/arkts-observed-and-objectlink.md) object, specify the key or customize the **name** property.
>
> 6. The storage path for data is application-level. If different modules use the same key and the same encryption partition for **globalConnect**, only one copy of the data will be stored in the application.
>
> 7. If **globalConnect** is used with the same key but different encryption levels, the data will be stored with the encryption level of the first **globalConnect** call, and the data in **PersistenceV2** will also be stored with this encryption level.
>
> 8. Avoid using **connect** and **globalConnect** together because they have different data copy paths. If they must be used together, make sure the keys are unique to avoid application crashes.
>
> 9. To enable EL5 encryption, configure the **ohos.permission.PROTECT_SCREEN_LOCK_DATA** field in the **module.json** file. For details, see [Declaring Permissions](../../security/AccessToken/declare-permissions.md).

**Example**
This example is provided for you to understand the usage of **globalConnect**. You need to write your own @Entry component for complete usage.

<!--code_no_check-->
```ts
import { PersistenceV2, Type, ConnectOptions } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

@ObservedV2
class SampleChild {
  @Trace childId: number = 0;
  groupId: number = 1;
}

@ObservedV2
export class Sample {
  // For complex objects, use the @Type decorator to ensure successful serialization.
  @Type(SampleChild)
  @Trace father: SampleChild = new SampleChild();
}

// If no key is provided, the type name is used as the key. If the encryption level is not specified, the default EL2 level is used.
const p: Sample = PersistenceV2.globalConnect({ type: Sample, defaultCreator: () => new Sample() })!;

// Use key:global1 for connection and set the encryption level to EL1.
const p1: Sample = PersistenceV2.globalConnect({
  type: Sample,
  key: 'global1',
  defaultCreator: () => new Sample(),
  areaMode: contextConstant.AreaMode.EL1
})!;

// Use key:global2 for connection and use the constructor function. If the encryption level not specified, the default EL2 level is used.
const p2: Sample = PersistenceV2.globalConnect({ type: Sample, key: 'global2', defaultCreator: () => new Sample() })!;

// Use key:global3 for connection and set the encryption parameter ranging from 0 to 4; otherwise, a crash occurs. In this case, EL3 is set.
const p3: Sample = PersistenceV2.globalConnect({
  type: Sample,
  key: 'global3',
  defaultCreator: () => new Sample(),
  areaMode: 3
})!;

```
### globalConnect<sup>23+</sup>
 static globalConnect\<T extends CollectionType<S\>, S extends object\>(
  type: ConnectOptionsCollections\<T, S\> | ConnectOptions\<T\>
  ): T | undefined

Stores key-value pair data on the application disk. Supports the persistence of the following collection types: [Array, Map, Set, Date, collections.Array, collections.Map, collections.Set](../../ui/state-management/arkts-new-persistencev2.md#collection-types-supported-by-globalconnect). Note that when persisting data of the Array\<ClassA> type, you need to call [makeObserved](#makeobserved) to make the returned object observed. Multi-level nested sets are not supported. For example, **Array<Array\<ClassA>>** persistence is not supported.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name  | Type  | Mandatory| Description              |
| -------- | ------ | ---- | ---------------------- |
| type | [ConnectOptionsCollections\<T, S\>](#connectoptionscollections23)\| [ConnectOptions\<T\>](#connectoptions18)|  Yes  | Passed **globalConnect** parameters. For details, see the description of **ConnectOptions** and **ConnectOptionsCollections**. If **defaultSubCreator** is provided in **ConnectOptionsCollections**, **defaultCreator** must be provided. The collection item type S must be the same as the return type of **defaultSubCreator**.|

When you use **defaultSubCreator** in **globalConnect**, you must provide **defaultCreator**. The return type of the **defaultSubCreator** function must be the same as the collection item type returned by **defaultCreator**.
When **globalConnect** persists data of the **Array\<ClassA>** type, you need to use the **defaultSubCreator** option to instruct the state management framework to create an instance of **ClassA**. The following is an example of using **globalConnect** to persist data of the **Array\<ClassA>** type:

```typescript
class ClassA {
  propA: number;
  // ...
}

@ComponentV2
struct Page1 {
  // The top-level persistent data type is Array<ClassA>.
  @Local arr: Array<ClassA> = PersistenceV2.globalConnect({
    type: Array<ClassA>,
    defaultCreator: () => UIUtils.makeObserved(new Array<ClassA>()),
    // Add defaultSubCreator to notify the state management framework of how to create ClassA objects.
    // Add makeObserved to the persistent data. Otherwise, the persistence will fail.
    defaultSubCreator: () => UIUtils.makeObserved(new ClassA())
  })!
  // ...
}
```

**Return value**

|Type  |Description                |
|----------|-----------------------------------|
|T \| undefined    |Returns the data if creation or acquisition is successful; otherwise, returns **undefined**.   |

**Example**

The following is the sample code for **globalConnect** to persist data of the Map type:
```typescript
import { PersistenceV2, ConnectOptions } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Page1 {
  // globalConnect supports the persistence of data of the Map type.
  @Local map: Map<number, number> = PersistenceV2.globalConnect({
    type: Map<number, number>, defaultCreator: () => new Map<number, number>();
  })!
  output: string[] = [];

  // Start the application. When you access the application for the first time, the following information is displayed: restored Map.size=0, map.get(0)=undefined, map.get(1)=undefined, map.get(2)=undefined.
  // Kill the application. When you access the application for the second time, the following information is displayed: restored Map.size=1, map.get(0)=0, map.get(1)=undefined, map.get(2)=undefined.
  // Kill the application. When you access the application for the third time, the following information is displayed: restored Map.size=2, map.get(0)=0, map.get(1)=1, map.get(2)=undefined.
  // Kill the application. When you access the application for the fourth time, the following information is displayed: restored Map.size=3, map.get(0)=0, map.get(1)=1, map.get(2)=2.
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
### save

static&nbsp;save\<T\>(keyOrType:&nbsp;string&nbsp;|&nbsp;TypeConstructorWithArgs\<T\>):&nbsp;void

Persists the specified key-value pair data once.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description              |
| -------- | ------ | ---- | ---------------------- |
| keyOrType | string \| TypeConstructorWithArgs\<T\> | Yes  | Key to be persisted. If a type is specified, the key for persistence is the name of the type.|

>**NOTE**
>
>Since changes to non-[\@Trace](../../ui/state-management/arkts-new-observedV2-and-trace.md) decorated data do not automatically trigger persistence through [PersistenceV2](../../ui/state-management/arkts-new-persistencev2.md), you can call this API to manually persist the data for the corresponding key when needed.
>
>It is useless to manually persist the keys that are not in the **connect** state in the memory.

**Example**

<!--code_no_check-->

```ts
@ObservedV2
class SampleClass {
  @Trace p: number = 0;
}

// Assuming there is a key named key_as2 in PersistenceV2, the following will persist the data for this key-value pair.
PersistenceV2.save('key_as2');

// Assuming there is a key named SampleClass in PersistenceV2, the following will persist the data for this key-value pair.
PersistenceV2.save(SampleClass);

// Assuming there is no key named key_as1 in PersistenceV2, this operation is meaningless.
PersistenceV2.save('key_as1');
```

### notifyOnError

static notifyOnError(callback: PersistenceErrorCallback | undefined): void

Called when persistence fails.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description              |
| -------- | ------ | ---- | ---------------------- |
| callback | PersistenceErrorCallback \| undefined  | Yes  | Callback called when persistence fails.|

**Example**

```ts
// Called when persistence fails.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});
```

## ConnectOptions<sup>18+</sup>

Defines the parameter type for **globalConnect**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|Parameter  |Type   |Read-Only  |Optional   |Description     |
|--------|------------|------------|-----------|--------------|
|type        | TypeConstructorWithArgs\<T\>   |No  |No  |Specified type.        |
|key         | string   |No  |Yes  |Input key. If no value is passed in, the type name is used as the key.            |
|defaultCreator   | StorageDefaultCreator\<T\>   |No  |Yes  |Default constructor. You are advised to pass this parameter. If **globalConnect** is connected to the key for the first time, an error is reported if this parameter is not passed in.|
|areaMode      | contextConstant.AreaMode   |No  |Yes   |Encryption level, ranging from EL1 to EL5 (corresponding to the value from 0 to 4). For details, see [Encryption Levels](../../application-models/application-context-stage.md#obtaining-and-modifying-encryption-levels). If no value is passed in, EL2 is used by default. Storage paths vary based on the encryption levels. If the input value of encryption level is not in the range of **0** to **4**, a crash occurs.|

## ConnectOptionsCollections<sup>23+</sup>

Defines the parameter type for [globalConnect](#globalconnect23) API. ConnectOptionsCollections is inherited from [ConnectOptions](#connectoptions18). You can use the **ConnectOptionsCollections** input parameter to persist container data (such as **Array\<S>**).

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

|Parameter  |Type   |Read-Only  |Optional   |Description     |
|--------|------------|------------|-----------|--------------|
|defaultCreator   | [StorageDefaultCreator\<T\>](#storagedefaultcreatort)   |No  |Yes  |Persists container data. **defaultSubCreator** should be provided together with **defaultCreator**; otherwise, the container data cannot be persisted. The collection item type **S** must be the same as the return type of **defaultSubCreator**.|
|defaultSubCreator   | [StorageDefaultCreator\<S\>](#storagedefaultcreatort)   |No  |Yes  |Persists container data. If the return value of **defaultSubCreator** is **undefined** or **null**, the persistence fails. When a user-defined class collection (such as **Array\<ClassA>**) is persisted, the generic type **T** in **defaultCreator** is **Array\<ClassA>**, and **S** in **defaultSubCreator** is **ClassA**.|

The following shows the examples of **StorageDefaultCreator\<T>** and **StorageDefaultCreator\<S>**:

**Example**
```typescript
class ClassA {
  propA: number;
  // ...
}

@ComponentV2
struct Page {
  // The default creator of StorageDefaultCreator<T> is `() => UIUtils.makeObserved(new Array<ClassA>())`, in which the `T` type is `Array<ClassA>`
  // The default creator of StorageDefaultCreator<S> is `() =>UIUtils.makeObserved(new ClassA())`, in which the `S` type is `ClassA`.
  @Local arr: Array<ClassA> = PersistenceV2.globalConnect({
    type: Array<ClassA>,
    defaultCreator: () => UIUtils.makeObserved(new Array<ClassA>()),
    // Add defaultSubCreator to notify the state management framework of how to create ClassA objects.
    // Add makeObserved to the persistent data. Otherwise, the persistence will fail.
    defaultSubCreator: () => UIUtils.makeObserved(new ClassA())
  })!
  // ...
}
```

## CollectionType<sup>23+</sup>

type CollectionType\<S\> = Array\<S\> | Map\<string | number, S\> |
Set\<S\> | collections.Array\<S\> | collections.Map\<string | number, S\> | collections.Set\<S\>

Defines the types of persistent collection data supported by **globalConnect** using the generic type of the input parameter of **globalConnect**.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Type| Description                      |
| ---- | -------------------------- |
| Array\<S\>     | The value is of the array type.|
| Map\<string \| number, S\>     | The value is of the Map type.|
|Set\<S\>     | The value is of the Set type.|
|[collections.Array](../apis-arkts/arkts-apis-arkts-collections-Array.md)\<S\>     | The value is of the collections.Array type.|
|[collections.Map](../apis-arkts/arkts-apis-arkts-collections-Map.md)\<string \| number, S\>     | The value is of the collections.Map type.|
|[collections.Set](../apis-arkts/arkts-apis-arkts-collections-Set.md)\<S\>     | The value is of the collections.Set type.|

## ObservedResult<sup>23+</sup>

Provides the result of whether the object can be observed.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Parameter| Type| Read-Only |Optional| Description    |
| ------ | ---- | ---- | ---- | ------------ |
| isObserved | boolean  | No|  No  | Whether an object can be observed.<br>**true**: The object can be observed.<br>**false**: The object cannot be observed.|
| reason | string  | No| No  | Reason for the object's observability.<br>For the object that cannot be observed: The object itself cannot be observed.<br>For the object that can be observed:<br> 1. The V1 object is decorated by the [@Observed](./../../ui/state-management/arkts-observed-and-objectlink.md) decorator or the object is converted by the [makeV1Observed](#makev1observed19) method.<br> 2. The V1 object is decorated by the [@Observed](./../../ui/state-management/arkts-observed-and-objectlink.md) decorator or the object is converted by the [makeV1Observed](#makev1observed19) method, but the object is not used by the UI component.<br> 3. The V1 object is converted by the [enableV2Compatibility](#enablev2compatibility19) method and then passed to the V2 component.<br> 4. The V1 object is converted by the [enableV2Compatibility](#enablev2compatibility19) method and then passed to the V2 component, but is not used by the V2 component.<br> 5. The V2 object is decorated by the [@ObservedV2 or @Trace](./../../ui/state-management/arkts-new-observedV2-and-trace.md) decorator.<br> 6. The V2 object is converted by the [makeObserved](#makeobserved) method.<br> 7. The V2 object is of the Array, Map, Set, or Date type.<br> 8. The V2 object is decorated by the [@ObservedV2 or @Trace](./../../ui/state-management/arkts-new-observedV2-and-trace.md) decorator, but is not used by the UI component.<br> 9. The V2 object is converted by the [makeObserved](#makeobserved) method, but the object is not used by the UI component.<br> 10. The V2 object is of the Array, Map, Set, or Date type, but is not used by the UI component.|
| decoratorInfo | Array\<[DecoratorInfo](#decoratorinfo23)\>  | No| No  | Decorator and component information associated with the observable object. If the object cannot be observed, the array is empty.|

## DecoratorInfo<sup>23+</sup>

Defines the decorator and component information associated with the observable object.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Parameter| Type| Read-Only | Optional| Description    |
| ------ | ---- | ---- |---- | ------------ |
| decoratorName | string  | No| No  | Decorator name.<br>For a V1 object, the value is the name of the decorator associated with the object.<br> If the V1 object uses [@Track](./../../ui/state-management/arkts-track.md), the value is **'@Track'**.<br> If the V2 object uses [@Trace](./../../ui/state-management/arkts-new-observedV2-and-trace.md), the value is **'@Trace'**.<br> If the V2 object uses [makeObserved](#makeobserved), the value is **'MakeObserved'**.<br> If the V2 object uses [enableV2Compatibility](#enablev2compatibility19), the value is **'EnableV2Compatible'**.<br> If the V2 object uses built-in data, the value is **'ProxyObservedV2'**.|
| stateVariableName | string  | No| No  | Name of the attribute decorated by the decorator.|
| owningComponentOrClassName | string  | No| No  | Component name.<br>A component name is returned by the V1 object.<br> An object name is returned by the V1 object using [@Track](./../../ui/state-management/arkts-track.md) or V2 object.|
| owningComponentId | number  | No| No  | Component ID.<br>A component ID is returned by the V1 object.<br> **-1** is returned by the V1 object using [@Track](./../../ui/state-management/arkts-track.md) or V2 object.|
| dependentInfo | Array<[ElementInfo](#elementinfo23)>  | No| No  | Information about the component that uses the observable object. If the object is not used in any UI, an empty array is returned.|

## ElementInfo<sup>23+</sup>

Defines information about the components associated with the observable object, including system components and custom components.

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Parameter| Type| Read-Only | Optional| Description    |
| ------ | ---- | ---- |---- | ------------ |
| elementName | string  | No| No  | Component name.|
| elementId | number  | No| No  | Component ID.|

## UIUtils

Provides APIs for handling data transformations related to state management.

### getTarget

static getTarget\<T extends object\>(source: T): T

Obtains the original object from a proxy object wrapped by the state management framework. For details, see [getTarget API: Obtaining Original Objects](../../ui/state-management/arkts-new-getTarget.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| source | T    | Yes  | Source object.|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| T    | Original object of the source after the proxy added by the state management framework is removed.|

**Example**

```ts
import { UIUtils } from '@kit.ArkUI';

class NonObservedClass {
  name: string = 'Tom';
}

let nonObservedClass: NonObservedClass = new NonObservedClass();

@Entry
@Component
struct Index {
  @State someClass: NonObservedClass = nonObservedClass;

  build() {
    Column() {
      Text(`this.someClass === nonObservedClass: ${this.someClass === nonObservedClass}`) // false
      Text(`UIUtils.getTarget(this.someClass) === nonObservedClass: ${UIUtils.getTarget(this.someClass) ===
        nonObservedClass}`) // true
    }
  }
}
```

### getLifecycle<sup>23+</sup>

static getLifecycle\<T extends BaseCustomComponent\>(customComponent: T): CustomComponentLifecycle

Obtains the [lifecycle of a custom component](./arkui-ts/ts-custom-component-new-lifecycle.md).

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| customComponent | T    | Yes  | Custom component instance.|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| [CustomComponentLifecycle](./arkui-ts/ts-custom-component-new-lifecycle.md#customcomponentlifecycle)    | Lifecycle instance of a custom component obtained.|

**Example**

```ts
import { UIUtils, ComponentAppear } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State lifecycleState: number = -1;

  @ComponentAppear
  myAppear() {
    // Obtain the lifecycle instance of a custom component through UIUtils.getLifecycle, and query the current lifecycle of the custom component through getCurrentState.
    // The expected lifecycle is CustomComponentLifecycleState.APPEARED = 1.
    this.lifecycleState = UIUtils.getLifecycle(this).getCurrentState();
  }

  build() {
    Text(`${this.lifecycleState}`)
  }
}
```

### canBeObserved<sup>23+</sup>

static canBeObserved\<T extends object\>(source: T): ObservedResult

Determines whether a data object can be observed and returns the observation result. For details, see [canBeObserved API: Determining Whether an Object Can Be Observed](../../ui/state-management/arkts-new-canBeObserved.md).

**Atomic service API**: This API can be used in atomic services since API version 23.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| source | T    | Yes  | Data object to be determined. Array, Map, Set, and Date types are supported.<br>For details, see [canBeObserved API: Determining Whether an Object Can Be Observed](../../ui/state-management/arkts-new-canBeObserved.md).|

**Return value**

| Type| Description    |
| ---- | ------------ |
| [ObservedResult](#observedresult23)  | Returns a result about whether the object can be observed.|

**Example**

``` ts
import { UIUtils } from '@kit.ArkUI';
import { DecoratorInfo, ElementInfo } from '@ohos.arkui.StateManagement';
import { hilog } from '@kit.PerformanceAnalysisKit';

const TAG = 'CanBeObserved';

class Student {
  public name?: string;

  constructor(name?: string) {
    this.name = name ?? '';
  }

  // Provide a method in the object to determine whether the object can be observed.
  test(): void {
    const result = UIUtils.canBeObserved(this);
    // Whether the object can be observed.
    const isObserved = result.isObserved;
    hilog.info(0x00, TAG, `isObserved: ${JSON.stringify(isObserved)}`);
    // Reason for the object's observability.
    const reason = result.reason;
    hilog.info(0x00, TAG, `reason: ${reason}`);
    // Decorator information associated with the observable object.
    const decoratorInfoArr = result.decoratorInfo;
    decoratorInfoArr.forEach((decorator: DecoratorInfo) => {
      // Decorator name.
      const decoratorName = decorator.decoratorName;
      hilog.info(0x00, TAG, `decoratorName: ${decoratorName}`);
      // Name of the attribute decorated by the decorator.
      const stateVariableName = decorator.stateVariableName;
      hilog.info(0x00, TAG, `stateVariableName: ${stateVariableName}`);
      // Name of the component where the decorator is located.
      const owningName = decorator.owningComponentOrClassName;
      hilog.info(0x00, TAG, `owningComponentOrClassName: ${owningName}`);
      // ID of the component where the decorator is located.
      const owningId = decorator.owningComponentId;
      hilog.info(0x00, TAG, `owningComponentId: ${owningId}`);
      // Information about the component associated with the decorator.
      const dependentInfo = decorator.dependentInfo;
      dependentInfo.forEach((elementInfo: ElementInfo) => {
        // Name of the component associated with the decorator.
        const eleName = elementInfo.elementName;
        hilog.info(0x00, TAG, `elementName: ${eleName}`);
        // ID of the component associated with the decorator.
        const eleId = elementInfo.elementId;
        hilog.info(0x00, TAG, `elementId: ${eleId}`);
      })
    })
  }
}

@Entry
@Component
struct Index {
  @State student: Student = new Student('LiMei');

  build() {
    Column({ space: 20 }) {
      Classroom({ student: this.student })
      Home({ student: this.student })
      Button('test')
        .onClick(() => {
          // You can use this API on any page to determine whether the current object can be observed.
          this.student.test();
        })
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
  }
}

@Component
export struct Classroom {
  @State student: Student = new Student();

  build() {
    Column() {
      Text('Classroom ' + this.student.name)
      School({ student: this.student })
    }
  }
}

@Component
export struct Home {
  @State student: Student = new Student();

  build() {
    Column() {
      Text('Home ' + this.student.name)
    }
  }
}

@Component
export struct School {
  @State student: Student = new Student();

  build() {
    Column() {
      Text('School ' + this.student.name)
    }
  }
}
```

### makeObserved

static makeObserved\<T extends object\>(source: T): T

Converts ordinary unobservable data into observable data. For details, see [makeObserved API: Changing Unobservable Data to Observable Data](../../ui/state-management/arkts-new-makeObserved.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| source | T    | Yes  | Source object. It supports classes not decorated by @Observed or @ObservedV2, objects returned by **JSON.parse**, and classes decorated by @Sendable.<br>Array, Map, Set, and Date types are supported.<br>collections.Array, collections.Set, and collections.Map are supported.<br>For details, see [makeObserved API: Changing Unobservable Data to Observable Data](../../ui/state-management/arkts-new-makeObserved.md).|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| T    | Observable data.|

**Example**

```ts
import { UIUtils } from '@kit.ArkUI';

class NonObservedClass {
  name: string = 'Tom';
}

@Entry
@ComponentV2
struct Index {
  observedClass: NonObservedClass = UIUtils.makeObserved(new NonObservedClass());
  nonObservedClass: NonObservedClass = new NonObservedClass();

  build() {
    Column() {
      Text(`observedClass: ${this.observedClass.name}`)
        .onClick(() => {
          this.observedClass.name = 'Jane'; // This will trigger a UI update.
        })
      Text(`observedClass: ${this.nonObservedClass.name}`)
        .onClick(() => {
          this.nonObservedClass.name = 'Jane'; // This will not trigger a UI update.
        })
    }
  }
}
```

### enableV2Compatibility<sup>19+</sup>

static enableV2Compatibility\<T extends object\>(source: T): T

Enables V1 state variables to be observable in @ComponentV2. This API is primarily used in scenarios where V1 and V2 state management are mixed. For details, see [Mixing Use of State Management V1 and V2](../../ui/state-management/arkts-v1-v2-mixusage.md).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| source | T    | Yes  | Data source, which must be V1 state data.|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| T    | If the data source is V1 state data, returns data that can be observed in \@ComponentV2; otherwise, returns the data source itself.|


**Example**

```ts
import { UIUtils } from '@kit.ArkUI';

@Observed
class ObservedClass {
  name: string = 'Tom';
}

@Entry
@Component
struct CompV1 {
  @State observedClass: ObservedClass = new ObservedClass();

  build() {
    Column() {
      Text(`@State observedClass: ${this.observedClass.name}`)
        .onClick(() => {
          this.observedClass.name = 'State'; // This will trigger a UI update.
        })
      // Enable the V2 observation capability for the V1 state variable.
      CompV2({ observedClass: UIUtils.enableV2Compatibility(this.observedClass) })
    }
  }
}

@ComponentV2
struct CompV2 {
  @Param observedClass: ObservedClass = new ObservedClass();

  build() {
    // After the V2 observation capability is enabled for the V1 state variable, the first-level changes can be observed in V2.
    Text(`@Param observedClass: ${this.observedClass.name}`)
      .onClick(() => {
        this.observedClass.name = 'Param'; // This will trigger a UI update.
      })
  }
}
```

### makeV1Observed<sup>19+</sup>
static makeV1Observed\<T extends object\>(source: T): T

Wraps an unobservable object into an object that is observable by V1 state management. This API is equivalent to @Observed and can be used to initialize @ObjectLink.

This API can be used in conjunction with [enableV2Compatibility](#enablev2compatibility19) for scenarios where V1 and V2 state management are mixed. For details, see [Mixing Use of State Management V1 and V2](../../ui/state-management/arkts-v1-v2-mixusage.md).

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| source | T    | Yes  | Data source. Common classes, Array, Map, Set, and Date types are supported.<br>The [collections](../apis-arkts/arkts-apis-arkts-collections.md) type and [\@Sendable](../../arkts-utils/arkts-sendable.md) decorated classes are not supported.<br>**undefined** and **null** are not supported. V2 state management data and the return value of [makeObserved](#makeobserved) are not supported.|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| T    | For supported input parameter types, returns data observable by V1 state management. For unsupported input parameter types, returns the data source object itself.|

**Example**

```ts
import { UIUtils } from '@kit.ArkUI';

class Outer {
  outerValue: string = 'outer';
  inner: Inner;

  constructor(inner: Inner) {
    this.inner = inner;
  }
}

class Inner {
  interValue: string = 'inner';
}

@Entry
@Component
struct Index {
  @State outer: Outer = new Outer(UIUtils.makeV1Observed(new Inner()));

  build() {
    Column() {
      // The return value of makeV1Observed can be used to initialize @ObjectLink.
      Child({ inner: this.outer.inner })
    }
    .height('100%')
    .width('100%')
  }
}

@Component
struct Child {
  @ObjectLink inner: Inner;

  build() {
    Text(`${this.inner.interValue}`)
      .onClick(() => {
        this.inner.interValue += '!';
      })
  }
}
```

### makeBinding<sup>20+</sup>
static makeBinding\<T\>(getter: GetterCallback\<T\>): Binding\<T\>

Creates a read-only one-way data binding instance, which is used to construct the argument of the **Binding** type in the \@Builder function.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| getter | [GetterCallback\<T\>](#gettercallback20)    | Yes  | Callback used to obtain the value. Each value access triggers this function to obtain the latest value.|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| [Binding\<T\>](#bindingt20)    | Returns a read-only one-way data binding instance with a **value** attribute, which is used to obtain the currently bound value. The value can only be read and cannot be directly modified.|

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: Binding<number>) {
  Row() {
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // num1.value += 1; will throw an error because the Binding element does not support modification.
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;
  @Local number2: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        /**
         * Creates a read-only binding instance.
         * @param getter - Function for returning this.number1.
         * @returns Read-only Binding<number> object.
         *
         * Features:
         * 1. The value is recalculated each time when .value is accessed.
         * 2. The value cannot be directly modified.
         */
        UIUtils.makeBinding<number>(
          () => this.number1 // GetterCallback
        )
      )
    }
  }
}
```

### makeBinding<sup>20+</sup>
static makeBinding\<T\>(getter: GetterCallback\<T\>, setter: SetterCallback\<T\>): MutableBinding\<T\>

Creates a mutable two-way data binding instance, which is used to construct the argument of the **MutableBinding** type in the \@Builder function.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| getter | [GetterCallback\<T\>](#gettercallback20)    | Yes  | Callback used to obtain the value. Each value access triggers this function to obtain the latest value.|
| setter | [SetterCallback\<T\>](#settercallback20)    | Yes  | Callback used to update the value. Each modification to **.value** triggers this function.|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| [MutableBinding\<T\>](#mutablebindingt20)    | Returns a two-way data binding instance with a **value** attribute, which allows you read and modify data. If the value is set, the system checks whether the value type matches the generic type **T**.|

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num2: MutableBinding<number>) {
  Row() {
    Button(`Custom Button: ${num2.value}`)
      .onClick(() => {
        // MutableBinding type, which can be modified.
        num2.value += 1;
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;
  @Local number2: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        /**
         * Creates a mutable binding.
         * @param getter - Function that returns this.number2.
         * @param setter - Callback called when the binding value is modified.
         * @returns A mutable MutableBinding<number> object.
         *
         * Features:
         * 1. Read and write operations are supported.
         * 2. The setter callback is automatically called when .value is modified.
         */
        UIUtils.makeBinding<number>(
          () => this.number2, // GetterCallback
          (val: number) => {
            this.number2 = val;
          }) // SetterCallback
      )
    }
  }
}
```

### addMonitor<sup>20+</sup>
static addMonitor(target: object, path: string | string[], monitorCallback: MonitorCallback, options?: MonitorOptions): void

Dynamically adds a listener to the state variable of state management V2. For details, see [addMonitor and clearMonitor APIs: Dynamically Adding and Removing Listeners](../../ui/state-management/arkts-new-addMonitor-clearMonitor.md).

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| target | object | Yes  | Target object. Only [\@ComponentV2](../../ui/state-management/arkts-create-custom-components.md#componentv2) and [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md) instances are supported.<br>If an unsupported type is provided, a runtime error is thrown. For error code details, see the table below.|
| path | string \| string[]    | Yes  | Name path of the variable to be listened for. You can specify a path or pass a string array to specify multiple variable paths to be listened for at a time.<br>Only string and string array are supported. If an unsupported type is provided, a runtime error is thrown. For error code details, see the table below.|
| monitorCallback | [MonitorCallback](#monitorcallback20)   | Yes  | Listener function registered with the corresponding state variable. That is, when the state variable corresponding to the path changes, a specific function is called.<br>If an unsupported type is provided, a runtime error is thrown. For error code details, see the table below.|
| options | [MonitorOptions](#monitoroptions20)   | No  | Configuration item of the listener function. For details, see [MonitorOptions](#monitoroptions20).|


**Error codes**
For details about the error codes, see [State Management Error Codes](./errorcode-stateManagement.md).
| ID| Error Message|
| ------- | -------------------------------- |
|130000|The target is not a custom component instance or V2 class instance.|
|130001|The path is invalid.|
|130002|monitorCallback is not a function or an anonymous function.|

**Example**
In the following example:
1. In the constructor of **ObservedClass**, add the synchronous listener callback **onChange** to the **name** attribute.
2. Click the **Text** component and change the value of **name** to **Jack** and **Jane**. The **onChange** callback is triggered twice. The following logs are printed:
<!--code_no_check-->
```text
ObservedClass property name change from Tom to Jack
ObservedClass property name change from Jack to Jane
```

```Typescript
import { UIUtils } from '@kit.ArkUI';

@ObservedV2
class ObservedClass {
  @Trace name: string = 'Tom';

  onChange(mon: IMonitor) {
    mon.dirty.forEach((path: string) => {
      console.info(`ObservedClass property ${path} change from ${mon.value(path)?.before} to ${mon.value(path)?.now}`);
    });
  }

  constructor() {
    // Add the synchronous listener callback this.onChange for the name attribute to this ObservedClass instance.
    UIUtils.addMonitor(this, 'name', this.onChange, { isSynchronous: true });
  }
}

@Entry
@ComponentV2
struct Index {
  @Local observedClass: ObservedClass = new ObservedClass();

  build() {
    Column() {
      Text(`name: ${this.observedClass.name}`)
        .fontSize(20)
        .onClick(() => {
          this.observedClass.name = 'Jack';
          this.observedClass.name = 'Jane';
        })
    }
  }
}
```

### clearMonitor<sup>20+</sup>
static clearMonitor(target: object, path: string | string[], monitorCallback?: MonitorCallback): void

Deletes the listener added to the state variable of the state management V2 by calling the [addMonitor](#addmonitor20) API. For details, see [addMonitor and clearMonitor APIs: Dynamically Adding and Removing Listeners](../../ui/state-management/arkts-new-addMonitor-clearMonitor.md).

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| target | object | Yes  | Target object. Only [\@ComponentV2](../../ui/state-management/arkts-create-custom-components.md#componentv2) and [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md) instances are supported.<br>If an unsupported type is provided, a runtime error is thrown. For error code details, see the table below.|
| path | string \| string[]   | Yes  | Name path of the variable to be deleted. You can specify a path or pass a string array to delete the listener functions of multiple state variables at a time.<br>Only string and string array are supported. If an unsupported type is provided, a runtime error is thrown. For error code details, see the table below.|
| monitorCallback | [MonitorCallback](#monitorcallback20)   | No  | Listener function to be deleted.<br>If this parameter is not specified, all listener functions registered with the variable corresponding to the path will be deleted.<br>If an unsupported type is provided, a runtime error is thrown. For error code details, see the table below.|

**Error codes**
For details about the error codes, see [State Management Error Codes](./errorcode-stateManagement.md).

| ID| Error Message|
| ------- | -------------------------------- |
|130000|The target is not a custom component instance or V2 class instance.|
|130001|The path is invalid.|
|130002|monitorCallback is not a function or an anonymous function.|

**Example**
In the following example:
1. In the constructor of **ObservedClass**, add the synchronous listener callback **onChange** to the **age** attribute.
2. Click the **Text** component to trigger the auto-increment of the value of **age**, which then triggers the **onChange** callback function. The following log is printed:
   <!--code_no_check-->
   ```text
   ObservedClass property age change from 10 to 11
   ```
3. Click **clear monitor** to delete the **onChange** callback function usd to listen for the **age** attribute.
4. Click the **Text** component again to trigger the auto-increment of the value of **age**, which will not trigger the **onChange** callback function.

```ts
import { UIUtils } from '@kit.ArkUI';

@ObservedV2
class ObservedClass {
  @Trace age: number = 10;

  onChange(mon: IMonitor) {
    mon.dirty.forEach((path: string) => {
      console.info(`ObservedClass property ${path} change from ${mon.value(path)?.before} to ${mon.value(path)?.now}`);
    });
  }

  constructor() {
    // Add the synchronous listener callback this.onChange for the age attribute to this ObservedClass instance.
    UIUtils.addMonitor(this, 'age', this.onChange);
  }
}

@Entry
@ComponentV2
struct Index {
  @Local observedClass: ObservedClass = new ObservedClass();

  build() {
    Column() {
      Text(`age: ${this.observedClass.age}`)
        .fontSize(20)
        .onClick(() => {
          // Click to trigger age++ and the onChange callback.
          this.observedClass.age++;
        })
      Button('clear monitor')
        .onClick(() => {
          // Click clearMonitor and delete the listener function onChange of age from this.observedClass.
          // Click the button again to trigger age++ but not the listener function onChange.
          UIUtils.clearMonitor(this.observedClass, 'age', this.observedClass.onChange);
        })
    }
  }
}
```

### applySync<sup>22+</sup>

static applySync\<T\>(task: TaskCallback): T

Synchronously updates a specified state variable. This API receives a closure function and updates only the internal modifications, including the updates of [@Computed](../../ui/state-management/arkts-new-computed.md) and [@Monitor](../../ui/state-management/arkts-new-monitor.md) decorators, and re-rendering of the UI nodes. For details, see [applySync/flushUpdates/flushUIUpdates APIs: Synchronous Update](../../ui/state-management/arkts-new-applySync-flushUpdates-flushUIUpdates.md).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                         | Mandatory| Description                                            |
| ------ | ----------------------------- | ---- | ------------------------------------------------ |
| task   | [TaskCallback](#taskcallback22) | Yes  | Closure function. The state variable modification generated in the closure will be executed synchronously.|

**Return value**

| Type| Description                      |
| ---- | -------------------------- |
| T    | Return value obtained by executing the closure function.|

**Error codes**

For details about the error codes, see [State Management Error Codes](./errorcode-stateManagement.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 140001   | The function is not allowed to be called in @Computed. |

**Example**

```ts
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local w: number = 50; // Width.
  @Local h: number = 50; // Height.
  @Local message: string = 'Hello';

  build() {
    Column() {
      Button('change size')
        .margin(20)
        .onClick(() => {
          // Values are changed additionally before the animation is executed.
          UIUtils.applySync(() => {
            this.w = 100;
            this.h = 100;
            this.message = 'Hello World';
          });
          // The size of the column box gradually changes from (100 × 100) to (200 × 200) within 1s, and the text in the box changes to "Hello ArkUI".
          this.getUIContext().animateTo({
            duration: 1000
          }, () => {
            console.info(`animateTo-in, w=${this.w}, h=${this.h}`);
            this.w = 200;
            this.h = 200;
            this.message = 'Hello ArkUI';
            console.info(`animateTo-out, w=${this.w}, h=${this.h}`);
          });
        })
      // Column box.
      Column() {
        Text(`${this.message}`)
      }
      .backgroundColor('#ff17a98d')
      .width(this.w)
      .height(this.h)
    }
  }
}
```

### flushUpdates<sup>22+</sup>

static flushUpdates(): void

Synchronously updates all state variable modifications before this API call, including the updates of @Computed and @Monitor decorators, and re-rendering of the UI nodes. For details, see [applySync/flushUpdates/flushUIUpdates APIs: Synchronous Update](../../ui/state-management/arkts-new-applySync-flushUpdates-flushUIUpdates.md).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Error codes**

For details about the error codes, see [State Management Error Codes](./errorcode-stateManagement.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 140001   | The function is not allowed to be called in @Computed. |
| 140002   | The function is not allowed to be called in @Monitor.  |

**Example**

```ts
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local w: number = 50; // Width.
  @Local h: number = 50; // Height.
  @Local message: string = 'Hello';

  build() {
    Column() {
      Button('change size')
        .margin(20)
        .onClick(() => {
          // Values are changed additionally before the animation is executed.
          this.w = 100;
          this.h = 100;
          this.message = 'Hello World';
          UIUtils.flushUpdates();
          // The size of the column box gradually changes from (100 × 100) to (200 × 200) within 1s, and the text in the box changes to "Hello ArkUI".
          this.getUIContext().animateTo({
            duration: 1000
          }, () => {
            console.info(`animateTo-in, w=${this.w}, h=${this.h}`);
            this.w = 200;
            this.h = 200;
            this.message = 'Hello ArkUI';
            console.info(`animateTo-out, w=${this.w}, h=${this.h}`);
          });
        })
      // Column box.
      Column() {
        Text(`${this.message}`)
      }
      .backgroundColor('#ff17a98d')
      .width(this.w)
      .height(this.h)
    }
  }
}
```

### flushUIUpdates<sup>22+</sup>

static flushUIUpdates(): void

Processes all state variable modifications before this API call and synchronizes the [dirty](../../ui/state-management/arkts-state-management-introduce.md#triggering-updates) UI nodes. However, it does not synchronize the execution of @Computed and @Monitor decorators. For details, see [applySync/flushUpdates/flushUIUpdates: Synchronous Update](../../ui/state-management/arkts-new-applySync-flushUpdates-flushUIUpdates.md).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Error codes**

For details about the error codes, see [State Management Error Codes](./errorcode-stateManagement.md).

| ID| Error Message                                              |
| -------- | ------------------------------------------------------ |
| 140001   | The function is not allowed to be called in @Computed. |
| 140002   | The function is not allowed to be called in @Monitor.  |

**Example**

```ts
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local w: number = 50; // Width.
  @Local h: number = 50; // Height.
  @Local message: string = 'Hello';

  build() {
    Column() {
      Button('change size')
        .margin(20)
        .onClick(() => {
          // Values are changed additionally before the animation is executed.
          this.w = 100;
          this.h = 100;
          this.message = 'Hello World';
          UIUtils.flushUIUpdates();
          // The size of the column box gradually changes from (100 × 100) to (200 × 200) within 1s, and the text in the box changes to "Hello ArkUI".
          this.getUIContext().animateTo({
            duration: 1000
          }, () => {
            console.info(`animateTo-in, w=${this.w}, h=${this.h}`);
            this.w = 200;
            this.h = 200;
            this.message = 'Hello ArkUI';
            console.info(`animateTo-out, w=${this.w}, h=${this.h}`);
          });
        })
      // Column box.
      Column() {
        Text(`${this.message}`)
      }
      .backgroundColor('#ff17a98d')
      .width(this.w)
      .height(this.h)
    }
  }
}
```

## TaskCallback<sup>22+</sup>

type TaskCallback = () => T

Defines a synchronous callback.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type| Description                      |
| ---- | -------------------------- |
| T    | Return value obtained by executing the closure function.|

## MonitorOptions<sup>20+</sup>

Defines the optional parameter of [addMonitor](#addmonitor20), which is used to configure the callback type.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Parameter| Type| Read-Only| Optional| Description    |
| ------ | ---- | ---- | ---- | ------------ |
|isSynchronous|boolean|No|Yes|Whether the current callback is a synchronous callback. **true**: The current callback is a synchronous callback. **false** (default value): The current callback is an asynchronous callback.|

## MonitorCallback<sup>20+</sup>
type MonitorCallback = (monitorValue: IMonitor) => void

Listener callback function of the [IMonitor](./arkui-ts/ts-state-management-watch-monitor.md#imonitor12) type.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| monitorValue | IMonitor | Yes  | Change information passed by the callback.|

## StorageDefaultCreator\<T\>

type StorageDefaultCreator\<T\> = () => T

Obtains the default constructor.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
|   T  | Default constructor.|

**Example**

```ts
import { PersistenceV2 } from '@kit.ArkUI';

@ObservedV2
class SampleClass {
  @Trace id: number = 0;
  count: number = 1;
}

@ObservedV2
class FatherSampleClass {
  @Trace sampleClass: SampleClass = new SampleClass();
}

// Persist the key-value pair whose key is SampleClass and value is new SampleClass(), and assign it to source.
// StorageDefaultCreator refers to () => new FatherSampleClass().
const source: FatherSampleClass | undefined = PersistenceV2.connect(FatherSampleClass, () => new FatherSampleClass());

@Entry
@Component
struct SampleComp {
  data: FatherSampleClass | undefined = source;

  build() {
    Column() {
      Text(`${this.data?.sampleClass.id}`)
    }
  }
}
```

## TypeConstructorWithArgs\<T\>

Represents a class constructor that accepts arbitrary arguments.

### new

new(...args: any): T

Creates and returns an instance of the specified type T.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| ...args | any    | No  | Function arguments.  |

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| T    | Instance of the T type.|

**Example**

```ts
import { PersistenceV2 } from '@kit.ArkUI';

@ObservedV2
  // TypeConstructorWithArgs refers to the SampleClass constructor.
class SampleClass {
  @Trace id: number = 0;
  count: number = 1;
}

@ObservedV2
class FatherSampleClass {
  @Trace sampleClass: SampleClass = new SampleClass();
}

// Persist the key-value pair whose key is SampleClass and value is new SampleClass(), and assign it to source.
const source: FatherSampleClass | undefined = PersistenceV2.connect(FatherSampleClass, () => new FatherSampleClass());

@Entry
@Component
struct SampleComp {
  data: FatherSampleClass | undefined = source;

  build() {
    Column() {
      Text(`${this.data?.sampleClass.id}`)
    }
  }
}
```

## PersistenceErrorCallback

type PersistenceErrorCallback = (key: string, reason: 'quota' | 'serialization' | 'unknown', message: string) => void

Defines a callback used to return the cause of the persistence failure.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| key | string    | Yes  | Key of the error.  |
|reason| 'quota' \| 'serialization' \| 'unknown'    | Yes  | Reason of the error.  |
| message | string    | Yes  | Extra information about the error.  |

**Example**

```ts
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace id: number = 0;
  count: number = 10;
}

@ObservedV2
export class Sample {
  // For complex objects, use the @Type decorator to ensure successful serialization.
  @Type(SampleChild)
  @Trace sampleChild: SampleChild = new SampleChild();
}

// Callback used to receive persistence errors.
// PersistenceErrorCallback refers to (key: string, reason: string, msg: string) => {console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);}.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@Entry
@ComponentV2
struct Index {
  // Create a KV pair whose key is Sample in PersistenceV2 (if the key exists, the data in PersistenceV2 is returned) and associate it with data.
  // Add @Local to decorate the data attribute that needs to change the connected object. (Changing the connected object is not recommended.)
  @Local data: Sample = PersistenceV2.connect(Sample, () => new Sample())!;
  pageStack: NavPathStack = new NavPathStack();

  build() {
    Text(`Index add 1 to data.id: ${this.data.sampleChild.id}`)
      .fontSize(30)
      .onClick(() => {
        this.data.sampleChild.id++;
      })
  }
}
```

## TypeConstructor\<T\>

Represents a class constructor.

### new

new(): T

Creates and returns an instance of the specified type T.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| T    | Instance of the T type.|

**Example**

```ts
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace id: number = 0;
  count: number = 10;
}

@ObservedV2
export class Sample {
  // For complex objects, use the @Type decorator to ensure successful serialization.
  // TypeConstructor refers to SampleChild.
  @Type(SampleChild)
  @Trace sampleChild: SampleChild = new SampleChild();
}

@Entry
@ComponentV2
struct Index {
  data: Sample = PersistenceV2.connect(Sample, () => new Sample())!;

  build() {
    Column() {
      Text(`Index add 1 to data.id: ${this.data.sampleChild.id}`)
        .fontSize(30)
        .onClick(() => {
          this.data.sampleChild.id++;
        })
    }
  }
}
```

## TypeDecorator

type TypeDecorator = \<T\>(type: TypeConstructor\<T\>) => PropertyDecorator

Defines a property decorator.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| type | [TypeConstructor\<T\>](#typeconstructort)    | Yes  | Type of the class property.  |

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| PropertyDecorator    | Property decorator.|

**Example**

```ts
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace id: number = 0;
  count: number = 10;
}

@ObservedV2
export class Sample {
  // For complex objects, use the @Type decorator to ensure successful serialization.
  // TypeDecorator refers to @Type.
  @Type(SampleChild)
  @Trace sampleChild: SampleChild = new SampleChild();
}

@Entry
@ComponentV2
struct Index {
  data: Sample = PersistenceV2.connect(Sample, () => new Sample())!;

  build() {
    Column() {
      Text(`Index add 1 to data.id: ${this.data.sampleChild.id}`)
        .fontSize(30)
        .onClick(() => {
          this.data.sampleChild.id++;
        })
    }
  }
}
```

## GetterCallback<sup>20+</sup>

type GetterCallback\<T\> = () => T

Defines a callback used to obtain a value.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| T    | Value of the T type.|

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: Binding<number>) {
  Row() {
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // num1.value += 1; will throw an error because the Binding element does not support modification.
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;
  @Local number2: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        // The first parameter of the UIUtils.makeBinding function must be a GetterCallback.
        UIUtils.makeBinding<number>(
          () => this.number1 // GetterCallback
        )
      )
    }
  }
}
```

## SetterCallback<sup>20+</sup>

type SetterCallback\<T\> = (newValue: T) => void

Defines a callback used to set a value.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| newValue | T    | Yes  | Parameter of the T type.  |

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num2: MutableBinding<number>) {
  Row() {
    Button(`Custom Button: ${num2.value}`)
      .onClick(() => {
        // MutableBinding supports mutability. You can change the value of num2.value.
        num2.value += 1;
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;
  @Local number2: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        // The second parameter of the UIUtils.makeBinding function must be a SetterCallback.
        UIUtils.makeBinding<number>(
          () => this.number2, // GetterCallback
          (val: number) => {
            this.number2 = val;
          }) // SetterCallback is mandatory. Otherwise, a runtime error will be thrown.
      )
    }
  }
}
```

## Binding\<T\><sup>20+</sup>

Represents the generic class for read-only data binding, which can bind data of any type.

### value<sup>20+</sup>
get value(): T

Obtains a bound value.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type            | Description                                                        |
| -------------------- | ------------------------------------------------------------ |
| T |Returns a value whose type is the generic parameter T, which is the same as the type defined by **Binding\<T\>**.|

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: Binding<number>) {
  // The first parameter of CustomButton is Binding, which is a generic class for read-only data binding.
  Row() {
    // num1.value Binding can use the bound value.
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // num1.value += 1; will throw an error because the generic class bound to the read-only data does not support modification.
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;
  @Local number2: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        UIUtils.makeBinding<number>(
          () => this.number1 // GetterCallback
        )
      )
    }
  }
}
```

## MutableBinding\<T\><sup>20+</sup>

Represents a generic class for mutable data binding, which allows the read and write operations on the bound value and provides complete **get** and **set** accessors.

### value<sup>20+</sup>
set value(newValue: T)

Provides the **set** accessor to set a new value for the current bound value. The **set** accessor must be provided when the **MutableBinding** class instance is constructed. Otherwise, a runtime error will be thrown when the **set** accessor is triggered.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| newValue  | T | Yes  | New value, whose type is the generic parameter T, which is the same as the type defined in **MutableBinding\<T\>**.|

### value<sup>20+</sup>
get value(): T

Provides a **get** accessor to obtain the current bound value.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type            | Description                                                        |
| -------------------- | ------------------------------------------------------------ |
| T |Returns a value whose type is the generic parameter T, which is the same as the type defined by **Binding\<T\>**.|

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num2: MutableBinding<number>) {
  // The second parameter of CustomButton is MutableBinding, which is a generic class of mutable data binding.
  Row() {
    Button(`Custom Button: ${num2.value}`)
      .onClick(() => {
        // The generic class of mutable data binding can be used to modify the bound value.
        num2.value += 1;
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;
  @Local number2: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        UIUtils.makeBinding<number>(
          () => this.number2, // GetterCallback
          (val: number) => {
            this.number2 = val;
          }) // SetterCallback is mandatory. Otherwise, a runtime error will be thrown.
      )
    }
  }
}
```
<!--no_check-->