# ArkTS-Dyn使用ArkTS-Sta状态管理互操作

## 概述
从API version 22开始，支持在ArkTS-Dyn中使用ArkTS-Sta组件进行状态管理互操作。适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景，并遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。


完整示例结构如下图所示：

```text
project/
├── entry/          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── library/         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

下面的代码示例展示了在ArkTS-Dyn中与ArkTS-Sta状态变量进行互操作。

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { MainPage } from 'library';

@Entry
@Component
struct ParentComp {
  @State message: string = 'Hello Interop';
  @Provide message5: string = 'Provide Interop';

  build() {
    Column() {
      Button(this.message)
        .onClick((e: ClickEvent) => {
          this.message += '~';
        })
      MainPage({
        message1: this.message,
        message2: this.message,
        message3: this.message,
        message4: this.message,
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
  "library": "file:../library"
}
```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
'use static'

// library/src/main/ets/components/MainPage.ets
import { Component, Column, Text, Color } from '@ohos.arkui.component';
import { State, Link, PropRef, Provide, Consume } from '@ohos.arkui.stateManagement';

@Component
export struct MainPage {
  @State message1: string = 'static State';
  @Link message2: string;
  @PropRef message3: string = 'static Prop';
  @Provide message4: string = 'static Provide';
  @Consume message5: string;

  build() {
    Column() {
      Text(this.message1)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message1 += '!';
        })
      Text(this.message2)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message2 += '!';
        })
      Text(this.message3)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message3 += '!';
        })
      Text(this.message4)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message4 += '!';
        })
      Text(this.message5)
        .fontSize(30)
        .fontColor(Color.Blue)
        .onClick(() => {
          this.message5 += '!';
        })
    }
    .padding(20)
    .backgroundColor(Color.White)
  }
}
```

```TypeScript
'use static'

// library/index.ets
export { MainPage } from './src/main/ets/components/MainPage';
```