# ArkTS-Sta使用ArkTS-Dyn WrappedBuilder对象

## 概述

WrappedBuilder对象互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用WrappedBuilder对象的场景。

## 架构原理

在互操作场景下，[compatibleWrappedBuilder方法](../reference/apis-arkui/arkui-ts/ts-interop-compatible-WrappedBuilder.md)将ArkTS-Dyn的WrappedBuilder对象转换为占位组件，从而链接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。


## 设计理念

WrappedBuilder对象互操作适用于主模块使用ArkTS-Sta、子模块使用ArkTS-Dyn的场景。

- 渐进式迁移：逐步将ArkTS-Dyn组件迁移到新版本。

- 使用旧WrappedBuilder对象：使用稳定的ArkTS-Dyn WrappedBuilder对象。

## 限制条件

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

- 遵循ArkTS-Dyn WrappedBuilder对象的使用[限制条件](./state-management/arkts-wrapBuilder.md#限制条件)。

- compatibleWrappedBuilder函数建议在自定义组件的build函数或者\@Builder函数内使用。

- compatibleWrappedBuilder函数的第一个参数需要传递ArkTS 1.1的WrappedBuilder对象，传递其他类型对象会导致UI异常。

- compatibleWrappedBuilder函数支持的\@Builder函数的参数最多不超过10个，否则将引发运行时异常。

## 开发场景

### 在ArkTS-Sta引用ArkTS-Dyn中的WrappedBuilder对象，并通过引用传递参数

由于动静态类型差异，ArkTS-Dyn的WrappedBuilder对象类型在ArkTS-Sta上下文中被转换为了Any类型，UI互操作编译工具无法对Any类型进行编译期适配优化，因此开发者需要显式调用互操作接口[compatibleWrappedBuilder](../reference/apis-arkui/arkui-ts/ts-interop-compatible-WrappedBuilder.md)来使用ArkTS-Dyn的WrappedBuilder对象。


以下示例展示了在ArkTS-Sta上下文中使用动态WrappedBuilder对象的方法来显示“Hello World!”。

示例如下：

- 创建ArkTS-Dyn子模块`har1_1`，在`har1_1/src/main/ets/components`目录创建并导出WrappedBuilder对象。

```TypeScript
// har1_1/src/main/ets/components/MainPage.ets

class Tmp {
  paramA2: string = 'Hello World!';
}

@Builder
function overBuilder(param: Tmp) {
  Column() {
    Text(param.paramA2)
  }
}

export const globalBuilder: WrappedBuilder<[Tmp]> = wrapBuilder(overBuilder);
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "har1_1": "file:../har1_1"
}
```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn WrappedBuilder对象。

```TypeScript
'use static'

// entry/src/main/ets/pages/MainPage.ets
import { Entry, Component, Column, Button, ClickEvent, compatibleWrappedBuilder } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

import { globalBuilder } from 'har1_1';

@Entry
@Component
struct MainPage {
  @State stateVar: string = 'Hello World!';

  build() {
    Column() {
      // 无需显式使用占位组件API，框架会自动处理
      let globalBuilderParam = ESValue.instantiateEmptyObject()
      globalBuilderParam.setProperty(ESValue.wrap('paramA2'), ESValue.wrap(this.stateVar))
      compatibleWrappedBuilder(globalBuilder, globalBuilderParam)

      Button('Click me').onClick((e: ClickEvent) => {
        this.stateVar = 'Hello ArkUI!';
      })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
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
