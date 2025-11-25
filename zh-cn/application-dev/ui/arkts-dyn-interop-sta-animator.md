# 在ArkTS-Dyn中使用ArkTS-Sta的帧动画（Animator）

从API version 22开始，支持在ArkTS-Dyn中获取ArkTS-Sta中的帧动画对象([AnimateResult](../reference/apis-arkui/js-apis-arkui-UIContext.md#createanimator))，能调用帧动画对象的控制接口，包括[play](../reference/apis-arkui/js-apis-animator.md#play)、[pause](../reference/apis-arkui/js-apis-animator.md#pause)、[finish](../reference/apis-arkui/js-apis-animator.md#finish)、[cancle](../reference/apis-arkui/js-apis-animator.md#cancel)。不建议对从ArkTS-Sta获取的[AnimateResult](../reference/apis-arkui/js-apis-arkui-UIContext.md#createanimator)对象调用[reset](../reference/apis-arkui/js-apis-animator.md#reset9)接口。在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，导出ArkTS-Sta的接口，在ArkTS-Dyn的页面中直接调用。

完整示例结构如下所示。

```test
project/
├── entry/          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets         # 调用动画的文件
│
└── library/         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets      # animator所在的文件
```

ArkTS-Sta中调用[createAnimator](../reference/apis-arkui/js-apis-arkui-UIContext.md#createanimator)等接口，其使用规格限制与非互操作场景相同。

示例如下：

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建页面。

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import { AnimatorResult, AnimatorOptions } from '@ohos.animator';
  import { Button, ClickEvent, Column, Component, Color, Row } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';

  @Component
  export struct createAnimatorD2S {
    @State tSize1: number = 30;

    build() {
      Row(){
        Column() {
          Button("createAnimatorD2S").backgroundColor('#FFFF00FF')
            .onClick((e: ClickEvent) => {
              let options: AnimatorOptions = {
                duration: 1500,
                easing: "ease",
                delay: 1000,
                fill: "forwards",
                direction: "normal",
                iterations: 1,
                begin: 30,
                end: 90,
              };
              let animatorResult: AnimatorResult = this.getUIContext().createAnimator(options);
              animatorResult.onFrame = (value: number) => {
                this.tSize1 = value;
              }
              animatorResult.play();
            })
        
          Column() {}
          .width(this.tSize1)
          .height(100)
          .backgroundColor(Color.Red)
        }
        .width('100%')
      }
      .height('100%')
    }
  }

  ```

- 在ArkTS-Sta子模块`library`中导出页面。

  ```TypeScript
  // library/Index.ets
  export { createAnimatorD2S } from './src/main/ets/components/MainPage'

  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
    'library': 'file:../library',
  }
  ```

- 在ArkTS-Dyn主模块中引入ArkTS-Sta的页面。

  ```TypeScript
  // entry/src/main/ets/pages/Index.ets
  import { createAnimatorD2S } from 'library';

  @Entry
  @Component
  struct Index {

    build() {
      Column() {
          createAnimatorD2S()
      }.height(200).backgroundColor("#99489ee0")
    }
  }
  ```