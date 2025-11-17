# 在ArkTS-Sta中使用ArkTS-Dyn的@ObservedV2和@Trace（类属性变化观测）

## 概述

从API version 22开始，支持从ArkTS-Sta的自定义组件中调用或修改ArkTS-Dyn的[ObservedV2与@Trace](../ui/state-management/arkts-new-observedV2-and-trace.md)修饰类，数据变更实现UI刷新，在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，通过调用[enableCompatibleObservedV2ForStatic](../reference/apis-arkui/arkui-ts/ts-interop-compatible-ObservedV2.md#enableCompatibleObservedV2ForStatic)方法即可。


## 使用限制

- 遵循ArkTS-Dyn @ObservedV2与@Trace的[使用限制](../ui/state-management/arkts-new-observedv2-and-trace.md#使用限制)；

- 遵循ArkTS-Sta @ObservedV2与@Trace的[使用限制](../ui/state-management-static/arkts-static-new-observedv2-and-trace.md#使用限制)；

- 不能在非UI线程中直接修改ArkTS-Sta组件中使用的ArkTS-Dyn @ObservedV2装饰的数据成员的值，否则会运行异常；

- 遵循[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)规范，如不支持ArkTS-Dyn对象继承ArkTS-Sta对象。


## 使用场景

基于以下示例结构，说明在ArkTS-Sta自定义组件中调用ArkTS-Dyn @ObservedV2修饰的类的场景。

```text
project/
├── entry/                            # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # ArkTS-Sta主模块入口页面，引入ArkTS-Dyn @ObservedV2修饰的类
│
└── dynamic_module/                   # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets   # 导出ArkTS-Dyn @ObservedV2修饰的类
```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

@ObservedV2
export class ObservedV2ForStatic {
  @Trace name: string = '';
  @Trace model:  ObservedV2ForStatic2 = new ObservedV2ForStatic2('Tom', 12);

  constructor(name: string, model: ObservedV2ForStatic2) {
    this.name = name;
    this.model = model;
  }
}

@ObservedV2
export class ObservedV2ForStatic2 { // 供ArkTS-Sta主模块使用的类
  // 定义@Trace修饰的属性
  @Trace name: string = '';
  @Trace age: number = 0;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```

```TypeScript
// dynamic_module/Index.ets

export { ObservedV2ForStatic2 } from './src/main/ets/components/MainPage'; // 导出供ArkTS-Sta主模块使用的类
```

- 在主模块 `entry`的 `oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

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

import { Entry, Row, Text, Column, Component, Button, ComponentV2, enableCompatibleObservedV2ForStatic } from '@ohos.arkui.component';
import { State, ObservedV2, Trace } from '@ohos.arkui.stateManagement';

import { ObservedV2ForStatic2 } from 'dynamic_module'; // 引入ArkTS-Dyn @ObservedV2修饰的类

@Entry
@ComponentV2
struct Index { // ArkTS-Sta自定义组件
  // 创建ArkTS-Dyn @ObservedV2修饰类的实例
  person: ObservedV2ForStatic2 = new ObservedV2ForStatic2('Jack', 25);

  aboutToAppear() {
    // 启用ArkTS-Dyn @ObservedV2与ArkTS-Sta组件的互操作开关，以支持@Trace属性变化观测
    enableCompatibleObservedV2ForStatic(this.person);
  }

  build() {
    Column() {
      // 显示name属性
      Text(`age: ${this.person.age}`)
      Button('add age')
        .onClick(() => {
          // 修改@Trace修饰的age属性，UI会刷新
          this.person.age = this.person.age + 1;
        })
    }
  }
}
```
