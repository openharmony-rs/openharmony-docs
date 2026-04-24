# 自定义组件生命周期
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @seaside_wu1; @xin11112-->
<!--Designer: @chenbenzhi-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

## 概述

已有的[自定义组件生命周期](../state-management/arkts-page-custom-components-lifecycle.md)回调函数触发只取决于事件的触发，在某些特定的情况下，会出现自定义组件生命周期回调函数的触发顺序不符合预期。比如：[aboutToDisappear在特定情况下会误调用aboutToAppear、组件未展开被复用时，会误调用aboutToReuse](#生命周期回调函数的区别)。新的自定义组件生命周期回调函数受[状态机](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#customcomponentlifecyclestate)限制，生命周期回调函数调用时机符合预期。

自定义组件生命周期，即用[@Component](../state-management/arkts-create-custom-components.md#component)或[@ComponentV2](../state-management/arkts-create-custom-components.md#componentv2)装饰的自定义组件的生命周期，从API version 24开始，提供以下生命周期装饰器：

- [\@ComponentInit](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentinit)：\@ComponentInit装饰的函数在自定义组件即将构造完毕时执行。可以在此函数中注册监听和修改变量。

- [\@ComponentAppear](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentappear)：组件即将出现时回调该装饰器装饰的函数，具体时机为在创建自定义组件的新实例后，在执行其build函数之前执行。

- [\@ComponentBuilt](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentbuilt)：在组件首次渲染触发的build函数执行完成后，回调该装饰器装饰的函数，后续组件重新渲染将不再回调该函数。开发者可以在此阶段实现数据上报等不影响实际UI的功能。

- [\@ComponentDisappear](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentdisappear)：该装饰器装饰的函数在自定义组件析构销毁之前执行。不建议在\@ComponentDisappear装饰的函数中改变状态变量，特别是@Link变量的修改可能会导致应用程序行为不稳定。

- [\@ComponentReuse](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentreuse)：当可复用的自定义组件从缓存中重新添加到节点树时调用该装饰器装饰的函数，以接收组件的构造入参。最后，\@ComponentReuse装饰的函数会递归遍历所有子组件，对每个完成复用的组件调用\@ComponentReuse装饰的函数。

- [\@ComponentRecycle](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentrecycle)：当组件被回收后触发，先执行应用程序中定义的必要回收操作，完成回收后调用该装饰器装饰的函数。最后，\@ComponentRecycle装饰的函数会递归遍历所有子组件，对每个完成回收的组件调用\@ComponentRecycle装饰的函数。

自定义组件生命周期受状态机限制，流程如下图所示。

![custom-component-lifecycle-demo1](../state-management/figures/customcomponent-lifecycle-new-state.png)

### 自定义组件的创建和渲染流程

1. 自定义组件的创建：自定义组件的实例由ArkUI框架创建。

2. 初始化自定义组件的成员变量：通过本地默认值或者构造函数传递参数来初始化自定义组件的成员变量，初始化顺序为成员变量的定义顺序。

3. 在首次渲染的时候，执行build函数渲染系统组件，如果子组件为自定义组件，则创建自定义组件的实例。在首次渲染的过程中，框架会记录状态变量和组件的映射关系，当状态变量改变时，驱动其相关的组件刷新。

### 自定义组件的删除

例如if组件的分支改变或ForEach循环渲染中数组的个数改变，组件将被移除：

1. 在删除组件之前，将调用其\@ComponentDisappear装饰的生命周期函数，标记着该节点将要被销毁。ArkUI的节点删除机制是：后端节点直接从组件树上摘下，后端节点被销毁，对前端节点解引用，前端节点已经没有引用时，将被Ark虚拟机垃圾回收。

2. 自定义组件和它的变量将被删除，如果组件有同步的变量（如[@Link](../state-management/arkts-link.md)、[@Prop](../state-management/arkts-prop.md)、[@StorageLink](../state-management/arkts-appstorage.md#storagelink)），将从[同步源](../state-management/arkts-state-management-overview.md)上取消注册。

## 限制条件

- \@ComponentInit、\@ComponentAppear、\@ComponentBuilt、\@ComponentDisappear、\@ComponentReuse和\@ComponentRecycle只能在\@Component或者\@ComponentV2装饰的struct中使用，否则编译会报错。

- \@ComponentInit、\@ComponentAppear、\@ComponentBuilt、\@ComponentDisappear和\@ComponentRecycle装饰的函数不能有入参，否则编译会报错。

- 在\@Component装饰的struct中，\@ComponentReuse装饰的函数可以没有入参或者有一个入参，否则编译会报错。

- 在\@ComponentV2装饰的struct中，\@ComponentReuse装饰的函数不能有入参，否则编译会报错。

- 新增生命周期装饰器不能与状态变量装饰器联合使用。例如，\@ComponentInit、\@ComponentAppear、\@ComponentBuilt、\@ComponentDisappear、\@ComponentReuse和\@ComponentRecycle不能与[\@State](./arkts-static-state.md)、[\@Local](./arkts-static-new-local.md)等装饰器一起使用，否则编译会报错。

- 新增生命周期装饰器建议单独使用，不与其他装饰器联合使用。比如生命周期装饰器和[\@Computed](./arkts-static-new-computed.md)联合使用时，生命周期装饰器不生效。
  ```typescript
  @Computed
  @ComponentAppear
  get sum() {
    return 1 + 2 + 3; // 错误用法，生命周期装饰器装饰get方法不生效
  }
  ```
- 当自定义组件没有使用生命周期装饰器，且没有注册监听，使用[getCurrentState](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#getcurrentstate)查询自定义组件当前生命周期状态时，返回值永远为[CustomComponentLifecycleState.INIT](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#customcomponentlifecyclestate)

## 使用场景

### 自定义组件嵌套使用

通过以下示例，来详细说明自定义组件在嵌套使用时，自定义组件生命周期的调用时序：

```typescript
'use static'

import { hilog } from '@kit.PerformanceAnalysisKit';
import { ComponentAppear, ComponentBuilt, ComponentDisappear, Entry, Component, State, Column, Button, Text } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State show: boolean = true; // 控制Parent的创建和删除
  @State btnColor: string = '#FF007DFF';
  build() {
    Column() {
      // 按下按钮修改show的值，可以控制Parent的创建和删除
      Button('delete Parent And Child')
        .margin(20)
        .backgroundColor(this.btnColor)
        .onClick(() => {
          this.show = !this.show;
        })
      if (this.show) {
        Parent()
      }
    }
  }
}
@Component
struct Parent {
  @State showChild: boolean = true;
  @State btnColor: string = '#FF007DFF';
  // 组件生命周期ComponentAppear，在Parent创建实例后，执行build函数之前回调myAppear
  @ComponentAppear
  myAppear() {
    hilog.info(0x0000, 'testTag', 'Parent myAppear');
  }
  // 组件生命周期ComponentBuilt，在Parent首次渲染触发的build函数执行完成之后回调myBuilt
  @ComponentBuilt
  myBuilt() {
    hilog.info(0x0000, 'testTag', 'Parent myBuilt');
  }
  // 组件生命周期ComponentDisappear，在Parent析构销毁之前回调myDisappear
  @ComponentDisappear
  myDisappear() {
    hilog.info(0x0000, 'testTag', 'Parent myDisappear');
  }

  build() {
    Column() {
      // this.showChild为true，创建Child子组件，执行Child myAppear
      if (this.showChild) {
        Child()
      }
      Button('delete Child')
        .margin(20)
        .backgroundColor(this.btnColor)
        .onClick(() => {
          // 更改this.showChild为false，删除Child子组件，执行Child myDisappear
          // 更改this.showChild为true，添加Child子组件，执行Child myAppear
          this.showChild = !this.showChild;
        })
    }
  }
}

@Component
struct Child {
  @State title: string = 'Hello World';
  // 组件生命周期ComponentDisappear，在Child析构销毁之前回调myDisappear
  @ComponentDisappear
  myDisappear() {
    hilog.info(0x0000, 'testTag', 'Child myDisappear');
  }
  // 组件生命周期ComponentBuilt，在Child首次渲染触发的build函数执行完成之后回调myBuilt
  @ComponentBuilt
  myBuilt() {
    hilog.info(0x0000, 'testTag', 'Child myBuilt');
  }
  // 组件生命周期ComponentAppear，在Child创建实例后，执行build函数之前回调myAppear
  @ComponentAppear
  myAppear() {
    hilog.info(0x0000, 'testTag', 'Child myAppear');
  }

  build() {
    Text(this.title)
      .fontSize(50)
      .margin(20)
      .onClick(() => {
        this.title = 'Hello ArkUI';
      })
  }
}
```

以上示例中，Index页面包含两个自定义组件，一个是Parent，一个是Child，Parent及其子组件Child分别声明了各自的自定义组件生命周期装饰器装饰的函数（myAppear / myBuilt / myDisappear）。

- 应用冷启动的初始化流程为：Parent myAppear --&gt; Parent build --&gt; Parent myBuilt --&gt; Child myAppear --&gt; Child build --&gt; Child myBuilt。此处体现了自定义组件懒展开特性，即Parent执行完myBuilt之后才会执行Child组件的myAppear。日志输出信息如下：

   ```text
   Parent myAppear
   Parent myBuilt
   Child myAppear
   Child myBuilt
   ```

- 点击Button按钮，更改showChild为false，删除Child组件，执行Child myDisappear函数。

- 如果点击Button按钮，更改show为false，或者直接退出应用，则会触发以下生命周期：Parent myDisappear --&gt; Child myDisappear，此处体现了自定义组件删除顺序也是从父到子。日志输出信息如下：

   ```text
   Parent myDisappear
   Child myDisappear
   ```

- 最小化应用或者应用进入后台，当前Index页面未被销毁，所以并不会执行组件的myDisappear。

- 如果showChild的默认值为false，则应用冷启动的初始化流程为：Parent myAppear --&gt; Parent build --&gt; Parent myBuilt。日志输出信息如下：

   ```text
   Parent myAppear
   Parent myBuilt
   ```
- 如果showChild的默认值为false，此时点击Button按钮更改show为false或者直接退出应用，则只执行Parent myDisappear函数。

- 如果showChild的默认值为false，此时点击Button按钮，更改showChild为true，添加Child组件，添加流程为：Child myAppear --&gt; Child build --&gt; Child myBuilt。日志输出信息如下：

   ```text
   Child myAppear
   Child myBuilt
   ```
当showChild为默认值true时，该示例的生命周期流程图如下所示：

![custom-component-lifecycle-demo2](../state-management/figures/custom-component-lifecycle-nest.png)

### 自定义组件回收复用

通过以下示例，来详细说明自定义组件在使用时，回收复用的生命周期调用时序：

```typescript
'use static'

import { ComponentInit, ComponentAppear, ComponentBuilt, ComponentDisappear, ComponentReuse, ComponentRecycle, Entry, Component, State, Column, Button, Reusable, Text, ReuseObject } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export class Message {
  value: string | undefined;
  constructor(value: string) {
    this.value = value;
  }
}
@Entry
@Component
struct Index {
  @State switchReuse: boolean = true;

  build() {
    Column() {
      Button('Hello')
        .fontSize(30)
        .onClick(() => {
          this.switchReuse = !this.switchReuse;
        })
      // 通过改变switchReuse，实现Child的回收和复用
      // 更改this.switchReuse为false，回收Child子组件，执行Child myRecycle
      // 更改this.switchReuse为true，复用Child子组件，执行Child myReuse
      if (this.switchReuse) {
        // 如果只有一个复用的组件，可以不用设置reuseId。
        Child({ message: new Message('Child') })
      }
    }
    .height('100%')
    .width('100%')
  }
}

@Reusable
@Component
struct Child {
  @State message: Message = new Message('Child');
  @State label: string = 'HelloWorld';
  @State switchReuse: boolean = true;
  // 组件生命周期ComponentInit，在Child初始化执行完成之后回调myInit
  @ComponentInit
  myInit() {
    hilog.info(0x0000, 'testTag', 'Child myInit');
  }
  // 组件生命周期ComponentAppear，在Child创建实例后，执行build函数之前回调myAppear
  @ComponentAppear
  myAppear() {
    this.label = 'myAppear';
    hilog.info(0x0000, 'testTag', 'Child myAppear');
  }
  // 组件生命周期ComponentBuilt，在Child首次渲染触发的build函数执行完成之后回调myBuilt
  @ComponentBuilt
  myBuilt() {
    this.label = 'myBuilt';
    hilog.info(0x0000, 'testTag', 'Child myBuilt');
  }
  // 组件生命周期ComponentRecycle，在Child触发回收时回调myRecycle
  @ComponentRecycle
  myRecycle() {
    this.label = 'myRecycle';
    hilog.info(0x0000, 'testTag', 'Child myRecycle');
  }
  // 组件生命周期ComponentDisappear，在Child析构销毁之前回调myDisappear
  @ComponentDisappear
  myDisappear() {
    this.label = 'myDisappear';
    hilog.info(0x0000, 'testTag', 'Child myDisappear');
  }
  // 组件生命周期ComponentReuse，在Child触发复用时回调myReuse
  @ComponentReuse
  myReuse(params?: ReuseObject) {
    this.label = 'myReuse';
    hilog.info(0x0000, 'testTag', 'Child myReuse');
  }

  build() {
    Column() {
      Text(this.message.value)
        .fontSize(30)
      Button('Hello')
        .fontSize(30)
        .onClick(() => {
          this.switchReuse = !this.switchReuse;
        })
      if (this.switchReuse) {
        GrandChild({ message: new Message('GrandChild') })
      }
    }
    .borderWidth(1)
    .height(100)
  }
}

@Reusable
@Component
struct GrandChild {
  @State message: Message = new Message('GrandChild');
  @State label: string = 'HelloWorld';
  @State switchReuse: boolean = true;
  // 组件生命周期ComponentInit，在GrandChild初始化执行完成之后回调myInit
  @ComponentInit
  myInit() {
    hilog.info(0x0000, 'testTag', 'GrandChild myInit');
  }
  // 组件生命周期ComponentAppear，在GrandChild创建实例后，执行build函数之前回调myAppear
  @ComponentAppear
  myAppear() {
    this.label = 'myAppear';
    hilog.info(0x0000, 'testTag', 'GrandChild myAppear');
  }
  // 组件生命周期ComponentBuilt，在GrandChild首次渲染触发的build函数执行完成之后回调myBuilt
  @ComponentBuilt
  myBuilt() {
    this.label = 'myBuilt';
    hilog.info(0x0000, 'testTag', 'GrandChild myBuilt');
  }
  // 组件生命周期ComponentRecycle，在GrandChild触发回收时回调myRecycle
  @ComponentRecycle
  myRecycle() {
    this.label = 'myRecycle';
    hilog.info(0x0000, 'testTag', 'GrandChild myRecycle');
  }
  // 组件生命周期ComponentDisappear，在GrandChild析构销毁之前回调myDisappear
  @ComponentDisappear
  myDisappear() {
    this.label = 'myDisappear';
    hilog.info(0x0000, 'testTag', 'GrandChild myDisappear');
  }
  // 组件生命周期ComponentReuse，在GrandChild触发复用时回调myReuse
  @ComponentReuse
  myReuse(params?: ReuseObject) {
    this.label = 'myReuse';
    hilog.info(0x0000, 'testTag', 'GrandChild myReuse');
  }

  build() {
    Column() {
      Text(this.message.value)
        .fontSize(30)
    }
    .borderWidth(1)
    .height(100)
  }
}
```

以上示例中，Index页面包含自定义组件Child，Child组件包含自定义组件GrandChild。Child和GrandChild分别声明了各自的自定义组件生命周期装饰器装饰的函数（myInit / myAppear / myBuilt / myRecycle / myReuse / myDisappear）。

- 应用冷启动的初始化流程为：Child myInit --&gt; Child myAppear --&gt; GrandChild myInit --&gt; Child myBuilt --&gt; GrandChild myAppear --&gt; GrandChild myBuilt。此处体现了自定义组件懒展开特性，即Child执行完myBuilt之后才会执行GrandChild组件的myAppear。日志输出信息如下：

   ```text
   Child myInit
   Child myAppear
   GrandChild myInit
   Child myBuilt
   GrandChild myAppear
   GrandChild myBuilt
   ```

- 点击Button按钮，更改showChild为false，回收Child组件和GrandChild组件，执行Child和GrandChild的myRecycle函数。

   ```text
   Child myRecycle
   GrandChild myRecycle
   ```

### 自定义组件生命周期的注册监听

[CustomComponentLifecycleObserver](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#customcomponentlifecycleobserver)用于监听自定义组件的生命周期，开发者可以根据自己的需求重写CustomComponentLifecycleObserver中的回调函数。

```typescript
'use static'

import { ComponentInit, ComponentDisappear, UIUtils, CustomComponentLifecycleObserver, CustomComponentLifecycle, Entry, Component, State, Column, Button, FontWeight, Reusable, Text, ReuseObject } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export class Message {
  value: string | undefined;
  constructor(value: string) {
    this.value = value;
  }
}

@Entry
@Component
struct Index {
  @State switchReuse: boolean = true;

  build() {
    Column() {
      Button('Hello')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.switchReuse = !this.switchReuse;
        })
      if (this.switchReuse) {
        // 如果只有一个复用的组件，可以不用设置reuseId。
        Child({ message: new Message('Child') })
      }
    }
    .height('100%')
    .width('100%')
  }
}

@Reusable
@Component
struct Child {
  @State message: Message = new Message('AboutToReuse');
  @State label: string = 'HelloWorld';
  // 组件生命周期ComponentInit，在Child初始化执行完成之后回调myInit
  @ComponentInit
  myInit(): void {
    registerObserver(UIUtils.getLifecycle(this));
  }
  // 组件生命周期ComponentDisappear，在Child析构销毁之前回调myDisappear
  @ComponentDisappear
  myDisappear(): void {
    unRegisterObserver(UIUtils.getLifecycle(this));
  }

  build() {
    Column() {
      Text(this.message.value)
        .fontSize(30)
    }
  }
}

export class MyObserver implements CustomComponentLifecycleObserver {
  // 重写CustomComponentLifecycleObserver中的生命周期事件
  // 被监听的自定义组件创建实例后，执行build函数之前回调aboutToAppear
  aboutToAppear() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToAppear');
  }
  // 被监听的自定义组件首次渲染触发的build函数执行完成之后回调onDidBuild
  onDidBuild() {
    hilog.info(0x0000, 'testTag', 'MyObserver onDidBuild');
  }
  // 被监听的自定义组件触发复用时回调aboutToReuse
  aboutToReuse(params?: ReuseObject) {
    // params存在时，为V1的复用；
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToReuse');
  }
  // 被监听的自定义组件触发回收时回调aboutToRecycle
  aboutToRecycle() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToRecycle');
  }
  // 被监听的自定义组件析构销毁之前回调myDisappear
  aboutToDisappear() {
    hilog.info(0x0000, 'testTag', 'MyObserver aboutToDisappear');
  }
}

// 创建Observer对象
const observer = new MyObserver();
export function registerObserver(lifeCycle: CustomComponentLifecycle) {
  // 向lifeCycle注册监听
  lifeCycle.addObserver(observer);
}
export function unRegisterObserver(lifeCycle: CustomComponentLifecycle) {
  // 向lifeCycle取消注册监听
  lifeCycle.removeObserver(observer);
}
```

在@ComponentDisappear装饰的函数中解除注册监听，所以监听器无法监听到aboutToDisappear。

按两次Hello按钮，然后关闭程序，此时日志输出信息如下：

```text
MyObserver aboutToAppear
MyObserver onDidBuild
MyObserver aboutToRecycle
MyObserver aboutToReuse
```

可以在组件的onAppear和onDisAppear中注册和解除监听。在onAppear中注册监听，此时组件已经处于Appeared状态，所以无法监听组件的aboutToAppear。

```typescript
Column() {
  Text('Hello World')
}
// 在onAppear中注册监听
.onAppear(() => {
  registerObserver(UIUtils.getLifecycle(this));
})
// 在onDisAppear中解除监听
.onDisAppear(() => {
  unRegisterObserver(UIUtils.getLifecycle(this));
})
```

## 生命周期回调函数的区别

### \@ComponentAppear、\@ComponentDisappear与aboutToAppear、aboutToDisappear的区别

自定义组件在INIT状态时，即将转化为APPEARED时，先调用aboutToAppear后调用\@ComponentAppear装饰的函数。

自定义组件在INIT状态、BUILT状态或RECYCLED状态时，即将转化为DISAPPEARED时，先调用\@ComponentDisappear装饰的函数后调用aboutToDisappear。

aboutToAppear是自定义组件build之前执行，aboutToDisappear是自定义组件销毁前执行。但有时自定义组件没有build，就被销毁。为了执行一个完整的生命周期，aboutToDisappear会判断，该组件是否执行了aboutToAppear，如果没有执行便强制触发一次aboutToAppear。\@ComponentAppear装饰的函数和\@ComponentDisappear装饰的函数受状态机约束，\@ComponentDisappear装饰的函数不会误调用\@ComponentAppear装饰的函数。例子如下所示：

```typescript
// Index.ets
'use static'

import { SwiperExample } from './SwiperPage';
import { Entry, Component, State, TabsController, RelativeContainer, Text, Button } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  controller: TabsController = new TabsController();
  @State show: boolean = false;
  @State currentTabIndex: number = 0;

  build() {
    RelativeContainer() {
      Text('start')
        .fontSize(50)
        .fontColor('#000')
        .id('text')
        .onClick(() => {
          // this.show为true，创建SwiperExample；this.show为false，销毁SwiperExample
          this.show = !this.show;
        })
      if (this.show) {
        SwiperExample()
          .id('TableExample')
          .width('100%')
          .height('auto')
        Button('delete')
          .onClick(() => {
            // 此时this.show为true，按下后this.show为false，销毁SwiperExample
            this.show = !this.show;
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

```typescript
// SwiperPage.ets
'use static'

import { ComponentAppear, ComponentDisappear, Component, State, Text, Color, TextAlign, IDataSource, DataChangeListener, Entry, Column, SwiperController, Swiper, ForEach, Row, Button } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Component
export struct SwiperPage {
  @State name: string = 'SwiperPage';
  // SwiperPage创建实例后，执行build函数之前回调aboutToAppear
  aboutToAppear(): void {
    hilog.info(0x0000, 'testTag', 'SwiperPage aboutToAppear %{public}s', this.name);
  }
  // SwiperPage析构销毁之前回调aboutToDisappear
  aboutToDisappear(): void {
    hilog.info(0x0000, 'testTag', 'SwiperPage aboutToDisappear %{public}s', this.name);
  }
  // 组件生命周期ComponentAppear，在SwiperPage创建实例后，执行build函数之前回调myAppear
  @ComponentAppear
  myAppear(): void {
    hilog.info(0x0000, 'testTag', 'SwiperPage myAppear %{public}s', this.name);
  }
  // 组件生命周期ComponentDisappear，在SwiperPage析构销毁之前回调myDisappear
  @ComponentDisappear
  myDisappear(): void {
    hilog.info(0x0000, 'testTag', 'SwiperPage myDisappear %{public}s', this.name);
  }

  build() {
    Text(this.name.toString())
      .width('90%')
      .height(160)
      .fontColor(Color.Black)
      .backgroundColor(0xAFEEEE)
      .textAlign(TextAlign.Center)
      .fontSize(30)
  }
}

// 用于Swiper里数据迭代的数据源
class MyDataSource implements IDataSource<string> {
  list: string[] = [];
  constructor(list: string[]) {
    this.list = list;
  }
  totalCount(): int {
    return this.list.length;
  }
  getData(index: int): string {
    return this.list[index];
  }
  registerDataChangeListener(listener: DataChangeListener): void {}
  unregisterDataChangeListener(listener: DataChangeListener): void {}
}

@Entry
@Component
export struct SwiperExample {
  private swiperController: SwiperController = new SwiperController()
  private data: MyDataSource = new MyDataSource([])
  private list: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11']; // 创建12个SwiperPage
  @State selectedTabIndex: int = 0;
  // 组件生命周期ComponentAppear，在SwiperExample创建实例后，执行build函数之前回调myAppear
  // myAppear实现this.data初始化
  @ComponentAppear
  myAppear(): void {
    this.data = new MyDataSource(this.list);
  }

  build() {
    Column() {
      Swiper(this.swiperController) {
        ForEach(this.data.list, (item: string) => {
          SwiperPage({
            name: item
          })
        })
      }
      .index(this.selectedTabIndex)
      .autoPlay(false)
      .disableSwipe(true)
      .indicator(false)
      .width('100%')
      .cachedCount(2) // 以当前节点为基础，往前缓存两个节点，往后缓存两个节点
      .onChange((index) => {
        this.selectedTabIndex = index;
      })
      Row() {
        Button('showNext')
          .onClick(() => {
            // 切换到下一个SwiperPage
            this.swiperController.showNext();
          })
        Button('showPrevious')
          .onClick(() => {
            // 切换到上一个SwiperPage
            this.swiperController.showPrevious();
          })
      }
      .margin(5)
    }
    .width('100%')
    .margin({ top: 5 })
  }
}
```
启动程序后，先按start按钮，此时只有swipe缓存的五个节点开始执行aboutToAppear和myAppear，非缓存的节点未触发aboutToAppear和myAppear。

日志输出信息如下：

```text
SwiperPage:aboutToAppear 0
SwiperPage:myAppear 0
SwiperPage:aboutToAppear 11
SwiperPage:myAppear 11
SwiperPage:aboutToAppear 1
SwiperPage:myAppear 1
SwiperPage:aboutToAppear 10
SwiperPage:myAppear 10
SwiperPage:aboutToAppear 2
SwiperPage:myAppear 2
```

此时关闭程序，缓存的五个节点正常触发aboutToDisappear，但是非缓存的节点触发aboutToDisappear前，会强制触发aboutToAppear。无论是否是缓存节点，myDisappear不会误触发myAppear。

```text
SwiperPage:myDisappear 0
SwiperPage:aboutToDisappear 0
SwiperPage:myDisappear 1
SwiperPage:aboutToDisappear 1
SwiperPage:myDisappear 2
SwiperPage:aboutToDisappear 2
SwiperPage:aboutToAppear 3
SwiperPage:myDisappear 3
SwiperPage:aboutToDisappear 3
SwiperPage:aboutToAppear 4
SwiperPage:myDisappear 4
SwiperPage:aboutToDisappear 4
...
```

### \@ComponentReuse、\@ComponentRecycle与aboutToReuse、aboutToRecycle的区别

自定义组件在RECYCLED状态时，即将转化为BUILT时，先调用aboutToReuse后调用\@ComponentReuse装饰的函数。

自定义组件在BUILT状态时，即将转化为RECYCLED时，先调用aboutToRecycle后调用\@ComponentRecycle装饰的函数。

```typescript
'use static'

import { ComponentAppear, ComponentBuilt, ComponentReuse, Entry, Component, State, Column, Button, Reusable, Require, PropRef, ReuseObject, Text } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct ReusableTest {
  // 程序开始时，ReusableComp1和ReusableComp2已创建，ReusableComp3并未创建
  @State flag1: boolean = true;
  @State flag2: boolean = false;
  build() {
    Column() {
      // this.flag1为true时，创建ReusableComp1和ReusableComp2
      // this.flag1为false时，删除已创建的ReusableComp1和ReusableComp2
      Button('a')
        .onClick(() => {
          this.flag1 = !this.flag1;
        })
      // this.flag2为true时，创建ReusableComp1和ReusableComp3
      // this.flag2为false时，删除已创建的ReusableComp1和ReusableComp3
      Button('b')
        .onClick(() => {
          this.flag2 = !this.flag2;
        })
      if (this.flag1) {
        ReusableComp1({ flag: true })
      }
      if (this.flag2) {
        ReusableComp1({ flag: false })
      }
    }
  }
}

@Reusable
@Component
struct ReusableComp1 {
  @Require @PropRef flag: boolean = true;
  build() {
    // flag为true时，创建ReusableComp2
    // flag为false时，创建ReusableComp3
    if (this.flag) {
      ReusableComp2()
    } else {
      ReusableComp3()
    }
  }
}

// 可复用的自定义组件ReusableComp2
@Reusable
@Component
struct ReusableComp2 {
  build() {
    Text('A')
  }
}

// 可复用的自定义组件ReusableComp3
@Reusable
@Component
struct ReusableComp3 {
  // ReusableComp3创建实例后，执行build函数之前回调aboutToAppear
  aboutToAppear(): void {
    hilog.info(0x0000, 'testTag', 'ReusableComp3 aboutToAppear');
  }
  // ReusableComp3触发复用时回调aboutToReuse
  aboutToReuse(params: ReuseObject): void {
    hilog.info(0x0000, 'testTag', 'ReusableComp3 aboutToReuse');
  }
  // 组件生命周期ComponentReuse，在ReusableComp3触发复用时回调myReuse
  @ComponentReuse
  myReuse(params: ReuseObject): void {
    hilog.info(0x0000, 'testTag', 'ReusableComp3 myReuse');
  }
  // 组件生命周期ComponentAppear，在ReusableComp3创建实例后，执行build函数之前回调myAppear
  @ComponentAppear
  myAppear(): void {
    hilog.info(0x0000, 'testTag', 'ReusableComp3 myAppear');
  }
  // 组件生命周期ComponentBuilt，在ReusableComp3首次渲染触发的build函数执行完成之后回调myBuilt
  @ComponentBuilt
  myBuilt(): void {
    hilog.info(0x0000, 'testTag', 'ReusableComp3 myBuilt');
  }

  build() {
    Text('B')
  }
}
```

按下a按钮，此时ReusableComp2进入回收状态，再按下b按钮，此时ReusableComp3第一次被创建，此时日志输出信息如下：

```text
ReusableComp3 aboutToReuse
ReusableComp3 aboutToAppear
ReusableComp3 myAppear
ReusableComp3 myBuilt
```

ReusableComp3从未创建过，但按下b按钮后，ReusableComp3的aboutToReuse误调用，同时ReusableComp3的aboutToAppear和myBuilt被调用。而myReuse没有被误调用，这是因为myReuse受状态机约束，当组件不是RECYCLED状态时，不会执行myReuse。
