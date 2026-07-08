# TaskPool任务与宿主线程通信 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)任务通常通过返回值向宿主线程返回最终结果。如果任务执行过程中还需要持续通知进度、分段返回数据或上报状态，可以使用Task.sendData发送中间数据，并在宿主线程通过onReceiveData注册回调接收。

ArkTS-Sta中Task.sendData发送的数据默认按共享对象引用传递，不需要Structured Clone，也不需要Sendable对象。若发送的是可变对象，宿主线程和TaskPool任务线程需要自行保证并发访问安全。

下面以图片数据加载进度通知为例说明。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 实现接收消息的方法

```ts
// ArkTS-Sta示例
// TaskSendDataUsage.ets
export function notice(data: int): void {
  console.info("TaskPool task loaded pictures: " + data); // TaskPool task loaded pictures: 6（首次回调，后续每次递增6）
}
```

## 在TaskPool任务中发送数据

任务函数可以调用taskpool.Task.sendData向宿主线程发送中间数据。sendData只能在TaskPool任务中调用，并且调用前需要在宿主线程注册onReceiveData回调。

```ts
// ArkTS-Sta示例
// IconItemSource.ets
export class IconItemSource {
  image: string = "";
  text: string = "";

  constructor(image: string = "", text: string = "") {
    this.image = image;
    this.text = text;
  }
}
```

```ts
// ArkTS-Sta示例
// TaskSendDataUsage.ets
import { IconItemSource } from "./IconItemSource";

export function loadPictureSendData(count: int): Array<IconItemSource> {
  let iconItemSourceList: Array<IconItemSource> = [];

  for (let index = 0; index < count; index++) {
    let numStart: int = index * 6;
    iconItemSourceList.push(new IconItemSource("$media:startIcon", "item" + (numStart + 1)));
    iconItemSourceList.push(new IconItemSource("$media:background", "item" + (numStart + 2)));
    iconItemSourceList.push(new IconItemSource("$media:foreground", "item" + (numStart + 3)));
    iconItemSourceList.push(new IconItemSource("$media:startIcon", "item" + (numStart + 4)));
    iconItemSourceList.push(new IconItemSource("$media:background", "item" + (numStart + 5)));
    iconItemSourceList.push(new IconItemSource("$media:foreground", "item" + (numStart + 6)));

    taskpool.Task.sendData(iconItemSourceList.length);
  }

  return iconItemSourceList;
}
```

## 在宿主线程接收数据

通过taskpool.Task.onReceiveData注册回调后，TaskPool任务调用Task.sendData发送的数据会回调到注册回调的宿主线程。

```ts
// ArkTS-Sta示例
import { IconItemSource } from "./IconItemSource";
import { loadPictureSendData, notice } from "./TaskSendDataUsage";

async function executeTaskWithProgress(): Promise<void> {
  let loadPictureTask: taskpool.Task = new taskpool.Task(loadPictureSendData, 30);
  loadPictureTask.onReceiveData(notice);

  let result: Array<IconItemSource> =
    (await taskpool.execute(loadPictureTask)) as Array<IconItemSource>;

  console.info("final picture count: " + result.length); // final picture count: 180
}
```

sendData支持传递多个参数，回调函数的参数列表需要与发送的数据匹配。

```ts
// ArkTS-Sta示例
function reportProgress(total: int): int {
  taskpool.Task.sendData("loading", total);
  return total;
}

async function receiveMultipleArgs(): Promise<void> {
  let task: taskpool.Task = new taskpool.Task(reportProgress, 100);
  task.onReceiveData((state: string, total: int): void => {
    console.info(state + ": " + total); // loading: 100
  });

  await taskpool.execute(task);
}
```

## 使用约束

- Task.sendData只能在TaskPool任务中调用。在非TaskPool任务中调用会抛出异常。
- 调用Task.sendData前必须通过onReceiveData注册回调，否则会抛出异常。
- onReceiveData不传参数时，会清除当前Task上的接收回调。
- 同一个Task重复注册onReceiveData时，后注册的回调会覆盖之前的回调。
- 发送对象、数组或ArrayBuffer时，ArkTS-Sta默认传递共享引用。多线程读写可变数据时，需要使用同步机制。

更多TaskPool接口说明请参见[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)。
