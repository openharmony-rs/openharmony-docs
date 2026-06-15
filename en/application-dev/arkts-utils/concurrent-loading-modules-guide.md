# Concurrent Loading of Service Modules
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @huanghello-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

During application launch, multiple service modules need to be loaded. For example, in a mapping application, different modules such as positioning, ride-hailing, and navigation are required. Initializing all these modules in the UI main thread can significantly increase the cold start time of the application. To address this, these modules should be loaded concurrently in separate background threads to reduce launch latency.

By leveraging the TaskPool capabilities provided by ArkTS, different service initialization tasks can be offloaded to child threads. Service modules can be implemented in C++ as [NativeBinding objects](transferabled-object.md) or defined in ArkTS as [Sendable objects](arkts-sendable.md). The initialized modules can then be returned to the UI main thread for use. The implementation involves the following steps:

1. Define each service module (SDK) (using Sendable objects as an example).

   Define the calculator service module as follows:

   <!-- @[define_calculator_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/sdk/Calculator.ets) -->
   
   ``` TypeScript
   import { collections } from '@kit.ArkTS';
   
   @Sendable
   export class Calculator {
     public history?: collections.Array<collections.Array<string>>;
     public totalCount: number = 0;
   
     // Perform initialization.
     static init(): Calculator {
       let calc = new Calculator();
       calc.totalCount = 0;
       calc.history = collections.Array.create(calc.totalCount, collections.Array.create(2, ''));
       return calc;
     }
   
     // Perform the addition operation.
     add(a: number, b: number) {
       let result = a + b;
       this.newCalc(`${a} + ${b}`, `${result}`);
       return result;
     }
   
     // Perform the subtraction operation.
     sub(a: number, b: number) {
       let result = a - b;
       this.newCalc(`${a} - ${b}`, `${result}`);
       return result;
     }
   
     // Perform the multiplication operation.
     mul(a: number, b: number) {
       let result = a * b;
       this.newCalc(`${a} * ${b}`, `${result}`);
       return result;
     }
   
     // Perform the division operation.
     div(a: number, b: number) {
       let result = a / b;
       this.newCalc(`${a} / ${b}`, `${result}`);
       return result;
     }
   
     // Obtain historical records.
     getHistory(): collections.Array<collections.Array<string>> {
       return this.history!;
     }
   
     // Print historical records.
     showHistory() {
       for (let i = 0; i < this.totalCount; i++) {
         console.info(`${i}: ${this.history![i][0]} = ${this.history![i][1]}`);
       }
     }
   
     // Add new calculation records.
     private newCalc(opt: string, ret: string) {
       let newRecord = new collections.Array<string>(opt, ret);
       this.totalCount = this.history!.unshift(newRecord);
     }
   }
   ```

   Define the timer service module as follows:

   <!-- @[define_timer_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/sdk/TimerSdk.ets) -->
   
   ``` TypeScript
   @Sendable
   export class TimerSdk {
   
     // Perform initialization.
     static init(): TimerSdk {
       let timer = new TimerSdk();
       return timer;
     }
   
     // Count down.
     async countdown(time: number) {
       return new Promise((resolve: (value: boolean) => void) => {
         setTimeout(() => {
           resolve(true);
         }, time);
       });
     }
   }
   ```

2. In the UI main thread, trigger the distribution of service modules to child threads, and use them in the UI main thread after loading is complete. The following is an example:

   <!-- @[distribute_child_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/PracticalCases/entry/src/main/ets/managers/ConcurrentLoadingModulesGuide.ets) -->
   
   ``` TypeScript
   import { Calculator } from '../sdk/Calculator';
   import { TimerSdk } from '../sdk/TimerSdk';
   import { taskpool } from '@kit.ArkTS';
   
   // Initialize the Calculator.
   @Concurrent
   function initCalculator(): Calculator {
     return Calculator.init();
   }
   
   // Initialize the TimerSdk.
   @Concurrent
   function initTimerSdk(): TimerSdk {
     return TimerSdk.init();
   }
   
   @Entry
   @Component
   struct Index {
     @State calculateAdd: string = 'calculate add';
     @State showHistory: string = 'show history';
     @State countdown: string = 'countdown';
     calc?: Calculator;
     timer?: TimerSdk;
   
     aboutToAppear(): void {
       taskpool.execute(initCalculator).then((ret) => {
         this.calc = ret as Calculator;
       })
       taskpool.execute(initTimerSdk).then((ret) => {
         this.timer = ret as TimerSdk;
       })
     }
   
     build() {
       Row() {
         Column() {
           Text(this.calculateAdd)
             .id('add')
             .fontSize(50)
             .fontWeight(FontWeight.Bold)
             .alignRules({
               center: { anchor: '__container__', align: VerticalAlign.Center },
               middle: { anchor: '__container__', align: HorizontalAlign.Center }
             })
             .onClick(async () => {
               let result = this.calc?.add(1, 2)
               console.info(`Result is ${result}`)
               this.calculateAdd = 'success';
             })
           Text(this.showHistory)
             .id('show')
             .fontSize(50)
             .fontWeight(FontWeight.Bold)
             .alignRules({
               center: { anchor: '__container__', align: VerticalAlign.Center },
               middle: { anchor: '__container__', align: HorizontalAlign.Center }
             })
             .onClick(async () => {
               this.calc?.showHistory();
               this.showHistory = 'success';
             })
           Text(this.countdown)
             .id('get')
             .fontSize(50)
             .fontWeight(FontWeight.Bold)
             .alignRules({
               center: { anchor: '__container__', align: VerticalAlign.Center },
               middle: { anchor: '__container__', align: HorizontalAlign.Center }
             })
             .onClick(async () => {
               console.info(`Timer start`);
               await this.timer?.countdown(1000);
               console.info(`Timer end`);
               this.countdown = 'success';
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
