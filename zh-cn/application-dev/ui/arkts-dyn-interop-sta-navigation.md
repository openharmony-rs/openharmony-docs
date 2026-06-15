# 在ArkTS-Dyn中使用ArkTS-Sta的组件导航（Navigation）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @tsj_20201-->
<!--Designer: @tsj_20201-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

从API version 22开始，支持从ArkTS-Dyn的[Navigation](../reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md)调用ArkTS-Sta的[NavDestination](../reference/apis-arkui/arkui-ts/ts-basic-components-navdestination.md)页面实现导航跳转。在ArkTS-Sta互操作场景下，导出ArkTS-Sta的NavDestination子页面，在ArkTS-Dyn的Navigation中直接调用。


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

  <!-- @[PageOne](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ResourceInteropDyn/library/src/main/ets/components/PageOne.ets) -->
  
  ``` TypeScript
  // library/src/main/ets/components/MainPage.ets
  import { Component, NavDestination, Text } from '@kit.ArkUI';
  
  @Component
  export struct PageOne {
    build(): void {
      NavDestination() {
        Text('this is PageOne').fontSize(28)
      }
    }
  }
  ```

  <!-- @[export_navigation](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ResourceInteropDyn/library/Index.ets) -->
  
  ``` TypeScript
  export { PageOne } from './src/main/ets/components/PageOne';
  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
      'library': 'file:../library',
  }
  ```

- 在ArkTS-Dyn主模块中引入ArkTS-Sta的页面。

  <!-- @[navigation](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ResourceInteropDyn/entry/src/main/ets/pages/NavigationPage.ets) -->
  
  ``` TypeScript
  // entry\src\main\ets\pages\NavigationPage.ets
  import { PageOne } from 'library';
  
  @Entry
  @Component
  struct NavigationPage {
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
              let info: NavPathInfo = new NavPathInfo("PageOne", undefined)
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
