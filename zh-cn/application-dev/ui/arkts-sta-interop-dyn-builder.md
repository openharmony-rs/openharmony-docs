# ArkTS-Sta使用ArkTS-Dyn全局自定义构建函数

## 概述

全局自定义构建函数互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用全局自定义构建函数的场景。


## 架构原理

在互操作场景下，将ArkTS-Dyn全局自定义构建函数的调用转换为占位组件，链接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。


## 设计理念

全局自定义构建函数互操作适用于主模块使用ArkTS-Sta、子模块使用ArkTS-Dyn的场景。

- 渐进式迁移：逐步将ArkTS-Dyn组件迁移到新版本。

- 使用旧全局自定义构建函数：使用稳定的ArkTS-Dyn全局自定义构建函数。

## 参数传递规则

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

- 遵循ArkTS-Dyn自定义构建函数[参数传递规则](./state-management/arkts-builder.md#参数传递规则)。

- ArkTS-Dyn全局自定义构建函数的参数最多不超过10个。

## 开发场景

### 在ArkTS-Sta中引用ArkTS-Dyn的全局自定义构建函数显示UI

ArkUI互操作能力支持在静态上下文中使用动态模块的\@Builder函数，使用规格限制与非互操作场景相同。

以下示例展示在静态上下文中使用动态模块的\@Builder函数来显示“Hello World!”。

示例如下：

- 创建ArkTS-Dyn子模块`har1_1`，在`har1_1/src/main/ets/components`目录创建并导出全局自定义构建函数。

```TypeScript
// har1_1/src/main/ets/components/MainPage.ets

@Builder
export function showTextBuilder() {
  Text('Hello World!')
    .fontSize(30)
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "har1_1": "file:../har1_1"
}
```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn全局自定义构建函数。

```TypeScript
'use static'

// entry/src/main/ets/pages/MainPage.ets
import { Entry, Component, Column } from '@ohos.arkui.component';

import { showTextBuilder } from 'har1_1';

@Entry
@Component
struct MainPage {
  build() {
    Column() {
      // 无需显式使用占位组件API，框架会自动处理
      showTextBuilder()
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
