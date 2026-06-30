# 使用TaskPool执行独立的耗时任务 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

独立耗时任务是指任务执行过程不依赖宿主线程上下文，任务完成后只需要将最终结果返回给宿主线程。ArkTS-Sta中可以使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)执行这类任务，任务函数在TaskPool工作线程中运行，执行结果通过Promise返回。

ArkTS-Sta中taskpool为内置能力，不需要从@kit.ArkTS导入；普通函数可以作为TaskPool任务函数，不需要使用@Concurrent装饰。

下面通过加载图标列表数据说明。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 实现任务数据类型

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

## 实现耗时任务

```ts
// ArkTS-Sta示例
// IndependentTask.ets
import { IconItemSource } from "./IconItemSource";

export function loadPicture(count: int): Array<IconItemSource> {
  let iconItemSourceList: Array<IconItemSource> = [];

  for (let index = 0; index < count; index++) {
    let numStart: int = index * 6;
    iconItemSourceList.push(new IconItemSource("$media:startIcon", "item" + (numStart + 1)));
    iconItemSourceList.push(new IconItemSource("$media:background", "item" + (numStart + 2)));
    iconItemSourceList.push(new IconItemSource("$media:foreground", "item" + (numStart + 3)));
    iconItemSourceList.push(new IconItemSource("$media:startIcon", "item" + (numStart + 4)));
    iconItemSourceList.push(new IconItemSource("$media:background", "item" + (numStart + 5)));
    iconItemSourceList.push(new IconItemSource("$media:foreground", "item" + (numStart + 6)));
  }

  return iconItemSourceList;
}
```

## 执行TaskPool任务

可以直接将函数传给taskpool.execute，也可以先创建taskpool.Task对象后再执行。任务返回值通过Promise异步返回给宿主线程。

```ts
// ArkTS-Sta示例
import { IconItemSource } from "./IconItemSource";
import { loadPicture } from "./IndependentTask";

async function executeIndependentTask(): Promise<void> {
  let loadPictureTask: taskpool.Task = new taskpool.Task(loadPicture, 30);
  let result: Array<IconItemSource> =
    (await taskpool.execute(loadPictureTask)) as Array<IconItemSource>;

  console.info("The length of iconItemSourceList is " + result.length); // The length of iconItemSourceList is 180
}
```

也可以直接提交函数和参数。

```ts
// ArkTS-Sta示例
async function executeFunction(): Promise<void> {
  let result: Array<IconItemSource> =
    (await taskpool.execute(loadPicture, 30)) as Array<IconItemSource>;

  console.info("The length of iconItemSourceList is " + result.length); // The length of iconItemSourceList is 180
}
```

## 使用建议

- 独立耗时任务应尽量减少对宿主线程状态的依赖，只通过参数传入任务所需数据，通过返回值返回最终结果。
- ArkTS-Sta跨线程传递对象时默认共享对象引用。如果任务需要独立快照，应在提交任务前显式拷贝数据。
- TaskPool适合短时、可拆分或批量后台任务。需要固定线程或长期驻留时，建议使用[EAWorker简介 (ArkTS-Sta)](eaworker-introduction.md)。
- 任务函数访问共享可变对象时，需要使用锁、原子类型或并发容器保证并发安全。
