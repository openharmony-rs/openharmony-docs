# ArkTS-Sta使用ArkTS-Dyn状态管理V2互操作

## 概述

状态管理V2互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景。


## 架构原理

[占位组件](../reference/apis-arkui/arkui-ts/ts-interop-compatible-component.md)链接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。

ArkTS-Sta的状态变量会同步创建一个ArkTS-Dyn的代理状态变量，用于与ArkTS-Dyn的状态变量进行状态传递。


## 设计理念

UI状态管理互操作适用于主模块使用ArkTS-Sta、子模块使用ArkTS-Dyn的场景。


## 约束与限制

- 遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。


## 开发场景

### 在ArkTS-Sta引用ArkTS-Dyn中的自定义组件并使用状态管理V2

下面的代码示例展示了在ArkTS-Sta中与ArkTS-Dyn状态变量V2进行互操作。

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn组件。

```TypeScript
'use static';

// entry/src/main/ets/pages/Index.ets
import { Entry, ComponentV2, Column, Button, ClickEvent } from '@ohos.arkui.component';
import { State, Provide } from '@ohos.arkui.stateManagement';

import { MainPage } from 'library';

@Entry
@ComponentV2
struct ParentComp {
  @Local message1: string = 'Hello Interop';
  @Provider message2: string = 'Provider Interop';
  
  build() {
    Column() {
      Button(this.message1)
        .onClick((e: ClickEvent) => {
          this.message1 += '~';
        })
      MainPage({
        message1: this.message1,
        changeFactory: (param: string) => {
          param+= '@Event';
        }
      })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
  }
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "library": "file:../library",
}
```

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
// library/src/main/ets/components/MainPage.ets

@ComponentV2
export struct MainPage {
  @Param message1: string = 'dynamic Param';
  @Consumer message2: string = 'dynamic Consumer';
  @Event changeFactory: (param: string) => void = (param: string) => {};

  build() {
    Column() {
      Text(this.message1)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message1 += '!';
        })
      Text(this.message2)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message2 += '!';
        })
      Button('excute changeFactory')
        .onClick(() => {
          this.changeFactory(this.message2);
        })
    }
    .padding(20)
    .backgroundColor(Color.White)
  }
}
```

```TypeScript
// library/index.ets
export { MainPage } from from './src/main/ets/components/MainPage';
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
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```


# ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作

## 概述

状态管理V2互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景。


## 架构原理

[占位组件](../reference/apis-arkui/arkui-ts/ts-interop-compatible-component.md)链接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。

ArkTS-Dyn的状态变量会同步创建一个ArkTS-Sta的代理状态变量，用于与ArkTS-Sta的状态变量进行状态传递。


## 设计理念

UI状态管理互操作适用于主模块使用ArkTS-Dyn、子模块使用ArkTS-Sta的场景。


## 约束与限制

- 遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。


## 开发场景

### 在ArkTS-Dyn引用ArkTS-Sta中的自定义组件并使用状态管理V2

下面的代码示例展示了在ArkTS-Dyn中与ArkTS-Sta状态变量V2进行互操作。

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript

// entry/src/main/ets/pages/Index.ets
import { MainPage } from 'library';

@Entry
@ComponentV2
struct ParentComp {
  @Local message1: string = 'Hello Interop';
  @Provider message2: string = 'Provider Interop';
  
  build() {
    Column() {
      Button(this.message1)
        .onClick((e: ClickEvent) => {
          this.message1 += '~';
        })
      MainPage({
        message1: this.message1,
        changeFactory: (param: string) => {
          param+= '@Event';
        }
      })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
  }
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "library": "file:../library",
}
```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
'use static';

// library/src/main/ets/components/MainPage.ets
import { Entry, ComponentV2, Column, Button, ClickEvent } from '@ohos.arkui.component';
import { Param, Consumer, Event } from '@ohos.arkui.stateManagement';

@ComponentV2
export struct MainPage {
  @Param message1: string = 'static Param';
  @Consumer message2: string = 'static Consumer';
  @Event changeFactory: (param: string) => void = (param: string) => {};

  build() {
    Column() {
      Text(this.message1)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick((e: ClickEvent) => {
          this.message1 += '!';
        })
      Text(this.message2)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick((e: ClickEvent) => {
          this.message2 += '!';
        })
      Button('excute changeFactory')
        .onClick((e: ClickEvent) => {
          this.changeFactory(this.message2);
        })
    }
    .padding(20)
    .backgroundColor(Color.White)
  }
}
```

```TypeScript
// library/index.ets
export { MainPage } from from './src/main/ets/components/MainPage';
```



### 完整示例结构

```text
project/
├── entry/          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── MainPage.ets
│
└── library/         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```