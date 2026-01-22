# 在ArkTS-Sta中使用ArkTS-Dyn的自定义组件

## 概述

从API version 23开始，支持在[ArkTS-Sta](../quick-start/arkts-interop-overview.md)中使用ArkTS-Dyn自定义组件。

在互操作场景下，[占位组件](../reference/apis-arkui/arkui-ts/ts-interop-compatible-component.md)链接ArkTS-Sta和ArkTS-Dyn的UI节点，构建完整的UI界面。


## 使用限制

- 在ArkTS-Sta中，不能对ArkTS-Dyn的自定义组件设置通用样式，否则会导致编译错误；

```TypeScript
'use static'

// entry/src/main/ets/pages/Index.ets
import { Entry, Component, Column, Stack } from '@ohos.arkui.component';
import { MainPage } from 'dynamic_module'; // 从ArkTS-Dyn模块中导入

@Entry
@Component
struct Index {

  build() {
    Column() {
      // 不支持对ArkTS-Dyn自定义组件设置通用样式，如下代码将产生编译报错
      MainPage({ message: 'Hello World!' })
        .width(100)

      // 可以通过嵌套一个ArkTS-Sta Stack组件，将通用样式设置在Stack组件上
      Stack() {
        MainPage({ message: 'Hello World!' })
      }
      .width(100)
    }
  }
}
```

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets
@Component
export struct MainPage { // 从ArkTS-Dyn模块中导出
  message: string = '';

  build() {
    Text(this.message)
      .fontSize(30)
  }
}
```

- ArkTS-Sta中不支持通过[@Reusable](state-management/arkts-reusable.md)/[@ReusableV2](state-management/arkts-new-reusableV2.md)装饰器复用ArkTS-Dyn自定义组件。


## 使用场景

ArkUI互操作能力支持在ArkTS-Sta中使用ArkTS-Dyn的自定义组件，包括创建并传递参数。

基于以下示例结构，说明在ArkTS-Sta中使用ArkTS-Dyn的自定义组件的场景。

```text
project/
├── entry/                          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets    # ArkTS-Sta主模块入口页面
│
└── dynamic_module/                  # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets # 定义ArkTS-Dyn自定义组件并导出
```

示例如下：

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

@Component
export struct ChildComponent {
  message: string = 'Hello World!';

  build() {
    Column() {
      Text(this.message)
        .fontSize(30)
        .fontColor(Color.Blue)
    }
    .padding(20)
    .backgroundColor(Color.White)
  }
}

@ComponentV2
export struct ChildComponentV2 {
  message: string = 'Hello WorldV2!';

  build() {
    Column() {
      Text(this.message)
        .fontSize(30)
        .fontColor(Color.Blue)
    }
    .padding(20)
    .backgroundColor(Color.White)
  }
}
```

```TypeScript
// dynamic_module/index.ets

export { ChildComponent, ChildComponentV2 } from './src/main/ets/components/MainPage';
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module"
}
```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn自定义组件。

```TypeScript
'use static'

// entry/src/main/ets/pages/Index.ets
import { Entry, Component, Column, ComponentV2 } from '@ohos.arkui.component';

import { ChildComponent, ChildComponentV2 } from 'dynamic_module';

@Entry
@Component
struct Index {
  build() {
    Column() {
      // 直接使用ArkTS-Dyn自定义组件
      ChildComponent()

      // 也可以将ArkTS-Dyn自定义组件封装在ArkTS-Sta自定义组件中嵌套使用
      MainPage()

      IndexV2()
    }
    .width('100%')
    .height('100%')
  }
}

@Component
struct MainPage {
  build() {
    Column() {
      ChildComponent()
    }
  }
}

@ComponentV2
struct IndexV2 {
  build() {
    Column() {
      // 直接使用ArkTS-Dyn自定义组件
      ChildComponentV2()

      // 也可以将ArkTS-Dyn自定义组件封装在ArkTS-Sta自定义组件中嵌套使用
      MainPageV2()
    }
    .width('100%')
    .height('100%')
  }
}

@ComponentV2
struct MainPageV2 {
  build() {
    Column() {
      ChildComponentV2()
    }
  }
}
```
