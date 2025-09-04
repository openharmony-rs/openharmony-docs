# ArkTS1.2使用ArkTS1.1 FrameNode

## 概述

[FrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md)对象互操作适用于[ArkTS1.2互操作](../quick-start/arkts-interop-overview.md)中使用FrameNode对象的场景。

## 架构原理

在互操作场景下，支持在ArkTS1.1创建的FrameNode对象传递到ArkTS1.2。

## 设计理念

FrameNode对象互操作适用于主模块使用ArkTS1.2、子模块使用ArkTS1.1的场景。

- 渐进式迁移：逐步将ArkTS1.1命令式节点迁移到新版本。

- 使用旧FrameNode对象：使用稳定的ArkTS1.1 FrameNode对象。

## 限制条件

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

- 遵循ArkTS1.1 FrameNode对象的使用[限制条件](../reference/apis-arkui/js-apis-arkui-frameNode.md#istransferred20)。

## 开发场景

### 在ArkTS1.2引用ArkTS1.1中创建的FrameNode对象。

通过在ArkTS1.2中引用ArkTS1.1创建的FrameNode对象显示Text文本。

示例如下：

- 创建ArkTS1.1子模块`har1_1`，在`har1_1/src/main/ets/components`目录创提供创建FrameNode方法。

```TypeScript
// har1_1/src/main/ets/components/MainPage.ets
import { UIContext } from  '@ohos.arkuiu.UIContext';
import { typeNode FrameNode } from '@ohos.arkui.node';

export function createFrameNode(context:Object): Object {
  let uiContext:UIContext = uiContext as UIContext;
  let textNode = typeNode.createNodde(uiContext, 'Text');
  textNode.initialize('hello word');
  return textNode;
}

```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "har1_1": "file:../har1_1"
}
```

- 在ArkTS1.2主模块中引入ArkTS1.1 WrappedBuilder对象。

```TypeScript
'use static';

// entry/src/main/ets/pages/MainPage.ets
import { Entry, Component, Column, Button, ClickEvent, compatibleWrappedBuilder } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

import { createFrameNode } from 'har1_1';

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
├── entry/          # ArkTS1.2主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── MainPage.ets
│
└── har1_1/         # ArkTS1.1子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```
