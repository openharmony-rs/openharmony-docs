# 在ArkTS-Sta中使用ArkTS-Dyn的自定义构建函数（@Builder）

## 概述

从API version 23开始，支持在ArkTS-Sta中使用ArkTS-Dyn自定义构建函数([\@Builder](./state-management/arkts-builder.md))。适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中使用@Builder自定义构建函数的场景。


## 使用限制

- 遵守ArkTS-Dyn自定义构建函数[限制条件](./state-management/arkts-builder.md#限制条件)；

- ArkTS-Dyn自定义构建函数的参数最多不超过10个，否则会编译报错。


## 使用场景

\@Builder的参数传递包括[按引用传递](./state-management/arkts-builder.md#按引用传递参数)与[按值传递](./state-management/arkts-builder.md#按值传递参数)，详见[参数传递规则](./state-management/arkts-builder.md#参数传递规则)。


### 按引用传递参数

仅接收一个参数且该参数为对象字面量时为按引用传递参数，其余情况均为按值传递参数。该对象字面量包含状态变量时，其变化会触发\@Builder函数内的UI刷新。

由于ArkTS-Dyn不支持跨语言创建对象字面量，因此ArkTS-Sta创建对象字面量时，需要使用ArkTS-Sta侧的对象。

如下示例展示了ArkTS-Sta引用ArkTS-Dyn自定义构建函数按引用传递参数的场景。

完整示例结构如下所示：

```text
project/
├── entry/                             # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets      # 调用@Builder并按引用传递
│
└── static_module/                     # ArkTS-Sta子模块
│   └── src/
│       └── main/
│           └── ets/
│               └── components/
│                   └── MainPage.ets    # Person类定义
│
└── dynamic_module/                     # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets    # 定义@Builder
```

示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录创建并导出`Person`类。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
export class Person { // ArkTS-Sta侧的对象字面量类型
  name: string = '';
  age: number = 0;
}
```

```TypeScript
'use static'

// static_module/index.ets
export { Person } from './src/main/ets/components/MainPage'; // 导出ArkTS-Sta Person类
```

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出自定义构建函数。且在`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets
import { Person } from 'static_module';

@Builder
export function personInfo(person: Person) { // 按引用传递参数
  Column(){
    Text(`Name: ${person.name}`)
    Text(`Age: ${person.age}`)
  }
}
```

```TypeScript
// dynamic_module/index.ets
export { personInfo } from './src/main/ets/components/MainPage';
```

```json
// dynamic_module/oh-package.json5

"dependencies": {
  "static_module": "file:../static_module"
}
```

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn自定义构建函数。且在`oh-package.json5`文件中配置子模块依赖。

```TypeScript
'use static'

// entry/src/main/ets/pages/Index.ets
import { Entry, Component, Column, Button } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

import { personInfo } from 'dynamic_module';

@Entry
@Component
struct Parent {
  @State name: string = 'Kevin';
  @State age: number = 20;

  build() {
    Column() {
      // 传入对象字面量，状态变量的改变引起@Builder的UI刷新
      personInfo({ name: this.name, age: this.age })
      Button('changeName')
        .onClick(() => {
          // 变化状态变量name，触发@Builder内部UI刷新
          this.name += 'a';
        })
      Button('changeAge')
        .onClick(() => {
          // 变化状态变量age，触发@Builder内部UI刷新
          this.age += 1;
        })
    }
  }
}
```

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module"
}
```


### 按值传递参数

调用@Builder函数默认按值传递，当传入状态变量时，其变化不会触发@Builder内部UI刷新。

完整示例结构如下图所示：

```text
project/
├── entry/                            # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets     # 调用@Builder并按值传递参数
│
└── dynamic_module/                   # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets   # 定义@Builder并导出
```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出@Builder自定义构建函数。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

@Builder
export function showTextBuilder(input: string) { // 按值传递参数，不会触发UI刷新
  Text(input)
    .fontSize(30)
}
```

```TypeScript
// dynamic_module/index.ets

export { showTextBuilder } from './src/main/ets/components/MainPage'; // 导出@Builder函数
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn自定义构建函数。

```TypeScript
'use static'

// entry/src/main/ets/pages/Index.ets
import { Entry, Component, Column } from '@ohos.arkui.component';

import { showTextBuilder } from 'dynamic_module'; // 引入@Builder函数

@Entry
@Component
struct MainPage {
  build() {
    Column() {
      // 直接使用ArkTS-Dyn自定义构建函数
      showTextBuilder('Hello World!')
    }
    .width('100%')
    .height('100%')
  }
}
```


### 按回调函数传递参数

不支持通过[`UIUtils.makeBinding()`函数、`Binding`类、`MutableBinding`类](./state-management/arkts-builder.md#@Builder支持状态变量刷新)实现@Builder函数中状态变量的刷新。
