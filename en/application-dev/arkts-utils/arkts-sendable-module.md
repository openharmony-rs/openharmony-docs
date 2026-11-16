# Shared Module
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=5372ac64df42816fd44031056dcb6cce1a906d97 translatedAt=2026-11-04T09:06:11.557Z pushedAt=2026-11-04T09:34:35.523Z nl=1 -->

A shared module is a module that is loaded only once in a process. The 'use shared' directive is used to mark whether a module is a shared module.

A non-shared module is loaded once in the same thread and multiple times in different threads, creating a new module object in each thread. Currently, only shared modules can be used to implement process-wide singletons.


## Constraints

- 'use shared' must be written at the top level of an ArkTS file, that is, after the import statements and before other statements.

  The shared property cannot be passed on. That is, importing a shared module does not make a non-shared module shared.


- Shared modules are only supported in .ets files.

- [side-effects-import](arkts-module-side-effects.md) is not allowed in a shared module.

  A shared module is loaded only once within a single process and can be used across multiple threads.<br>
  When a shared module is loaded, non-shared modules that it imports are not loaded immediately. Instead, these non-shared modules are lazy-imported within the current thread when their exported variables are accessed. Non-shared modules are isolated across threads, and are lazy-loaded when accessed by different threads.<br>
  Because **side-effects-import** does not involve exported variables, it is not loaded and is not supported.

  ```TypeScript
  // test.ets
  console.info("This runs immediately when imported");
  ```

  ```TypeScript
  // sharedModule.ets
  // side-effects-import is not allowed. Compilation error.
  import "./test";
  'use shared'
  ```

- All variables exported by shared modules must be Sendable objects.

  Since shared modules are shared across concurrent instances, all exported objects must be Sendable. For details, see [Sendable Data Types](arkts-sendable.md#sendable-data-types).

- Shared modules do not support the **re-export** syntax.

  ```TypeScript
  // test.ets
  export let num = 1;
  export let str = 'aaa';
  ```

  ```TypeScript
  // share.ets
  // Shared module
  'use shared'
  export * from './test'; // Compilation error.
  export {num, str} from './test'; // May cause unknown runtime exceptions.
  ```


- Shared modules can import or be imported by both shared and non-shared modules. There are no restrictions on importing or being imported by shared modules.

- A shared module can be loaded only through static loading, [napi_load_module](../reference/native-lib/napi.md#napi_load_module), or [napi_load_module_with_info](../reference/native-lib/napi.md#napi_load_module_with_info).

  Static loading is supported:

  ```TypeScript
  // test.ets
  import { num } from './A';
  ```

  Loading a shared module as a worker entry is not supported and will cause a runtime error:

  ```TypeScript
  // test.ets
  import { worker } from '@kit.ArkTS';
  let wk = new worker.ThreadWorker('./A');
  ```

  ```TypeScript
  // A.ets
  'use shared'
  export let num: number = 10;
  ```

## Usage Example

1. Export a Sendable object from a shared module.
   <!-- @[export_sendable_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableObjectRelated/entry/src/main/ets/managers/sharedModule.ets) --> 
   
   ``` TypeScript
   // Shared module
   import { ArkTSUtils } from '@kit.ArkTS';
   
   // Declare the current module as a shared module, which can only export Sendable data.
   'use shared'
   
   // Shared module, singletonA is globally unique.
   @Sendable
   class SingletonA {
     private count_: number = 0;
     public lock_: ArkTSUtils.locks.AsyncLock = new ArkTSUtils.locks.AsyncLock();
   
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

2. Operate an object exported from the shared module across multiple threads.
   <!-- @[multi_thread_operate_exported_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableObjectRelated/entry/src/main/ets/managers/ArktsSendableModule.ets) --> 
   
   ``` TypeScript
   import { ArkTSUtils, taskpool } from '@kit.ArkTS';
   import { singletonA } from './sharedModule';
   
   // ...
   
   @Concurrent
   async function increaseCount() {
     await singletonA.increaseCount();
     console.info(`SharedModule: count is: ${await singletonA.getCount()}`);
   }
   
   @Concurrent
   async function printCount() {
     console.info(`SharedModule: count is: ${await singletonA.getCount()}`);
   }
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Hello World';
     @State mainThreadPrint: string = 'MainThread print count';
     @State taskpoolPrint: string = 'Taskpool print count';
     @State mainThreadIncrease: string = 'MainThread increase count';
     @State taskpoolIncrease: string = 'Taskpool increase count';
   
     build() {
       Row() {
         Column() {
           Button(this.mainThreadPrint)
             .id('MainThread print count')
             .onClick(async () => {
               await printCount();
               this.mainThreadPrint = 'success';
             })
           Button(this.taskpoolPrint)
             .id('Taskpool print count')
             .onClick(async () => {
               await taskpool.execute(printCount);
               this.taskpoolPrint = 'success';
             })
           Button(this.mainThreadIncrease)
             .id('MainThread increase count')
             .onClick(async () => {
               await increaseCount();
               this.mainThreadIncrease = 'success';
             })
           Button(this.taskpoolIncrease)
             .id('Taskpool increase count')
             .onClick(async () => {
               await taskpool.execute(increaseCount);
               this.taskpoolIncrease = 'success';
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
