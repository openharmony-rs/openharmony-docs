# 在ArkTS-Dyn中使用ArkTS-Sta的资源（Resource）

从API version 22开始，支持在ArkTS-Dyn中调用ArkTS-Sta的Resource资源。在[ArkTS-Sta互操作](../quick-start/arkts-interop-overview.md)场景下，导出ArkTS-Sta的接口，在ArkTS-Dyn的页面中直接调用。

完整示例结构如下所示。

```test
project/
├── entry/          # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets         # 调用资源的文件
│
└── library/         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets      # 资源创建文件
```

示例如下：

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建页面。

  ```TypeScript
  // library/src/main/ets/components/MainPage.ets
  import { $r } from '@ohos.arkui.component';
  import transfer from '@ohos.transfer';

  export function createResource(): Any {
    // $r("app.string.EFG")需替换为开发者所需要的资源
    let res = $r("app.string.EFG");
    let res2 = transfer.transferDynamic(res, 'Global.Resource');
    return res2;
  }
  ```

- 在ArkTS-Sta子模块`library`中导出页面。

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

- 在ArkTS-Dyn主模块中引入ArkTS-Sta的页面。

  ```TypeScript
  // entry/src/main/ets/pages/Index.ets
  import { createResource } from 'library';

  @Entry
  @Component
  struct Index {
    // $r("app.string.res")需替换为开发者所需要的资源
    @State resText: Resource = $r("app.string.res");
    // $r("app.color.start_window_background"需替换为开发者所需要的资源
    @State resTextColor: Resource = $r("app.color.start_window_background");

    build() {
      Column() {
        Button("createResource").height(35)
          .onClick((e: ClickEvent) => {
            let res = createResource() as Resource;
            this.resText = res;
          })
        Text(this.resText).backgroundColor(this.resTextColor).height(70)
      }
      .height('100%')
      .width('100%')
      .alignItems(HorizontalAlign.Start)
    }
  }
  ```