# ArkTS-Sta使用ArkTS-Dyn @ObservedV2数据和@Trace数据互操作

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lishihao16-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

## 概述

从API version 22开始，支持从ArkTS-Sta的自定义组件中调用或修改ArkTS-Dyn的[ObservedV2与@Trace](../ui/state-management/arkts-new-observedV2-and-trace.md)修饰类，数据变更实现UI刷新，在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，通过调用[enableCompatibleObservedV2ForStatic](../reference/apis-arkui/arkui-ts/ts-interop-compatible-ObservedV2.md#enableCompatibleObservedV2ForStatic)方法即可。

## 在ArkTS-Sta的自定义组件中调用ArkTS-Dyn的@ObservedV2修饰的类

示例结构如下：

```test
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

示例如下：

- ArkTS-Sta示例：

```TypeScript
'use static'
// entry/src/main/ets/pages/Index.ets

import { Entry, Row, Text, Column, Component, Button, ComponentV2, enableCompatibleObservedV2ForStatic } from '@ohos.arkui.component';
import { State, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
import hilog from '@ohos.hilog';
import { ObservedV2ForStatic2 } from 'library';

@Entry
@ComponentV2
struct Index {
  person: ObservedV2ForStatic2 = new ObservedV2ForStatic2('张三', 25);
  aboutToAppear() {
    enableCompatibleObservedV2ForStatic(this.person);
  }

  build() {
    Column() {
      Text(`年龄: ${this.person.age}`)
      Button('增加年龄')
        .onClick(() => {
          this.person.age = this.person.age + 1;
        })
    }
  }
}
```

- 在主模块 `entry`的 `oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
    'library': 'file:../library',
}
```

- ArkTS-Dyn示例：

```TypeScript
// library/src/main/ets/components/MainPage.ets
@ObservedV2
export class ObservedV2ForStatic2 {
  @Trace name: string = '';
  @Trace age: number = 0;
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
@ObservedV2
export class ObservedV2ForStatic {
  @Trace name: string = '';
  @Trace model:  ObservedV2ForStatic2 = new ObservedV2ForStatic2('张三',12);
  constructor(name: string, model: ObservedV2ForStatic2) {
    this.name = name;
    this.model = model;
  }
}
```
