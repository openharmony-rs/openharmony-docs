# Sendable Object Refactoring Practice

<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=90bafeeb8be1710ba45283072539a7fe269de2b1 translatedAt=2026-08-31T12:38:12.202Z pushedAt=2026-08-31T14:47:48.777Z -->

## Introduction

This document describes the typical usage of @hadss/turbo-trans-json (hereinafter referred to as **TurboTransJSON**) and @hadss/turbo-trans-protobuf (hereinafter referred to as **TurboTransProtobuf**) in the [TurboTrans](https://gitcode.com/openharmony-sig/turbo_trans) third-party library for operating Sendable objects in ArkTS:

- Use **TurboTransJSON** to deserialize a JSON string into an object and convert it to a Sendable object for passing between concurrent instances. This is suitable for converting a plain object or JSON string into a Sendable object. For details, see [Use TurboTransJSON to Serialize/Deserialize and Generate Sendable Objects](#use-turbotransjson-to-serializedeserialize-and-generate-sendable-objects).

- Use **TurboTransProtobuf** to generate @Sendable message classes through .proto and perform encoding/decoding. For details, see [Use TurboTransProtobuf to Generate Sendable Objects and Encode/Decode](#use-turbotransprotobuf-to-generate-sendable-objects-and-encodedecode).

- After using TurboTransJSON or TurboTransProtobuf to convert and generate Sendable objects, if you also need to bind the UI for component refresh, see [Use makeObserved to Convert a Sendable Object to an Observable Object](#use-makeobserved-to-convert-a-sendable-object-to-an-observable-object).

## Using the TurboTrans Third-Party Library to Operate Sendable Objects

### Use TurboTransJSON to Serialize/Deserialize and Generate Sendable Objects

1. Environment configuration

   Import the TurboTrans third-party library.

   <!-- @[transferableObject_jsonPlugin](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/hvigor/hvigor-config.json5) -->

   ``` JSON5
     "dependencies": {
   // ...
       "@hadss/turbo-trans-json-plugin": "latest",
     },
   ```

   Install the third-party library in the project directory or module using ohpm.

   ```shell
   ohpm install @hadss/turbo-trans-core @hadss/turbo-trans-json
   ```

   For the plugin to take effect, add the relevant plugin configuration to the hvigorfile.ts file in the project root directory.

   <!-- @[transferableObject_configPlugin](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/hvigorfile.ts) --> 

   ``` TypeScript
   import { turboTransJsonPlugin } from '@hadss/turbo-trans-json-plugin';
   import { hvigor } from '@ohos/hvigor';
   import { appTasks } from '@ohos/hvigor-ohos-plugin';
   
   export default {
     system: appTasks, /* Built-in plugin of Hvigor. It cannot be modified. */
     plugins: [
       turboTransJsonPlugin(hvigor, {
         ignoreModuleNames: ['TurboTransCore', 'TurboTransJSON', 'PerformanceBaseline', 'TurboTransProtobuf'], // Ignored modules
         scanDir: ['src/main/ets'], // Scan directory
         deserializationMode: 'performance', // Deserialization mode
       }),
     ]       /* Custom plugin to extend the functionality of Hvigor. */
   }
   ```

2. Define a serializable model.

   Mark the class to be serialized with the @Serializable decorator, add the generateSendable property, and use `@SerialName()` to customize the property configuration, where:

   - `@Serializable({ generateSendable: true })`: indicates that the Sendable type and conversion method corresponding to this model need to be generated.

   - `@SerialName({ name: 'xxx' })`: binds class properties to JSON field names.

     <!-- @[transferableObject_Layout](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/turbotrans_JSON/layout.ets) --> 

     ``` TypeScript
     // Path of this file in the project: entry/src/main/ets/turbotrans_JSON/layout.ets
     import { Serializable, SerialName } from '@hadss/turbo-trans-core';
     import { collections } from '@kit.ArkTS';
     // ...
     
     @Serializable({ generateSendable: true})
     export class Layout {
       @SerialName({ name: 'type'})
       public type: string = '';
       @SerialName({ name: 'arr'})
       public arr: number[] = [];
     }
     
     @Sendable
     export class LayoutS {
       public type: string = '';
       public arr: collections.Array<number> = new collections.Array();
     }
     ```

3. Deserialize from a JSON string to a plain object (TJSON.fromString).

   Use `TJSON.fromString<Model>(jsonStr, Model)` to deserialize from a JSON string to a plain object. You can use `ArkTSUtils.isSendable(obj)` for verification. The project example demonstrates two input sources, and after deserialization it continues to convert the plain object to a Sendable object, forming the first half of the "JSON string -> plain object -> Sendable object" chain.

   - The testJSON1 method serializes a plain object to a JSON string through `JSON.stringify()`, then deserializes the JSON string back to a plain object, and finally converts it to a Sendable object.

   - The testJSON2 method deserializes a hand-written JSON string to a plain object, and then converts it to a Sendable object.

     <!-- @[transferableObject_testJSON](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/turbotrans_JSON/test1.ets) --> 

     ``` TypeScript
     // Path of this file in the project: entry/src/main/ets/turbotrans_JSON/test1.ets
     import { TJSON } from '@hadss/turbo-trans-json';
     import { Layout, LayoutS } from 'entry/ets/turbotrans_JSON/layout';
     import type { ITSerializable } from '@hadss/turbo-trans-json';
     import { ArkTSUtils } from '@kit.ArkTS';
     
     export function testJSON1(): LayoutS {
       let obj = new Layout();
       obj.type = 'Test';
       obj.arr = [3, 4];
       let str = JSON.stringify(obj);
       let layoutNormal = TJSON.fromString<Layout>(str, Layout);
       console.info('testJSON1 layout arr: ' + layoutNormal.arr);
       let layoutSendable = (layoutNormal as object as ITSerializable).toSendable();
       if (ArkTSUtils.isSendable(layoutSendable)) {
         console.info('expect layout from JSON string is Sendable');
       } else {
         console.error('test occur error');
       }
       let layoutS = layoutSendable as LayoutS;
       return layoutS;
     }
     
     export function testJSON2(): LayoutS {
       let layoutStr = '{"type":"Text","arr":[3,4]}';
       let layoutNormal = TJSON.fromString<Layout>(layoutStr, Layout);
       console.info('testJSON2 layout arr: ' + layoutNormal.arr);
       let layoutSendable = (layoutNormal as object as ITSerializable).toSendable();
       if (ArkTSUtils.isSendable(layoutSendable)) {
         console.info('expect layout from simple string is Sendable');
       } else {
         console.error('test occur error');
       }
       let layoutS = layoutSendable as LayoutS;
       return layoutS;
     }
     ```

4. Convert a plain object to a Sendable object (toSendable).

   When `generateSendable: true` takes effect, `toSendable()` is generated in the build output to convert a plain object to a Sendable object. The key point is that it performs necessary container conversion on the plain object, for example converting `number[]` to `collections.Array<number>`. The following code is automatically generated by the compile-time tool, and the file is located in the entry/src/generated/ets/turbotrans_JSON directory.

   ``` TypeScript
   import { collections } from '@kit.ArkTS';

   toSendable(): SendableLayout {
     const sendable = new SendableLayout();
   
     // Assign a non-constructor property.
     sendable.type = this.type;
     sendable.arr = new collections.Array(...this.arr);
   
     return sendable;
   }
   ```

  Meanwhile, the generated Sendable type usually provides `toOrigin()`, which is used to restore a Sendable object to a plain object when you need to continue processing it as a plain object, reuse existing logic, or serialize it again. The following code is automatically generated by the compile-time tool and is located in the entry/src/generated/ets/turbotrans_JSON directory.

   ``` TypeScript
   @Sendable
   export class SendableLayout implements lang.ISendable {
     public type: string = '';
     public arr: collections.Array<number> = new collections.Array();

     toOrigin(): Layout {
       const origin = new Layout();
       origin.type = this.type;
       origin.arr = new Array(...this.arr);
       return origin;
     }
   }
   ```

  The JSON path forms a complete loop:

  JSON string -> `TJSON.fromString()` -> plain object -> `toSendable()` -> Sendable object -> `toOrigin()` -> plain object.

### Use TurboTransProtobuf to Generate Sendable Objects and Encode/Decode

1. Environment configuration

   Import the TurboTrans third-party library.

   ```ts
   "dependencies": {
       // ...
       "@hadss/turbo-trans-protobuf-plugin": "latest"
   },
   ```

   Install the third-party library using ohpm in the project directory or module.

   ```shell
   ohpm install @hadss/turbo-trans-protobuf
   ```

   For the plugin to take effect, add the relevant plugin configuration to the hvigorfile.ts file in the project root directory.

   ```ts
   import { turboTransProtobufPlugin } from '@hadss/turbo-trans-protobuf-plugin';
   import { hvigor } from '@ohos/hvigor';
   import { appTasks } from '@ohos/hvigor-ohos-plugin';
   
   export default {
     system: appTasks, /* Built-in plugin of Hvigor. It cannot be modified. */
     plugins: [
       turboTransProtobufPlugin({
         saveDir: 'src/main/ets/protobuf', // Directory for saving generated code.
         ignoreModuleNames: ['TurboTransCore', 'PerformanceBaseline', 'TurboTransProtobufCommon'], // Modules to ignore.
         sendable: true, // Whether to enable sendable.
         debug: false, // Whether to enable debug.
         scanDir: ['protobuf'], // Directories to scan.
       }),
     ]       /* Custom plugin to extend the functionality of Hvigor. */
   }
   ```

2. Write the proto file.

   The .proto file must be placed in the scanDir directory configured for the turboTransProtobufPlugin in the hvigorfile.ts file at the project root directory to take effect. For example, in the sample project, the .proto file is located at `entry/protobuf/test_pb.proto`.

   ```proto
   syntax = "proto3";
   
   message test_pb {
       int32 value_int32 = 1;
       int64 value_int64 = 2;
       uint32 value_uint32 = 3;
       uint64 value_uint64 = 4;
       sint32 value_sint32 = 5;
       sint64 value_sint64 = 6;
       fixed32 value_fixed32 = 7;
       fixed64 value_fixed64 = 8;
       sfixed32 value_sfixed32 = 9;
       sfixed64 value_sfixed64 = 10;
       float value_float = 11;
       double value_double = 12;
       bool value_bool = 13;
       string value_string = 14;
       bytes value_bytes = 15;
   }
   ```

3. Build to generate the Sendable message class.

   After building, the Sendable message class is generated in the saveDir result directory configured for the turboTransProtobufPlugin in the hvigorfile.ts file at the project root directory. For example, in the sample project, entry/src/main/ets/protobuf/test_pb.ets is generated.

   - `test_pb.create()`: Creates an instance.

   - `test_pb.encode(message)`: Encodes the instance into an ArrayBuffer.

   - `test_pb.decode(buffer)`: Decodes the binary data back to test_pb.

4. Create a Sendable message object and perform encoding and decoding.

   Use the encode/decode methods provided by the generated class to complete binary serialization/deserialization, and the message object obtained after decoding can still be passed onward as a Sendable object. After encoding and decoding, test_pb still retains the Sendable feature, so it can also continue to enter the UI binding process as the return value of a concurrent task, just like the Sendable object generated through the JSON path. In the following example, the testProtobuf method first creates a test_pb instance, then encodes it into binary data, and finally decodes it back to test_pb and verifies that it is still a Sendable object.

   ```ts
   import { test_pb } from '../protobuf/test_pb'
   import { ArkTSUtils, collections } from '@kit.ArkTS';
   
   function testCreate() {
     const obj = test_pb.create();
     obj.value_int32 = 1;
     obj.value_int64 = 2;
     obj.value_uint32 = 3;
     obj.value_uint64 = 4;
     obj.value_sint32 = 5;
     obj.value_sint64 = 6;
     obj.value_fixed32 = 7;
     obj.value_fixed64 = 8;
     obj.value_sfixed32 = 9;
     obj.value_sfixed64 = 10;
     obj.value_float = 11;
     obj.value_double = 12;
     obj.value_bool = true;
     obj.value_string = `TestProtobuf_Success`;
     obj.value_bytes?.fill(13);
   
     if (ArkTSUtils.isSendable(obj)) {
       console.info("create a sendable object");
     }
   
     return obj;
   }
   
   function testencode(obj: test_pb) {
     return test_pb.encode(obj);
   }
   
   function testdecode(data: ArrayBuffer | collections.ArrayBuffer) {
     let obj = test_pb.decode(data);
     console.info(`expect value_int32 ${obj?.value_int32} = 1`);
     console.info(`expect value_double ${obj?.value_double} = 12`);
     if (ArkTSUtils.isSendable(obj)) {
       console.info("decode a sendable object");
     }
   }
   
   export function testProtobuf(): test_pb {
     let obj = testCreate();
     let buf = testencode(obj);
     if (buf) {
       testdecode(buf);
     }
     return obj;
   }
   ```

## Use makeObserved to Convert a Sendable Object to an Observable Object

Use the [UIUtils.makeObserved()](../reference/apis-arkui/js-apis-stateManagement.md#makeobserved) method to convert a Sendable object to an observable object.

- Define a concurrent task.

- Use `taskpool.execute()` to obtain the Sendable object returned by the concurrent task, and then convert it to an observable object through `UIUtils.makeObserved()`.

- When a property of the observable object changes, the bound UI component automatically refreshes its display.

### Define Concurrent Tasks

Define the observeJSON1 and observeJSON2 concurrent tasks

<!-- @[transferableObject_observeJSON](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/pages/concurrentFunc.ets) -->

``` TypeScript
import { LayoutS } from '../turbotrans_JSON/layout';
import { testJSON1, testJSON2 } from '../turbotrans_JSON/test1';

@Concurrent
export function observeJSON1(): LayoutS {
  return testJSON1();
}

@Concurrent
export function observeJSON2(): LayoutS {
  return testJSON2();
}
```

Define the observeProtobuf concurrent task

``` TypeScript
import { testProtobuf } from '../turbotrans_protobuf/test1'
import { test_pb } from '../protobuf/test_pb'

@Concurrent
export function observeProtobuf(): test_pb {
  return testProtobuf();
}
```

### Execute an Asynchronous Task Through taskpool and Convert a Sendable Object to an Observable Object

In `runTests()`, a concurrent task is executed through `taskpool.execute()`. After the returned Sendable object is obtained, it is wrapped as an observable object with `UIUtils.makeObserved()` and written back to the UI state. In this way, the data link becomes "concurrent task return -> convert to observable object -> component auto refresh".

The object engineering example of executing the observeJSON1 concurrent task and returning a Sendable object is as follows:

<!-- @[transferableObject_makeObserved](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
runTests() {
  taskpool.execute(observeJSON1).then((res) => {
    this.layout = UIUtils.makeObserved(res as LayoutS);
  })
}
```

The object engineering example of executing the observeProtobuf concurrent task and returning a Sendable object is as follows:

``` TypeScript
runTestsPb() {
  taskpool.execute(observeProtobuf).then((res) => {
    this.pb = UIUtils.makeObserved(res as test_pb);
  })
}
```

### Create a UI component to observe Sendable object property changes in real time

In Index.ets, the task return value is saved through the `@Local` state, and then the Text component binds `pb.value_string` and `layout.type`. Here, pb stores the Sendable object (of the test_pb type) returned by observeProtobuf, and layout stores the Sendable object (of the LayoutS type) returned by observeJSON1.

The Sendable object engineering example returned by observeJSON1 is as follows:

<!-- @[transferableObject_Text](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/pages/Index.ets) --> 

``` TypeScript
import { LayoutS } from '../turbotrans_JSON/layout';
import { taskpool } from '@kit.ArkTS';
import { observeJSON1 } from './concurrentFunc';
import { UIUtils } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  // Replace with pb: test_pb = test_pb.create(); to use the scenario where observeProtobuf returns a Sendable object.
  // @Local test_pb = test_pb.create();
  @Local layout: LayoutS = new LayoutS();

  build() {
    Column() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .margin({ top: 20 })

      Button('Run TaskPool test')
        .width('80%')
        .height(50)
        .margin({ top: 20, bottom: 20 })
        .onClick(() => {
          this.runTests();
        })
        .id('button')

      Scroll() {
        Column() {

          Text(`TestJSON: ${this.layout.type}`)
            .fontSize(24)
            .textAlign(TextAlign.Start)
            .backgroundColor(Color.White)
            .padding(10)
            .borderRadius(8)
            .margin({ bottom: 10 })
            .width('100%')
        }
        .width('100%')
        .padding(10)
      }
      .height('60%')
      .width('100%')
    }
    .height('100%')
    .width('100%')
    .padding(20)
    .backgroundColor('#F5F5F5')
  }

// ...
}
```