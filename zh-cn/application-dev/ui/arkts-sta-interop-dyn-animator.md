# 在ArkTS-Sta中使用ArkTS-Dyn的帧动画（Animator）

从API version 22开始，支持在ArkTS-Sta中创建[AnimateResult](../reference/apis-arkui/js-apis-arkui-UIContext.md#createanimator)调用ArkTS-Dyn的[play](../reference/apis-arkui/js-apis-animator.md#play)、[pause](../reference/apis-arkui/js-apis-animator.md#pause)、[finish](../reference/apis-arkui/js-apis-animator.md#finish)、[cancle](../reference/apis-arkui/js-apis-animator.md#cancel)等接口实现动画的播放、暂停、结束、删除。在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，导出ArkTS-Dyn的play等接口，在ArkTS-Sta的页面中直接调用。

完整示例结构如下所示。

```test
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets       # Animator所在的文件
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets     # 调用动画的文件
```

示例如下：

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录创建页面。

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function createAnimatorS2D(obj: object) : object {
    obj.play()
    return obj;
  }
  
  ```

- 在ArkTS-Dyn子模块`library`中导出页面。

  ```TypeScript
  // library/Index.ets
  export { createAnimatorS2D } from './src/main/ets/components/MainPage';

  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
    'library': 'file:../library',
  }
  ```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn的页面。

  ```TypeScript
  // entry\src\main\ets\pages\Index.ets
  import { Entry, Builder, Button, ClickEvent, Column, Component,
    Row, Text } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import transfer from '@ohos.transfer';
  import { createAnimatorS2D } from 'library';
  import { AnimatorResult, AnimatorOptions } from '@ohos.animator';

  @Entry
  @Component
  struct Index {
    @State tSize2: number = 10;

    build() {
      Column() {
        Button("createAnimatorS2D").backgroundColor('#FFFF00FF')
          .onClick((e: ClickEvent) => {
            let options: AnimatorOptions = {
              duration: 3500,
              easing: "ease",
              delay: 1000,
              fill: "forwards",
              direction: "normal",
              iterations: 1,
              begin: 10,
              end: 40,
            };
            let animatorResult = this.getUIContext().createAnimator(options);

            animatorResult.onFrame = (value: number) => {
              this.tSize2 = value;
            }
            let animatorResult2 = transfer.transferDynamic(animatorResult, 'ArkUI.Animator') as Object;
            let moduleName = ESValue.load("library/Index");
            let arrayBufferStatic2Dynamic = moduleName.getProperty('createAnimatorS2D');
            arrayBufferStatic2Dynamic.invoke(animatorResult2);
          })
        Text('createAnimatorS2D').fontSize(this.tSize2)
      }
    }
  }
  ```