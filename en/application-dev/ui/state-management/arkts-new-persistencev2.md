# PersistenceV2: Persisting UI State
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zzq212050299-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

To enhance the state management framework's capability of persistently storing UIs, you can use **PersistenceV2** to persist data.

**PersistenceV2** is an optional singleton object within an application. Its purpose is to persist UI-related data so that their values are the same upon application re-start as they were when the application was closed.

**PersistenceV2** provides the state variable persistence capability. You can bind the same key through **connect** or **globalConnect** to implement the persistence capability during state variable change and application cold start.

Before reading this topic, you are advised to read [\@ComponentV2](./arkts-new-componentV2.md), [\@ObservedV2 and \@Trace](./arkts-new-observedV2-and-trace.md), and API reference of [PersistentV2](../../reference/apis-arkui/js-apis-stateManagement.md#persistencev2).

>**NOTE**
>
>**PersistenceV2** is supported since API version 12.
>
>**globalConnect** is supported since API version 18. The behavior of **globalConnect** is the same as that of **connect**. The only difference is that the underlying storage path of **connect** is a module-level path, while that of **globalConnect** is an application-level path. For details, see the section [Using connect and globalConnect in Different Modules](#using-connect-and-globalconnect-in-different-modules).


## Overview

**PersistenceV2** is a singleton to be created when the application UI is started. It provides central storage for application state data that is accessible at the application level Data is accessed through a unique key string. Unlike AppStorageV2, PersistenceV2 also stores the latest data on the device disk (persistent). In this way, the selected result can still be saved even when the application is closed.

For a [\@ObservedV2](./arkts-new-observedV2-and-trace.md) object associated with **PersistenceV2**, the change of the [\@Trace](./arkts-new-observedV2-and-trace.md) attribute of the object triggers automatic persistence of the entire associated object. If necessary, you can call **PersistenceV2** APIs to manually perform persistence. Note that the class attributes that are persisted by PersistenceV2 must have initial values. Otherwise, persistence is not supported.

**PersistenceV2** can synchronize application state attributes with UI components and can be accessed during implementation of application service logic as well.

**PersistenceV2** supports state sharing among multiple UIAbility instances in the [main thread](../../application-models/thread-model-stage.md) of an application.

## How to Use

- connect: creates or obtains the stored data.

>**NOTE**
>
>1. When matching the key with the [\@Observed](./arkts-observed-and-objectlink.md) object, specify the key or customize the **name** attribute.
>
>2. The data storage path is at the module level. That is, the data copy is stored in the persistent file of the corresponding module when the module calls the **connect** function. If multiple modules use the same key, the data of the module that uses the **connect** function first is used, and the data in **PersistenceV2** is also stored in the module that uses the **connect** function first.
>
>3. The storage path, determined when the first ability of the application is started, is the module to which the ability belongs. If an ability calls the **connect** function and can be started by different modules, the number of data copies is the same as the number of startup modes of the ability.

- globalConnect: creates or obtains the stored data.
- remove: deletes the stored data of a specified key. If a key that does not exist in **PersistenceV2** is deleted, a warning is reported.
- keys: Returning All Keys Stored in PersistenceV2 Includes all keys in the module-level and application-level storage paths.
- save: Persisting Stored Data Manually
- **notifyOnError**: Callback for Responding to a Serialization or Deserialization Failure When data is stored to disks, the data needs to be serialized. If a key fails to be serialized, the error is unpredictable. As a result, this API can be called to capture exceptions.

For details about the preceding APIs, see [State Management API Guide](../../reference/apis-arkui/js-apis-stateManagement.md).

## Constraints

1. This singleton must be used together with the UI thread only. Other threads, for example, @Sendable decorator is not supported.

2. Types such as **collections.Set** and **collections.Map** are not supported.

3. Non-built-in types, such as [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md), NativePointer, and [ArrayList](../../reference/apis-arkts/js-apis-arraylist.md), are not supported.

4. A single key supports a maximum of 8 KB data. If the data is too large, the persistence fails.

5. The data to be persisted must be a class object. Container types (such as Array, Set, and Map), built-in constructed objects (such as Date and Number), and basic types (such as string, number, and boolean) are not supported. If you need to persist non-class objects, you are advised to use [Preferences](../../database/preferences-guidelines.md) for data persistence.

6. Objects that used for loop reference are not supported.

7. Automatic persistency is triggered only when [\@Trace](./arkts-new-observedV2-and-trace.md) data is changed. The change of state variables in V1, [\@Observed](./arkts-observed-and-objectlink.md) objects, and common data does not trigger persistency.

8. Do not store a large amount of persistent data. Otherwise, frame freezing may occur.

9. Do not use **connect** and **globalConnect** together. If you have to, their keys must be different; otherwise, a crash occurs.

10. PersistenceV2 must be associated with a UI instance. The persistence operation must be called after the UI instance is initialized (that is, after the [loadContent](../../reference/apis-arkui/arkts-apis-window-WindowStage.md#loadcontent9) callback is triggered).
```ts
// EntryAbility.ets
// The following is a code snippet. You need to complete it in EntryAbility.ets.
import { PersistenceV2 } from '@kit.ArkUI';

// Define a class outside EntryAbility.
@ObservedV2
class Storage {
  @Trace isPersist: boolean = false;
}

// Call PersistenceV2 in the loadContent callback of onWindowStageCreate.
onWindowStageCreate(windowStage: window.WindowStage): void {
  windowStage.loadContent('pages/Index', (err) => {
    if (err.code) {
      return;
    }
    PersistenceV2.connect(Storage, () => new Storage());
  });
}
```

11. If you have strong requirements on data persistence, for example, the persistence time, you are advised to use [Preferences](../../database/preferences-guidelines.md) for data persistence. Note: PersistenceV2 and Preferences cannot be used together because the data stored in Preferences does not have state variable information, and the deserialized data cannot trigger automatic storage of PersistenceV2.

## Use Scenarios

### Storing Data Between Two Pages

Data page
```ts
// Sample.ets
import { Type } from '@kit.ArkUI';

// Data center
@ObservedV2
class SampleChild {
  @Trace p1: number = 0;
  p2: number = 10;
}

@ObservedV2
export class Sample {
  // For complex objects, use the @Type decorator to ensure successful serialization.
  @Type(SampleChild)
  @Trace f: SampleChild = new SampleChild();
}
```

Page 1
```ts
// Page1.ets
import { PersistenceV2 } from '@kit.ArkUI';
import { Sample } from '../Sample';

// Register a callback for serialization failure.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

@Entry
@ComponentV2
struct Page1 {
  // Create a KV pair whose key is Sample in PersistenceV2 (if the key exists, the data in PersistenceV2 is returned) and associate it with prop.
  // Add @Local to decorate the prop attribute that needs to change the connected object. (Changing the connected object is not recommended.)
  @Local prop: Sample = PersistenceV2.connect(Sample, () => new Sample())!;
  pageStack: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.pageStack) {
      Column() {
        Button('Go to page2')
          .onClick(() => {
            this.pageStack.pushPathByName('Page2', null);
          })

        Button('Page1 connect the key Sample')
          .onClick(() => {
            // Create a KV pair whose key is Sample in PersistenceV2 (if the key exists, the data in PersistenceV2 is returned) and associate it with prop.
            // Changing the connected object for the prop attribute is not recommended.
            this.prop = PersistenceV2.connect(Sample, 'Sample', () => new Sample())!;
          })

        Button('Page1 remove the key Sample')
          .onClick(() => {
            // After being deleted from PersistenceV2, prop will no longer be associated with the value whose key is Sample.
            PersistenceV2.remove(Sample);
          })

        Button('Page1 save the key Sample')
          .onClick(() => {
            // If the sample is in the connect state, persist the KV pair of the Sample.
            PersistenceV2.save(Sample);
          })

        Text(`Page1 add 1 to prop.p1: ${this.prop.f.p1}`)
          .fontSize(30)
          .onClick(() => {
            this.prop.f.p1++;
          })

        Text(`Page1 add 1 to prop.p2: ${this.prop.f.p2}`)
          .fontSize(30)
          .onClick(() => {
            // The page is not re-rendered, but the value of p2 is changed.
            this.prop.f.p2++;
          })

        // Obtain all keys in the current PersistenceV2.
        Text(`all keys in PersistenceV2: ${PersistenceV2.keys()}`)
          .fontSize(30)
      }
      }
  }
}
```

Page 2
```ts
// Page2.ets
import { PersistenceV2 } from '@kit.ArkUI';
import { Sample } from '../Sample';

@Builder
export function Page2Builder() {
  Page2()
}

@ComponentV2
struct Page2 {
  // Create a KV pair whose key is Sample in PersistenceV2 (if the key exists, the data in PersistenceV2 is returned) and associate it with prop.
  // Add @Local to decorate the prop attribute that needs to change the connected object. (Changing the connected object is not recommended.)
  @Local prop: Sample = PersistenceV2.connect(Sample, () => new Sample())!;
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Button('Page2 connect the key Sample1')
          .onClick(() => {
            // Create a KV pair whose key is Sample1 in PersistenceV2 (if the key exists, the data in PersistenceV2 is returned) and associate it with prop.
            // Changing the connected object for the prop attribute is not recommended.
            this.prop = PersistenceV2.connect(Sample, 'Sample1', () => new Sample())!;
          })

        Text(`Page2 add 1 to prop.p1: ${this.prop.f.p1}`)
          .fontSize(30)
          .onClick(() => {
            this.prop.f.p1++;
          })

        Text(`Page2 add 1 to prop.p2: ${this.prop.f.p2}`)
          .fontSize(30)
          .onClick(() => {
            // The page is not re-rendered, but the value of p2 is changed, which is performed after re-initialization.
            this.prop.f.p2++;
          })

        // Obtain all keys in the current PersistenceV2.
        Text(`all keys in PersistenceV2: ${PersistenceV2.keys()}`)
          .fontSize(30)
      }
    }
    .onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}
```
When using **Navigation**, create a **route_map.json** file as shown below in the **src/main/resources/base/profile** directory, replacing the value of **pageSourceFile** with the actual path to **Page2**. Then, add **"routerMap": "$profile: route_map"** to the **module.json5** file.
```json
{
  "routerMap": [
    {
      "name": "Page2",
      "pageSourceFile": "src/main/ets/pages/Page2.ets",
      "buildFunction": "Page2Builder",
      "data": {
        "description" : "PersistenceV2 example"
      }
    }
  ]
}
```

### Using globalConnect to Store Data

```ts
import { PersistenceV2, Type, ConnectOptions } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// Register a callback for serialization failure.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

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

@Entry
@ComponentV2
struct Page1 {
  @Local refresh: number = 0;
  // If no key is provided, the type name is used as the key. If the encryption level is not specified, the default EL2 level is used.
  @Local p: Sample = PersistenceV2.globalConnect({type: Sample, defaultCreator:() => new Sample()})!;

  // Use key:global1 for connection and set the encryption level to EL1.
  @Local p1: Sample = PersistenceV2.globalConnect({type: Sample, key:'global1', defaultCreator:() => new Sample(), areaMode: contextConstant.AreaMode.EL1})!;

  // Use key:global2 for connection and use the constructor function. If no encryption parameter is passed in, EL2 is used by default.
  options: ConnectOptions<Sample> = {type: Sample, key: 'global2', defaultCreator:() => new Sample()};
  @Local p2: Sample = PersistenceV2.globalConnect(this.options)!;

  // Use key:global3 for connection and set the encryption parameter ranging from 0 to 4; otherwise, a crash occurs. In this case, EL3 is set.
  @Local p3: Sample = PersistenceV2.globalConnect({type: Sample, key:'global3', defaultCreator:() => new Sample(), areaMode: 3})!;

  build() {
    Column() {
      /**************************** Display data **************************/
      // Data decorated by @Trace can be automatically persisted to disks.
      Text('Key Sample: ' + this.p.father.childId.toString())
        .onClick(()=> {
          this.p.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)
      Text('Key global1: ' + this.p1.father.childId.toString())
        .onClick(()=> {
          this.p1.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)
      Text('Key global2: ' + this.p2.father.childId.toString())
        .onClick(()=> {
          this.p2.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)
      Text('Key global3: ' + this.p3.father.childId.toString())
        .onClick(()=> {
          this.p3.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)
      /**************************** The keys API **************************/
      // keys() is not updated by itself. You need to use the state variable to update it.
      Text('Persist keys: ' + PersistenceV2.keys().toString() + ' refresh: ' + this.refresh)
        .onClick(() => {
          this.refresh += 1;
        })
        .fontSize(25)

      /**************************** The remove API **************************/
      Text('Remove key Sample: ' + 'refresh: ' + this.refresh)
        .onClick(() => {
          // Removing this key will disconnect from PersistenceV2. After that, PersistenceV2 cannot store data even if it is reconnected.
          PersistenceV2.remove(Sample);
          this.refresh += 1;
        })
        .fontSize(25)
      Text('Remove key global1: ' + 'refresh: ' + this.refresh)
        .onClick(() => {
          // Removing this key will disconnect from PersistenceV2. After that, PersistenceV2 cannot store data even if it is reconnected.
          PersistenceV2.remove('global1');
          this.refresh += 1;
        })
        .fontSize(25)
      Text('Remove key global2: ' + 'refresh: ' + this.refresh)
        .onClick(() => {
          // Removing this key will disconnect from PersistenceV2. After that, PersistenceV2 cannot store data even if it is reconnected.
          PersistenceV2.remove('global2');
          this.refresh += 1;
        })
        .fontSize(25)
      Text('Remove key global3: ' + 'refresh: ' + this.refresh)
        .onClick(() => {
          // Removing this key will disconnect from PersistenceV2. After that, PersistenceV2 cannot store data even if it is reconnected.
          PersistenceV2.remove('global3');
          this.refresh += 1;
        })
        .fontSize(25)
      /**************************** reConnect **************************/
      // Fail to connect to the previous state variable after reconnection. Therefore, data cannot be saved.
      Text('ReConnect key global2: ' + 'refresh: ' + this.refresh)
        .onClick(() => {
          // Removing this key will disconnect from PersistenceV2. After that, PersistenceV2 cannot store data even if it is reconnected.
          PersistenceV2.globalConnect(this.options);
          this.refresh += 1;
        })
        .fontSize(25)

      /**************************** The save API **************************/
      Text('not save key Sample: ' + this.p.father.groupId.toString() + ' refresh: ' + this.refresh)
        .onClick(() => {
          // Objects that are not saved by @Trace cannot be automatically stored.
          this.p.father.groupId += 1;
          this.refresh += 1;
        })
        .fontSize(25)
      Text('save key Sample: ' + this.p.father.groupId.toString() + ' refresh: ' + this.refresh)
        .onClick(() => {
          // Objects that are not saved by @Trace cannot be automatically stored. You need to call the key for storage.
          this.p.father.groupId += 1;
          PersistenceV2.save(Sample);
          this.refresh += 1;
        })
        .fontSize(25)
    }
    .width('100%')
  }
}
```

### Using connect and globalConnect in Different Modules

Pay attention to the following points when using connect to store data:

1. connect uses the module-level storage path. The path of the module that is started first is used as the storage path. When data is written back from the memory to the disk, the data is written back to the path of the first module that is connected. If the application is started from another module, the path of the new module is used as the storage path.

2. When different modules use the same key, the key-value pair saved in the module that is started first is written back to the corresponding module.

Pay attention to the storage path of globalConnect:

Although globalConnect is an application-level path, you can set different encryption partitions. Different encryption partitions indicate different storage paths. The connect does not support the setting of encryption partitions. However, when the encryption level of a module is switched, the storage path of the module is switched to the corresponding encryption partition path.

Create a module based on the project and redirect to the new module based on the sample code. The sample code is as follows:

```ts
module 1
import { PersistenceV2, Type } from '@kit.ArkUI';
import { contextConstant, common, Want } from '@kit.AbilityKit';

// Register a callback for serialization failure.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

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

@Entry
@ComponentV2
struct Page1 {
  @Local refresh: number = 0;
  // Use key:global1 for connection and set the encryption level to EL1.
  @Local p1: Sample = PersistenceV2.globalConnect({type: Sample, key:'globalConnect1', defaultCreator:() => new Sample()})!;

  // Use key:global2 for connection and use the constructor function. If no encryption parameter is passed in, EL2 is used by default.
  @Local p2: Sample = PersistenceV2.connect(Sample, 'connect2', () => new Sample())!;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      /**************************** Display data **************************/
      Text('Key globalConnect1: ' + this.p1.father.childId.toString())
        .onClick(()=> {
          this.p1.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)
      Text('Key connect2: ' + this.p2.father.childId.toString())
        .onClick(()=> {
          this.p2.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)

      /**************************** Redirection **************************/
      Button('Redirection newModule').onClick (() => { // is used between different modules. globalConnect is recommended.
        let want: Want = {
          deviceId: '', // If deviceId is empty, the current device is used.
          bundleName: 'com.example.myPersistenceV2', // View in app.json5.
          moduleName: 'newModule', // View in module.json5 of the module to be redirected to. This parameter is optional.
          abilityName: 'NewModuleAbility', // Ability to be redirected to. View in the ability.ets file of the redirected module.
          uri:'src/main/ets/pages/Index'
        }
        // context is the UIAbilityContext of the initiator UIAbility.
        this.context.startAbility(want).then(() => {
          console.info('start ability success');
        }).catch((err: Error) => {
          console.error(`start ability failed. code is ${err.name}, message is ${err.message}`);
        })
      })
    }
    .width('100%')
    .borderWidth(3)
    .borderColor(Color.Blue)
    .margin({top: 5, bottom: 5})
  }
}
```

```ts
// Module 2
import { PersistenceV2, Type } from '@kit.ArkUI';
import { contextConstant } from '@kit.AbilityKit';

// Register a callback for serialization failure.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

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

@Entry
@ComponentV2
struct Page1 {
  @Local a: number = 0;
  // Use key:global1 for connection and set the encryption level to EL1.
  @Local p1: Sample = PersistenceV2.globalConnect({type: Sample, key:'globalConnect1', defaultCreator:() => new Sample()})!;

  // Use key:global2 for connection and use the constructor function. If no encryption parameter is passed in, EL2 is used by default.
  @Local p2: Sample = PersistenceV2.connect(Sample, 'connect2', () => new Sample())!;

  build() {
    Column() {
      /**************************** Display data **************************/
      Text('Key globalConnect1: ' + this.p1.father.childId.toString())
        .onClick(()=> {
          this.p1.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)
      Text('Key connect2: ' + this.p2.father.childId.toString())
        .onClick(()=> {
          this.p2.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)
    }
    .width('100%')
  }
}
```

When you use different startup modes for newModule, the following symptoms may occur:

*   Start the **newModule** and change the variables bound to **globalConnect1** and **connect2**. For example, change the value of **childId** to **5**.
* Exit the application, clear the background, start the module entry, and start **newModule** by pressing the redirection key. The value of **globalConnect1** is **5**, and the value of **connect2** remains **1**.
* **globalConnect** is an application-level storage path. For a key, the entire application has only one storage path for the corresponding encryption level. **connect** is a module-level storage path. Each encryption level has a different storage path according to the startup mode of the module.

## Suggestions

You are advised to use the new API **globalConnect** to create and obtain data. The storage specifications and memory specifications of **globalConnect** are the same for an application, and the encryption level can be set without switching the encryption mode of ability. If your application does not involve multiple modules, using **connect** will not affect your application.

### Migrating from connect to globalConnect

```ts
// Use connect to store data.
import { PersistenceV2, Type } from '@kit.ArkUI';

// Register a callback for serialization failure.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

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

@Entry
@ComponentV2
struct Page1 {
  @Local refresh: number = 0;
  // Use key:connect2 to store data.
  @Local p: Sample = PersistenceV2.connect(Sample, 'connect2', () => new Sample())!;

  build() {
    Column({space: 5}) {
      /**************************** Display data **************************/
      Text('Key connect2: ' + this.p.father.childId.toString())
        .onClick(() => {
          this.p.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)

      /**************************** The save API **************************/
      // Non-state variables can be refreshed only by using the state variable refresh.
      Text('save key Sample: ' + this.p.father.groupId.toString() + ' refresh:' + this.refresh)
        .onClick(() => {
          // Objects that are not saved by @Trace cannot be automatically stored. You need to call the key for storage.
          this.p.father.groupId += 1;
          PersistenceV2.save('connect2');
          this.refresh += 1;
        })
        .fontSize(25)
    }
    .width('100%')
  }
}
```

```ts
// Migrate to globalConnect.
import { PersistenceV2, Type } from '@kit.ArkUI';

// Register a callback for serialization failure.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}`);
});

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

// Auxiliary data used to determine whether data migration is complete.
@ObservedV2
class StorageState {
  @Trace isCompleteMoving: boolean = false;
}

function move() {
  let movingState = PersistenceV2.globalConnect({type: StorageState, defaultCreator: () => new StorageState()})!;
  if (!movingState.isCompleteMoving) {
    let p: Sample = PersistenceV2.connect(Sample, 'connect2', () => new Sample())!;
    PersistenceV2.remove('connect2');
    let p1 = PersistenceV2.globalConnect({type: Sample, key: 'connect2', defaultCreator: () = > p})!; // You can use the default constructor.
    // For assigned value decorated by @Trace, it is automatically saved.
    p1.father = p.father;
    // Set the migration flag to true.
    movingState.isCompleteMoving = true;
  }
}

move();

@Entry
@ComponentV2
struct Page1 {
  @Local refresh: number = 0;
  // Store data with key: connect2.
  @Local p: Sample = PersistenceV2.globalConnect({type: Sample, key:'connect2', defaultCreator:() => new Sample()})!;

  build() {
    Column({space: 5}) {
      /**************************** Display data **************************/
      Text('Key connect2: ' + this.p.father.childId.toString())
        .onClick(() => {
          this.p.father.childId += 1;
        })
        .fontSize(25)
        .fontColor(Color.Red)

      /**************************** The save API **************************/
      // Non-state variables can be refreshed only by using the state variable refresh.
      Text('save key connect2: ' + this.p.father.groupId.toString() + ' refresh:' + this.refresh)
        .onClick(() => {
          // Objects that are not saved by @Trace cannot be automatically stored. You need to call the key for storage.
          this.p.father.groupId += 1;
          PersistenceV2.save('connect2');
          this.refresh += 1;
        })
        .fontSize(25)
    }
    .width('100%')
  }
}
```

To migrate data from **connect** to **globalConnect**, you should assign the value bound to the key to **globalConnect** for storage. When the custom component uses **globalConnect** for connection, the data bound to **globalConnect** is the data saved using **connect**. You can customize the **move** function and move the data to a proper position.
