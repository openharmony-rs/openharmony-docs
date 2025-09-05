# ArkTS1.2使用ArkTS1.1 FrameNode

## 概述
// D:\code\oh_code\docs\zh-cn\application-dev\reference\apis-arkui\arkui-ts\ts-types.md
[Resource](../reference/apis-arkui/arkui-ts/ts-types.md)对象互操作适用于[ArkTS1.2互操作](../quick-start/arkts-interop-overview.md)中使用Resource对象的场景。

## 架构原理

在互操作场景下，支持在ArkTS1.1创建的Resouece对象传递到ArkTS1.2。

## 设计理念

FrameNode对象互操作适用于主模块使用ArkTS1.2、子模块使用ArkTS1.1的场景。

- 渐进式迁移：逐步将ArkTS1.1命令式节点迁移到新版本。

- 使用旧FrameNode对象：使用稳定的ArkTS1.1 FrameNode对象。

## 限制条件

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

## 开发场景

### 在ArkTS1.2引用ArkTS1.1中创建的Resource对象。

通过在ArkTS1.2中引用ArkTS1.1创建的FrameNode对象显示Text文本。

示例如下：

- 创建ArkTS1.1子模块`library`，在`library/src/main/ets/components`目录创提创建ArkTS1.1FrameNode的方法。

```TypeScript
// library/src/main/ets/components/MainPage.ets
import { UIContext } from  '@ohos.arkui.UIContext';
import { typeNode, FrameNode } from '@ohos.arkui.node';

export function createFrameNode(context:Object): Object {
  let uiContext:UIContext = context as UIContext;
  let textNode = typeNode.createNode(uiContext, 'Text');
  textNode.initialize('hello word');
  return textNode;
}
```
```TypeScript
// library/Index.ets
export { createFrameNode} from './src/main/ets/components/MainPage';
```


- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "library": "file:../library"
}
```

- 在ArkTS1.2主模块中引入ArkTS1.1 WrappedBuilder对象。

```TypeScript
// entry/src/main/ets/pages/Index.ets

'use static'

import { Entry, Text, Column, Component, NodeContainer} from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import {NodeController ,FrameNode, typeNode } from '@ohos.arkui.node'
import transfer from '@ohos.transfer'
import {UIContext} from '@ohos.arkui.UIContext'
import { createFrameNode } from 'library'

export function FrameNodeTrans(uiContext:UIContext):FrameNode {
  // 通过互操作转换ArkTS1.2UIContext对象为ArkTS1.1UIContext对象
  let uiContextDynamic = transfer.transferDynamic(uiContext, 'ArkUI.UIContext');
  // 调用ArkTS1.1的方法创建FrameNode对象
  let frameNode = createFrameNode(uiContextDynamic! as Object);
  // 通过互操作转换ArkTS1.1FrameNode对象为ArkTS1.2FrameNode对象
  let frameNodeStatic = transfer.transferStatic(frameNode, 'ArkUI.FrameNode')! as FrameNode;
  return frameNodeStatic;
}
class TestNodeController extends NodeController {
  makeNode(uiContext:UIContext):FrameNode|null {
      let rootNode = new FrameNode(uiContext);
      rootNode.commonAttribute.width(100);
      rootNode.commonAttribute.height(100);
      rootNode.appendChild(FrameNodeTrans(uiContext));
      return rootNode;
  }
}

@Entry
@Component
struct MyStateSample {
  nodeController: TestNodeController = new TestNodeController();
  build() {
    Column(undefined) {
       NodeContainer(this.nodeController).width(100).height(100).border({width:1})
    }
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
│                   └── Index.ets
│
└── library/         # ArkTS1.1子模块
    └── src/
       ├── main/
       │     └── ets/
       │        └── components/
       │          └── MainPage.ets
       └── Index.ets
```
