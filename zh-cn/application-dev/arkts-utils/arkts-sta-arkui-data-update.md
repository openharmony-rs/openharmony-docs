# ArkUI数据更新场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

当网络下载、本地计算或数据库查询等耗时操作需要将结果展示到界面时，可以使用[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)在后台线程处理数据，并在宿主线程中更新ArkUI状态变量。ArkTS-Sta中对象默认可跨线程共享，但ArkUI状态对象和UIUtils.makeObserved返回的可观察数据应在UI线程侧使用，不建议直接传入TaskPool任务中修改。

动态ArkTS文档中的示例通常使用@Sendable对象配合makeObserved更新ArkUI数据。ArkTS-Sta不需要@Sendable表达共享语义，且静态makeObserved主要支持Array、Map、Set、Date和interface字面量。静态场景中建议让后台任务返回普通数据对象，在宿主线程重新执行makeObserved，再整体替换UI状态。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。
> - 本文示例使用UIUtils.makeObserved包装interface字面量数据。若业务数据模型是可控的class类型，也可以使用[ObservedV2和Trace](../ui/state-management-static/arkts-static-new-observedV2-and-trace.md)定义UI层ViewModel，但后台任务仍建议只返回普通数据结果，由宿主线程更新UI状态。

## 定义数据类型

使用interface定义需要展示的数据结构，并提供创建数据对象的方法。后台线程返回的是普通对象，不包含ArkUI可观察代理。

```ts
// ArkTS-Sta示例
// ProfileData.ets
export interface ProfileData {
  name: string;
  age: int;
  gender: int;
  likes: int;
  follow: boolean;
}

export function createProfileData(
  name: string,
  age: int,
  gender: int,
  likes: int,
  follow: boolean
): ProfileData {
  return {
    name: name,
    age: age,
    gender: gender,
    likes: likes,
    follow: follow
  } as ProfileData;
}
```

## 在TaskPool任务中生成数据

TaskPool任务只处理普通数据。不要在任务中访问ArkUI组件，也不要在任务中修改宿主线程持有的可观察对象。

```ts
// ArkTS-Sta示例
// ProfileTask.ets
import { ProfileData, createProfileData } from './ProfileData'

export function threadGetData(name: string): ProfileData {
  console.info("threadGetData, name: " + name); // threadGetData, name: Tom

  return createProfileData(
    name + "-o",
    28,
    1,
    100,
    false
  );
}
```

## 在宿主线程更新ArkUI数据

宿主线程使用UIUtils.makeObserved将普通数据转换为可观察数据。按钮直接修改this.profile.name时，UI可以感知字段变化；TaskPool返回新数据后，需要在宿主线程重新执行makeObserved并整体替换this.profile。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { UIUtils } from '@kit.ArkUI'
import { ProfileData, createProfileData } from './ProfileData'
import { threadGetData } from './ProfileTask'

@Entry
@Component
struct Index {
  @State profile: ProfileData =
    UIUtils.makeObserved(createProfileData("Tom", 20, 1, 1, false)) as ProfileData;
  @State message: string = "ready";

  updateProfileByTask(): void {
    // 仅将普通字段传入TaskPool任务，不直接传入可观察对象。
    let sourceName: string = this.profile.name;
    taskpool.execute(threadGetData, sourceName).then((ret: Any) => {
      let data: ProfileData = ret as ProfileData;

      // TaskPool返回的是普通对象，在宿主线程重新转换为可观察数据。
      this.profile = UIUtils.makeObserved(data) as ProfileData;
      this.message = "updated";
      console.info("profile updated: " + this.profile.name); // profile updated: Tom-o (示例输出)
    });
  }

  build() {
    Column(undefined) {
      Text(this.profile.name).fontSize(20)
      Text("age: " + this.profile.age).fontSize(20)
      Text("likes: " + this.profile.likes).fontSize(20)
      Text(this.message).fontSize(20)

      Button("change name")
        .onClick((e: ClickEvent) => {
          // profile由makeObserved转换，直接修改字段可以触发UI刷新。
          this.profile.name += "0";
        })

      Button("task")
        .onClick((e: ClickEvent) => {
          this.updateProfileByTask();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用ObservedV2和Trace更新class对象

如果UI层数据模型是开发者可控的class，可以使用@ObservedV2和@Trace让类属性具备观测能力。后台任务仍然返回普通DTO对象，宿主线程负责把DTO字段写入可观察ViewModel。

```ts
// ArkTS-Sta示例
// ProfileViewModel.ets
import { ObservedV2, Trace } from '@kit.ArkUI'
import { ProfileData } from './ProfileData'

@ObservedV2
export class ProfileViewModel {
  @Trace name: string = "Tom";
  @Trace age: int = 20;
  @Trace likes: int = 1;

  update(data: ProfileData): void {
    this.name = data.name;
    this.age = data.age;
    this.likes = data.likes;
  }
}
```

使用ProfileViewModel时，宿主线程在TaskPool任务完成后调用update更新被@Trace标记的字段，即可触发使用这些字段的UI组件刷新。以下示例使用ComponentV2展示ProfileViewModel中的字段，并在TaskPool返回后调用update更新界面。

```ts
// ArkTS-Sta示例
// Index.ets
import { Button, ClickEvent, Column, ComponentV2, Entry, Local, Text } from '@kit.ArkUI'
import { ProfileData } from './ProfileData'
import { threadGetData } from './ProfileTask'
import { ProfileViewModel } from './ProfileViewModel'

@Entry
@ComponentV2
struct Index {
  profileViewModel: ProfileViewModel = new ProfileViewModel();
  @Local message: string = "ready";

  updateViewModelByTask(): void {
    let sourceName: string = this.profileViewModel.name;
    taskpool.execute(threadGetData, sourceName).then((ret: Any) => {
      let data: ProfileData = ret as ProfileData;
      this.profileViewModel.update(data);
      this.message = "updated";
      console.info("view model updated: " + this.profileViewModel.name); // view model updated: Tom-o
    });
  }

  build() {
    Column() {
      Text(this.profileViewModel.name).fontSize(20)
      Text("age: " + this.profileViewModel.age).fontSize(20)
      Text("likes: " + this.profileViewModel.likes).fontSize(20)
      Text(this.message).fontSize(20)
      Button("update view model")
        .onClick((e: ClickEvent) => {
          this.updateViewModelByTask();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用建议

- 后台线程只负责生成、查询或处理普通数据，不直接操作ArkUI组件和UI状态变量。
- UIUtils.makeObserved返回的可观察数据建议只在宿主线程使用。需要传给TaskPool时，应传递普通字段、普通对象副本，或重新构造普通DTO对象。
- ArkTS-Sta静态makeObserved主要用于Array、Map、Set、Date和interface字面量。普通class实例需要属性级观测时，优先使用@ObservedV2和@Trace。
- TaskPool返回新数据后，应在宿主线程整体替换状态变量，或调用UI层ViewModel的更新方法修改被观测字段。
- 多个线程共享同一份可变数据时，需要使用锁、原子类型或并发容器保护。UI刷新和共享数据同步是两个问题，不应混用。
