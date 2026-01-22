# 在ArkTS-Dyn中使用ArkTS-Sta自定义组件

## 概述

从API version 23开始，支持在ArkTS-Dyn中使用[ArkTS-Sta](../quick-start/arkts-interop-overview.md)自定义组件。


## 使用限制

- 在ArkTS-Dyn中，不能对ArkTS-Sta的自定义组件设置通用样式，否则会导致编译错误；

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { MainPage } from 'static_module'; // 从ArkTS-Sta模块中导入

@Entry
@Component
struct Index {

  build() {
    Column() {
      // 不支持对ArkTS-Sta自定义组件设置通用样式，如下代码将产生编译报错
      MainPage({ message: 'Hello World!' })
        .width(100)

      // 可以通过嵌套一个ArkTS-Dyn Stack组件，将通用样式设置在Stack组件上
      Stack() {
        MainPage({ message: 'Hello World!' })
      }
      .width(100)
    }
  }
}
```

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Text, Component } from '@ohos.arkui.component';

@Component
export struct MainPage { // 从ArkTS-Sta模块中导出
  message: string = '';

  build() {
    Text(this.message)
      .fontSize(30)
  }
}
```

- ArkTS-Dyn中不支持通过[@Reusable](state-management/arkts-reusable.md)/[@ReusableV2](state-management/arkts-new-reusableV2.md)装饰器复用ArkTS-Sta自定义组件。


## 使用场景

ArkUI互操作能力支持在ArkTS-Dyn中使用ArkTS-Sta的自定义组件，包括创建并传递参数。

基于以下示例结构，说明在ArkTS-Dyn中使用ArkTS-Sta的自定义组件的场景。

```text
project/
├── entry/                            # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets      # 在ArkTS-Dyn中引入并使用ArkTS-Sta自定义组件
│
└── static_module/                     # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets   # 定义ArkTS-Sta自定义组件并导出
```

示例如下：

- 创建ArkTS-Sta子模块`static_module`，在`static_module/src/main/ets/components`目录创建并导出自定义组件。如何创建子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```TypeScript
'use static'

// static_module/src/main/ets/components/MainPage.ets
import { Text, Column, Component, ComponentV2, Color } from '@ohos.arkui.component';

@Component
export struct ChildComponentV1 {
  message: string = 'Hello World V1!';

  build() {
    Column() {
      Text(this.message)
        .fontSize(30)
    }
    .padding(20)
  }
}

@ComponentV2
export struct ChildComponentV2 {
  message: string = 'Hello World V2!';

  build() {
    Column() {
      Text(this.message)
        .fontSize(30)
    }
    .padding(20)
  }
}
```

```TypeScript
'use static'

// static_module/Index.ets
export { ChildComponentV1, ChildComponentV2 } from './src/main/ets/components/MainPage';
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。如何导入和使用子模块参考共享包（[HAR](../quick-start/har-package.md)）说明。

```json
// entry/oh-package.json5

"dependencies": {
  "static_module": "file:../static_module"
}
```

- 在ArkTS-Dyn主模块中引入ArkTS-Sta组件。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { ChildComponentV1, ChildComponentV2 } from 'static_module';

@Entry
@Component
struct Index {
  build() {
    Column() {
      // 直接使用ArkTS-Sta自定义组件
      ChildComponentV1()

      // 也可以将ArkTS-Sta自定义组件封装在ArkTS-Dyn自定义组件中嵌套使用
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
      // 使用ArkTS-Sta自定义组件
      ChildComponentV1()
    }
    .width('100%')
  }
}

@ComponentV2
struct IndexV2 {
  build() {
    Column() {
      // 直接使用ArkTS-Sta自定义组件
      ChildComponentV2()

      // 也可以将ArkTS-Sta自定义组件封装在ArkTS-Dyn自定义组件中嵌套使用
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
      // 使用ArkTS-Sta自定义组件
      ChildComponentV2()
    }
    .width('100%')
  }
}
```
