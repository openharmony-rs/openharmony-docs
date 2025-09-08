# ArkTS1.2使用ArkTS1.1 RenderNode

## 概述

[RenderNode](../reference/apis-arkui/js-apis-arkui-renderNode.md)对象互操作适用于[ArkTS1.2互操作](../quick-start/arkts-interop-overview.md)中使用RenderNode对象的场景。

## 架构原理

在互操作场景下，支持在ArkTS1.1创建的RenderNode对象传递到ArkTS1.2。

## 设计理念

RenderNode对象互操作适用于主模块使用ArkTS1.2、子模块使用ArkTS1.1的场景。

- 渐进式迁移：逐步将ArkTS1.1命令式节点迁移到新版本。

- 使用旧RenderNode对象：使用稳定的ArkTS1.1 RenderNode对象。

## 限制条件

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

## 开发场景

### 在ArkTS1.2引用ArkTS1.1中创建的RenderNode对象。

通过在ArkTS1.2中引用ArkTS1.1创建的RenderNode对象显示Text文本。

示例如下：

- 创建ArkTS1.1子模块`library`，在`library/src/main/ets/components`目录创提创建ArkTS1.1RenderNode的方法。

```TypeScript
// library/src/main/ets/components/MainPage.ets
import { RenderNode } from '@ohos.arkui.node'

export function renderNodeTest():Object {
  let shapeMaskTestNode =new RenderNode();
  shapeMaskTestNode.position = { x: 0, y: 0 };
  shapeMaskTestNode.size = { width: 80, height: 80 }
  shapeMaskTestNode.backgroundColor = 0xff0000ff;
  return shapeMaskTestNode;
}
```
```TypeScript
// library/Index.ets
export { renderNodeTest } from './src/main/ets/components/MainPage';
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

import { Entry, Text, Column, Component, NodeContainer, Resource, Button } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import transfer from '@ohos.transfer'
import { UIContext } from '@ohos.arkui.UIContext'
import { FrameNode, RenderNode, NodeController } from '@ohos.arkui.node'
import { renderNodeTest } from 'library'

function renderNodeTrans(): RenderNode{
  let renderNode = renderNodeTest();
  let renderNodeStatic = transfer.transferStatic(renderNode, 'ArkUI.RenderNode')! as RenderNode;
  return renderNodeStatic;
}

class TestNodeController extends NodeController {
  makeNode(uiContext: UIContext): FrameNode | null {
    let rootNode = new FrameNode(uiContext);
    const rootRenderNode = rootNode?.getRenderNode();
    if (rootRenderNode !== null) {
      rootRenderNode?.appendChild(renderNodeTrans());
    }
    return rootNode;
  }
}

@Entry
@Component
struct MyStateSample {
  nodeController: TestNodeController = new TestNodeController();

  build() {
    Column(undefined) {
      NodeContainer(this.nodeController)
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
