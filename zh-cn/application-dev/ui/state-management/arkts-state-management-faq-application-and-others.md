# 应用内状态变管理其他常见问题
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

本文将介绍应用内状态管理的常见问题以及其他常见问题。

## 在并发线程中使用ArkUI装饰器导致报错

### 懒加载包含装饰器的文件

状态管理装饰器仅限于在UI线程使用，不允许在未加载ArkUI框架的[并发线程](../../arkts-utils/multi-thread-concurrency-overview.md)中使用。由于并发线程未加载完整的ArkUI框架逻辑，因此框架中定义的状态管理装饰器也不会被加载到并发线程中。若在并发线程中使用状态管理装饰器，将出现`ReferenceError: xxx is not defined`。在如下示例中，尽管并发线程并未实际使用[\@Observed](./arkts-observed-and-objectlink.md)装饰的类，但仍会打印`ReferenceError: Observed is not defined`的报错信息。这是因为并发线程在逐层解析文件依赖时，最终会加载到定义\@Observed装饰器的`Observed.ets`文件，从而触发该错误。

【反例】

```ts
// src/main/ets/pages/Index.ets
import { ErrorEvent, worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  build() {
    Button('New Worker')
    .onClick(() => {
      // 创建Worker对象。
      const newWorker = new worker.ThreadWorker('../workers/Worker.ets');

      // 注册onmessage回调，捕获宿主线程接收到来自其创建的Worker通过workerPort.postMessage接口发送的消息。该回调在宿主线程执行。
      newWorker.onmessage = (e: MessageEvents) => {
        let data: string = e.data;
        console.info('newWorker onmessage is: ', data);
      };

      // 注册onAllErrors回调，捕获Worker线程的onmessage回调、timer回调以及文件执行等流程产生的全局异常。该回调在宿主线程执行。
      newWorker.onAllErrors = (err: ErrorEvent) => {
        console.error('workerInstance onAllErrors message is: ' + err.message);
      };

      // 注册onmessageerror回调，当Worker对象接收到无法序列化的消息时被调用，在宿主线程执行。
      newWorker.onmessageerror = () => {
        console.error('workerInstance onmessageerror');
      };

      // 注册onexit回调，当Worker销毁时被调用，在宿主线程执行。
      newWorker.onexit = (e: number) => {
        // Worker正常退出时，code为0；异常退出时，code为1。
        console.info('workerInstance onexit code is: ', e);
      };

      // 发送消息给Worker线程。
      newWorker.postMessage('[Main] message from the main thread');
    })
  }
}
```

```ts
// src/main/ets/workers/Worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
import { testWithoutObserved } from '../pages/ImportObserved';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

// 注册onmessage回调，当Worker线程收到来自其宿主线程通过postMessage接口发送的消息时被调用，在Worker线程执行。
workerPort.onmessage = (e: MessageEvents) => {
  // 调用testWithoutObserved函数。
  testWithoutObserved();
  let data: string = e.data;
  console.info('workerPort onmessage is: ', data);

  // 向宿主线程发送消息。
  workerPort.postMessage('[Worker] message from the workerPort');
};

// 注册onmessageerror回调，当Worker对象接收到一条无法被序列化的消息时被调用，在Worker线程执行。
workerPort.onmessageerror = () => {
  console.error('workerPort onmessageerror');
};

// 注册onerror回调，捕获Worker在执行过程中发生的异常，在Worker线程执行。
workerPort.onerror = (err: ErrorEvent) => {
  console.error('workerPort onerror err is: ', err.message);
};
```

```ts
// src/main/ets/pages/ImportObserved.ets
import { innerTest } from './Observed';

export function testWithObserved(): void {
  innerTest();
  console.info('ImportObserved::testWithObserved call');
}

export function testWithoutObserved(): void {
  console.info('ImportObserved::testWithoutObserved call');
}
```

```ts
// src/main/ets/pages/Observed.ets
export function innerTest(): void {
  console.info('Observed::innerTest call');
}

@Observed
export class Person {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```

可以使用[lazy import](../../arkts-utils/arkts-lazy-import.md)懒加载包含装饰器的文件，子线程则不会加载到对应文件。

【正例】

```ts
// src/main/ets/pages/Index.ets
import { ErrorEvent, worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  build() {
    Button('New Worker')
    .onClick(() => {
      // 创建Worker对象。
      const newWorker = new worker.ThreadWorker('../workers/Worker.ets');

      // 注册onmessage回调，捕获宿主线程接收到来自其创建的Worker通过workerPort.postMessage接口发送的消息。该回调在宿主线程执行。
      newWorker.onmessage = (e: MessageEvents) => {
        let data: string = e.data;
        console.info('newWorker onmessage is: ', data);
      };

      // 注册onAllErrors回调，捕获Worker线程的onmessage回调、timer回调以及文件执行等流程产生的全局异常。该回调在宿主线程执行。
      newWorker.onAllErrors = (err: ErrorEvent) => {
        console.error('workerInstance onAllErrors message is: ' + err.message);
      };

      // 注册onmessageerror回调，当Worker对象接收到无法序列化的消息时被调用，在宿主线程执行。
      newWorker.onmessageerror = () => {
        console.error('workerInstance onmessageerror');
      };

      // 注册onexit回调，当Worker销毁时被调用，在宿主线程执行。
      newWorker.onexit = (e: number) => {
        // Worker正常退出时，code为0；异常退出时，code为1。
        console.info('workerInstance onexit code is: ', e);
      };

      // 发送消息给Worker线程。
      newWorker.postMessage('[Main] message from the main thread');
    })
  }
}
```

```ts
// src/main/ets/workers/Worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
import { testWithoutObserved } from '../pages/ImportObserved';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

// 注册onmessage回调，当Worker线程收到来自其宿主线程通过postMessage接口发送的消息时被调用，在Worker线程执行。
workerPort.onmessage = (e: MessageEvents) => {
  // 调用testWithoutObserved函数。
  testWithoutObserved();
  let data: string = e.data;
  console.info('workerPort onmessage is: ', data);

  // 向宿主线程发送消息。
  workerPort.postMessage('[Worker] message from the workerPort');
};

// 注册onmessageerror回调，当Worker对象接收到一条无法被序列化的消息时被调用，在Worker线程执行。
workerPort.onmessageerror = () => {
  console.error('workerPort onmessageerror');
};

// 注册onerror回调，捕获Worker在执行过程中发生的异常，在Worker线程执行。
workerPort.onerror = (err: ErrorEvent) => {
  console.error('workerPort onerror err is: ', err.message);
};
```

```ts
// 使用lazy import懒加载包含装饰器的文件。
import lazy { innerTest } from './Observed';

export function testWithObserved(): void {
  innerTest();
  console.info('ImportObserved::testWithObserved call');
}

export function testWithoutObserved(): void {
  console.info('ImportObserved::testWithoutObserved call');
}
```

```ts
// src/main/ets/pages/Observed.ets
export function innerTest(): void {
  console.info('Observed::innerTest call');
}

@Observed
export class Person {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```

### 装饰器使用隔离

子线程中调用的函数所在的文件中定义了状态管理装饰器，在加载时同样会加载到对应文件，打印`ReferenceError`报错。由于调用的函数与状态管理装饰器的定义存在于同一文件，使用懒加载的方式无法解决该问题，此时可以将调用函数移出该文件单独定义。

【反例】

```ts
// src/main/ets/pages/Index.ets
import { ErrorEvent, worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  build() {
    Button('New Worker')
    .onClick(() => {
      // 创建Worker对象。
      const newWorker = new worker.ThreadWorker('../workers/Worker.ets');

      // 注册onmessage回调，捕获宿主线程接收到来自其创建的Worker通过workerPort.postMessage接口发送的消息。该回调在宿主线程执行。
      newWorker.onmessage = (e: MessageEvents) => {
        let data: string = e.data;
        console.info('newWorker onmessage is: ', data);
      };

      // 注册onAllErrors回调，捕获Worker线程的onmessage回调、timer回调以及文件执行等流程产生的全局异常。该回调在宿主线程执行。
      newWorker.onAllErrors = (err: ErrorEvent) => {
        console.error('workerInstance onAllErrors message is: ' + err.message);
      };

      // 注册onmessageerror回调，当Worker对象接收到无法序列化的消息时被调用，在宿主线程执行。
      newWorker.onmessageerror = () => {
        console.error('workerInstance onmessageerror');
      };

      // 注册onexit回调，当Worker销毁时被调用，在宿主线程执行。
      newWorker.onexit = (e: number) => {
        // Worker正常退出时，code为0；异常退出时，code为1。
        console.info('workerInstance onexit code is: ', e);
      };

      // 发送消息给Worker线程。
      newWorker.postMessage('[Main] message from the main thread');
    })
  }
}
```

```ts
// src/main/ets/workers/Worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
import { testWithObserved } from '../pages/ImportObserved';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

// 注册onmessage回调，当Worker线程收到来自其宿主线程通过postMessage接口发送的消息时被调用，在Worker线程执行。
workerPort.onmessage = (e: MessageEvents) => {
  // 调用testWithObserved函数。
  testWithObserved();
  let data: string = e.data;
  console.info('workerPort onmessage is: ', data);

  // 向宿主线程发送消息。
  workerPort.postMessage('[Worker] message from the workerPort');
};

// 注册onmessageerror回调，当Worker对象接收到一条无法被序列化的消息时被调用，在Worker线程执行。
workerPort.onmessageerror = () => {
  console.error('workerPort onmessageerror');
};

// 注册onerror回调，捕获Worker在执行过程中发生的异常，在Worker线程执行。
workerPort.onerror = (err: ErrorEvent) => {
  console.error('workerPort onerror err is: ', err.message);
};
```

```ts
// src/main/ets/pages/ImportObserved.ets
import { innerTest } from './Observed';

export function testWithObserved(): void {
  innerTest();
  console.info('ImportObserved::testWithObserved call');
}

export function testWithoutObserved(): void {
  console.info('ImportObserved::testWithoutObserved call');
}
```

```ts
// src/main/ets/pages/Observed.ets
export function innerTest(): void {
  console.info('Observed::innerTest call');
}

@Observed
export class Person {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```

【正例】

```ts
// src/main/ets/pages/Index.ets
import { ErrorEvent, worker, MessageEvents } from '@kit.ArkTS';

@Entry
@Component
struct Index {
  build() {
    Button('New Worker')
    .onClick(() => {
      // 创建Worker对象。
      const newWorker = new worker.ThreadWorker('../workers/Worker.ets');

      // 注册onmessage回调，捕获宿主线程接收到来自其创建的Worker通过workerPort.postMessage接口发送的消息。该回调在宿主线程执行。
      newWorker.onmessage = (e: MessageEvents) => {
        let data: string = e.data;
        console.info('newWorker onmessage is: ', data);
      };

      // 注册onAllErrors回调，捕获Worker线程的onmessage回调、timer回调以及文件执行等流程产生的全局异常。该回调在宿主线程执行。
      newWorker.onAllErrors = (err: ErrorEvent) => {
        console.error('workerInstance onAllErrors message is: ' + err.message);
      };

      // 注册onmessageerror回调，当Worker对象接收到无法序列化的消息时被调用，在宿主线程执行。
      newWorker.onmessageerror = () => {
        console.error('workerInstance onmessageerror');
      };

      // 注册onexit回调，当Worker销毁时被调用，在宿主线程执行。
      newWorker.onexit = (e: number) => {
        // Worker正常退出时，code为0；异常退出时，code为1。
        console.info('workerInstance onexit code is: ', e);
      };

      // 发送消息给Worker线程。
      newWorker.postMessage('[Main] message from the main thread');
    })
  }
}
```

```ts
// src/main/ets/workers/Worker.ets
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
import { testWithObserved } from '../pages/ImportObserved';

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

// 注册onmessage回调，当Worker线程收到来自其宿主线程通过postMessage接口发送的消息时被调用，在Worker线程执行。
workerPort.onmessage = (e: MessageEvents) => {
  // 调用testWithObserved函数。
  testWithObserved();
  let data: string = e.data;
  console.info('workerPort onmessage is: ', data);

  // 向宿主线程发送消息。
  workerPort.postMessage('[Worker] message from the workerPort');
};

// 注册onmessageerror回调，当Worker对象接收到一条无法被序列化的消息时被调用，在Worker线程执行。
workerPort.onmessageerror = () => {
  console.error('workerPort onmessageerror');
};

// 注册onerror回调，捕获Worker在执行过程中发生的异常，在Worker线程执行。
workerPort.onerror = (err: ErrorEvent) => {
  console.error('workerPort onerror err is: ', err.message);
};
```

```ts
// src/main/ets/pages/ImportObserved.ets
import { innerTest } from './Addition';

export function testWithObserved(): void {
  innerTest();
  console.info('ImportObserved::testWithObserved call');
}

export function testWithoutObserved(): void {
  console.info('ImportObserved::testWithoutObserved call');
}
```

```ts
// src/main/ets/pages/Addition.ets
// 函数拆分，装饰器使用隔离。
export function innerTest(): void {
  console.info('Addition::innerTest call');
}
```

```ts
// src/main/ets/pages/Observed.ets
@Observed
export class Person {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```
