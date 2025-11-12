# ArkTS-Sta使用ArkTS-Dyn状态管理V2组件内互操作
状态管理V2互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景，遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。
完整示例结构如下图所示：
```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── MainPage.ets
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

下面的代码示例展示了在ArkTS-Sta中与ArkTS-Dyn状态变量V2进行互操作。

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets
'use static';

import { Entry, ComponentV2, Column, Button, ClickEvent } from '@ohos.arkui.component';
import { Local, Provider } from '@ohos.arkui.stateManagement';

import { MainPage } from 'library';

@Entry
@ComponentV2
struct ParentComp {
  @Local message1: string = 'Local Interop';
  @Provider() message2: string = 'Provider Interop';
  
  build() {
    Column() {
      Button(this.message1)
        .onClick((e: ClickEvent) => {
          this.message1 += '~';
        })
      Button(this.message2)
        .onClick((e: ClickEvent) => {
          this.message2 += '~';
        })
      MainPage({
        message1: this.message1,
        changeFactory: () => {
          this.message2 += '@Event';
        }
      })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
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

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
// library/src/main/ets/components/MainPage.ets

@ComponentV2
export struct MainPage {
  @Param message1: string = 'dynamic Param';
  @Consumer() message2: string = 'dynamic Consumer';
  @Event changeFactory: () => void = () => {};

  build() {
    Column() {
      Text(this.message1)
        .fontSize(30)
        .fontColor(Color.Blue)
      Text(this.message2)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message2 += '!';
        })
      Button('excute changeFactory')
        .onClick(() => {
          this.changeFactory();
        })
    }
    .padding(20)
    .backgroundColor(Color.White)
  }
}
```

```TypeScript
// library/index.ets
export { MainPage } from from './src/main/ets/components/MainPage';
```