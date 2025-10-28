# ArkTS-Dyn使用ArkTS-Sta @Builder按引用传递参数V2状态管理互操作

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lishihao16-->
<!--Designer: @lixingchi1-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

## 概述
状态管理V2互操作@Builder按引用传递参数适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用UI的场景，遵循[语言互操作](../quick-start/arkts-interop-overview.md#交互基本原则)的基本规范。

状态管理V2互操作@Builder按引用传递参数适用于以下场景：
- ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作全局自定义构建函数[@Builder](./state-management/arkts-builder.md)按引用传递参数时，传递的参数可为状态变量，且状态变量的改变会引起@Builder函数内的UI刷新。
- ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作自定义组件[@BuilderParam](./state-management/arkts-builderparam.md)成员属性@Builder按引用传递参数时，传递的参数可为状态变量，且状态变量的改变会引起@Builder函数内的UI刷新。
- ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作[WrappedBuilder](./state-management/arkts-wrapBuilder.md)对象@Builder按引用传递参数时，传递的参数可为状态变量，且状态变量的改变会引起@Builder函数内的UI刷新。

## ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作全局自定义构建函数@Builder

- ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作，涉及到引用类型传参，class必须是ArkTS-Dyn。

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
├── library/         # ArkTS-Sta子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets
│
└── dynamic/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

下面的代码示例展示了在ArkTS-Dyn中使用ArkTS-Sta的@Builder，使用V2状态变量驱动刷新。

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { overBuilder } from 'library';

@Entry
@ComponentV2
struct Index {
  @Local label: string = 'Local Interop';

  build() {
    Column() {
      Column() {
        // 在父组件中调用overBuilder组件时，
        // 把this.label通过引用传递的方式传给overBuilder组件。
        overBuilder({ paramA1: this.label })
        Button('Click me')
          .onClick(() => {
            // 单击Click me后，UI文本从Hello更改为ArkUI。
            this.label = 'ArkUI';
          })
      }
    }
  }
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "library": "file:../library",
  "dynamic": "file:../dynamic",
}
```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出全局自定义构建函数。

```TypeScript
'use static'
// library/src/main/ets/components/MainPage.ets
import { Builder, Row, Text } from '@ohos.arkui.component';
import { Tmp } from 'dynamic';

@Builder
export function overBuilder(params: Tmp) {
  Row() {
    Text(`UseStateVarByReference: ${params.paramA1} `)
  }
}
```

```TypeScript
// library/index.ets
export { overBuilder } from './src/main/ets/components/MainPage';
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic": "file:../dynamic",
}
```

- 创建ArkTS-Dyn子模块`dynamic`，在`dynamic/src/main/ets/components`目录创建并导出Class。

```TypeScript
// dynamic/src/main/ets/components/MainPage.ets
export class Tmp {
  paramA1: string = '';
}
```

```TypeScript
// dynamic/index.ets
export { Tmp } from './src/main/ets/components/MainPage';
```



## ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作自定义组件@BuilderParam成员属性@Builder按引用传递参数

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

下面的代码示例展示了在ArkTS-Dyn中使用ArkTS-Sta的@Builder，使用V2状态变量驱动刷新。

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets

import { CustomContainer } from 'library';

@Entry
@ComponentV2
struct CustomContainerUser {
  @Local text: string = 'header';

  @Builder
  localBuilder() {
    Text(this.text)
      .onClick((value: ClickEvent) => {
        this.text = 'changeHeader';
      })
  }

  build() {
    Column() {
      // 创建CustomContainer，在创建CustomContainer时，通过其后紧跟一个大括号“{}”形成尾随闭包
      // 作为传递给子组件CustomContainer的@BuilderParam 参数 closer: () => void
      CustomContainer() {
        Column() {
          Text(this.text)
        }
        .backgroundColor(Color.Yellow)
        .onClick((value: ClickEvent) => {
          this.text = 'changeHeader';
        })
      }

      // 通过参数初始化 @BuilderParam 成员。
      CustomContainer({ closer: this.localBuilder })
    }
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
'use static'
// library/src/main/ets/components/MainPage.ets
import { ComponentV2, Builder, BuilderParam, Text, Column } from '@ohos.arkui.component';

@ComponentV2
export struct CustomContainer {
  @Builder
  closerBuilder() {
  }

  @BuilderParam closer: () => void = this.closerBuilder;

  build() {
    Column() {
      this.closer()
    }
  }
}
```

```TypeScript
// library/index.ets
export { CustomContainer } from './src/main/ets/components/MainPage';
```

## ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作WrappedBuilder对象@Builder按引用传递参数

- ArkTS-Dyn使用ArkTS-Sta状态管理V2互操作，涉及到引用类型传参，class必须是ArkTS-Dyn。

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
├── library/         # ArkTS-Sta子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets
│
└── dynamic/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```


下面的代码示例展示了在ArkTS-Dyn中使用ArkTS-Sta的@Builder，使用V2状态变量驱动刷新。

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { globalBuilder } from 'library';

@Entry
@ComponentV2
struct MainPage {
  @Local stateVar: string = 'Hello World!';

  build() {
    Column() {
      wBuilder.builder({ paramA2: this.label.paramA2 })
      Button('Click me')
        .onClick((e: ClickEvent) => {
          this.stateVar = 'Hello ArkUI!';
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
  "dynamic": "file:../dynamic",
}
```

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
'use static'
// library/src/main/ets/components/MainPage.ets
import { ComponentV2, Builder, WrappedBuilder, Text, Column } from '@ohos.arkui.component';
import { Tmp } from 'dynamic';

@Builder
function overBuilder(param: Tmp) {
  Column() {
    Text(param.paramA2)
  }
}

export const wBuilder: WrappedBuilder<[Tmp]> = wrapBuilder(overBuilder);
```

```TypeScript
// library/index.ets
export { globalBuilder } from './src/main/ets/components/MainPage';
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic": "file:../dynamic",
}
```

- 创建ArkTS-Dyn子模块`dynamic`，在`dynamic/src/main/ets/components`目录创建并导出Class。

```TypeScript
// dynamic/src/main/ets/components/MainPage.ets

export class Tmp {
  paramA1: string = '';
}
```

```TypeScript
// dynamic/index.ets
export { Tmp } from './src/main/ets/components/MainPage';
```




