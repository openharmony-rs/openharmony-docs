# ArkTS-Dyn的Navigation调用ArkTS-Sta的NavDestination页面


从API version 20开始，支持从ArkTS-Dyn的Navigation调用ArkTS-Sta的NavDestination页面实现导航跳转。在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，导出ArkTS-Sta的NavDestination子页面，在ArkTS-Dyn的Navigation中直接调用。


完整示例结构如下图所示：

```test
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

ArkTS-Sta初始化NavDestination页面属性，其使用规格限制与非互操作场景相同。

示例如下：

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出页面。

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  'use static'
  import { Component, NavDestination, Text } from '@ohos.arkui.component';

  @Component
  export struct PageOne {
    build() {
      NavDestination() {
        Text('this is PageOne').fontSize(28)
      }
    }
  }
 
  // library/Index.ets
  'use static'
  export { PageOne } from './src/main/ets/components/MainPage'

  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
      'library': 'file:../library',
  }
  ```

- 在ArkTS-Dyn主模块中引入ArkTS-Sta动态模块的页面。

  ```TypeScript
  // entry\src\main\ets\pages\Index.ets
  import { PageOne } from 'library';

  @Entry
  @Component
  struct Index {
    @Builder
    PageBuilder(name: string, param: Object | null | undefined) {
      if (name == "PageOne") {
        PageOne()
      }
    }
    @State pathStack: NavPathStack = new NavPathStack()

    build() {
      Navigation(this.pathStack) {
        Column() {
          Button(`pushPath`)
            .width('80%')
            .height(40)
            .margin(10)
            .onClick((e?: ClickEvent) => {
              let info: NavPathInfo = new NavPathInfo("PageOne", new Object())
              this.pathStack.pushPath(info)
            })
        }
      }
      .navDestination(this.PageBuilder)
      .title('PageHome')
      .height("100%")
    }
  }
  ```