# Long-Running Task Development Guide (TaskPool)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=ef97b4f4e99b757e3a4cb9958ae751b6d982f951 translatedAt=2026-11-04T09:23:46.734Z pushedAt=2026-11-04T12:47:07.706Z nl=1 -->

This section provides a development guide for continuous tasks using TaskPool, with the example of periodically collecting sensor data.

## Using TaskPool to Listen for Sensor Data

1. Import the required module.

   <!-- @[taskpool_listen_sensor_data_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/LongTimeTaskGuide.ets) -->
   
   ``` TypeScript
   import { sensor } from '@kit.SensorServiceKit';
   import { taskpool } from '@kit.ArkTS';
   import { BusinessError, emitter } from '@kit.BasicServicesKit';
   ```

2. Define a continuous task to listen for sensor data internally and register a destruction notification via emitter.

   <!-- @[taskpool_listen_sensor_data_concurrent](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/LongTimeTaskGuide.ets) -->
   
   ``` TypeScript
   @Concurrent
   async function sensorListener(): Promise<void> {
     sensor.on(sensor.SensorId.ACCELEROMETER, (data) => {
       emitter.emit({ eventId: 0 }, { data: data });
     }, { interval: 1000000000 });
   
     emitter.on({ eventId: 1 }, () => {
       sensor.off(sensor.SensorId.ACCELEROMETER)
       emitter.off(1)
     })
   }
   ```

3. Add the ohos.permission.ACCELEROMETER permission to the application. In the "module" field of module.json5, add the "requestPermissions" field as shown in the following code example to configure the related permission.

   ```json
   "requestPermissions": [
     {
       "name": "ohos.permission.ACCELEROMETER"
     }
   ]
   ```
4. Define the registration and destruction behavior in the host thread.
   - Registration: Initiate the continuous task and receive listening data via emitter.
   - Destruction: Send an event to cancel sensor listening and terminate the continuous task.

   <!-- @[taskpool_listen_sensor_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/LongTimeTaskGuide.ets) -->
   
   ``` TypeScript
   import { sensor } from '@kit.SensorServiceKit';
   import { taskpool } from '@kit.ArkTS';
   import { BusinessError, emitter } from '@kit.BasicServicesKit';
   
   @Concurrent
   async function sensorListener(): Promise<void> {
     sensor.on(sensor.SensorId.ACCELEROMETER, (data) => {
       emitter.emit({ eventId: 0 }, { data: data });
     }, { interval: 1000000000 });
   
     emitter.on({ eventId: 1 }, () => {
       sensor.off(sensor.SensorId.ACCELEROMETER)
       emitter.off(1)
     })
   }
   
   @Entry
   @Component
   struct Index {
     sensorTask?: taskpool.LongTask
     @State addListener: string = 'Add listener';
     @State deleteListener: string = 'Delete listener';
   
     build() {
       Column() {
         Text(this.addListener)
           .id('Add listener')
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
           .onClick(() => {
             this.sensorTask = new taskpool.LongTask(sensorListener);
             emitter.on({ eventId: 0 }, (data) => {
               // Do something here
               console.info(`Receive ACCELEROMETER data: {${data.data?.x}, ${data.data?.y}, ${data.data?.z}}`);
             });
             taskpool.execute(this.sensorTask).then(() => {
               this.addListener = 'success';
               console.info('Add listener of ACCELEROMETER success');
             }).catch((e: BusinessError) => {
               this.addListener = 'failed';
             })
           })
         Text(this.deleteListener)
           .id('Delete listener')
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
           .onClick(() => {
             emitter.emit({ eventId: 1 });
             emitter.off(0);
             if (this.sensorTask != undefined) {
               taskpool.terminateTask(this.sensorTask);
               this.deleteListener = 'success';
             } else {
               console.error('sensorTask is undefined.');
               this.deleteListener = 'failed';
             }
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```
