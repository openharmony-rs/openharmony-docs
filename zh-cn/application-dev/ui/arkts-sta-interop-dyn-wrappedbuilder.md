# 在ArkTS-Sta中使用ArkTS-Dyn的wrapBuilder（封装全局@Builder）

## 概述

从API version 23开始，支持在ArkTS-Sta中使用ArkTS-Dyn的[WrappedBuilder对象](./state-management/arkts-wrapBuilder.md)。适用于[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)中封装全局[\@Builder](./state-management/arkts-builder.md)的场景。

在互操作场景下，[compatibleWrappedBuilder方法](../reference/apis-arkui/arkui-ts/ts-interop-compatible-WrappedBuilder.md)将ArkTS-Dyn的WrappedBuilder对象转换为占位组件，从而链接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。


## 使用限制

- 遵循ArkTS-Dyn WrappedBuilder对象的[使用限制](./state-management/arkts-wrapBuilder.md#限制条件)；

- `compatibleWrappedBuilder`函数建议在自定义组件的build函数或者\@Builder函数内使用；

- `compatibleWrappedBuilder`函数的第一个参数需要传递ArkTS-Dyn的WrappedBuilder对象，传递其他类型对象会导致UI异常；

- `compatibleWrappedBuilder`函数支持的\@Builder函数的参数最多不超过10个，否则将引发运行时异常。

## 使用场景

由于动静态类型差异，ArkTS-Dyn的WrappedBuilder对象类型在ArkTS-Sta上下文中被转换为了Any类型，UI互操作编译工具无法对Any类型进行编译期适配优化，因此开发者需要显式调用互操作接口[compatibleWrappedBuilder](../reference/apis-arkui/arkui-ts/ts-interop-compatible-WrappedBuilder.md)来使用ArkTS-Dyn的WrappedBuilder对象。


基于以下示例结构，说明在ArkTS-Sta上下文中使用动态WrappedBuilder对象的场景。

```text
project/
├── entry/                           # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── MainPage.ets  # ArkTS-Sta主模块入口页面
│
└── dynamic_module/                   # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets  # ArkTS-Dyn子模块页面，导出WrappedBuilder对象
```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出WrappedBuilder对象。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

// 定义字面量类
class Tmp {
  prop: string = 'Hello World!';
}

@Builder
function overBuilder(param: Tmp) { // 按引用传递参数，可以触发UI更新
  Column() {
    Text(param.prop)
  }
}

// 导出WrappedBuilder对象
export const globalBuilder: WrappedBuilder<[Tmp]> = wrapBuilder(overBuilder);
```

```TypeScript
// dynamic_module/index.ets

export { globalBuilder } from './src/main/ets/components/MainPage'; // 导出WrappedBuilder对象
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn WrappedBuilder对象。

```TypeScript
'use static'

// entry/src/main/ets/pages/MainPage.ets
import { Entry, Component, Column, Button, ClickEvent, compatibleWrappedBuilder } from '@ohos.arkui.component';
import { State } from '@ohos.arkui.stateManagement';

import { globalBuilder } from 'dynamic_module'; // 引入ArkTS-Dyn模块导出的WrappedBuilder对象

@Entry
@Component
struct MainPage {
  @State stateVar: string = 'Hello World!';
  flag: boolean = true;

  build() {
    Column() {
      // 构造WrappedBuilder函数的参数对象
      let globalBuilderParam = ESValue.instantiateEmptyObject();
      // 设置参数prop的值为@State变量
      globalBuilderParam.setProperty(ESValue.wrap('prop'), ESValue.wrap(this.stateVar))
      // 显式使用占位compatibleWrappedBuilder函数，链接ArkTS-Dyn的WrappedBuilder对象
      compatibleWrappedBuilder(globalBuilder, globalBuilderParam)

      Button('Click me').onClick((e: ClickEvent) => {
        // 点击按钮时更新@State变量，触发UI更新
        this.flag = !this.flag;
        if (this.flag) {
          this.stateVar = 'Hello static!';
        } else {
          this.stateVar = 'Hello dynamic!';
        }
      })
    }
    .width('100%')
    .height('100%')
  }
}
```
