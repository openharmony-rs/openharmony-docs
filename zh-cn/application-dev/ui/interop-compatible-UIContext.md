# ArkTS1.1使用ArkTS1.2 UIContext

## 概述
从API version 20开始，[UIContext](../reference/apis-arkui/js-apis-arkui-UIContext.md)对象互操作适用于[ArkTS1.2互操作](../quick-start/arkts-interop-overview.md)中使用UIContext对象的场景。

## 架构原理

在互操作场景下，支持在ArkTS1.1使用ArkTS1.2创建的UIContext。

## 设计理念

UIContext对象互操作适用于主模块使用ArkTS1.2、子模块使用ArkTS1.1的场景。

- 渐进式迁移：逐步将涉及UIContext的代码迁移到ArkTS1.2。

- 使用旧的UIContext对象：使用稳定的ArkTS1.1 UIContext对象。

## 限制条件

- 遵循语言[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)的规范。

## 开发场景

### 在ArkTS1.1中使用ArkTS1.2获取的UIContext对象。

通过在ArkTS1.2中引用ArkTS1.1创建的Resource对象显示Text文本。

### 完整示例结构

完整代码结构树

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


示例如下：

- 创建ArkTS1.1子模块`library`，在`library/src/main/ets/components`目录创提创建ArkTS1.1 使用UIContext的方法。

```TypeScript
// library/src/main/ets/components/MainPage.ets

import { UIContext } from '@kit.ArkUI';

const vpTest:number = 200;
export function uiContextTest(uiContext:Object): number {
  let uiContextDynamic = uiContext as UIContext;
  return uiContextDynamic.px2vp(vpTest);
}
```
```TypeScript
// library/Index.ets

export { uiContextTest } from './src/main/ets/components/MainPage';
```


- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "library": "file:../library"
}
```

- 在ArkTS1.2主模块中获取UIContext并传递给ArkTS1.1。

```TypeScript
// entry/src/main/ets/pages/Index.ets

'use static'

import { Entry, Column, Component, Resource, Image } from '@ohos.arkui.component';
import transfer from '@ohos.transfer';
import { uiContextTest } from 'library';
import { UIContext } from '@ohos.arkui.UIContext';

// uiContext互操作
export function uiContextTrans(uiContext:UIContext): number {
  let uiContextDynamic = transfer.transferDynamic(uiContext, 'ArkUI.UIContext');
  return uiContextTest(uiContextDynamic);
}

@Entry
@Component
struct MyStateSample {
  build() {
    Column(undefined) {
        Column()
          .backgroundColor('#ff00ff00')
          .size({width:uiContextTrans(this.getUIContext()), height:uiContextTrans(this.getUIContext())})
    }
  }
}
```
