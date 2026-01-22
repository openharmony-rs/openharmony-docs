# 在ArkTS-Dyn中使用ArkTS-Sta管理组件拥有的状态

## 概述

从API version 23开始，ArkTS-Dyn使用ArkTS-Sta管理组件拥有的状态，涉及状态管理V1交互的场景主要包括：

1. ArkTS-Sta子组件通过ArkTS-Dyn父组件初始化状态数据并进行状态绑定。

2. ArkTS-Sta子组件通过[@Consume](../ui/state-management-static/arkts-static-provide-and-consume.md)和ArkTS-Dyn祖先节点进行交互。


## 使用限制

- 遵循ArkTS-Dyn @State的[使用限制](../ui/state-management/arkts-state.md#限制条件)；

- 遵循ArkTS-Dyn @Prop的[使用限制](../ui/state-management/arkts-prop.md#限制条件)；

- 遵循ArkTS-Dyn @Link的[使用限制](../ui/state-management/arkts-link.md#限制条件)；

- 遵循ArkTS-Dyn @Provide和@Consume的[使用限制](../ui/state-management/arkts-provide-and-consume.md#限制条件)；

- 遵循ArkTS-Sta @State的[使用限制](../ui/state-management-static/arkts-static-state.md#限制条件)；

- 遵循ArkTS-Sta @PropRef的[使用限制](../ui/state-management-static/arkts-static-propref.md#限制条件)；

- 遵循ArkTS-Sta @Link的[使用限制](../ui/state-management-static/arkts-static-link.md#限制条件)；

- 遵循ArkTS-Sta @Provide和@Consume的[使用限制](../ui/state-management-static/arkts-static-provide-and-consume.md#限制条件)。


## 使用场景

基于以下示例结构，说明ArkTS-Dyn使用ArkTS-Sta管理组件拥有的状态的场景。

```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets    # 定义ArkTS-Dyn主模块组件ParentComp
│
└── static_module/                   # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 定义ArkTS-Sta自定义组件Child
```

示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录创建并导出自定义组件`Child`。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Component, Column, Text, Color } from '@ohos.arkui.component';
import { State, Link, PropRef, Provide, Consume } from '@ohos.arkui.stateManagement';

@Component
export struct Child { // ArkTS-Sta自定义组件
  @State stateMessage: string = 'static State';
  @Link linkMessage: string;
  @PropRef propMessage: string = 'static PropRef';
  @Provide provideMessage: string = 'static Provide';
  @Consume consumeMessage: string;

  build() {
    Column() {
      Text(this.stateMessage)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          // 点击文本，修改@State状态变量
          this.stateMessage += '!';
        })
      Text(this.linkMessage)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          // 点击文本，修改@Link状态变量
          this.linkMessage += '!';
        })
      Text(this.propMessage)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          // 点击文本，修改@PropRef状态变量
          this.propMessage += '!';
        })
      Text(this.provideMessage)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          // 点击文本，修改@Provide状态变量
          this.provideMessage += '!';
        })
      Text(this.consumeMessage)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          // 点击文本，修改@Consume状态变量
          this.consumeMessage += '!';
        })
    }
    .padding(20)
  }
}
```

```TypeScript
'use static'

// static_module/index.ets
export { Child } from './src/main/ets/components/MainPage'; // 导出ArkTS-Sta自定义组件Child
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "static_module": "file:../static_module"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets

import { Child } from 'static_module'; // 引入ArkTS-Sta子模块中的自定义组件Child

@Entry
@Component
struct ParentComp {
  @State message: string = 'Hello Interop';
  @Provide consumeMessage: string = 'Provide Interop';

  build() {
    Column() {
      Button(this.message)
        .onClick((e: ClickEvent) => {
          // 点击按钮，修改@State状态变量
          this.message += '~';
        })
      // 使用ArkTS-Sta子组件Child，并通过状态绑定与其进行交互
      Child({
        stateMessage: this.message,
        linkMessage: this.message,
        propMessage: this.message,
        provideMessage: this.message
      })
    }
    .width('100%')
    .height('100%')
  }
}
```
