# @ohos.arkui.StateManagement (State Management)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926; @liwenzhen3; @zzq212050299-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @HelloCrease-->

The state management module provides data storage, persistent data management, UIAbility data storage, and environment state and tools required by applications.

>**NOTE**
>
>The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.


The meanings of T and S in this topic are as follows:


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

static connect\<T extends object\>( <br>
      type: TypeConstructorWithArgs\<T\>, <br>
      keyOrDefaultCreator?: string | StorageDefaultCreator\<T\>, <br>
      defaultCreator?: StorageDefaultCreator\<T\> <br>
): T | undefined

Stores key-value pair data in the application memory. If the given key already exists in [AppStorageV2](../../ui/state-management/arkts-new-appstoragev2.md), the corresponding value is returned. Otherwise, a default value is constructed using the default value constructor and returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description              |
| -------- | ------ | ---- | ---------------------- |
| type | [TypeConstructorWithArgs\<T\>](#typeconstructorwithargst) | Yes  | Type. If no key is specified, the name of the type is used as the key.|
| keyOrDefaultCreator | string \| [StorageDefaultCreator\<T\>](#storagedefaultcreatort) | No  | Key, or the constructor for obtaining the default value.|
| defaultCreator | StorageDefaultCreator\<T\> | No  | Constructor for obtaining the default value.|

>**NOTE**
>
>1. The second parameter is used when no **key** is specified, and the third parameter is used otherwise (including when the second parameter is invalid).
>
>2. If the data has been stored in AppStorageV2, you can obtain the stored data without using the default constructor. If the data has not been stored, you must specify a default constructor; otherwise, an application exception will be thrown.
>
>3. Ensure that the data types match the key. Connecting different types of data to the same key will result in an application exception.
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

static remove\<T\>(keyOrType: string | TypeConstructorWithArgs\<T\>): void

Removes the specified key-value pair from [AppStorageV2](../../ui/state-management/arkts-new-appstoragev2.md). If the specified key does not exist in AppStorageV2, the removal will fail.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description              |
| -------- | ------ | ---- | ---------------------- |
| keyOrType | string \| TypeConstructorWithArgs\<T\> | Yes  | Key to be removed. If a type is specified, the key to be deleted is the name of that type.|

>**NOTE**
>
>Attempting to remove a key that does not exist in AppStorageV2 will result in a warning.


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

static keys(): Array\<string\>

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
| type    |[ConnectOptions\<T\>](#connectoptions18)    |Yes |**connect** parameter passed in. For details, see the description of **ConnectOptions**.|

**Return value**

|Type  |Description                |
|----------|-----------------------------------|
|T \| undefined    |Returns the data if creation or acquisition is successful; otherwise, returns **undefined**.   |

> **NOTE**
>
> 1. The second parameter is used when no **key** is specified, and the third parameter is used otherwise (including when the second parameter is invalid).
>
> 2. If the data has been stored in PersistenceV2, you can obtain the stored data without using the default constructor. Otherwise, you must specify a default constructor to avoid application exceptions.
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
> 8. Avoid using **connect** and **globalConnect** together, because they have different data copy paths. If they must be used together, make sure the keys are unique to avoid application crashes.
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

// Use the key 'global1' with an encryption level of EL1 for connection.
const p1: Sample = PersistenceV2.globalConnect({
  type: Sample,
  key: 'global1',
  defaultCreator: () => new Sample(),
  areaMode: contextConstant.AreaMode.EL1
})!;

// Use the key 'global2' with the constructor function for connection. If no encryption level is specified, the default EL2 level is used.
const p2: Sample = PersistenceV2.globalConnect({ type: Sample, key: 'global2', defaultCreator: () => new Sample() })!;

// Use the key 'global3' with an explicit encryption level value (3 in this example) for connection. Note that values outside the valid range of 0-4 will cause application crashes.
const p3: Sample = PersistenceV2.globalConnect({
  type: Sample,
  key: 'global3',
  defaultCreator: () => new Sample(),
  areaMode: 3
})!;

```

### save

static save\<T\>(keyOrType: string | TypeConstructorWithArgs\<T\>): void

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
| callback | PersistenceErrorCallback \| undefined  | Yes  | Callback invoked when persistence fails.|

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

|Name  |Type   |Read-Only  |Optional   |Description     |
|--------|------------|------------|-----------|--------------|
|type        | TypeConstructorWithArgs\<T\>   |No  |No  |Specified type.        |
|key         | string   |No  |Yes  |key used for connection. If it is not provided, the name of the type is used as the key.            |
|defaultCreator   | StorageDefaultCreator\<T\>   |No  |Yes  |Default constructor. It is recommended that this parameter be passed in. If **globalConnect** is called for the first time with a key and this parameter is not provided, an error will occur.|
|areaMode      | contextConstant.AreaMode   |No  |Yes   |Encryption level, ranging from EL1 to EL5 (corresponding to the value from 0 to 4). For details, see [Encryption Levels](../../application-models/application-context-stage.md#obtaining-and-modifying-encryption-levels). If no value is passed in, EL2 is used by default. Storage paths vary based on the encryption levels. If the input value of encryption level is not in the range of **0** to **4**, a crash occurs.|

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
### makeObserved

static makeObserved\<T extends object\>(source: T): T

Converts ordinary unobservable data into observable data. For details, see [makeObserved API: Changing Unobservable Data to Observable Data](../../ui/state-management/arkts-new-makeObserved.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| source | T    | Yes  | Source object. The class decorated with @Observed or @ObservedV2, the object returned by JSON.parse, and the class decorated with @Sendable are supported.<br>Array, Map, Set, and Date types are supported.<br>**collection.Array**, **collection.Set**, and **collection.Map** are supported.<br>For details, see [makeObserved API: Changing Unobservable Data to Observable Data](../../ui/state-management/arkts-new-makeObserved.md).|

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
| T    | If the data source is V1 state data, returns data that can be observed in @ComponentV2; otherwise, returns the data source itself.|


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
          this.observedClass.name = 'State'; // Refresh
        })
      // Enable V2 observability for the V1 state variable.
      CompV2({ observedClass: UIUtils.enableV2Compatibility(this.observedClass) })
    }
  }
}

@ComponentV2
struct CompV2 {
  @Param observedClass: ObservedClass = new ObservedClass();

  build() {
    // After V2 observability is enabled for the V1 state variable, the first-layer changes can be observed in V2.
    Text(`@Param observedClass: ${this.observedClass.name}`)
      .onClick(() => {
        this.observedClass.name = 'Param'; // Refresh
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
| source | T    | Yes  | Data source. Common class, Array, Map, Set, and Date types are supported.<br>The [collections](../apis-arkts/arkts-apis-arkts-collections.md) type and [@Sendable](../../arkts-utils/arkts-sendable.md) decorated classes are not supported.<br>**undefined** and **null** are not supported. V2 state management data and the return value of [makeObserved](#makeobserved) are not supported.|

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

Creates a read-only one-way data binding instance, which is used to construct the actual parameter corresponding to the Binding parameter type in the \@Builder function.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| getter | [GetterCallback\<T\>](#gettercallback20)    | Yes  | Callback function for obtaining the value. The function is executed each time the value is accessed to obtain the latest value.|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| [Binding\<T\>](#bindingt20)    | The value attribute contains only one value, which is used to obtain the currently bound value. The value can be read but cannot be directly modified.|

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: Binding<number>) {
  Row() {
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // num1.value += 1; will report an error because Binding does not support modification.
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

Creates a mutable binding instance for building the actual parameter whose parameter type is MutableBinding in the \@Builder function.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| getter | [GetterCallback\<T\>](#gettercallback20)    | Yes  | Callback function for obtaining the value. The function is executed each time when the value is accessed to obtain the latest value.|
| setter | [SetterCallback\<T\>](#settercallback20)    | Yes  | Defines how to update the value. This function is automatically called when .value is modified.|

**Return value**

| Type| Description                                            |
| ---- | ------------------------------------------------ |
| [MutableBinding\<T\>](#mutablebindingt20)    | Contains the value attribute. You can read and modify data through .value. When the value is set, the system checks whether the type matches the generic T.|

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
         * @returns Returns a mutable MutableBinding<number> object.
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

Adds a listener to a state variable of State Management 2.0. For details, see [addMonitor/clearMonitor](../../ui/state-management/arkts-new-addMonitor-clearMonitor.md).

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| target | object | Yes  | Target object. Only [\@ComponentV2](../../ui/state-management/arkts-new-componentV2.md) and [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md) instances are supported.<br>If the type is not supported, a runtime error is thrown. For details about the error code, see the table.|
| path | string \| string[]    | Yes  | Path of the variable to be listened to. You can specify a path or pass a string array to specify multiple variable paths to be listened to at a time.<br>Only strings and string arrays are supported. If the type is not supported, a runtime error is thrown. For details about the error code, see the table.|
| monitorCallback | [MonitorCallback](#monitorcallback20)   | Yes  | Listening function registered for the corresponding state variable. That is, when the state variable corresponding to the path changes, the corresponding function is called back.<br>If the type is not supported, a runtime error is thrown. For details about the error code, see the table.|
| options | [MonitorOptions](#monitoroptions20)   | No  | Configuration item of the listening function. For details, see [MonitorOptions](#monitoroptions20).|


**Error codes**
For details about the error codes, see [State Management Error Codes](./errorcode-stateManagement.md).
| ID| Error Message|
| ------- | -------------------------------- |
|130000|The target is not a custom component instance or V2 class instance.|
|130001|The path is invalid.|
|130002|monitorCallback is not a function or an anonymous function.|

**Example**
In the following example:
1. In the constructor of ObservedClass, add the synchronization listening callback onChange for the name attribute.
2. Click the Text component and change the value of name to Jack and Jane. The onChange callback is triggered twice. The logs are as follows:
<!--code_no_check-->
```
ObservedClass property name change from Tom to Jack
ObservedClass property name change from Jack to Jane
```

```ts
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
    // Add the listening callback this.onChange of the name attribute to the instance this of ObservedClass. The listening callback is synchronous.
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

Deletes the listener added to the state variable of the state management V2 by calling [addMonitor](#addmonitor20). For details, see [addMonitor/clearMonitor](../../ui/state-management/arkts-new-addMonitor-clearMonitor.md).

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| target | object | Yes  | Target object. Only the [\@ComponentV2](../../ui/state-management/arkts-new-componentV2.md) and [\@ObservedV2](../../ui/state-management/arkts-new-observedV2-and-trace.md) instances are supported.<br>If the type is not supported, a runtime error is thrown. For details about the error code, see the table below.|
| path | string \| string[]   | Yes  | Name path of the variable whose listener is to be deleted. You can specify a path or pass a string array to delete the listener functions of multiple state variables at a time.<br>Only strings and arrays are supported. If the type is not supported, a runtime error is thrown. For details about the error code, see the table below.|
| monitorCallback | [MonitorCallback](#monitorcallback20)   | No  | Listener function to be deleted.<br>If this parameter is not passed, all listener functions registered with the variable corresponding to path are deleted.<br>If the type is not supported, a runtime error is thrown. For details about the error code, see the table below.|

**Error codes**
For details about the error codes, see [State Management Error Codes](./errorcode-stateManagement.md).
| ID| Error Message|
| ------- | -------------------------------- |
|130000|The target is not a custom component instance or V2 class instance.|
|130001|The path is invalid.|
|130002|monitorCallback is not a function or an anonymous function.|

**Example**
In the following example:
1. Add the synchronous listening callback onChange of the age attribute to the constructor of ObservedClass.
2. Click the Text component to trigger the age increment. The onChange listening callback function is triggered. The log information is as follows:
<!--code_no_check-->
```
ObservedClass property age change from 10 to 11
```
3. Click clear monitor to delete the onChange listening function of age.
4. Click the Text component again to trigger the age increment. The onChange function is not triggered.

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
    //Add the listening callback this.onChange of the name attribute to the instance this of ObservedClass. The listening callback is synchronous.
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
          //Click to trigger age++. The onChange callback is triggered.
          this.observedClass.age++;
        })
      Button('clear monitor')
        .onClick(() => {
          //Click clearMonitor to delete the onChange listening function of age in this.observedClass.
          // Click the button again to trigger age++. The onChange listener is not triggered.
          UIUtils.clearMonitor(this.observedClass, 'age', this.observedClass.onChange);
        })
    }
  }
}
```

## MonitorOptions<sup>20+</sup>

Optional parameter of [addMonitor](#addmonitor20), which is used to configure the callback type.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description    |
| ------ | ---- | ---- | ---- | ------------ |
|isSynchronous|boolean|No|Yes|Whether the current callback function is a synchronous callback. true: synchronous callback. The default value is false, indicating an asynchronous callback.|

## MonitorCallback<sup>20+</sup>
type MonitorCallback = (monitorValue: IMonitor) => void

Listener callback function of the [IMonitor](./arkui-ts/ts-state-management-watch-monitor.md#imonitor12) type.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| monitorValue | IMonitor | Yes  | Changed information passed by the callback function.|

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

// Persist the key-value pair with the key SampleClass and the value as an instance of SampleClass(), and assign it to variable source.
// StorageDefaultCreator refers to the function () => new FatherSampleClass().
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

// Persist the key-value pair with the key SampleClass and the value as an instance of SampleClass(), and assign it to variable source.
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

Represents the callback invoked when persistence fails.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| key | string    | Yes  | Key associated with the error.  |
|reason| 'quota' \| 'serialization' \| 'unknown'    | Yes  | Type of the error.  |
| message | string    | Yes  | Additional information about the error.  |

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
  // Create a key-value pair with the key Sample in PersistenceV2 (if the key exists, the data in PersistenceV2 is returned) and associate it with data.
  // Add @Local to decorate the data property that needs to change the connected object. (Changing the connected object is not recommended.)
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

Class constructor.

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

Property decorator.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description    |
| ------ | ---- | ---- | ------------ |
| type | [TypeConstructor\<T\>](#typeconstructort)    | Yes  | Type of the class property decorated.  |

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

Callback method for obtaining the value.

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
        // num1.value += 1; will report an error because the Binding type cannot be modified.
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
        // The first parameter of the UIUtils.makeBinding function must be GetterCallback.
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

Sets the callback method of the value.

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
        // MutableBinding supports modification. num2.value can be modified.
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
        // The second parameter of the UIUtils.makeBinding function must be SetterCallback.
        UIUtils.makeBinding<number>(
          () => this.number2, // GetterCallback
          (val: number) => {
            this.number2 = val;
          }) // SetterCallback must be provided. Otherwise, a runtime error will occur when the function is triggered.
      )
    }
  }
}
```

## Binding\<T\><sup>20+</sup>

A generic class for read-only data binding, which can bind data of any type.

### value<sup>20+</sup>
get value(): T

Provides the get accessor to obtain the bound value.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type            | Description                                                        |
| -------------------- | ------------------------------------------------------------ |
| T |The return value type is the generic parameter T, which is the same as the type defined by Binding\<T\>.|

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: Binding<number>) {
  // The first parameter of CustomButton is Binding, a generic class for read-only data binding.
  Row() {
    // num1.value Binding can use the bound value.
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // num1.value += 1; will report an error, as the generic class for read-only data binding cannot modify the value.
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

A generic class for variable data binding, which allows read and write operations on the bound value and provides complete get and set accessors.

### value<sup>20+</sup>
set value(newValue: T)

Provides the set accessor to set the bound value. The set accessor must be provided when a MutableBinding instance is constructed. Otherwise, a runtime error occurs when the set accessor is triggered.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| newValue  | T | Yes  | The parameter type is the generic parameter T, which is the same as the type defined by MutableBinding\<T\>.|

### value<sup>20+</sup>
get value(): T

Provides the get accessor to obtain the current binding value.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type            | Description                                                        |
| -------------------- | ------------------------------------------------------------ |
| T |The return value type is the generic parameter T, which is the same as the type defined by Binding\<T\>.|

**Example**

```ts
import { Binding, MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num2: MutableBinding<number>) {
  // The second parameter of CustomButton is MutableBinding, a generic class of mutable data binding.
  Row() {
    Button(`Custom Button: ${num2.value}`)
      .onClick(() => {
        // The generic class of mutable data binding can modify the bound value.
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
          }) // SetterCallback must be provided. Otherwise, a runtime error occurs when the callback is triggered.
      )
    }
  }
}
```
