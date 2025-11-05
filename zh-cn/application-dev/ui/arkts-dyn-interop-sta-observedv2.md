# ArkTS-Dyn使用ArkTS-Sta @ObservedV2数据和@Trace数据互操作

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lishihao16-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

## 概述

从API version 22开始，支持从ArkTS-Dyn的自定义组件中调用或修改ArkTS-Sta的[ObservedV2与@Trace](./state-management-static/arkts-static-new-observedV2-and-trace.md)修饰类，数据变更实现UI刷新，通过调用[enableCompatibleObservedV2ForDynamic](../reference/apis-arkui/arkui-ts/ts-interop-compatible-ObservedV2.md#enableCompatibleObservedV2ForDynamic)方法即可。

## 在ArkTS-Dyn的自定义组件中调用ArkTS-Sta的@ObservedV2修饰的类

示例结构如下：

```test
project/
├── entry/          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── library/         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

示例如下：

- ArkTS-Dyn示例：

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { ObservedV2ForStatic, setEnableCompatibleObservedV2ForDynamic } from 'library';

@Entry
@ComponentV2
export struct Index {
  person: ObservedV2ForStatic = new ObservedV2ForStatic('张三', 9);

  aboutToAppear() {
    setEnableCompatibleObservedV2ForDynamic(this.person);
  }
  build() {
    Row() {
      Column() {
        Text(`姓名: ${this.person.name}`)
        Text(`年龄: ${this.person.age}`)
        Button("增加年龄")
          .onClick(() => {
            this.person.age++; // 触发UI刷新
          })
      }
      .width('100%')
    }
    .height('100%')
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

- 创建ArkTS-Sta示例：

```TypeScript
'use static'
// library/src/main/ets/components/MainPage.ets

import { Entry, Text, Column, Component, Button, ClickEvent,enableCompatibleObservedV2ForDynamic } from '@ohos.arkui.component';
import { State, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
import hilog from '@ohos.hilog';

// 导出ArkTS-Sta中实现的enableCompatibleObservedV2ForDynamic方法
export function setEnableCompatibleObservedV2ForDynamic(T: Object) {
  enableCompatibleObservedV2ForDynamic(T);
}

@ObservedV2
export class ObservedV2ForStatic {
  @Trace name: string = '';
  @Trace age: number = 0;
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```
