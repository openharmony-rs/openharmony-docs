# 在ArkTS-Sta中使用ArkTS-Dyn的组件导航（Navigation）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @tsj_20201-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

从API version 22开始，支持从ArkTS-Sta的[Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md)调用ArkTS-Dyn的[NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md)页面实现导航跳转。在ArkTS-Sta互操作场景下，导出ArkTS-Dyn的NavDestination子页面，在ArkTS-Sta的Navigation中直接调用。


完整示例结构如下图所示：

```test
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

ArkTS-Dyn初始化NavDestination页面属性，其使用规格限制与非互操作场景相同。

示例如下：

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录创建并导出页面。

  <!-- @[page_one](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ResourceInterop/library/src/main/ets/components/MainPage.ets) -->
  
  ``` TypeScript
  @Component
  export struct PageOne {
    build() {
      NavDestination() {
        Text('this is PageOne')
          .fontSize(28)
          .fontWeight(700)
          .margin({ top: 50 })
      }
    }
  }
  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
      'library': 'file:../library',
  }
  ```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn的页面。

  <!-- @[navigation_page](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ResourceInterop/entry/src/main/ets/pages/NavigationPage.ets) -->
  
  ``` TypeScript
  // entry\src\main\ets\pages\NavigationPage.ets
  import {
    Entry,
    Builder,
    Button,
    ClickEvent,
    Column,
    Component,
    NavPathStack,
    Navigation,
    NavPathInfo,
    NavDestination,
  } from '@kit.ArkUI';
  import { PageOne } from 'library';
  
  let pathStack: NavPathStack = new NavPathStack()
  
  @Entry
  @Component
  struct NavigationPage {
    @Builder
    PageBuilder(name: string, param: Object | null | undefined) {
      if (name == "PageOne") {
        PageOne()
      }
    }
  
    build() {
      Navigation(pathStack) {
        Column() {
          Button(`pushPath`)
            .width('80%')
            .height(40)
            .margin(10)
            .onClick((e?: ClickEvent) => {
              let info: NavPathInfo = new NavPathInfo("PageOne", new Object())
              pathStack.pushPath(info)
            })
        }
      }
      .navDestination(this.PageBuilder)
      .title('PageHome')
      .height("100%")
    }
  }
  ```
