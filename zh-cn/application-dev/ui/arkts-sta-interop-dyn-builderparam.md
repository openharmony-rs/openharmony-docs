# 在ArkTS-Sta中使用ArkTS-Dyn的@BuilderParam（引用@Builder函数）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lixingchi1; @katabanga-->
<!--Designer: @lixingchi1; @katabanga-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

## 概述

从API version 23开始，支持在ArkTS-Sta中使用[\@Builder](./state-management/arkts-builder.md)函数初始化ArkTS-Dyn自定义组件的\@BuilderParam成员属性。

在阅读本文档前，建议阅读：[\@BuilderParam](./state-management/arkts-builderparam.md#装饰器使用说明)。


## 使用限制

- 遵循ArkTS-Sta自定义构建函数[限制条件](./state-management/arkts-builder.md#限制条件)；

- 遵循ArkTS-Dyn \@BuilderParam装饰器[限制条件](./state-management/arkts-builderparam.md#限制条件)。


## 使用场景

ArkTS-Sta @Builder函数初始化ArkTS-Dyn自定义组件@BuilderParam成员属性，使用规格限制与非互操作场景相同。

基于以下示例结构，说明在ArkTS-Sta中给ArkTS-Dyn自定义组件的\@BuilderParam赋值来显示UI的场景。

```text
project/
├── entry/                         # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaBuilderparam.ets   # ArkTS-Sta主模块入口页面
│
└── dynamic_module/                 # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets # 定义ArkTS-Dyn自定义组件并导出
```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

<!-- @[StaBuilderparamMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderparam/dynamic_module/src/main/ets/components/MainPage.ets) -->

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

@Component
export struct CustomContainer { // 导出ArkTS-Dyn自定义组件
  text: number = 0;

  @Builder
  closerBuilder() {
  }

  // 使用@BuilderParam装饰器声明成员属性closer，ArkTS-Sta的@Builder函数将传递给该成员属性
  @BuilderParam closer: () => void = this.closerBuilder;

  build() {
    Column() {
      // 使用传入的@BuilderParam成员属性closer构建UI
      this.closer()
    }
    .width('100%')
  }
}
```

<!-- @[StaBuilderparamDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderparam/dynamic_module/Index.ets) -->

```TypeScript
// dynamic_module/Index.ets

export { CustomContainer } from './src/main/ets/components/MainPage'; // 导出自定义组件
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn的自定义组件。

<!-- @[StaBuilderparam](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderparam/entry/src/main/ets/pages/StaBuilderparam.ets) -->

```TypeScript
// entry/src/main/ets/pages/StaBuilderparam.ets
import { Entry, Component, Builder, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

import { CustomContainer } from 'dynamic_module';

@Entry
@Component
struct CustomContainerUser { // 主模块中使用ArkTS-Dyn自定义组件
  @State text: int = 0;

  @Builder
  localBuilder() {
    Text(`${this.text}`)
      .fontSize(20)
      .margin(10)
      .onClick((value: ClickEvent) => {
        // 修改成员属性text的值
        this.text++;
      })
  }

  build() {
    Column() {
      // 创建CustomContainer，在创建CustomContainer时，通过其后紧跟一个大括号"{}"形成尾随闭包
      // 作为传递给子组件CustomContainer的@BuilderParam参数closer
      CustomContainer({ text: this.text }) {
        Column() {
          Text(`${this.text}`)
            .fontSize(20)
            .margin(10)
        }
        .onClick((value: ClickEvent) => {
          this.text++;
        })
      }
      // 通过参数初始化@BuilderParam成员
      CustomContainer({ text: this.text, closer: this.localBuilder })
    }
    .width('100%')
  }
}
```

示例效果图：

![arkts-sta-interop-dyn-builderparam-demo1](figures/arkts-sta-interop-dyn-builderparam-demo1.gif)
