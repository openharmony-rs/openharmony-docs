# Shared Module
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @lijiamin2025-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

A shared module, marked with **use shared**, is loaded only once in a process.

A non-shared module is loaded once in the same thread and multiple times in different threads, creating a new module object in each thread. Currently, only shared modules can be used to implement process-wide singletons.


## Constraints

- Similar to **use strict**, **use shared** must be placed at the top level of ArkTS files and should appear after **import** statements but before any other code.

  The shared property cannot be passed on. That is, importing a shared module does not make a non-shared module shared.


- Shared modules are only supported in .ets files.

- **side-effects-import** is not allowed in shared modules.

  A shared module is loaded only once within a single process and can be used across multiple threads.<br>
  When a shared module is loaded, non-shared modules that it imports are not loaded immediately. Instead, these non-shared modules are lazy-imported within the current thread when their exported variables are accessed. Non-shared modules are isolated across threads, and are lazy-loaded when accessed by different threads.<br>
  Because **side-effects-import** does not involve exported variables, it is not loaded and is not supported.
  ```ts
  // test.ets
  console.info("This runs immediately when imported");
  ```

  ```ts
  // sharedModule.ets
  // side-effects-import is not allowed. Compilation error.
  import "./test";
  "use shared"
  ```

- All variables exported by shared modules must be Sendable objects.

  Since shared modules are shared across concurrent instances, all exported objects must be Sendable. For details, see [Sendable Data Types](arkts-sendable.md#sendable-data-types).

- Shared modules do not support the **re-export** syntax.

  ```ts
  // test.ets
  export let num = 1;
  export let str = 'aaa';
  ```

  ```ts
  // share.ets
  // Shared module
  'use shared'
  export * from './test'; // Compilation error.
  export {num, str} from './test'; // Runtime error.
  ```


- Shared modules can import or be imported by both shared and non-shared modules. There are no restrictions on importing or being imported by shared modules.

- Only static loading, **napi_load_module**, or **napi_load_module_with_info** can be used to load shared modules.
  ```ts
  // test.ets
  import { num } from './A'; // Static loading is supported.

  import { worker } from '@kit.ArkTS';
  let wk = new worker.ThreadWorker("./A"); // Other methods of loading shared modules are not supported and will result in runtime errors.
  ```
  ```ts
  // A.ets
  'use shared'
  export let num: number = 10;
  ```

## Usage Example

1. Export a Sendable object from a shared module.

   ```ts
   // Shared module sharedModule.ets
   import { ArkTSUtils } from '@kit.ArkTS';
   
   // Declare the current module as shared. Only Sendable data can be exported.
   "use shared"
   
   // Shared module. SingletonA is globally unique.
   @Sendable
   class SingletonA {
     private count_: number = 0;
     lock_: ArkTSUtils.locks.AsyncLock = new ArkTSUtils.locks.AsyncLock()
   
     public async getCount(): Promise<number> {
       return this.lock_.lockAsync(() => {
         return this.count_;
       })
     }
   
     public async increaseCount() {
       await this.lock_.lockAsync(() => {
         this.count_++;
       })
     }
   }
   
   export let singletonA = new SingletonA();
   ```
   <!-- @[export_sendable_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/SendableObject/SendableObjectRelated/entry/src/main/ets/managers/sharedModule.ets) -->

2. Operate an object exported from the shared module across multiple threads.

   ```ts
   import { taskpool } from '@kit.ArkTS';
   import { singletonA } from './sharedModule';
   
   @Concurrent
   async function increaseCount() {
     await singletonA.increaseCount();
     console.info("SharedModule: count is:" + await singletonA.getCount());
   }
   
   @Concurrent
   async function printCount() {
     console.info("SharedModule: count is:" + await singletonA.getCount());
   }
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Hello World';
   
     build() {
       Row() {
         Column() {
           Button("MainThread print count")
             .onClick(async () => {
               await printCount();
             })
           Button("Taskpool print count")
             .onClick(async () => {
               await taskpool.execute(printCount);
             })
           Button("MainThread increase count")
             .onClick(async () => {
               await increaseCount();
             })
           Button("Taskpool increase count")
             .onClick(async () => {
               await taskpool.execute(increaseCount);
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
   <!-- @[ multi_thread_operate_exported_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/InterThreadCommunicationObjects/SendableObject/SendableObjectRelated/entry/src/main/ets/managers/ArktsSendableModule.ets) -->
