# 在ArkTS-Dyn中使用ArkTS-Sta的矩阵变换（matrix4）

从API version 22开始，支持在ArkTS-Dyn中调用ArkTS-Sta的[matrix4.init](../reference/apis-arkui/js-apis-matrix4.md#matrix4init)创建四阶矩阵，通过[translate](../reference/apis-arkui/js-apis-matrix4.md#translate)、[scale](../reference/apis-arkui/js-apis-matrix4.md#scale)、[rotate](../reference/apis-arkui/js-apis-matrix4.md#rotate)函数实现组件的平移、缩放、旋转。在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，导出ArkTS-Sta的接口，在ArkTS-Dyn的页面中直接调用。

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
                    └── MainPage.ets      # 四阶矩阵创建文件
```

示例如下：

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建页面。

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import { Button, ClickEvent, Column, Component, Color, Row } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import matrix4 from '@ohos.matrix4';

  @Component
  export struct createMatrixS2D {
    @State matrix: matrix4.Matrix4Transit = matrix4.identity();

    build() {
      Row(){
        Column() {
          Button("matrixS2D").backgroundColor('#FFFF00FF')
            .onClick((e: ClickEvent) => {
              this.matrix = matrix4.init(
                [1.0, 0.0, 0.0, 0.0,
                  0.0, 1.0, 0.0, 0.0,
                  0.0, 0.0, 1.0, 0.0,
                  0.0, 0.0, 0.0, 1.0])
                .translate({ x: 50, y: 50 })
                .scale({ x: 2, y: 2 })
                .rotate({
                  x: 1,
                  y: 1,
                  z: 2,
                  angle: 30
                });
            })
        
          Column() {}
          .width(100)
          .height(100)
          .margin(50)
          .backgroundColor(Color.Red)
          .transform(this.matrix)
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
  export { createMatrixS2D } from './src/main/ets/components/MainPage'

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
  import { createMatrixS2D } from 'library';

  @Entry
  @Component
  struct Index {

    build() {
      Column() {
          createMatrixS2D()
      }.height(400).backgroundColor("#99489ee0")
    }
  }
  ```