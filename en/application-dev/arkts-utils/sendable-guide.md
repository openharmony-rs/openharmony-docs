---
kits: ["ArkTS / Ark Programming Language"]
description: "Introduces typical use scenarios of Sendable objects: transferring large data across concurrent instances by reference to avoid serialization deep copy overhead, and passing class instance objects with methods across concurrent instances, with ready-to-reference development examples."
keywords: [Sendable use scenarios, large data transfer, pass-by-reference, instance objects with methods, deep copy optimization, cross-concurrent instance, shared objects]
doctype: guide
status: active
---

# Use Scenarios of Sendable
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:43:52.864Z pushedAt=2026-11-12T09:10:26.912Z nl=2 -->

Sendable objects are passed by reference across concurrent instances by default. This approach is more efficient than serialization and does not lose class member methods. Therefore, Sendable is particularly useful in two scenarios:

- Transmitting a large amount of data (for example, data exceeding 100 KB) across concurrent instances

- Passing class instances carrying methods across concurrent instances

## Transmitting Large Data Across Concurrent Instances

Serialization overhead increases linearly with the amount of data. When transmitting large data volumes (100 KB taking approximately 1 ms), the copying overhead can significantly impact application performance. On the contrary, passing objects by reference can greatly enhance performance.

**Example**
<!-- @[across_concurrent_instance_transfer_large_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableScenarios/bigdata/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { taskpool } from '@kit.ArkTS';
import { TestTypeA, TestTypeB, Test } from './sendable';
import { BusinessError, emitter } from '@kit.BasicServicesKit';

// Simulate data processing in a concurrent function.
@Concurrent
async function taskFunc(obj: Test) {
  console.info(`test task res1 is: ${obj.data1.name} res2 is: ${obj.data2.name}`);
}

async function test() {
  // Use TaskPool to pass data.
  let a: TestTypeA = new TestTypeA('testTypeA');
  let b: TestTypeB = new TestTypeB('testTypeB');
  let obj: Test = new Test(a, b);
  let task: taskpool.Task = new taskpool.Task(taskFunc, obj);
  await taskpool.execute(task);
}

@Concurrent
function sensorListener() {
  // Listening logic
  // ...
  console.info('Monitoring logic');
}

@Entry
@Component
struct Index {
  @State listenerTask: string = 'Listener task';
  @State dataProcessingTask: string = 'Data processing task';

  build() {
    Column() {
      Text(this.listenerTask)
        .id('Listener task')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          let sensorTask = new taskpool.LongTask(sensorListener);
          // ...
          taskpool.execute(sensorTask).then(() => {
            this.listenerTask = 'success';
            console.info('Add listener of ACCELEROMETER success');
          }).catch((e: BusinessError) => {
            // Process error
            this.listenerTask = 'failed';
          });
        });
      Text(this.dataProcessingTask)
        .id('Data processing task')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          test().then(() => {
            this.dataProcessingTask = 'success';
          }).catch((e: BusinessError) => {
            this.dataProcessingTask = 'failed';
            console.error('taskpool execute failed. Code: ' + e.code + ', message: ' + e.message);
          });
        });
    }
    .height('100%')
    .width('100%')
  }
}
```


<!-- @[across_concurrent_instance_transfer_large_data](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableScenarios/bigdata/src/main/ets/pages/sendable.ets) -->  

``` TypeScript
// Assemble large data in a Sendable class.
@Sendable
export class TestTypeA {
  public name: string = 'A';
  constructor(name: string) {
    this.name = name;
  }
}

@Sendable
export class TestTypeB {
  public name: string = 'B';
  constructor(name: string) {
    this.name = name;
  }
}

@Sendable
export class Test {
  public data1: TestTypeA;
  public data2: TestTypeB;
  constructor(arg1: TestTypeA, arg2: TestTypeB) {
    this.data1 = arg1;
    this.data2 = arg2;
  }
}
```



## Passing Class Instances Carrying Methods Across Concurrent Instances

Methods are lost during serialization of instance objects. Therefore, in scenarios where instance methods must be called, passing objects by reference is essential. If data parsing is required during processing, use the [ASON utility](ason-parsing-generation.md).

**Example**
<!-- @[across_concurrent_instance_pass_class_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableScenarios/crossconcurrency/src/main/ets/pages/Index.ets) --> 

``` TypeScript
import { taskpool, ArkTSUtils } from '@kit.ArkTS';
import { SendableTestClass, ISendable } from './sendable';

// Simulate data processing in a concurrent function.
@Concurrent
async function taskFunc(sendableObj: SendableTestClass) {
  console.info(`SendableTestClass: name is: ${sendableObj.printName()}, age is: ${sendableObj.printAge()}, sex is: ${sendableObj.printSex()}`);
  sendableObj.setAge(28);
  console.info(`SendableTestClass: age is: ${sendableObj.printAge()}`);

  // Parse the sendableObj.arr data to generate a JSON string.
  let str = ArkTSUtils.ASON.stringify(sendableObj.arr);
  console.info(`SendableTestClass: str is: ${str}`);

  // Parse the data and generate ISendable data.
  let jsonStr = '{"name": "Alexa", "age": 23, "sex": "female"}';
  let obj = ArkTSUtils.ASON.parse(jsonStr) as ISendable;
  console.info(`SendableTestClass: type is: ${typeof obj}`);
  console.info(`SendableTestClass: name is: ${(obj as object)?.['name']}`); // Output: 'Alexa'
  console.info(`SendableTestClass: age is: ${(obj as object)?.['age']}`); // Output: 23
  console.info(`SendableTestClass: sex is: ${(obj as object)?.['sex']}`); // Output: 'female'
}

async function test() {
  // Use TaskPool to pass data.
  let obj: SendableTestClass = new SendableTestClass();
  let task: taskpool.Task = new taskpool.Task(taskFunc, obj);
  await taskpool.execute(task);
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

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
        .onClick(async () => {
          await test();
          this.message = 'success';
        });
    }
    .height('100%')
    .width('100%')
  }
}
```

<!-- @[across_concurrent_instance_pass_class_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ConcurrentThreadCommunication/SendableScenarios/crossconcurrency/src/main/ets/pages/sendable.ets) --> 

``` TypeScript
// Define the mock class Test to simulate a class with methods that needs to be passed during development.
import { lang, collections } from '@kit.ArkTS';

export type ISendable = lang.ISendable;

@Sendable
export class SendableTestClass {
  public name: string = 'John';
  public age: number = 20;
  public sex: string = 'man';
  public arr: collections.Array<number> = new collections.Array<number>(1, 2, 3);

  constructor() {
  }

  setAge(age: number): void {
    this.age = age;
  }

  printName(): string {
    return this.name;
  }

  printAge(): number {
    return this.age;
  }

  printSex(): string {
    return this.sex;
  }
}
```
