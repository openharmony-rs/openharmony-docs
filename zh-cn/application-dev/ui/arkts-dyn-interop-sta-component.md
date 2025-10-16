# 在ArkTS-Dyn中使用ArkTS-Sta自定义组件

从API version 20开始，UI自定义组件互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景。

完整示例结构如下：

```text
project/
├── entry/          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── MainPage.ets
│
└── library/         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── ChildComponent.ets
```

ArkUI互操作能力支持动态上下文调用静态模块的自定义组件，包括创建并传递参数。

以下示例展示了如何在动态上下文中使用静态模块的自定义组件。

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

  ```TypeScript
  'use static'

  // library/src/main/ets/components/ChildComponent.ets
  import { Text, Column, Component, ComponentV2, Color } from '@ohos.arkui.component';

  @Component
  export struct ChildComponentV1 {
    message: string = 'Hello World V1!';
  
    build() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontColor(Color.Blue)
      }
      .padding(20)
      .backgroundColor('#F1E666')
    }
  }

  @ComponentV2
  export struct ChildComponentV2 {
    message: string = 'Hello World V2!';
  
    build() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontColor(Color.Blue)
      }
      .padding(20)
      .backgroundColor(Color.White)
    }
  }
  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5
  
  "dependencies": {
    "library": "file:../library",
  }
  ```

- 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

  ```TypeScript
  // entry/src/main/ets/pages/MainPage.ets
  import { ChildComponentV1, ChildComponentV2 } from 'library';

  @Entry
  @Component
  struct MainPageV1 {
    build() {
      Column() {
        // 无需显式使用占位组件API，框架会自动处理
        ChildComponentV1()
        ChildComponentV2()
        MainPageV2()
      }
      .width('100%')
      .height('100%')
      .backgroundColor('#FFF3F5')
    }
  }

  @ComponentV2
  struct MainPageV2 {
    build() {
      Column() {
        // 无需显式使用占位组件API，框架会自动处理
        ChildComponentV1()
        ChildComponentV2()
      }
      .width('100%')
    }
  }
  ```