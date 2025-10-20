# ArkTS1.2并发迁移规则

本指南旨在讲述ArkTS新的并发特性和使用方法。

## 共享对象不添加装饰器@Sendable

**规则：** `arkts-limited-stdlib-no-sendable-decorator`

**规则解释：**

新增对象天然共享特性，无需添加@Sendable装饰器。

**变更原因：**

ArkTS演进新增了对象天然共享特性，不再依赖Sendable特性，无需再添加@Sendable装饰器。

**适配建议：**

删掉共享对象中的@Sendable装饰器。

**示例：**

**ArkTS1.1**
```typescript
@Sendable
class A {}
```

**ArkTS1.2**
```typescript
class A {}
```

## 共享函数不添加装饰器@Concurrent

**规则：** `arkts-limited-stdlib-no-concurrent-decorator`

**规则解释：**

新增函数对象天然共享特性，无需添加@Concurrent装饰器。

**变更原因：**

ArkTS演进新增了对象天然共享特性，不再依赖Concurrent特性，无需再为共享函数添加@Concurrent装饰器。

**适配建议：**

删掉共享函数中的@Concurrent装饰器。

**示例：**

**ArkTS1.1**
```typescript
@Concurrent
function func() {}
```

**ArkTS1.2**
```typescript
function func() {}
```

## 不支持Worker

**规则：** `arkts-no-need-stdlib-worker`

**规则解释：**

ArkTS内存天然共享，无需像传统的Actor模型一样通过消息传递来管理线程间的通信和状态隔离，不需要再基于Actor模型实现Worker。

**变更原因：**

ArkTS演进为内存天然共享模型，跨线程数据交互无需再依赖Actor模型的Worker机制。

**适配建议：**

使用ArkTS1.2提供的新线程[API-EAWorker](../reference/native-lib/eaworker_managed.md)。

**示例：**

**ArkTS1.1**
```typescript
// Worker.ets
import { worker, MessageEvents, ThreadWorkerGlobalScope } from '@kit.ArkTS';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

// 注册onmessage回调，当worker线程收到其宿主线程通过postMessage接口发送的消息时被调用
workerPort.onmessage = (e: MessageEvents) => {
  let data: string = e.data;
  console.info('workerPort onmessage is: ', data);
}

// 向宿主线程发送消息
workerPort.postMessage('hello hostThread');
```

```typescript
// Index.ets
import { worker, MessageEvents } from '@kit.ArkTS';

let workerInstance = new worker.ThreadWorker('entry/ets/workers/Worker.ets');

// 注册onmessage回调，当宿主线程接收到其创建的worker通过workerPort.postMessage接口发送的消息时被调用
workerInstance.onmessage = (e: MessageEvents) => {
  let data: string = e.data;
  console.info('workerInstance onmessage is: ', data);
}
// 发送消息给worker线程
workerInstance.postMessage('hello worker!')

// 执行结果为：
// workerPort onmessage is: hello worker!
// workerInstance onmessage is： hello hostThread！
```

**ArkTS1.2**
```typescript
let eaw = new EAWorker();
eaw.start();
eaw.run<void>(():void => {
    console.info('hello, eaworker!');
});

eaw.join();
```

## 共享模块不需要use shared修饰

**规则：** `arkts-limited-stdlib-no-use-shared`

**规则解释：**

新增对象天然共享特性，无需添加use shared。

**变更原因：**

ArkTS演进新增对象天然共享特性，模块及对象默认支持跨线程共享，无需再使用use shared显示声明。

**适配建议：**

删除use shared显示声明。

**示例：**

**ArkTS1.1**
```typescript
// test.ets
export let num = 1;
// shared.ets
'use shared'
export {num} from './test';
```

**ArkTS1.2**
```typescript
export let num = 1;
```

## 共享函数不需要use concurrent修饰

**规则：** `arkts-limited-stdlib-no-use-concurrent`

**规则解释：**

新增对象天然共享特性，无需添加use concurrent。

**变更原因：**

ArkTS演进新增对象天然共享特性，函数默认支持跨线程安全共享，无需再使用use shared显示声明。

**适配建议：**

删除use shared显示声明。

**示例：**

**ArkTS1.1**
```typescript
function func() {
'use concurrent' 
}
```

**ArkTS1.2**
```typescript
function func() {}
```

## 原生容器默认共享，不需要Sendable容器

**规则：** `arkts-no-need-stdlib-sendable-containers`

**规则解释：**

新增对象天然共享特性，不再依赖Sendable特性。可直接使用ArkTS1.2原生容器进行跨线程安全访问。

**变更原因：**

ArkTS演进新增对象天然共享特性，原生容器默认支持跨线程安全访问，无需再依赖Sendable容器或collections.前缀。

**适配建议：**

使用ArkTS1.2原生容器，删除collections.前缀。

**示例：**

**ArkTS1.1**
```typescript
import { collections } from '@kit.ArkTS';

let array = new collections.Array<number>();
```

**ArkTS1.2**
```typescript
let array = new Array<number>();
```

## 内存默认共享，不提供ASON

**规则：** `arkts-no-need-stdlib-ason`

**规则解释：**

新增对象天然共享特性，不再依赖Sendable特性，对象跨线程传递无需ASON序列化，而使用标准的JSON.stringify方法简化数据操作。

**变更原因：**

ArkTS演进新增对象天然共享特性，不再依赖Sendable特性。

**适配建议：**

- 将ASON.stringify()方法调用直接更改为JSON.stringify()，并删除ArkTSUtils.前缀。
- 扫描出存在的ASON.parse，由开发者根据相应的[JSON](../arkts-utils/arkts-json.md) API进行修改。

**示例：**

**ArkTS1.1**
```typescript
import { collections } from '@kit.ArkTS';
import { ArkTSUtils } from '@kit.ArkTS';
let arr = new collections.Array(1, 2, 3);
let str = ArkTSUtils.ASON.stringify(arr);
console.info(str);
```

**ArkTS1.2**
```typescript
let arr = new Array<number>(1, 2, 3);
let str = JSON.stringify(arr);
console.info(str);
```

## 内存默认共享，不提供SharedArrayBuffer

**规则：** `arkts-no-need-stdlib-sharedArrayBuffer`

**规则解释：**

新增对象天然共享特性，ArrayBuffer默认共享，不需要SharedArrayBuffer。

**变更原因：**

ArkTS演进新增对象天然共享特性，ArrayBuffer默认支持跨线程安全共享，无需再使用SharedArrayBuffer，简化并发数据共享机制。

**适配建议：**

ArkTS1.2使用ArrayBuffer，将ArkTS1.1中使用的SharedArrayBuffer改为ArrayBuffer。

**示例：**

**ArkTS1.1**
```typescript
let sab: SharedArrayBuffer = new SharedArrayBuffer(20);
let int32 = new Int32Array(sab);
```

**ArkTS1.2**
```typescript
let sab: ArrayBuffer = new ArrayBuffer(20);
let int32 = new Int32Array(sab);
```

## 不提供isConcurrent接口

**规则：** `arkts-limited-stdlib-no-support-isConcurrent`

**规则解释：**

新增对象天然共享特性，所有函数都是共享的，不需要提供isConcurrent。

**变更原因：**

ArkTS演进新增对象天然共享特性，所有函数默认跨线程安全共享，无需再通过isConcurrent接口判断并发性。

**适配建议：**

删除共享函数中isConcurrent调用点。

**示例：**

**ArkTS1.1**
```typescript
import { taskpool } from '@kit.ArkTS';
@Concurrent
function test() {}
let result: Boolean = taskpool.isConcurrent(test);
```

**ArkTS1.2**
不支持isConcurrent接口。

## taskpool、process、ArkTSUtils不需要import

**规则：** `arkts-limited-stdlib-no-import-concurrency`

**规则解释：**

taskpool、process、ArkTSUtils已基于ArkTS实现提供，不依赖于其他模块，不再需要import。

**变更原因：**

ArkTS演进为taskpool、process、ArkTSUtils提供原生支持，无需import即可直接使用。

**适配建议：**

删除taskpool、process、ArkTSUtils前的import，改为直接使用，并且process更名为StdProcess。

**示例：**

**ArkTS1.1**
```typescript
import { taskpool } from '@kit.ArkTS';

@Concurrent
function test() {}

taskpool.execute(test);
```

**ArkTS1.2**
```typescript
function test() {}

taskpool.execute(test);
```

## AsyncLock不需要import

**规则：** `arkts-limited-stdlib-no-import-concurrency`

**规则解释：**

AsyncLock实现基于ArkTS提供，不依赖其他模块，不再需要import，且不需要添加ArkTSUtils.locks.前缀。

**变更原因：**

ArkTS演进为AsyncLock提供原生支持，无需import和ArkTSUtils.locks.前缀即可直接使用。

**适配建议：**

删除AsyncLock前的import，改为直接使用，同时删除AsyncLock的ArkTSUtils.locks.前缀。

**示例：**

**ArkTS1.1**
```typescript
import { ArkTSUtils } from '@kit.ArkTS'

let lock: ArkTSUtils.locks.AsyncLock = new ArkTSUtils.locks.AsyncLock();
```

**ArkTS1.2**
```typescript
let lock: AsyncLock = new AsyncLock();
```

## process更名为StdProcess，且不需要import

**规则：** `arkts-change-process-to-StdProcess`

**规则解释：**

StdProcess实现基于ArkTS提供，不依赖其他模块，不再需要import。为避免占用process关键字，更名为StdProcess。

**变更原因：**

ArkTS演进为进程管理提供原生StdProcess支持，无需import即可直接使用，且为避免与关键字冲突，将process更名为StdProcess。

**适配建议：**

删除process前的import，改为直接使用，同时将process全部替换为StdProcess。

**示例：**

**ArkTS1.1**
```typescript
import { process } from '@kit.ArkTS';

let result = process.is64Bit();
let pro = new process.ProcessManager();
let pres = pro.getUidForName('tool');
```

**ArkTS1.2**
```typescript
let result = StdProcess.is64Bit();
let pro = new StdProcess.ProcessManager();
let pres = pro.getUidForName('tool');
```

## 移除taskpool setCloneList接口

**规则：** `arkts-limited-stdlib-no-setCloneList`

**规则解释：**

内存默认共享，不需要提供setCloneList来拷贝传递对象。如果仍然需要以拷贝语义使用数组对象，可以调用Array.from()方法手动拷贝。

**变更原因：**

ArkTS演进为内存默认共享模型，对象跨线程传递时无需通过setCloneList接口手动设置克隆，需拷贝时可显式调用Array.from()方法。

**适配建议：**

删除setCloneList调用。

**示例：**

**ArkTS1.1**
```typescript
import { taskpool } from '@kit.ArkTS';

@Sendable
class TestClass {
  public str: string = 'sendable: TestClass';
}

@Concurrent
function testFunc(array: Array<TestClass>) {
  let testInstance = array[0];
  return testInstance.str;
}

let testInstance: TestClass = new TestClass();
let array = new Array<TestClass>();
array.push(testInstance);
let task = new taskpool.Task(testFunc, array);
task.setCloneList(array);
taskpool.execute(task).then((res: Object):void => {
  console.info('sendable: task res is: ' + res);
  console.info('sendable: array length: ' + array.length);
});
// 执行结果为
// sendable: task res is: sendable: TestClass
// sendable: array length: 1
```

**ArkTS1.2**
```typescript
class TestClass {
  public str: string = 'TestClass';
}

function testFunc(array: Array<TestClass>) {
  let testInstance = array[0];
  array.push(new TestClass());
  return testInstance.str;
}

let testInstance: TestClass = new TestClass();

// 以拷贝语义传递数组，testFunc内的修改不会作用到array1对象上。这段代码不应该执行在顶层作用域，注意异步事件环境。
async function copyTrans() {
  let array1 = new Array<TestClass>();
  array1.push(testInstance);
  let task1 = new taskpool.Task(testFunc, Array.from(array1));
  taskpool.execute(task1).then((res: Any):void => {
    console.info('task1 res is: ' + res);
    console.info('array1 length: ' + array1.length);
  });
}

// 使用引用传递数组，testFunc内的修改会作用到array2对象上。这段代码不应该执行在顶层作用域，注意异步事件环境。
async function referenceTrans() {
  let array2 = new Array<TestClass>();
  array2.push(testInstance);
  let task2 = new taskpool.Task(testFunc, array2);
  taskpool.execute(task2).then((res: Any):void => {
    console.info('task2 res is: ' + res);
    console.info('array2 length: ' + array2.length);
  });
}
// 两个函数的执行结果为：
// task1 res is: TestClass
// array1 length: 1
// task2 res is: TestClass
// array2 length: 2
```

## 移除taskpool setTransferList接口

**规则：** `arkts-limited-stdlib-no-setTransferList`

**规则解释：**

内存默认共享，不需要提供setTransferList来跨线程传递ArrayBuffer对象。

**变更原因：**

ArkTS演进为内存默认共享模型，ArrayBuffer等对象默认支持跨线程安全访问，无需再提供setTransferList接口手动设置传输列表。

**适配建议：**

删除setTransferList调用。

**示例：**

**ArkTS1.1**
```typescript
import { taskpool } from '@kit.ArkTS';

@Concurrent
function testTransfer(arg1: ArrayBuffer, arg2: ArrayBuffer): number {
  console.info('testTransfer arg1 byteLength: ' + arg1.byteLength);
  console.info('testTransfer arg2 byteLength: ' + arg2.byteLength);
  return 100;
}

let buffer: ArrayBuffer = new ArrayBuffer(8);
let view: Uint8Array = new Uint8Array(buffer);
let buffer1: ArrayBuffer = new ArrayBuffer(16);
let view1: Uint8Array = new Uint8Array(buffer1);

console.info('testTransfer view byteLength: ' + view.byteLength);
console.info('testTransfer view1 byteLength: ' + view1.byteLength);
// 执行结果为：
// testTransfer view byteLength: 8
// testTransfer view1 byteLength: 16

let task: taskpool.Task = new taskpool.Task(testTransfer, view, view1);
task.setTransferList([view.buffer, view1.buffer]);
taskpool.execute(task).then((res: Object) => {
  console.info('test result: ' + res);
}).catch((e: string) => {
  console.error('test catch: ' + e);
})
console.info('testTransfer view2 byteLength: ' + view.byteLength);
console.info('testTransfer view3 byteLength: ' + view1.byteLength);
// 经过transfer转移之后值为0，执行结果为：
// testTransfer view2 byteLength: 0
// testTransfer view3 byteLength: 0
```

**ArkTS1.2**
```typescript
function testTransfer(arg1: Uint8Array, arg2: Uint8Array): number {
  console.info('testTransfer arg1 byteLength: ' + arg1.byteLength);
  console.info('testTransfer arg2 byteLength: ' + arg2.byteLength);
  return 100.0;
}

// 这段代码不应该执行在顶层作用域，注意异步事件环境。
async function removeSetTransferList() {
  let buffer: ArrayBuffer = new ArrayBuffer(8);
  let view: Uint8Array = new Uint8Array(buffer);
  let buffer1: ArrayBuffer = new ArrayBuffer(16);
  let view1: Uint8Array = new Uint8Array(buffer1);

  console.info('testTransfer view byteLength: ' + view.byteLength);
  console.info('testTransfer view1 byteLength: ' + view1.byteLength);
  // 执行结果为：
  // testTransfer view byteLength: 8
  // testTransfer view1 byteLength: 16

  let task: taskpool.Task = new taskpool.Task(testTransfer, view, view1);
  taskpool.execute(task).then((res: Any):void => {
    console.info('test result: ' + res);
  }).catch((e: Error): void => {
    console.error('test catch: ' + e);
  })
  // 内存共享，此处可直接访问view,view1的内容，不需要使用setTransferList
  // 执行结果为：
  // testTransfer arg1 byteLength: 8
  // testTransfer arg2 byteLength: 16
  // test result: 100

  // 如果需要保持原有传递语义，需要手动拷贝并清理原数组
  let task2: taskpool.Task = new taskpool.Task(testTransfer, Uint8Array.from(view), Uint8Array.from(view1));
  taskpool.execute(task2).then((res: Any) => {
    console.info('test result: ' + res);
  })
  view = new Uint8Array(0);
  view1 = new Uint8Array(0);
}
```

## 删除ISendable接口

**规则：** `arkts-no-need-stdlib-ISendable`

**规则解释：**

新增对象天然共享特性，无需实现ISendable接口。

**变更原因：**

ArkTS演进新增对象天然共享特性，所有对象默认支持跨线程安全传递，无需再继承ISendable。

**适配建议：**

删除'implements lang.ISendable'语句，无需再使用ISendable接口。

**示例：**

**ArkTS1.1**
```typescript
import { lang } from '@kit.ArkTS';

@Sendable
class CustomData implements lang.ISendable {
    data1: number;
    data2: string;
    constructor(data1: number, data2: string) {
        this.data1 = data1;
        this.data2 = data2;
    }
}
```

**ArkTS1.2**
```typescript
class CustomData {
    data1: number;
    data2: string;
    constructor(data1: number, data2: string) {
        this.data1 = data1;
        this.data2 = data2;
    }
}
```

## 删除isSendable接口

**规则：** `arkts-no-need-stdlib-isSendable`

**规则解释:**

新增对象天然共享特性，无需判断是否为Sendable数据类型。

**变更原因：**

ArkTS演进新增对象天然共享特性，所有对象默认跨线程安全传递，无需再通过isSendable接口判断数据类型。

**适配建议：**

删除ArkTSUtils.isSendable()，取消判断。

**示例：**

**ArkTS1.1**
```typescript
import { ArkTSUtils } from '@kit.ArkTS'

@Sendable
function sendableFunc() {
  console.info('sendableFunc')
}

if (ArkTSUtils.isSendable(sendableFunc)) {
  console.info('sendableFunc is Sendable');
} else {
  console.info('sendableFunc is not Sendable');
}
```

**ArkTS1.2**

内存共享，不需要判断是否为Sendable对象，不再提供isSendable接口。

## taskpool.execute()返回类型由Promise\<Object>变更为Promise\<NullishType>

**规则：** `arkts-taskpool-execute-generic-type-object-to-nullishtype`

**规则解释：**

ArkTS1.1中taskpool execute返回值声明为Promise\<Object>，但实际可以返回值为undefined的Promise。ArkTS1.2中undefined和Object为不同类型，相互之间无法进行类型转换。

**变更原因：**

ArkTS1.2中undefined与Object为互不兼容的类型。为准确匹配execute()可能返回undefined的实际语义，返回类型由Promise\<Object>调整为Promise\<NullishType>，以确保类型安全。

**适配建议：**

将Promise中的Object参数修改为NullishType参数类型。

**示例：**

**ArkTS1.1**
```typescript
import { taskpool } from '@kit.ArkTS';

// 场景一:
@Concurrent
function printLog(str: number): number {
  console.info("printLog called: " + str);
  return str;
}

async function test1() {
  let task = new taskpool.Task(printLog, 10.0);
  let a3: Object = await taskpool.execute(task);
}

// 场景二：
async function test2() {
  let task = new taskpool.Task(printLog, 10.0);
  let a3 = taskpool.execute(task);
  a3.then((res: Object) => {
    // ...
  })
}
```

**ArkTS1.2**
```typescript
// 场景一：
function printLog(str: number): number {
    console.info("printLog called: " + str);
    return str;
}
async function test1() {
    let task = new taskpool.Task(printLog, 10.0);
    let a3: Object = (await taskpool.execute(task)) as Object;

    // or let a3: NullishType = await taskpool.execute(task);
}

// 场景二：
async function test2() {
    let task = new taskpool.Task(printLog, 10.0);
    let a3 = taskpool.execute(task);
    a3.then((res: NullishType) => {
        console.info("d");
    })
}
```

## Promise的reject函数只能接受Error类型作为参数

**规则：** `arkts-limited-stdlib-promise-reject-type-error`

**规则解释：**

ArkTS1.2中加强类型限制，有以下规格限制：

- throw只能抛出Error及其子类。

-  await Promise对象时，如果该Promise被reject，需要抛出其被reject的原因。

-  Promise构造函数中的reject方法，和静态reject方法，需要使用Error及其子类作为入参。

**变更原因：**

ArkTS1.2强化了错误处理类型安全，规定了Promise的reject必须使用Error类型，确保错误传递的规范性和一致性。

**适配建议：**

调用Promise构造器的reject回调和静态方法reject时，使用Error及其子类作为函数入参。

**示例：**

**ArkTS1.1**
```typescript
let p = new Promise<string>((resolve, reject) => {
    reject("error")
});
Promise.reject("error");
```

**ArkTS1.2**
```typescript
let p = new Promise<string>((resolve, reject) => {
    reject(new Error("error"))
});
Promise.reject(new Error("error"));
```

## Promise的then和catch方法的onrejected回调参数类型只能标注为Error或其父类类型

**规则：** `arkts-limited-stdlib-promise-onrejected-type-error`

**规则解释：**

ArkTS1.2中加强类型限制，且类型转换具有运行时语义。为了保证类型安全，规格中限制函数间赋值遵循逆变原则，子类型入参回调无法赋值给父类型入参回调。

**变更原因：**

ArkTS1.2强化类型安全，规定Promise的onrejected回调参数类型必须为Error或其父类，且遵循逆变原则确保赋值安全，以避免运行时类型错误。

**适配建议：**

调用Promise的then方法和catch方法时，onReject回调的入参类型改为Error。

**示例：**

**ArkTS1.1**
```typescript
import { BusinessError } from "@kit.BasicServicesKit";

let p = new Promise<string>((resolve, reject) => {
  reject(new Error("error"))
});
p.then(() => {}, (e: BusinessError) => {
  console.info(String(e))})
p.catch((e: BusinessError) => { console.info(String(e))})
```

**ArkTS1.2**
```typescript
import { BusinessError } from "@ohos.base";

let p = new Promise<string>((resolve, reject) => {
    reject(new BusinessError())
});
p.then(() => { }, (e: Error) => {
    let err = e as BusinessError;
    console.info(String(err));
})
p.catch((e: Error) => {
    let err = e as BusinessError;
    console.info(String(err));
})
```

## 不支持用户自定义声明PromiseFulfilledResult、PromiseRejectedResult和PromiseSettledResult 

**规则：** `arkts-not-support-PromiseSettledResult-customization`

**规则解释：**

ArkTS1.2不支持用户自定义声明PromiseFulfilledResult、PromiseRejectedResult和PromiseSettledResult。

**变更原因：**

ArkTS1.2不允许多次定义同名interface。

**适配建议：**

删除用户自定义的PromiseFulfilledResult、PromiseRejectedResult和PromiseSettledResult接口。

**示例：**

**ArkTS1.1**
```typescript
interface PromiseFulfilledResult<T> {
  status: "fulfilled";
  value: T;
}

interface PromiseRejectedResult {
  status: "rejected";
  reason: string;
}

type PromiseSettledResult<T> = PromiseFulfilledResult<T> | PromiseRejectedResult;
```

**ArkTS1.2**

已删除用户自定义的PromiseFulfilledResult、PromiseRejectedResult和PromiseSettledResult。


## 不支持编译阶段根据PromiseSettledResult的status值确定其实际类型

**规则：** `arkts-not-support-PromiseSettledResult-smartcast`

**规则解释：**

智能转换是编译器会在某些场景下（如instanceof、null检查、上下文推导等）识别出对象的具体类型，无需手动转换，而是自动将变量转换为相应类型的方法。ArkTS1.2中不支持对类的成员变量进行智能转换。

**变更原因：**

ArkTS1.2不支持对类的成员变量进行智能类型转换，需要判断后使用as转换成实际类型。

**适配建议：**

判断成员变量后，手动使用as进行成员变量的类型转换。

**示例：**

**ArkTS1.1**
```typescript
let f1 = Promise.resolve<string>('fulfilled 1');
Promise.allSettled<string>([f1])
  .then((results: PromiseSettledResult<string>[]) => {
    results.forEach((result: PromiseSettledResult<string>) => {
      if (result.status === 'fulfilled') {
        console.log(`${result.value} `);
      } else {
        console.log(`${result.reason.message} `);
      }
    });
  })
```

**ArkTS1.2**
```typescript
let f1 = Promise.resolve<string>('fulfilled 1');
Promise.allSettled<string>([f1])
  .then((results: PromiseSettledResult<string>[]) => {
    results.forEach((result: PromiseSettledResult<string>) => {
      if (result.status === 'fulfilled') {
          let result1 = result as PromiseFulfilledResult<string>;
          console.log(result1.value);
            } else {
             let result1 = result as PromiseRejectedResult;
             console.log(result1.reason.message);
            }
      });
   })
```

## 不支持Promise\<Promise\<T>>的then方法调用 

**规则：** `arkts-no-support-nested-promise`

**规则解释：**

静态类型导致回调运行时类型转换失败，回调无法执行。

**变更原因：**

ArkTS1.2静态类型系统不支持Promise\<Promise\<T>>的隐式解包，直接调用then方法会导致运行时类型转换失败，使得回调无法执行。

**适配建议：**

声明时直接使用Promise\<T>。

**示例：**

**ArkTS1.1**
```typescript
let p = new Promise<Promise<number>>((res, rej) => { res(Promise.resolve(1.0)) });
p.then((res: Promise<number>) => { console.info(res+"") })
```

**ArkTS1.2**
```typescript
let p = new Promise<number>((res, rej) => { res(Promise.resolve(1.0))});
p.then((res: number) => { console.info(res)})
```

## Task的function属性改名为taskFunction

**规则：** `arkts-change-taskpool-Task-to-taskFunction`

**规则解释：**

ArkTS1.2中function为关键字，不能作为类属性。

**变更原因：**

ArkTS1.2中function为关键字，不能作为标识符使用。

**适配建议：**

将Task的function属性改名为taskFunction以避免语法冲突。

**示例：**

**ArkTS1.1**
```typescript
import { taskpool } from '@kit.ArkTS';

function testString(str: string) {
  console.info(str);

}
let task: taskpool.Task = new taskpool.Task(testString, "hello");
let func = task.function;
```

**ArkTS1.2**
```typescript
let func1 = (str: string): string => {
    return str;
};
let task: taskpool.Task = new taskpool.Task(func1, "hello");
let func = task.taskFunction;
```

## taskpool不提供GenericsTask

**规则：** `arkts-not-supprot-genericstask`

**规则解释：**

- ArkTS1.2中不支持以泛型数组的形式对回调参数类型进行校验。

- ArkTS1.2中不支持将非可变参数类型回调赋值给可变参数函数。 

**变更原因：**

ArkTS1.2类型系统不支持泛型数组参数校验及非可变参数向可变参数的赋值，故移除GenericsTask以保障类型安全。

**适配建议：**

需要时直接使用taskpool.Task，不使用GenericsTask。

**示例：**

**ArkTS1.1**
```typescript
import { taskpool } from '@kit.ArkTS';
@Concurrent
function testWithThreeParams(a: number, b: string, c: number): string {
  return b;
}
let task1: taskpool.Task = new taskpool.GenericsTask<[number, string, number], string>(testWithThreeParams, 100, "test", 100);
```

**ArkTS1.2**
```typescript
function testWithThreeParams(a: number, b: string, c: number): string {
  return b;
}
```

## 不支持在全局空间直接或间接调用async函数

**规则：** `arkts-not-support-global-async-call`

**规则解释：**

根据ArkTS1.2规格，全局初始化阶段不可以调用异步函数，否则会导致初始化结果难以推导。

**变更原因：**

ArkTS1.2禁止在全局初始化阶段调用异步函数，以避免初始化顺序不可控和结果难以推导的问题，确保程序确定性。

**适配建议：**

不在全局初始化阶段调用async函数。

**示例：**

**ArkTS1.1**
```typescript
async  function asynctest() {}
asynctest();
function f1() { asynctest(); }
f1();
```

**ArkTS1.2**
```typescript
async  function asynctest() {}
function f1() { asynctest(); }
function main() {
    asynctest();
    f1();
}
```

## Promise\<void>构造器中只支持使用resolve(undefined)

**规则：** `arkts-promise-with-void-type-need-undefined-as-resolve-arg`

**规则解释：**

ArkTS1.2中void不能作为变量类型声明；作为泛型时，在类实例化时会自动转换为undefined。

**变更原因：**

ArkTS1.2中void不能作为变量类型，Promise\<void>在实例化时转换为Promise\<undefined>，因此需使用resolve(undefined)确保类型一致。

**适配建议：**

所有Promise\<void>的resolve调用需要显式传入undefined，在异步回调中须通过箭头函数包装并明确参数。

**示例：**

**ArkTS1.1**
```typescript
let p1 = new Promise<void>((resolve, reject) => {
    resolve();
})
let p2 = new Promise<void>((resolve, reject) => {
    setTimeout(resolve, 10);
})
```

**ArkTS1.2**
```typescript
let p1 = new Promise<void>((resolve, reject) => {
    resolve(undefined);
})
let p2 = new Promise<void>((resolve, reject) => {
    setTimeout(() => {resolve(undefined)}, 10);
})    
```