# I/O Intensive Task Development (TaskPool)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=404e8f67bcb9eb1f1bc6bc4c58c9e48ab651c853 translatedAt=2026-11-04T09:20:47.991Z pushedAt=2026-11-04T09:36:31.291Z nl=1 -->


I/O intensive tasks are those requiring frequent I/O operations such as disk read/write and network communication. While asynchronous concurrency can address the thread blocking issue for single I/O tasks, it falls short in the case of I/O intensive tasks. This is where multithreaded concurrency comes into play.


The performance focus of I/O intensive tasks is not the CPU processing capability, but the speed and efficiency of I/O operations, since these tasks usually require frequent operations such as disk read/write and network communication. The following uses frequent read/write operations on a system file to simulate concurrency processing of I/O intensive tasks.


1. Define a concurrent function that frequently calls I/O operations.
   <!-- @[define_concurrent_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/write.ets) -->
   
   ``` TypeScript
   import { fileIo } from '@kit.CoreFileKit';
   
   // Define a concurrent function that frequently calls I/O operations.
   // Write data to the file.
   export async function write(data: string, filePath: string): Promise<void> {
     let file: fileIo.File = await fileIo.open(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
     await fileIo.write(file.fd, data);
     fileIo.close(file);
   }
   ```

   <!-- @[define_concurrent_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/IoIntensiveTaskDevelopment.ets) -->
   
   ``` TypeScript
   import { write } from './write';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { taskpool } from '@kit.ArkTS';
   import { common } from '@kit.AbilityKit';
   
   @Concurrent
   async function concurrentTest(context: common.UIAbilityContext): Promise<boolean> {
     let filePath1: string = context.filesDir + '/path1.txt'; // Application file path
     let filePath2: string = context.filesDir + '/path2.txt';
     // Write data to the file cyclically.
     let fileList: string[] = [];
     fileList.push(filePath1);
     fileList.push(filePath2);
     const writePromises: Promise<boolean | void>[] = [];
     for (let i: number = 0; i < fileList.length; i++) {
       const writePromise = write('Hello World!', fileList[i]).then(() => {
         console.info(`Succeeded in writing the file. FileList: ${fileList[i]}`);
       }).catch((err: BusinessError) => {
         console.error(`Failed to write the file. Code is ${err.code}, message is ${err.message}`);
         return false;
       });
       writePromises.push(writePromise);
     }
     try {
       const results: (boolean | void)[] = await Promise.all(writePromises);
       // Check whether any write operation failed.
       if (results.includes(false)) {
         return false;
       }
       return true;
     } catch (error) {
       return false;
     }
   }
   ```

2. Use **TaskPool** to execute the concurrent function with frequent intensive I/O operations. Specifically, call [execute()](../reference/apis-arkts/js-apis-taskpool.md#taskpoolexecute) to execute the tasks and process the scheduling result in the callback. For details about how to obtain **filePath1** and **filePath2** in the example, see [Obtaining Application File Paths](../application-models/application-context-stage.md#obtaining-application-file-paths). When using context in TaskPool, it must be prepared outside the concurrent function and passed as an argument.

   <!-- @[taskpool_execute_concurrent_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/IoIntensiveTaskDevelopment.ets) --> 
   
   ``` TypeScript
   @Entry
   @Component
   struct Index {
     @State message: string = 'Hello World';
     uiContext = this.getUIContext();
   
     build() {
       Row() {
         Column() {
           Text(this.message)
             .fontSize(50)
             .fontWeight(FontWeight.Bold)
             .onClick(() => {
               let context = this.uiContext?.getHostContext() as common.UIAbilityContext;
               // Use TaskPool to execute the concurrent function with frequent I/O operations.
               // When the array of files to process is large, I/O-intensive task distribution also preempts the UI main thread, so multithreading is required.
               taskpool.execute(concurrentTest, context).then(() => {
                 this.message = 'success';
                 // Process the scheduling result.
                 console.info('taskpool: execute success')
               }).catch((e: BusinessError) => {
                 this.message = 'failed';
                 console.error('concurrentTest is failed.');
               });
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
