# Overview of Multithreaded Concurrency

Multithreaded concurrency refers to the execution of multiple threads simultaneously within a single program, enhancing performance and resource utilization through parallel or alternating task execution. In the development of ArkTS applications, there are many service scenarios that require multithreaded concurrency. These scenarios can be categorized into three main types. For more details, [Multithreaded Development Practice Cases](batch-database-operations-guide.md).

- Service logic that involves heavy computation or multiple I/O read/write operations, which require extended execution time, such as image/video encoding and decoding, compression/decompression, and database operations.

- Service logic that includes listening for or periodically collecting data, which requires continuous operation over extended periods, such as periodically collecting sensor data.

- Service logic that follows the main thread's lifecycle or is bound to the main thread, such as in gaming platforms.


Concurrency models are used to implement concurrent tasks in different usage scenarios. Common concurrency models include those based on shared memory and those based on message communication.

The actor model is a typical example of a concurrency model based on message communication. It allows developers to avoid the complexity of dealing with locks and offers high concurrency, making it widely used.

Currently, ArkTS provides two concurrency capabilities: TaskPool and Worker, both of which are implemented based on the actor model.

For details about the comparison between the actor model and the shared memory concurrency model, see [Multithreaded Concurrency Models](#multithreaded-concurrency-models).

## Multithreaded Concurrency Models

Shared memory concurrency model: In this model, multiple threads execute tasks simultaneously. These threads rely on the same memory resource and have access permissions. Before accessing memory, threads must compete for and lock the memory's usage rights. Threads that fail to acquire the lock must wait for other threads to release the lock before proceeding.

Actor model: In this model, each thread is an independent actor, which has its own memory. Actors trigger the behavior of each other through message transfer. They cannot directly access the memory space of each other. 

Different from the shared memory concurrency model, the actor model provides independent memory space for each thread. As such, it avoids memory preemption and enhances development efficiency.

In the actor model, tasks and task results are transmitted through the inter-thread communication.

This topic uses the classic producer-consumer problem as an example to illustrate the differences between these two models in solving specific problems.

### Shared Memory Model

The following figure illustrates how to solve the producer-consumer issue using the shared memory model.

![image_0000002001497485](figures/image_0000002001497485.png)

To prevent problems like dirty reads and writes caused by simultaneous access, only one producer or consumer can access a shared memory container at any given moment. This means that producers and consumers need to compete for the lock of the container. Once a role secures the lock, others must wait until the lock is released before they can attempt to access the container.

```ts
// The pseudocode is used here to help you understand the differences between the shared memory model and the actor model.
class Queue {
  // ...
  push(value: number) {
  }

  empty(): boolean {
    // ...
    return true;
  }

  pop(value: number): number {
    // ...
    return value;
  }
}

class Mutex {
  // ...
  lock(): boolean {
    // ...
    return true;
  }

  unlock() {
  }
}

class BufferQueue {
  queue: Queue = new Queue();
  mutex: Mutex = new Mutex();

  add(value: number) {
    // Attempt to acquire the lock.
    if (this.mutex.lock()) {
      this.queue.push(value);
      this.mutex.unlock();
    }
  }

  take(value: number): number {
    let res: number = 0;
    // Attempt to acquire the lock.
    if (this.mutex.lock()) {
      if (this.queue.empty()) {
        res = 1;
        return res;
      }
      let num: number = this.queue.pop(value);
      this.mutex.unlock();
      res = num;
    }
    return res;
  }
}

// Construct a globally shared memory buffer.
let g_bufferQueue = new BufferQueue();

class Producer {
  constructor() {
  }

  run() {
    let value = Math.random();
    // Access to the bufferQueue object across threads.
    g_bufferQueue.add(value);
  }
}

class ConsumerTest {
  constructor() {
  }

  run() {
    // Access to the bufferQueue object across threads.
    let num = 123;
    let res = g_bufferQueue.take(num);
    if (res != null) {
      // Add consumption logic here.
    }
  }
}

function Main(): void {
  let consumer: ConsumerTest = new ConsumerTest();
  let producer: Producer = new Producer();
  let threadNum: number = 10;
  for (let i = 0; i < threadNum; i++) {
    // The following pseudocode simulates the startup of multiple threads to execute production tasks.
    // let thread = new Thread();
    // thread.run(producer.run());
    // consumer.run();
  }
}
```


### Actor Model

The following figure demonstrates how to use the TaskPool concurrency capability based on the actor model to solve the producer-consumer issue.

![image_0000001964697544](figures/image_0000001964697544.png)

In the actor model, different roles operate independently without sharing memory. Each role, such as the producer thread and the UI thread, runs within its own virtual machine instance, each with its own exclusive memory space. After generating a result, the producer sends the result to the UI thread through serialization. The UI thread processes the result and then sends a new task to the producer thread.

```ts
import { taskpool } from '@kit.ArkTS';

// Cross-thread concurrent tasks
@Concurrent
async function produce(): Promise<number> {
  // Add production logic here.
  console.info('producing...');
  return Math.random();
}

class Consumer {
  public consume(value: Object) {
    // Add consumption logic here.
    console.info('consuming value: ' + value);
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('start')
        }.onClick(() => {
          let produceTask: taskpool.Task = new taskpool.Task(produce);
          let consumer: Consumer = new Consumer();
          for (let index: number = 0; index < 10; index++) {
            // Execute the asynchronous concurrent production task.
            taskpool.execute(produceTask).then((res: Object) => {
              consumer.consume(res);
            }).catch((e: Error) => {
              console.error(e.message);
            })
          }
        })
        .width('20%')
        .height('20%')
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
<!-- @[actor_model](https://gitee.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/MultithreadedConcurrency/MultiThreadConcurrencyOverview/entry/src/main/ets/pages/Index.ets) -->

You can also wait until all the producer's tasks are complete, and then pass the results to the UI thread through serialization. After the UI thread receives the results, the consumer can handle them all together.

```ts
import { taskpool } from '@kit.ArkTS';

// Cross-thread concurrent tasks
@Concurrent
async function produce(): Promise<number> {
  // Add production logic here.
  console.info('producing...');
  return Math.random();
}

class Consumer {
  public consume(value: Object) {
    // Add consumption logic here.
    console.info('consuming value: ' + value);
  }
}

@Entry
@Component
struct Index {
  @State message: string = 'Hello World'

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('start')
        }.onClick(async () => {
          let dataArray = new Array<number>();
          let produceTask: taskpool.Task = new taskpool.Task(produce);
          let consumer: Consumer = new Consumer();
          for (let index: number = 0; index < 10; index++) {
            // Execute the asynchronous concurrent production task.
            let result = await taskpool.execute(produceTask) as number;
            dataArray.push(result);
          }
          for (let index: number = 0; index < dataArray.length; index++) {
            consumer.consume(dataArray[index]);
          }
        })
        .width('20%')
        .height('20%')
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## TaskPool and Worker

ArkTS provides two concurrency capabilities for you to choose from: TaskPool and Worker. For details about their operation mechanisms and precautions, see [TaskPool](taskpool-introduction.md) and [Worker](worker-introduction.md). For details about their differences in the implementation features and use cases, see [Comparison Between TaskPool and Worker](taskpool-vs-worker.md).
