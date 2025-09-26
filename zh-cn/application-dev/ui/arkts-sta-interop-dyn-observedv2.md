# ArkTS-Sta与ArkTS-Dyn@ObservedV2数据和@Trace数据互操作

## 概述

从API version 22开始，支持从ArkTS-Sta的自定义组件中调用或修改ArkTS-Dyn的ObservedV2数据以及@Trace数据修饰属性实现UI刷新，同时也支持ArkTS-Dyn的自定义组件修改ArkTS-Sta的ObservedV2数据以及@Trace数据修饰属性实现UI刷新，在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，通过调用[enableCompatibleObservedV2ForDynamic](../reference/apis-arkui/arkui-ts/ts-interop-compatible-ObservedV2.md)方法和[enableCompatibleObservedV2ForStatic](../reference/apis-arkui/arkui-ts/ts-interop-compatible-ObservedV2.md)方法来实现数据交互和UI刷新。

## 在ArkTS-Sta的自定义组件中调用ArkTS-Dyn的@ObservedV2修饰的类

完整示例结构如下图所示：

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

在ArkTS-Dyn中导出ObservedV2修饰的类。

示例如下：

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录创建并导出页面。

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
    @Trace model:  ObservedV2ForStatic2 = new ObservedV2ForStatic2("张三",12);
    constructor(name: string, model: ObservedV2ForStatic2) {
      this.name = name;
      this.model = model;
    }
  }
  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
      'library': 'file:../library',
  }
  ```
- 在ArkTS-Sta主模块中引入ArkTS-Dyn动态模块的页面。

  ```TypeScript
  'use static'
  // entry/src/main/ets/pages/Index.ets

  import { Entry, Row, Text, Column, Component, Button, ComponentV2, enableCompatibleObservedV2ForStatic } from '@ohos.arkui.component';
  import { State, ObservedV2, Trace } from '@ohos.arkui.stateManagement';
  import hilog from '@ohos.hilog';
  import { ObservedV2ForStatic2 } from 'dynamic';

  @Entry
  @ComponentV2
  struct Index {
    person: ObservedV2ForStatic2 = new ObservedV2ForStatic2("张三", 25);
    aboutToAppear(){
      enableCompatibleObservedV2ForStatic(this.person);
    }

    build() {
      Column() {
        Text(`年龄: ${this.person.age}` )
        Button('增加年龄')
          .onClick(() => {
            this.person.age = this.person.age +1;
          })
      }
    }
  }
  ```
