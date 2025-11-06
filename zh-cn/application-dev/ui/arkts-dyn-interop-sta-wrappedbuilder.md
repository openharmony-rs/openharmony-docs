# ArkTS-Dyn使用ArkTS-Sta WrappedBuilder对象

## 概述

从API version 22开始，支持在ArkTS-Dyn中使用ArkTS-Sta的WrappedBuilder对象。适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中封装全局\@Builder的场景。使用时需要遵守语言互操作[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)，以及ArkTS-Sta wrapBuilder方法[限制条件](./state-management/arkts-wrapBuilder.md#限制条件)。

\@Builder的参数传递包括[按值传递](#按值传递)与[按引用传递](#按引用传递)，详见[参数传递规则](./state-management/arkts-builder.md#参数传递规则)。

## 按值传递

WrapBuilder封装的\@Builder函数默认按值传递，当传入状态变量时，其变化不会触发\@Builder内部UI刷新。

完整示例结构如下所示：

```text
project/
├── entry/                            # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用WrappedBuilder
│
└── library/                          # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 定义WrappedBuilder

```

下面的代码示例展示了在ArkTS-Dyn中引用ArkTS-Sta的WrappedBuilder对象显示UI。

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出WrappedBuilder对象。

```TypeScript
'use static'

// library/src/main/ets/components/MainPage.ets
import { Builder, WrappedBuilder, wrapBuilder, Text } from '@ohos.arkui.component';

@Builder
function showTextBuilder(input: string) {
  Text(input)
    .fontSize(30)
}
export const globalBuilder: WrappedBuilder<@Builder (input: string) => void> = wrapBuilder(showTextBuilder);
```

```TypeScript
'use static'

// library/index.ets
export { globalBuilder } from './src/main/ets/components/MainPage';
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "library": "file:../library"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta WrappedBuilder对象。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { globalBuilder } from 'library';

@Entry
@Component
struct Parent {
  build() {
    Column() {
      globalBuilder.builder('Hello World!')
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
  }
}
```

## 按引用传递

ArkTS-Dyn调用ArkTS-Sta WrappedBuilder对象时，封装的\@Builder仅在接收一个参数且该参数为对象字面量时为引用传递，其余情况均为按值传递。该对象字面量包含状态变量时，其变化会触发\@Builder函数内部UI刷新。

由于ArkTS-Sta不支持跨语言创建对象字面量，因此ArkTS-Dyn创建对象字面量时，需要使用ArkTS-Dyn侧的对象。

完整示例结构如下所示：
```text
project/
├── entry/                          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets   # 调用WrappedBuilder并引用传递
│
└── dyn_library/                    # ArkTS-Dyn子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets # Person类定义
│
│
└── sta_library/                     # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets # 定义WrappedBuilder
```

下面的代码示例展示了ArkTS-Dyn引用ArkTS-Sta WrappedBuilder对象字面量更新的场景。

- 创建ArkTS-Dyn子模块`dyn_library`，在`dyn_library/src/main/ets/components`目录创建并导出class。

```TypeScript
// dyn_library/src/main/ets/components/MainPage.ets

export class Person {
  name: string = '';
  age: number = 0;
}
```

```TypeScript
// dyn_library/index.ets

export { Person } from './src/main/ets/components/MainPage';
```

- 创建ArkTS-Sta子模块`sta_library`，在`sta_library/src/main/ets/components`目录创建并导出WrappedBuilder对象。且在`oh-package.json5`文件中配置子模块依赖。

```TypeScript
'use static'

// sta_library/src/main/ets/components/MainPage.ets
import { Builder, WrappedBuilder, wrapBuilder, Text, Column } from '@ohos.arkui.component';
import { Person } from 'dyn_library';

@Builder
function personInfo(person: Person) {
  Column(){
    Text(`Name: ${person.name}`)
    Text(`Age: ${person.age}`)
  }
}

export const globalBuilder: WrappedBuilder<@Builder (person: Person) => void> = wrapBuilder(personInfo);
```

```TypeScript
'use static'

// sta_library/index.ets
export { globalBuilder } from './src/main/ets/components/MainPage';
```

```json
// sta_library/oh-package.json5

"dependencies": {
  "dyn_library": "file:../dyn_library"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta全局自定义构建函数。且在`oh-package.json5`文件中配置子模块依赖。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { globalBuilder } from 'sta_library';

@Entry
@Component
struct Parent {
  @State name: string = 'Kevin';
  @State age: number = 20;
  build() {
    Column() {
      // 传入对象字面量，状态变量的改变引起@Builder的UI刷新
      globalBuilder.builder({name: this.name, age: this.age})
      Button('changeName')
        .onClick(() => {
          this.name += 'a';
        })
      Button('changeAge')
        .onClick(() => {
          this.age += 1;
        })
    }
  }
}
```

```json
// entry/oh-package.json5

"dependencies": {
  "sta_library": "file:../sta_library"
}
```