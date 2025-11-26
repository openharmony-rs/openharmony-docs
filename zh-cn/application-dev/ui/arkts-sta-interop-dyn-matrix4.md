# 在ArkTS-Sta中使用ArkTS-Dyn的矩阵变换（matrix4）

从API version 22开始，支持在ArkTS-Sta中调用ArkTS-Dyn的[matrix4.init](../reference/apis-arkui/js-apis-matrix4.md#matrix4init)创建四阶矩阵，通过[translate](../reference/apis-arkui/js-apis-matrix4.md#translate)、[scale](../reference/apis-arkui/js-apis-matrix4.md#scale)、[rotate](../reference/apis-arkui/js-apis-matrix4.md#rotate)函数实现组件的平移、缩放、旋转。在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，导出ArkTS-Dyn的四阶矩阵对象，在ArkTS-Sta的页面中直接调用。

完整示例结构如下所示。

```test
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets       # 调用动画文件
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets     # 四阶矩阵创建文件
```

示例如下：

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录创建页面。

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import matrix4 from '@ohos.matrix4';

  export function createMatrixD2S() : object {
    let matrix = matrix4.init(
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
    return matrix;
  }
  
  ```

- 在ArkTS-Dyn子模块`library`中导出页面。

  ```TypeScript
  // library/Index.ets
  export { createMatrixD2S } from './src/main/ets/components/MainPage';

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
  // entry/src/main/ets/pages/Index.ets
  import { Entry, Button, ClickEvent, Column, Component, Text } from '@ohos.arkui.component';
  import { State } from '@ohos.arkui.stateManagement';
  import transfer from '@ohos.transfer';
  import { createMatrixD2S } from 'library';
  import matrix4 from '@ohos.matrix4';

  @Entry
  @Component
  struct Index {
    @State staticMatrix: matrix4.Matrix4Transit = matrix4.identity();

    build() {
      Column() {
        Button("matrixD2S").backgroundColor('#FFFF00FF')
          .onClick((e: ClickEvent) => {
            let myValue = createMatrixD2S();
            this.staticMatrix = transfer.transferStatic(myValue, 'ArkUI.Matrix4') as matrix4.Matrix4Transit;
          })
        Text('Hello World').fontSize(20).transform(this.staticMatrix).margin(40)
      }
    }
  }
  ```