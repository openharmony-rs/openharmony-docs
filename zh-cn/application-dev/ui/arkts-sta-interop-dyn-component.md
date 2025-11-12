# ArkTS-Sta使用ArkTS-Dyn自定义组件

## 概述

UI自定义组件互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景。


## 架构原理

[占位组件](../reference/apis-arkui/arkui-ts/ts-interop-compatible-component.md)链接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。


## 设计理念

UI自定义组件互操作适用于主模块使用ArkTS-Sta、子模块使用ArkTS-Dyn的场景。

- 渐进式迁移：逐步将ArkTS-Dyn组件迁移到新版本。

- 使用旧组件：使用稳定的ArkTS-Dyn自定义组件。


## 约束与限制

- 遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。

- 静态上下文的占位组件不能使用自定义组件的通用属性和方法。

- 静态上下文的自定义组件build函数可以使用动态类型自定义组件。

- 静态上下文的\@Builder函数可以使用动态类型自定义组件。

- 在静态上下文中，可以初始化动态类型自定义组件的内部成员对象。关于状态变量的初始化规则，请参见状态管理互操作。

- 在静态上下文中，不能对动态类型的自定义组件设置通用样式，否则会导致编译错误。
  ```
  'use static'
  import { Entry, Component, Stack, Column } from '@ohos.arkui.component';
  import { HelloComponent } from 'dynamic_module'; // 从动态模块中导入
  
  @Entry
  @Component
  struct ParentComponent {
  
    build() {
      Column() {
        // 不支持对动态自定义组件设置通用样式，如下代码将产生编译报错。
        HelloComponent({ message: 'Hello World!' })
          .width(100)
          .height(100)
  
        // 开发者可以通过嵌套一个Stack组件，将通用样式设置在Stack组件上。
        Stack() {
          HelloComponent({ message: 'Hello World!' })
        }.width(100).height(100)
      }
    }
  }
  ```
  ```
  // dynamic_module/src/main/ets/components/HelloComponent.ets
  @Component
  export struct HelloComponent { // 从动态模块中导出
    message: string = '';

    build() {
      Text(this.message)
        .fontSize(50)
        .fontColor(Color.Blue)
    }
  }
  ```

- 静态上下文中不支持通过@Reusable装饰器来使能动态类型自定义组件的回收复用。


## 开发场景

### 在ArkTS-Sta引用ArkTS-Dyn中的自定义组件显示UI

ArkUI互操作能力支持静态上下文使用动态模块的自定义组件，包括创建并传递参数。

以下示例展示了如何在静态上下文中使用动态模块的自定义组件来显示“Hello World!”。

- 创建ArkTS-Dyn子模块`har1_1`，在`har1_1/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// har1_1/src/main/ets/components/ChildComponent.ets

@Component
export struct ChildComponent {
  message: string = 'Hello World!';

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontColor(Color.Blue)
    }
    .padding(20)
    .backgroundColor(Color.White)
  }
}

@ComponentV2
export struct ChildComponentV2 {
  message: string = 'Hello World!';

  build() {
    Column() {
      Text(this.message)
        .fontSize(50)
        .fontColor(Color.Blue)
    }
    .padding(20)
    .backgroundColor(Color.White)
  }
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "har1_1": "file:../har1_1"
}
```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn组件。

```TypeScript
'use static'

// entry/src/main/ets/pages/MainPage.ets
import { Entry, Component, Column, ComponentV2 } from '@ohos.arkui.component';

import { ChildComponent, ChildComponentV2 } from 'har1_1';

@Entry
@Component
struct MainPage {
  build() {
    Column() {
      // 无需显式使用占位组件API，框架会自动处理
      ChildComponent()
      ChildComponentV2()
      MainPageV2()
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
  }
}

@ComponentV2
struct MainPageV2 {
  build() {
    Column() {
      ChildComponent()
      ChildComponentV2()
    }
  }
}
```


### 使用技巧

- 传递ArkTS-Sta数据到ArkTS-Dyn自定义组件。

```TypeScript
// ArkTS-Dyn子组件
@Component
export struct ChildComponent {
  name: string = '';

  build() {
    Text(`Hello ${this.name}`)
  }
}

// ArkTS-Sta主模块
ChildComponent({ name: 'ArkTS' })
```


- 事件回调处理时，可以将事件回调放置在ArkTS-Sta占位组件的父组件上，或放置在ArkTS-Dyn的子组件上。

```TypeScript
// 放在ArkTS-Dyn子组件上
import hilog from '@ohos.hilog';

@Component
export struct ChildComponent {

  build() {
    Button('Click')
      .onClick(() => {
        hilog.info(0x0000, 'Interop', 'Hello ArkTS-Dyn');
      })
  }
}
```

```TypeScript
// 放在ArkTS-Sta占位组件的父组件上
import { ClickEvent } from '@ohos.arkui.component';
import hilog from '@ohos.hilog';

Column() {
  ChildComponent()
}
.onClick((e: ClickEvent) => {
  hilog.info(0x0000, 'Interop', 'Hello ArkTS-Sta');
})
```


- ArkTS-Sta的占位组件不能使用自定义组件的通用属性和方法，可以通过传递样式数据给ArkTS-Dyn自定义组件来实现。

```TypeScript
// 在ArkTS-Dyn组件中添加样式透传属性
@Component
export struct ChildComponent {
  backgroundColor: string = '';

  build() {
    Column() {}
      .backgroundColor(this.backgroundColor)
  }
}

// ArkTS-Sta主模块
ChildComponent({ backgroundColor: '#F1F3F5' })
```

### 完整示例结构

```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── MainPage.ets
│
└── har1_1/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── ChildComponent.ets
```
