# 在ArkTS-Dyn中使用ArkTS-Sta的wrapBuilder（封装全局@Builder）

## 概述

从API version 23开始，支持在ArkTS-Dyn中使用ArkTS-Sta的[WrappedBuilder对象](./state-management/arkts-wrapBuilder.md)。适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中封装全局[\@Builder](./state-management/arkts-builder.md)的场景。


## 限制条件

- 遵循ArkTS-Sta WrappedBuilder对象的使用[限制条件](./state-management/arkts-wrapBuilder.md#限制条件)。


## 使用场景

\@Builder的参数传递包括[按值传递](#按值传递)与[按引用传递](#按引用传递)，详见[参数传递规则](./state-management/arkts-builder.md#参数传递规则)。


### 按引用传递参数

ArkTS-Dyn调用ArkTS-Sta WrappedBuilder对象时，封装的\@Builder仅在接收一个参数且该参数为对象字面量时为引用传递，其余情况均为按值传递。该对象字面量包含状态变量时，其变化会触发\@Builder函数内部UI刷新。

由于ArkTS-Sta不支持跨语言创建对象字面量，因此ArkTS-Dyn创建对象字面量时，需要使用ArkTS-Dyn侧的对象。

基于以下示例结构，说明在ArkTS-Dyn中引用ArkTS-Sta WrappedBuilder对象字面量更新的场景。

```text
project/
├── entry/                             # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets      # 调用WrappedBuilder对象并按引用传递参数
│
└── dynamic_module/                    # ArkTS-Dyn子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets    # Person类定义
│
│
└── static_module/                      # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets    # 定义WrappedBuilder对象
```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出class。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

// 定义Person类，作为对象字面量的类型
export class Person {
  name: string = '';
  age: number = 0;
}
```

```TypeScript
// dynamic_module/index.ets

export { Person } from './src/main/ets/components/MainPage'; // 导出Person类
```

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录创建并导出WrappedBuilder对象。且在`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Builder, WrappedBuilder, wrapBuilder, Text, Column } from '@ohos.arkui.component';
import { Person } from 'dynamic_module'; // 引入ArkTS-Dyn子模块的Person类

@Builder
function personInfo(person: Person) { // 按引用传递参数，对象字面量包含状态变量时，其变化会触发UI刷新
  Column() {
    Text(`Name: ${person.name}`)
    Text(`Age: ${person.age}`)
  }
}

export const globalBuilder: WrappedBuilder<@Builder (person: Person) => void> = wrapBuilder(personInfo);
```

```TypeScript
'use static'

// static_module/index.ets
export { globalBuilder } from './src/main/ets/components/MainPage'; // 导出WrappedBuilder对象
```

```json
// static_module/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta全局自定义构建函数。且在`oh-package.json5`文件中配置子模块依赖。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { globalBuilder } from 'static_module'; // 引入WrappedBuilder对象

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
          // 修改name状态变量，触发UI刷新
          this.name += 'a';
        })
      Button('changeAge')
        .onClick(() => {
          // 修改age状态变量，触发UI刷新
          this.age += 1;
        })
    }
  }
}
```

```json
// entry/oh-package.json5

"dependencies": {
  "static_module": "file:../static_module"
}
```


### 按值传递参数

wrapBuilder封装的\@Builder函数默认按值传递，当传入状态变量时，其变化不会触发\@Builder内部UI刷新。

基于以下示例结构，说明在ArkTS-Dyn中引用ArkTS-Sta的WrappedBuilder对象显示UI的场景。

```text
project/
├── entry/                            # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用WrappedBuilder对象
│
└── static_module/                    # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 定义WrappedBuilder对象

```

示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录创建并导出WrappedBuilder对象。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Builder, WrappedBuilder, wrapBuilder, Text } from '@ohos.arkui.component';

@Builder
function showTextBuilder(input: string) { // 按值传递参数，状态变量变化不会触发UI刷新
  Text(input)
    .fontSize(30)
}

// 使用wrapBuilder封装全局@Builder并导出
export const globalBuilder: WrappedBuilder<@Builder (input: string) => void> = wrapBuilder(showTextBuilder);
```

```TypeScript
'use static'

// static_module/index.ets
export { globalBuilder } from './src/main/ets/components/MainPage'; // 导出WrappedBuilder对象
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "static_module": "file:../static_module"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta WrappedBuilder对象。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { globalBuilder } from 'static_module'; // 引入WrappedBuilder对象

@Entry
@Component
struct Parent {
  @State inputText: string = 'Hello ArkTS-Dyn!';

  build() {
    Column() {
      // 状态变量的改变不会引起@Builder的UI刷新
      globalBuilder.builder(this.inputText)
    }
    .width('100%')
    .height('100%')
  }
}
```


## 常见问题

### 声明文件编译报错

由于[ArkTS-Sta wrapBuilder](./state-management/arkts-static-wrapBuilder.md#接口说明)与[ArkTS-Dyn wrapBuilder](./state-management/arkts-wrapBuilder.md#接口说明)的接口规格不一致，在部分复杂的WrappedBuilder场景下，编译时生成的ArkTS-Dyn声明文件可能报错，需要开发者手动修改声明文件报错位置后增量编译，以符合ArkTS-Dyn WrappedBuilder的语法规格。

以上文[按值传递参数](#按值传递参数)示例为例，定义WrappedBuilder的ArkTS-Sta源文件为`library/src/main/ets/components/MainPage.ets`，对应生成的ArkTS-Dyn声明文件位于`library/build/default/intermediates/declgen/default/declgenV1/library/src/main/ets/components/MainPage.d.ets`。正确的声明文件示例如下。

```TypeScript
import type { Record } from "../../../../../static.Record";

// ArkTS-Sta源码中使用：WrappedBuilder<@Builder (input: string) => void>
// ArkTS-Dyn声明文件修改为：WrappedBuilder<[string]>
// 如遇编译报错，参考本示例将生成写法替换为符合ArkTS-Dyn语法的形式
@Builder
export declare const globalBuilder: WrappedBuilder<[string]>;
```
