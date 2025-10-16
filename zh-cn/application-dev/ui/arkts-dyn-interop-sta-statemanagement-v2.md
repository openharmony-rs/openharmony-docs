# ArkTS-Dyn使用ArkTS-Sta状态管理V2组件内互操作
状态管理V2互操作适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景，遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。
完整示例结构如下图所示：
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
                    └── MainPage.ets
```

下面的代码示例展示了ArkTS-Dyn与ArkTS-Sta状态变量V2的互操作。

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript

// entry/src/main/ets/pages/Index.ets
import { MainPage } from 'library';

@Entry
@ComponentV2
struct ParentComp {
  @Local message1: string = 'Hello Interop';
  @Provider() message2: string = 'Provider Interop';
  
  build() {
    Column() {
      Button(this.message1)
        .onClick(() => {
          this.message1 += '~';
        })
      Button(this.message2)
        .onClick(() => {
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

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
// library/src/main/ets/components/MainPage.ets
'use static';

import { Entry, ComponentV2, Column, Button, ClickEvent, Text, Color } from '@ohos.arkui.component';
import { Param, Consumer, Event } from '@ohos.arkui.stateManagement';

@ComponentV2
export struct MainPage {
  @Param message1: string = 'static Param';
  @Consumer() message2: string = 'static Consumer';
  @Event changeFactory: () => void = () => {};

  build() {
    Column() {
      Text(this.message1)
        .fontSize(30)
        .fontColor(Color.Blue)
      Text(this.message2)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick((e: ClickEvent) => {
          this.message2 += '!';
        })
      Button('excute changeFactory')
        .onClick((e: ClickEvent) => {
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
'use static';
export { MainPage } from from './src/main/ets/components/MainPage';
```

