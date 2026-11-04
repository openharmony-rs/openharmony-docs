# Freezing Sendable Objects
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e8dba876a1b7d39f7c767932ca03dc0b32b0ffb0 translatedAt=2026-11-04T09:29:24.424Z pushedAt=2026-11-04T09:37:10.254Z nl=1 -->

Sendable objects can be frozen, making them read-only and preventing any modifications to their properties. Once frozen, these objects can be safely accessed across multiple concurrent instances without the need for locks. This is achieved using the [Object.freeze](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze) method.

> **NOTE**
> 
> The **Object.freeze** API cannot be used in .ets files.

## Usage Example

1. Encapsulate the **Object.freeze** method in a TS file.

   <!-- @[provide_encapsulate_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableObjectRelated/entry/src/main/ets/managers/helper.ts) --> 
   
   ``` TypeScript
   export function freezeObj(obj: any) {
     Object.freeze(obj);
   }
   ```

2. Call the **freeze** method to freeze an object and send it to a child thread.

   <!-- @[freeze_obj_send_child_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableObjectRelated/entry/src/main/ets/managers/SendableFreeze.ets) -->  
   
   ``` TypeScript
   import { freezeObj } from './helper';
   import { worker } from '@kit.ArkTS';
   
   @Sendable
   export class GlobalConfig {
     // Configuration properties and methods
     init() {
       // Initialization logic
       freezeObj(this) // Freeze the object after the initialization is complete.
     }
   }
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Sendable freezeObj Test';
   
     build() {
       RelativeContainer() {
         Text(this.message)
           .id('HelloWorld')
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
           .alignRules({
             center: { anchor: '__container__', align: VerticalAlign.Center },
             middle: { anchor: '__container__', align: HorizontalAlign.Center }
           })
           .onClick(() => {
             let gConfig = new GlobalConfig();
             gConfig.init();
             const workerInstance = new worker.ThreadWorker('entry/ets/workers/Worker.ets', { name: 'Worker1' });
             workerInstance.postMessage(gConfig);
             this.message = 'success';
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```


3. Perform operations on the frozen object directly in the child thread without locking.

   <!-- @[directly_operate_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableObjectRelated/entry/src/main/ets/workers/Worker.ets) --> 
   
   ``` TypeScript
   import { MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
   // import { GlobalConfig } from '../pages/Index';
   import { GlobalConfig } from '../managers/SendableFreeze';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   workerPort.onmessage = (e: MessageEvents) => {
     let gConfig: GlobalConfig = e.data;
     // Use the gConfig object.
   }
   ```
