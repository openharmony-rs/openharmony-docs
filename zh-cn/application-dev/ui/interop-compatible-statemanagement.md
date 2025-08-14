# ArkTS1.2使用ArkTS1.1状态管理互操作

## 概述

状态管理互操作适用于[ArkTS1.2互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景。


## 架构原理

[占位组件](../reference/apis-arkui/arkui-ts/ts-interop-compatible-component.md)链接ArkTS1.2和ArkTS1.1的UI节点，构建完整的UI界面。
ArkTS1.2的状态变量会同步创建一个ArkTS1.1的代理状态变量，用于与ArkTS1.1的状态变量进行状态传递。


## 设计理念

UI状态管理互操作适用于主模块使用ArkTS1.2、子模块使用ArkTS1.1的场景。


## 约束与限制

- 遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。

- ArkTS1.2的数据不支持深拷贝，因此ArkTS1.1的@Prop变量不能接收ArkTS1.2的引用类型数据。


## 开发场景

### 在ArkTS1.2引用ArkTS1.1中的自定义组件并使用状态管理

下面的代码示例展示了在ArkTS1.2中与ArkTS1.1状态变量进行互操作。

- 在ArkTS1.2主模块`entry`中引入ArkTS1.1组件。

```TypeScript
'use static';

// entry/src/main/ets/pages/Index.ets
import { Entry, Component, Column, Button, ClickEvent } from '@ohos.arkui.component';
import { State, Provide } from '@ohos.arkui.stateManagement';

import { MainPage } from 'library';
import { Info } from 'library2';

@Entry
@Component
struct ParentComp {
  @State message: string = 'Hello Interop';
  @Provide message5: string = 'Provide Interop';
  @State message6: Info = new Info();

  build() {
    Column() {
      Button(this.message)
        .onClick((e: ClickEvent) => {
          this.message += '~';
        })
      MainPage({
        message1: this.message,
        message2: this.message,
        message3: this.message,
        message4: this.message,
        message6: this.message6,
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
  "library2": "file:../library2",
}
```

- 创建ArkTS1.1子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
// library/src/main/ets/components/MainPage.ets
import { StaticClass, Info } from 'library2';

@Component
export struct MainPage {
  @State message1: string = 'dynamic State';
  @Link message2: string;
  @Prop message3: string = 'dynamic Prop';
  @Provide message4: string = 'dynamic Provide';
  @Consume message5: string;
  @ObjectLink message6: Info;
  @State message7: StaticClass = new StaticClass();

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
      Text(this.message3)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message3 += '!';
        })
      Text(this.message4)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message4 += '!';
        })
      Text(this.message5)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message5 += '!';
        })
      Text(this.message6.message)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message6.message += '!';
        })
      Text(this.message7.prop1)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message7.prop1 += '!';
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

- 在ArkTS1.1模块`library`的`oh-package.json5`文件中配置子模块依赖。

```json
// library/oh-package.json5

"dependencies": {
  "library2": "file:../library2",
}
```

- 创建ArkTS1.2子模块`library2`，在`library2/src/main/ets/components`目录创建并导出静态数据。

```TypeScript
// library2/src/main/ets/components/MainPage.ets

'use static';
import { Observed, Track } from '@ohos.arkui.stateManagement';

@Observed
export class StaticClass {
  @Track prop1: string = 'static prop1';
  @Track prop2: Array<number> = [1, 2];
  prop3: boolean = true;
}

@Observed
export class Info {
  message: string = 'Observed Interop';
}
```

```TypeScript
// library/index.ets
export { StaticClass, Info } from from './src/main/ets/components/MainPage';
```


### 完整示例结构

```text
project/
├── entry/          # ArkTS1.2主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── MainPage.ets
│
│── library/         # ArkTS1.1子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets
└── library2/         # ArkTS1.2子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```
