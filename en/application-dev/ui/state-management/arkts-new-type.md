# \@Type Decorator: Marking the Types of the Class Property
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=b4c16a3481f0a0bf24de133bf760018019cda10c translatedAt=2026-09-21T11:26:33.319Z pushedAt=2026-09-23T09:14:41.756Z -->

To prevent the loss of complex types of properties during class serialization, developers can use the [@Type](../../reference/apis-arkui/arkui-ts/ts-state-management-type.md#type) decorator to decorate class properties.

The purpose of `@Type` is to mark class properties. Used together with **PersistenceV2**, `@Type` can prevent type information loss during serialization. Before reading this topic, you are advised to read [PersistenceV2](./arkts-new-persistencev2.md).

>**NOTE**
>
> \@Type is supported since API version 12.
>
> This decorator can be used in atomic services since API version 12.

## Overview

\@Type marks class properties to avoid losing type information during class property serialization, facilitating class deserialization.

## Decorator Description

| \@Type Decorator| Description|
| ------------------- | ------------------------------------------------------------ |
| Parameters| Type.|
| Allowed type | Object class and built-in types such as Array, Date, Map, and Set. |

## Constraints

1. @Type can be used only in classes decorated with [\@ObservedV2](./arkts-new-observedV2-and-trace.md) and cannot be used in custom components.

   <!-- @[DataModel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NewType/entry/src/main/ets/pages/DataModel.ets) --> 

   ``` TypeScript
   class Sample {
     private data: number = 0;
   }
   @ObservedV2
   class Info {
     @Type(Sample)
     @Trace public sample: Sample = new Sample(); // Correct usage
   }
   ```

   ```ts
    @Observed
    class Info2 {
      @Type(Sample)
      sample: Sample = new Sample(); // Incorrect usage. @Type cannot be used in the @Observed decorated class. Otherwise, an error is reported during compilation.
    }
    @ComponentV2
    struct Index {
      @Type(Sample)
      sample: Sample = new Sample(); // Incorrect usage. @Type cannot be used in the custom component. Otherwise, an error is reported during compilation.
      build() {
      }
    }
   ```

2. Types such as **collections.Set** and **collections.Map** are not supported.

3. Non-built-in types, such as [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md), NativePointer, and other Native types, as well as ArkTS container types such as [ArrayList](../../reference/apis-arkts/js-apis-arraylist.md), are not supported.

4. Primitive types such as **string**, **number**, and **boolean**, are not supported.

5. Classes whose constructor functions contain parameters are not supported.

## Use Cases

### Saving Data for Persistence

<!-- @[NewType](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/NewType/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace childNumber: number = 1;
}

@ObservedV2
class Sample {
  // @Type is required for complex objects to ensure successful deserialization. If @Type is removed, deserialization fails.
  @Type(SampleChild)
  // If a class property does not have an initial value, it needs to be manually saved after being decorated with @Type. Otherwise, the persistence fails.
  // If a class property cannot be decorated with @Type, it must have an initial value to be persisted.
  @Trace sampleChild?: SampleChild = undefined;
}

@Entry
@ComponentV2
struct TestCase {
  @Local sample: Sample = PersistenceV2.connect(Sample, () => new Sample)!;

  build() {
    Column() {
      Text('childNumber value:' + this.sample.sampleChild?.childNumber)
        .fontSize(30)
        .margin(10)
        .onClick(() => {
          this.sample.sampleChild = new SampleChild();
          this.sample.sampleChild.childNumber = 2;
          PersistenceV2.save(Sample);
        })
    }
    .width('100%')
  }
}
```

![type-sync-0](./figures/type-sync-0.gif)

## FAQ

### \@Type Passing a Container Generic Type Instead of the Element Type

\@Type When decorating properties of container types such as `Array<T>`, `Set<T>`, and `Map<string, T>`, pass the class corresponding to the element type T, not the container generic type such as `Array<T>`. Generic parameters are erased at runtime, so `@Type(Array<T>)` is equivalent to `@Type(Array)`, and `@Type(Set<T>)` is equivalent to `@Type(Set)`. The framework cannot determine that the element type is T from them.

| Property Type | \@Type Should Pass | Should Not Pass |
|---|---|---|
| `Array<T>` | `T` | `Array<T>`, `Array` |
| `Set<T>` | `T` | `Set<T>`, `Set` |
| `Map<string, T>` | `T` | `Map<string, T>`, `Map` |

When T is a non-custom class such as a primitive type, Date, Array, Set, or Map, the framework natively supports deserialization, and the \@Type parameter does not affect the result. When T is a custom class, data can be saved normally on the first run, but when the application restarts and restores data from the disk, deserialization creates an empty container instance (such as `new Array()`) instead of `new T()`. The constructor of T is not executed, and the properties of T are not initialized. The deserialization result depends on the value type of T's properties after serialization: when the value is a primitive type or an object, it is implicitly converted to undefined; when the value is an array, an Error log is printed with error code 140107. The details are as follows:

| Property Type of T | Serialized Value | Deserialization Result |
|---|---|---|
| number, string, boolean | Primitive type | Implicitly converted to undefined, no error |
| Date | String | Implicitly converted to undefined, no error |
| Array, Set, Map | Array | An Error log is printed, error code 140107 |
| Custom class | Objects | Implicitly converted to undefined, no error |

In the following example, the element type ItemModel contains primitive type properties and container type properties. Using `@Type(Array<ItemModel>)` triggers the preceding issue when the application restarts:

```TypeScript
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class ItemModel {
  @Trace num: number = 1;
  @Trace arr: Array<number> = [1, 2, 3];
  @Trace set: Set<number> = new Set([1, 2, 3]);
}

@ObservedV2
class Data {
  @Type(Array<ItemModel>)
  // Incorrect usage: at runtime it degrades to @Type(Array), passing the container type instead of the element type.
  // During deserialization, new Array() is created instead of new ItemModel(), so the ItemModel constructor is not executed and the num, arr, and set properties are not initialized.
  // After serialization, num is a primitive type and is implicitly converted to undefined during deserialization; arr and set are arrays after serialization, and an Error log is printed during deserialization with error code 140107.
  // The same applies to Set<T> and Map<string, T> scenarios where @Type(Set<T>) or @Type(Map<string, T>) is passed.
  @Trace items: Array<ItemModel> = new Array();
}

@Entry
@ComponentV2
struct TestCase {
  @Local data: Data = PersistenceV2.connect(Data, () => new Data())!;

  build() {
    Column() {
      Button('push and save')
        .onClick(() => {
          this.data.items.push(new ItemModel());
          // Manually persist data to disk.
          PersistenceV2.save(Data);
        })
    }
  }
}
```

In the preceding example, after the button is clicked for the first time to store an ItemModel instance into the array and save it to the disk, the process is terminated. When the application is restarted for the second time, deserialization fails and the following Error log is printed:

```text
FIX THIS APPLICATION ERROR: For PersistenceV2 'Data' key has error, error code: 140107, message: The type of target 'undefined' mismatches the type of source 'object'
```

The correct approach is to change the \@Type parameter to the class corresponding to the element type T. This applies to `Array<T>`, `Set<T>`, and `Map<string, T>`:

```TypeScript
@ObservedV2
class Data {
  @Type(ItemModel) // Correct usage: pass the class corresponding to the element type ItemModel.
  @Trace items: Array<ItemModel> = new Array();
}
```
