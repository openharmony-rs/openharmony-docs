# 在ArkTS-Sta中使用ArkTS-Dyn的@Observed和@ObjectLink（嵌套类对象属性变化）

## 概述

ArkUI的组件间数据交互能力是支持父子组件、兄弟组件、跨层级组件之间传递、同步数据的机制。从API version 22开始，支持在ArkTS-Sta的UI组件中渲染和响应ArkTS-Dyn的动态数据和[@Observed](../ui/state-management/arkts-observed-and-objectlink.md)装饰的数据的变化。


## 使用限制

- 遵循ArkTS-Dyn @Observed和@ObjectLink的[使用限制](../ui/state-management/arkts-observed-and-objectlink.md#限制条件)；

- 遵循ArkTS-Dyn @Track的[使用限制](../ui/state-management/arkts-track.md#限制条件)；

- 遵循ArkTS-Sta @Observed和@ObjectLink的[使用限制](../ui/state-management-static/arkts-static-observed-and-objectlink.md#限制条件)；

- 遵循ArkTS-Sta @Track的[使用限制](../ui/state-management-static/arkts-static-track.md#限制条件)；

- 不能在非UI线程中直接修改ArkTS-Sta组件中使用的ArkTS-Dyn @Observed装饰的数据成员的值，否则会运行异常；

- 遵循[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)规范，如不支持ArkTS-Dyn对象继承ArkTS-Sta对象。


## 使用场景

基于以下示例结构，说明在ArkTS-Sta组件中使用动态数据和@Observed装饰数据的场景。

```text
project/
├── entry/                          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets    # 使用动态@Observed装饰的数据
│
└── dynamic_module/                  # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 导出动态@Observed装饰的数据

```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`src/main/ets/components`目录创建并导出动态@Observed装饰的数据。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

@Observed
export class MyClassA { // 定义动态@Observed装饰的类并导出
  @Track name: string = 'text: x';
  message: string = 'text: x';
}
```

- 在ArkTS-Dyn子模块`dynamic_module`的`Index.ets`文件中导出动态@Observed装饰的数据。

```TypeScript
// dynamic_module/Index.ets

export { MyClassA } from './src/main/ets/components/MainPage'; // 导出动态@Observed装饰的类
```

- 在主模块`entry`的`oh-package.json5`文件的`dependencies`字段中添加子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Sta主模块中使用import语句导入ArkTS-Dyn组件。

```TypeScript
'use static'

// entry/src/main/ets/pages/Index.ets
import { Entry, Component, Row, Column, Scroll, Button, ClickEvent, Text } from '@ohos.arkui.component';
import { State} from '@ohos.arkui.stateManagement';

// 引用ArkTS-Dyn动态@Observed装饰的数据
import { MyClassA } from 'dynamic_module';

@Entry
@Component
export struct Index { // ArkTS-Sta组件
  @State state: MyClassA = new MyClassA();

  build() {
    Scroll() {
      Row() {
        Column() {
          // 在ArkTS-Sta中使用动态@Observed装饰的数据
          Text(this.state.name)
            .height('10%')
          Row() {
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
            // 多线程中为动态@Observed装饰的数据中的成员赋值，会运行异常
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
