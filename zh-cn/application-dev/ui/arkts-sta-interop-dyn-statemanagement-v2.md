# 在ArkTS-Sta中使用ArkTS-Dyn管理组件拥有的状态

## 概述

从API version 23开始，ArkTS-Sta使用ArkTS-Dyn管理组件拥有的状态，涉及状态管理V2交互的场景主要包括：

1. ArkTS-Dyn子组件通过ArkTS-Sta父组件初始化状态数据并进行状态绑定。

2. ArkTS-Dyn子组件通过[@Consumer](../ui/state-management/arkts-new-provider-and-consumer.md)和ArkTS-Sta祖先节点进行交互。


## 使用限制

- 遵循ArkTS-Dyn @Local的[使用限制](../ui/state-management/arkts-new-local.md#限制条件)；

- 遵循ArkTS-Dyn @Param的[使用限制](../ui/state-management/arkts-new-param.md#限制条件)；

- 遵循ArkTS-Dyn @Event的[使用限制](../ui/state-management/arkts-new-event.md#限制条件)；

- 遵循ArkTS-Dyn @Provider和@Consumer的[使用限制](../ui/state-management/arkts-new-provider-and-consumer.md#限制条件)；

- 遵循ArkTS-Sta @Local的[使用限制](../ui/state-management-static/arkts-static-new-local.md#限制条件)；

- 遵循ArkTS-Sta @Param的[使用限制](../ui/state-management-static/arkts-static-new-param.md#限制条件)；

- 遵循ArkTS-Sta @Event的[使用限制](../ui/state-management-static/arkts-static-new-event.md#限制条件)；

- 遵循ArkTS-Sta @Provider和@Consumer的[使用限制](../ui/state-management-static/arkts-static-new-provider-and-consumer.md#限制条件)。


## 使用场景

基于以下示例结构，说明在ArkTS-Sta中与ArkTS-Dyn状态管理V2变量进行互操作的场景。

```text
project/
├── entry/                            # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 在ArkTS-Sta主模块中引入ArkTS-Dyn自定义组件，并给其状态变量赋值
│
└── dynamic_module/                   # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets   # 定义ArkTS-Dyn自定义组件，与ArkTS-Sta状态变量互操作
```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

@ComponentV2
export struct MainPage { // ArkTS-Dyn自定义组件
  // 通过@Param接收ArkTS-Sta父组件传递的状态变量
  @Param paramMessage: string = 'dynamic Param';
  // 通过@Consumer与ArkTS-Sta父节点进行交互
  @Consumer() consumerMessage: string = 'dynamic Consumer';
  // 通过@Event与ArkTS-Sta父组件进行交互
  @Event changeFactory: () => void = () => {};

  build() {
    Column() {
      Text(this.paramMessage)
        .fontSize(30)
      Text(this.consumerMessage)
        .fontSize(30)
        .onClick(() => {
          // 通过@Consumer修改ArkTS-Sta父节点的状态变量
          this.consumerMessage += '!';
        })
      Button('excute changeFactory')
        .onClick(() => {
          // 通过@Event修改ArkTS-Sta父组件的状态变量
          this.changeFactory();
        })
    }
    .padding(20)
  }
}
```

```TypeScript
// dynamic_module/index.ets
export { MainPage } from './src/main/ets/components/MainPage'; // 导出ArkTS-Dyn自定义组件
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn组件。

```TypeScript
'use static'

// entry/src/main/ets/pages/Index.ets
import { Entry, ComponentV2, Column, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Provider } from '@ohos.arkui.stateManagement';

import { MainPage } from 'dynamic_module'; // 引入ArkTS-Dyn自定义组件

@Entry
@ComponentV2
struct ParentComp { // ArkTS-Sta主组件
  // 定义ArkTS-Sta状态变量
  @Local localMessage: string = 'Local Interop';
  @Provider() consumerMessage: string = 'Provider Interop';
  
  build() {
    Column() {
      Button(this.localMessage)
        .onClick((e: ClickEvent) => {
          // 通过@Local修改本组件的状态变量
          this.localMessage += '~';
        })
      Button(this.consumerMessage)
        .onClick((e: ClickEvent) => {
          // 通过@Provider修改子节点的状态变量
          this.consumerMessage += '~';
        })
      // 引入ArkTS-Dyn自定义组件，并传递状态变量
      MainPage({
        paramMessage: this.localMessage,
        changeFactory: () => {
          this.consumerMessage += '@Event';
        }
      })
    }
    .width('100%')
    .height('100%')
  }
}
```
