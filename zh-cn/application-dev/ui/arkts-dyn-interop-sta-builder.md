# 在ArkTS-Dyn中使用ArkTS-Sta的自定义构建函数（@Builder）

## 概述

从API version 23开始，支持在ArkTS-Dyn中使用ArkTS-Sta自定义构建函数([\@Builder](./state-management/arkts-builder.md))。适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中引用\@Builder函数的场景。


## 使用限制

- 遵守ArkTS-Sta自定义构建函数[限制条件](./state-management/arkts-builder.md#限制条件)。


## 使用场景

\@Builder的参数传递包括[按引用传递](./state-management/arkts-builder.md#按引用传递参数)与[按值传递](./state-management/arkts-builder.md#按值传递参数)，详见[参数传递规则](./state-management/arkts-builder.md#参数传递规则)。


### 按引用传递参数

仅在接收一个参数且该参数为对象字面量时为引用传递，其余情况均为按值传递。该对象字面量包含状态变量时，其变化会触发\@Builder内部UI刷新。

由于ArkTS-Sta不支持跨语言创建对象字面量，因此ArkTS-Dyn创建对象字面量时，需要使用ArkTS-Dyn侧的对象。

如下示例展示了ArkTS-Dyn引用ArkTS-Sta自定义构建函数按引用传递参数的场景。

完整示例结构如下所示：
```text
project/
├── entry/                           # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets    # 调用@Builder并按引用传递
│
└── dynamic_module/                  # ArkTS-Dyn子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets  # Person类定义
│
└── static_module/                    # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 定义全局@Builder
```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并并导出`Person`类。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

// 定义Person对象字面量类，用于@Builder函数参数类型
export class Person {
  name: string = '';
  age: number = 0;
}
```

```TypeScript
// dynamic_module/index.ets

export { Person } from './src/main/ets/components/MainPage'; // 导出ArkTS-Dyn Person类
```

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录创建并导出全局自定义构建函数。且在`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Builder, Text, Column } from '@ohos.arkui.component';
import { Person } from 'dynamic_module'; // 引入ArkTS-Dyn侧的Person类

@Builder
export function personInfo(person: Person) { // 按引用传递参数，需传入对象字面量
  Column(){
    Text(`Name: ${person.name}`)
    Text(`Age: ${person.age}`)
  }
}
```

```TypeScript
'use static'

// static_module/index.ets
export { personInfo } from './src/main/ets/components/MainPage'; // 导出ArkTS-Sta @Builder函数
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
import { personInfo } from 'static_module'; // 引入@Builder函数

@Entry
@Component
struct Parent {
  @State name: string = 'Kevin';
  @State age: number = 20;
  build() {
    Column() {
      // 传入对象字面量，状态变量的改变引起@Builder的UI刷新
      personInfo({name: this.name, age: this.age})
      Button('changeName')
        .onClick(() => {
          // 变化name状态变量，触发@Builder内部UI刷新
          this.name += 'a';
        })
      Button('changeAge')
        .onClick(() => {
          // 变化age状态变量，触发@Builder内部UI刷新
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

调用\@Builder函数默认按值传递，当传入状态变量时，其变化不会触发\@Builder内部UI刷新。

基于以下示例结构，说明在ArkTS-Dyn中引用ArkTS-Sta的全局自定义构建函数显示UI的场景。

```text
project/
├── entry/                            # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用@Builder并按值传递参数
│
└── static_module/                    # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # 定义全局@Builder

```

示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录创建并导出全局自定义构建函数。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Builder, Text } from '@ohos.arkui.component';

@Builder
export function showTextBuilder(input: string) { // 按值传递参数，不会触发UI刷新
  Text(input)
    .fontSize(30)
}
```

```TypeScript
'use static'

// static_module/index.ets
export { showTextBuilder } from './src/main/ets/components/MainPage';
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "static_module": "file:../static_module"
}
```

- 在ArkTS-Dyn主模块`entry`中引入ArkTS-Sta全局自定义构建函数。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { showTextBuilder } from 'static_module'; // 引入@Builder函数

@Entry
@Component
struct Parent {
  build() {
    Column() {
      // 使用@Builder函数显示文本
      showTextBuilder('Hello World!')
    }
    .width('100%')
    .height('100%')
  }
}
```


### 按回调函数传递参数

不支持通过[`UIUtils.makeBinding()`函数、`Binding`类、`MutableBinding`类](./state-management/arkts-builder.md#@Builder支持状态变量刷新)实现@Builder函数中状态变量的刷新。
