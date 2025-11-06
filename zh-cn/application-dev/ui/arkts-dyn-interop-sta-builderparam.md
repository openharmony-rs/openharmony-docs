# ArkTS-Dyn \@Builder函数初始化ArkTS-Sta自定义组件\@BuilderParam成员属性

## 概述
从API version 22开始，支持在ArkTS-Dyn中使用\@Builder函数初始化ArkTS-Sta自定义组件的\@BuilderParam成员属性。适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中引用\@BuilderParam的场景。

使用时需要遵守：
- 语言互操作[交互基本原则](../quick-start/arkts-interop-overview.md#交互基本原则)。
- ArkTS-Dyn自定义构建函数[限制条件](./state-management/arkts-builder.md#限制条件)。
- ArkTS-Sta \@BuilderParam装饰器[限制条件](./state-management/arkts-builderparam.md#限制条件)。

\@Builder的参数传递包括[按值传递](#按值传递)与[按引用传递](#按引用传递)，详见[参数传递规则](./state-management/arkts-builder.md#参数传递规则)。


## 按值传递

初始化\@BuilderParam的\@Builder函数默认按值传递，当传入状态变量时，其变化不会触发\@Builder内部UI刷新

完整示例结构如下所示：

```text
project/
├── entry/                           # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets    # @Builder初始化@BuilderParam
│
└── library/                         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets # 定义@BuilderParam并调用
```

下面的代码示例展示了使用ArkTS-Dyn的\@Builder函数给ArkTS-Sta自定义组件的\@BuilderParam赋值并显示UI。


- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件。

```TypeScript
'use static'

// library/src/main/ets/components/MainPage.ets
import { Component, Builder, BuilderParam, Column } from '@ohos.arkui.component';

@Component
export struct Child {
  @Builder
  myBuilder(str: string) {
  }

  @BuilderParam customBuilderParam: (input: string) => void = this.myBuilder;

  build() {
    Column() {
      this.customBuilderParam('Hello World!')
    }
  }
}
```

```TypeScript
'use static'

// library/index.ets
export { Child } from './src/main/ets/components/MainPage';
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "library": "file:../library"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta的自定义组件，且传递\@Builder。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { Child } from 'library';

@Entry
@Component
struct Parent {
  @Builder
  myText(input: string) {
    Text(input)
  }

  build() {
    Column() {
      Child({customBuilderParam: this.myText})
    }
  }
}
```

## 按引用传递
ArkTS-Dyn使用\@Builder函数初始化ArkTS-Sta\@BuilderParam时，\@Builder仅在接收一个参数且该参数为对象字面量时为引用传递，其余情况均为按值传递。该对象字面量包含状态变量时，其变化会触发\@Builder内部UI刷新。

由于ArkTS-Sta不支持跨语言创建对象字面量，因此ArkTS-Sta创建对象字面量时，需要使用ArkTS-Sta侧的对象。

完整示例结构如下所示：
```text
project/
├── entry/                           # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets    # @Builder初始化@BuilderParam
│
└── library/                         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets # 定义Person类，定义@BuilderParam并引用传递
```

下面的代码示例展示了ArkTS-Dyn使用\@Builder函数初始化ArkTS-Sta\@BuilderParam字面量更新的场景。

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出自定义组件以及class。

```TypeScript
'use static'

// library/src/main/ets/components/MainPage.ets
import { Component, Builder, BuilderParam, Column, Button } from '@ohos.arkui.component';
import { State, Observed } from '@ohos.arkui.stateManagement';

@Observed
export class Person {
  name: string = '';
  age: number = 0;
}

@Component
export struct Child {
  @State name: string = 'Kevin';
  @State age: number = 20;
  @Builder
  myBuilder(person: Person) {
  }
  @BuilderParam customBuilderParam: (person: Person) => void = this.myBuilder;

  build() {
    Column() {
      this.customBuilderParam({name: this.name, age: this.age})
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

```TypeScript
'use static'

// library/index.ets
export { Person, Child } from './src/main/ets/components/MainPage';
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta的自定义组件，传递\@Builder。且在`oh-package.json5`文件中配置子模块依赖。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { Person, Child } from 'library';

@Entry
@Component
struct Parent {
  @Builder
  personInfo(person: Person) {
    Column() {
      Text(`Name: ${person.name}`)
      Text(`Age: ${person.age}`)
      }
  }

  build() {
    Column() {
      Child({customBuilderParam: this.personInfo})
    }
  }
}
```

```json
// entry/oh-package.json5

"dependencies": {
  "library": "file:../library"
}
```