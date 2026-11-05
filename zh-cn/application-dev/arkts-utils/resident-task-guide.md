---
kits: ["ArkTS / 方舟编程语言"]
description: "提供使用Worker开发常驻任务的指导：Worker持续执行任务直至宿主线程发送终止指令，示例演示Worker的自动创建、start与stop指令交互及任务执行，适用于需要长期后台运行的业务，并给出Worker数量规划与复用的指导。"
keywords: [常驻任务, Worker, ThreadWorker, 常驻线程, start与stop指令, 后台运行, 生命周期管理, Worker复用, Worker数量规划]
doctype: guide
status: active
---

# 常驻任务开发指导 (Worker)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

提供使用Worker进行常驻任务的开发指导。Worker将持续执行任务，直到宿主线程发送终止指令。

开发过程和示例如下：

1. DevEco Studio支持一键生成Worker，在对应的{moduleName}目录下任意位置，单击鼠标右键 &gt; New &gt; Worker，即可自动生成Worker的模板文件及配置信息。本文以创建“Worker”为例。

   此外，还支持手动创建Worker文件。具体方式和注意事项请参见[创建Worker的注意事项](worker-introduction.md#创建worker的注意事项)。

2. 首先导入Worker模块，然后在宿主线程中通过调用ThreadWorker的[constructor()](../reference/apis-arkts/js-apis-worker.md#constructor9)方法创建Worker对象，创建Worker对象的线程为宿主线程。 此处的宿主线程为UI主线程，宿主线程发送'start'以开始执行某个长期运行的任务，并接收子线程返回的相关消息。当不需要执行该任务时，发送'stop'以停止该任务的执行。在此示例中，任务将在10秒后结束。

   <!-- @[worker_receive_child_thread_message](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/ResidentTaskGuide.ets) --> 
   
   ``` TypeScript
   import { MessageEvents, worker } from '@kit.ArkTS';
   
   @Entry
   @Component
   struct Index {
     build() {
       Column() {
         Text('Listener task')
           .id('HelloWorld')
           .fontSize(50)
           .fontWeight(FontWeight.Bold)
           .onClick(() => {
             const workerInstance: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/Worker.ets');
             workerInstance.onmessage = (event: MessageEvents) => {
               console.info('UI主线程收到消息：', event.data);
             }
             workerInstance.postMessage({type: 'start'})
             // 10秒后停止worker
             setTimeout(() => {
               workerInstance.postMessage({ type: 'stop' });
             }, 10000);
           })
       }
       .height('100%')
       .width('100%')
     }
   }
   ```

3. 在Worker线程中，当接收到宿主线程发送的消息为'start'时，开始执行某个长时间不定期运行的任务，并实时向宿主线程返回消息。当接收到的消息为'stop'时，结束该任务的执行并返回相应的消息给宿主线程。

   <!-- @[worker_correspond_main_thread](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/Worker.ets) -->
   
   ``` TypeScript
   import { MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
   
   const workerPort: ThreadWorkerGlobalScope = worker.workerPort;
   let isRunning = false;
   workerPort.onmessage = (e: MessageEvents) => {
     const type = e.data.type as string;
     if (type === 'start') {
       if (!isRunning) {
         isRunning = true;
         // 开始常驻任务
         performTask();
       }
     } else if (type === 'stop') {
       isRunning = false;
     }
   }
   
   // 模拟常驻任务
   function performTask() {
     if (isRunning) {
       // 模拟某个长期运行的任务
       workerPort.postMessage('Worker is performing a task');
       // 1秒后再次执行任务
       setTimeout(performTask, 1000);
     } else {
       workerPort.postMessage('Worker has stopped performing the task');
       workerPort.close();
     }
   }
   ```

## Worker数量规划与复用

对于需要常驻多个Worker的场景，Worker数量并不是越多越好。每个Worker创建时会初始化独立的虚拟机实例、独立堆内存、解释器和模块系统等，基础内存开销约为数MB到20MB（内存开销构成详见[Worker运作机制](worker-introduction.md#worker运作机制)），Worker数量过多会在低内存设备上造成明显的内存压力。因此，Worker数量应由同一时刻需要并行执行的任务数决定，并尽量用少量Worker处理多类任务。

规划Worker数量的步骤如下：

1. 列出所有常驻任务，标注哪些任务需要同时并行执行。

2. 可以串行复用的任务合并到一个Worker中处理，通过消息中的type字段分发。

3. 最终Worker数量等于合并后不可再分的并行任务组数。

例如，应用有3个常驻任务（数据解析、日志上报、文件预处理），其中日志上报和文件预处理可以串行复用同一个Worker，数据解析需要独立并行执行，则最终只需要2个Worker。

对于合并到同一个Worker中的多类任务，宿主线程可以封装一个任务管理类，通过消息中的type字段区分任务类型并分发处理，示例如下：

<!-- @[worker_manager](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/managers/WorkerManager.ets) -->

``` TypeScript
import { worker, MessageEvents } from '@kit.ArkTS';

// 宿主线程发给Worker的消息，通过type字段区分任务类型
interface WorkerMessage {
  id: number;
  type: string;
  payload: string;
}

// Worker返回给宿主线程的处理结果
interface WorkerResult {
  id: number;
  success: boolean;
  result?: string;
  error?: string;
}

class WorkerManager {
  private workerInstance: worker.ThreadWorker | null = null;
  private taskCounter: number = 0;
  private pending: Map<number, (result: string) => void> = new Map();
  private rejectFuncs: Map<number, (reason: string) => void> = new Map();

  constructor() {
    this.workerInstance = new worker.ThreadWorker('entry/ets/workers/Dispatcher.ets');
    this.workerInstance.onmessage = (e: MessageEvents) => {
      const data = e.data as WorkerResult;
      if (data.success) {
        const resolver = this.pending.get(data.id);
        if (resolver) {
          resolver(data.result ?? '');
          this.pending.delete(data.id);
          this.rejectFuncs.delete(data.id);
        }
      } else {
        const reject = this.rejectFuncs.get(data.id);
        if (reject) {
          reject(data.error ?? '');
          this.pending.delete(data.id);
          this.rejectFuncs.delete(data.id);
        }
      }
    };

    this.workerInstance.onexit = (code) => {
      this.pending.clear();
      this.rejectFuncs.forEach(reject => reject('Worker exited'));
      this.rejectFuncs.clear();
    };
  }

  // 不同类型的任务复用同一个Worker，通过type分发
  execute(type: string, payload: string): Promise<string> {
    const id = ++this.taskCounter;
    return new Promise<string>((resolve, reject) => {
      if (this.workerInstance) {
        this.pending.set(id, resolve);
        this.rejectFuncs.set(id, reject);
        const message: WorkerMessage = { id, type, payload };
        this.workerInstance.postMessage(message);
      } else {
        reject('Worker is null');
      }
    });
  }

  destroy(): void {
    if (this.workerInstance) {
      this.workerInstance.terminate();
      this.workerInstance = null;
    }
  }
}

// 全局单例，通过该管理类复用单个Worker处理可串行的多类任务(需独立并行的任务应由单独的Worker处理)
const dispatcher: WorkerManager = new WorkerManager();

async function executeDemo() {
  try {
    let result = await dispatcher.execute('logReport', 'payload');
    console.info(`Execute result: ${result}`);
  } catch (e) {
    console.error(`Execute error: ${e}`);
  }
}
executeDemo();
```

<!-- @[worker_dispatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/ApplicationMultithreading/entry/src/main/ets/workers/Dispatcher.ets) -->

``` TypeScript
// workers/Dispatcher.ets
import { MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';

interface WorkerMessage {
  id: number;
  type: string;
  payload: string;
}

interface WorkerResult {
  id: number;
  success: boolean;
  result?: string;
  error?: string;
}

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (e: MessageEvents) => {
  const data = e.data as WorkerMessage;
  try {
    let result: string = '';
    // 根据type字段将消息分发到对应的处理逻辑，多类任务串行复用同一个Worker
    if (data.type === 'logReport') {
      result = logReport(data.payload);
    } else if (data.type === 'filePreprocess') {
      result = filePreprocess(data.payload);
    }
    const message: WorkerResult = { id: data.id, success: true, result: result };
    workerPort.postMessage(message);
  } catch (error) {
    const message: WorkerResult = { id: data.id, success: false, error: error.message };
    workerPort.postMessage(message);
  }
};

function logReport(payload: string): string {
  // 日志上报逻辑
  return 'logReport done';
}

function filePreprocess(payload: string): string {
  // 文件预处理逻辑
  return 'filePreprocess done';
}
```
