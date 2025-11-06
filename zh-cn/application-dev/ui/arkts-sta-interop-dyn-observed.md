# ArkTS-Sta与ArkTS-Dyn动态数据和@Observed数据的互操作

从API version 22起，ArkTS-Dyn动态数据与@Observed装饰的数据之间的交互操作可用于UI组件开发和数据绑定的场景，建议提前阅读: [ArkTS-Sta互操作概述](../quick-start/arkts-interop-overview.md)了解互操作能力框架。

完整示例结构如下：

```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── dynamic/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets

```

ArkUI的组件间数据交互能力是支持父子组件、兄弟组件、跨层级组件之间传递、同步数据的机制。从API version 22开始，支持在ArkTS-Sta的UI组件中渲染和响应ArkTS-Dyn的动态数据和@Observed数据的变化。

以下代码示例展示了如何在ArkTS-Sta组件中使用动态数据和@Observed数据。

- 创建ArkTS-Dyn子模块`dynamic`，在`src/main/ets/MainPage.ets`目录创建并导出动态@Observed数据。

  ```TypeScript
  // dynamic/src/main/ets/MainPage.ets

  @Observed
  export class MyClassA {
    @Track name: string = 'text: x';
    message: string = 'text: x';
  }
  ```

- 在主模块`entry`的`oh-package.json5`文件的`dependencies`字段中添加子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
    "dynamic": "file:../dynamic",
  }
  ```

- 在ArkTS-Sta主模块中使用import语句导入ArkTS-Dyn组件。

  ```TypeScript
  'use static'
  // entry/src/main/ets/pages/Index.ets

  import { Entry, Component, Row, Column, Scroll, Button, ClickEvent, Text, ColumnOptions, RowOptions, Color } from '@ohos.arkui.component';
  import { State} from '@ohos.arkui.stateManagement';
  // 引用ArkTS-Dyn动态@Observed装饰的数据
  import { MyClassA } from 'dynamic';

  @Entry
  @Component
  export struct Index {
    @State state: MyClassA = new MyClassA();

    build() {
      Scroll() {
        Row() {
          Column({ space: 20 } as ColumnOptions) {
            // 在ArkTS-Sta中使用动态@Observed装饰的数据
            Text(this.state.name)
              .height('10%')
              .backgroundColor(Color.Pink)
            Row({ space: 5 } as RowOptions) {
              // 单独为动态@Observed装饰的类中的某一个成员赋值
              Button('Member Assignment')
                .layoutWeight(1)
                .onClick((event: ClickEvent)=> {
                  this.state.name = 'state: x';
                })
              // 创建新对象整体为动态@Observed装饰的类中的成员赋值
              Button('Overall Assignment')
                .layoutWeight(1)
                .onClick((event: ClickEvent)=> {
                  let data = new MyClassA();
                  data.name = 'state: Hello';
                  this.state = data;
                })
              // 多线程中为动态@Observed装饰的数据中的成员赋值
              Button('Multithreading')
                .layoutWeight(1)
                .onClick((event: ClickEvent)=> {
                  const task = () =>{
                    let data = new MyClassA();
                    data.name = 'world';
                  }
                  taskpool.execute(task)
                })
            }
            .width('80%')
          }
          .width('100%')
        }
      }
      .height('100%')
    }
  }
  ```