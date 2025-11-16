# 在ArkTS-Dyn中使用ArkTS-Sta的@ObservedV2和@Trace（类属性变化观测）

## 概述

从API version 22开始，支持从ArkTS-Dyn的自定义组件中调用或修改ArkTS-Sta的[ObservedV2与@Trace](./state-management-static/arkts-static-new-observedV2-and-trace.md)修饰类，数据变更实现UI刷新，通过调用[enableCompatibleObservedV2ForDynamic](../reference/apis-arkui/arkui-ts/ts-interop-compatible-ObservedV2.md#enableCompatibleObservedV2ForDynamic)方法即可。


## 使用限制

- 遵循ArkTS-Dyn @ObservedV2与@Trace的[使用限制](../ui/state-management/arkts-new-observedv2-and-trace.md#使用限制)；

- 遵循ArkTS-Sta @ObservedV2与@Trace的[使用限制](../ui/state-management-static/arkts-static-new-observedv2-and-trace.md#使用限制)；

- 不能在非UI线程中直接修改ArkTS-Dyn组件中使用的ArkTS-Sta @Observed装饰的数据成员的值，否则会运行异常；

- 遵循[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)规范，如不支持ArkTS-Sta对象继承ArkTS-Dyn对象。


## 使用场景

基于以下示例结构，说明在ArkTS-Dyn自定义组件中调用ArkTS-Sta @ObservedV2修饰的类的场景。

```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets    # ArkTS-Dyn主模块入口页面，引入ArkTS-Sta @ObservedV2修饰的类
│
└── static_module/                   # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 导出ArkTS-Sta @ObservedV2修饰的类
```

示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Entry, Text, Column, Component, Button, ClickEvent, enableCompatibleObservedV2ForDynamic } from '@ohos.arkui.component';
import { State, ObservedV2, Trace } from '@ohos.arkui.stateManagement';

// 导出ArkTS-Sta中实现的enableCompatibleObservedV2ForDynamic方法
export function setEnableCompatibleObservedV2ForDynamic(T: Object) {
  // 调用enableCompatibleObservedV2ForDynamic方法，使ArkTS-Sta @Traced修饰的属性在ArkTS-Dyn中可观测
  enableCompatibleObservedV2ForDynamic(T);
}

@ObservedV2
export class ObservedV2ForStatic { // 定义静态@ObservedV2装饰的类并导出
  @Trace name: string = '';
  @Trace age: number = 0;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```

```TypeScript
'use static'

// static_module/Index.ets
export { setEnableCompatibleObservedV2ForDynamic, ObservedV2ForStatic } from './src/main/ets/components/MainPage';
```

- 在主模块 `entry`的 `oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5
"dependencies": {
  'static_module': 'file:../static_module'
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { setEnableCompatibleObservedV2ForDynamic, ObservedV2ForStatic }  from 'static_module';

@Entry
@ComponentV2
export struct Index {
  // 使用@State修饰ArkTS-Sta @ObservedV2装饰的类
  person: ObservedV2ForStatic = new ObservedV2ForStatic('Tom', 9);

  aboutToAppear() {
    // 调用setEnableCompatibleObservedV2ForDynamic方法，使ArkTS-Sta @Traced修饰的属性在ArkTS-Dyn中可观测
    setEnableCompatibleObservedV2ForDynamic(this.person);
  }
  build() {
    Row() {
      Column() {
        Text(`name: ${this.person.name}`)
        Text(`age: ${this.person.age}`)
        Button('add age')
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
