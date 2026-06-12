# 在ArkTS-Sta中使用ArkTS-Dyn的资源（Resource）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

从API version 22开始，支持在ArkTS-Sta中创建组件调用ArkTS-Dyn的Resource资源。在ArkTS-Sta互操作场景下，导出ArkTS-Dyn的Resource资源，在ArkTS-Sta的页面中直接调用。

完整示例结构如下所示。

```test
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets       # 页面所在的文件
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets     # 调用资源的文件
```

示例如下：

- 创建ArkTS-Dyn子模块`library`，在`library/src/main/ets/components`目录创建页面。

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  export function createResource() : object {
    // $r("app.string.TEST")需替换为开发者所需要的资源
    let res = $r("app.string.TEST");
    return res;
  }
  
  ```

- 在ArkTS-Dyn子模块`library`中导出页面。

  ```TypeScript
  // library/Index.ets
  export { createResource } from './src/main/ets/components/MainPage';

  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
    'library': 'file:../library',
  }
  ```

- 在ArkTS-Sta主模块中引入ArkTS-Dyn的页面。

  <!-- @[call_resource_sta](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/ResourceInterop/entry/src/main/ets/pages/ResInterop.ets) -->
  
  ``` TypeScript
  import { Entry, Button, ClickEvent, Column, Component, Text, FontWeight, ColumnOptions, State, $r } from '@kit.ArkUI';
  import { Resource } from 'global.resource';
  import transfer from '@ohos.transfer';
  import { createResource } from 'library';
  
  @Entry
  @Component
  struct ResInterop {
    // $r("app.string.res")需替换为开发者所需要的资源
    @State resText: Resource = $r("app.string.res");
    // $r("app.color.start_window_background"需替换为开发者所需要的资源
    @State resTextColor: Resource = $r("app.color.start_window_background");
  
    build() {
      Column() {
        Button("createResource").height(35)
          .onClick((e: ClickEvent) => {
            let res = createResource();
            let res2 = transfer.transferStatic(res, 'Global.Resource');
            this.resText = res2 as Resource;
          })
        Text(this.resText).backgroundColor(this.resTextColor).fontSize(26)
      }
    }
  }
  ```
