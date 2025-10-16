# ArkTS-Sta @Builder函数初始化ArkTS-Dyn自定义组件@BuilderParam成员属性

## 概述

适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中ArkTS-Sta @Builder函数初始化ArkTS-Dyn自定义组件@BuilderParam成员属性的场景。


## 架构原理

在互操作场景下，针对ArkTS-Dyn的自定义组件，通过`@BuilderParam`定制化功能模块。UI互操作通过编译期适配优化，支持在ArkTS-Sta上下文中初始化ArkTS-Dyn自定义组件的`@BuilderParam`成员属性，构建完整的UI界面。


## 设计理念

适用于主模块使用ArkTS-Sta、子模块使用ArkTS-Dyn的场景。

- 渐进式迁移：逐步将ArkTS-Dyn组件迁移到新版本。

- 使用ArkTS-Dyn带@BuilderParam的自定义组件。

## 参数传递规则

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

- 遵循ArkTS-Dyn自定义构建函数[参数传递规则](./state-management/arkts-builder.md#参数传递规则)。


## 开发场景

### 给ArkTS-Dyn自定义组件的\@BuilderParam赋值显示UI

ArkTS-Sta @Builder函数初始化ArkTS-Dyn自定义组件@BuilderParam成员属性，使用规格限制与非互操作场景相同。

以下示例展示在静态上下文中给ArkTS-Dyn自定义组件的\@BuilderParam赋值来显示UI。

示例如下：

- 创建ArkTS-Dyn子模块`har1_1`，在`har1_1/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
// har1_1/src/main/ets/components/MainPage.ets

@Component
export struct CustomContainer {
  @Builder
  closerBuilder() {
  }

  @BuilderParam closer: () => void = this.closerBuilder;

  build() {
    Column() {
      this.closer()
    }
  }
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "har1_1": "file:../har1_1"
}
```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn动态模块的自定义组件。

```TypeScript
'use static'

// entry/src/main/ets/pages/MainPage.ets
import { Entry, Component, Builder, Column, Text, ClickEvent, Color } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';
import { CustomContainer } from 'har1_1';

@Entry
@Component
struct CustomContainerUser {
  @State text: string = 'header';

  @Builder
  localBuilder() {
    Text(this.text)
      .onClick((value: ClickEvent) => {
        this.text = 'changeHeader';
      })
  }

  build() {
    Column() {
      // 创建CustomContainer，在创建CustomContainer时，通过其后紧跟一个大括号“{}”形成尾随闭包
      // 作为传递给子组件CustomContainer 的 @BuilderParam 参数 closer: () => void
      CustomContainer() {
        Column() {
          Text(this.text)
        }.backgroundColor(Color.Yellow)
        .onClick((value: ClickEvent) => {
          this.text = 'changeHeader';
        })
      }
      // 通过参数初始化 @BuilderParam 成员。
      CustomContainer({closer: this.localBuilder})
    }
  }
}
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
                    └── MainPage.ets
```
