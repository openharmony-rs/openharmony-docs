# ArkTS-Sta使用ArkTS-Dyn @Builder按引用传递参数V2状态管理互操作
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lixingchi1; @katabanga-->
<!--Designer: @lixingchi1; @katabanga-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

## 概述
状态管理V2互操作@Builder按引用传递参数适用于ArkTS-Sta互操作中使用UI的场景，遵循语言互操作的基本规范。

状态管理V2互操作@Builder按引用传递参数适用于以下场景：
- ArkTS-Sta使用ArkTS-Dyn状态管理V2互操作全局自定义构建函数[@Builder](./state-management/arkts-builder.md)按引用传递参数时，传递的参数可为状态变量，且状态变量的改变会引起@Builder函数内的UI刷新。
- ArkTS-Sta使用ArkTS-Dyn状态管理V2互操作自定义组件[@BuilderParam](./state-management/arkts-builderparam.md)成员属性@Builder按引用传递参数时，传递的参数可为状态变量，且状态变量的改变会引起@Builder函数内的UI刷新。
- ArkTS-Sta使用ArkTS-Dyn状态管理V2互操作[WrappedBuilder](./state-management/arkts-wrapBuilder.md)对象@Builder按引用传递参数时，传递的参数可为状态变量，且状态变量的改变会引起@Builder函数内的UI刷新。

## ArkTS-Sta使用ArkTS-Dyn状态管理V2互操作全局自定义构建函数@Builder按引用传递参数
完整示例结构如下图所示：
```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaBuilderV2Ref.ets
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

下面的代码示例展示了在ArkTS-Sta中使用ArkTS-Dyn的@Builder，使用V2状态变量驱动刷新。

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn组件。

<!-- @[StaBuilderV2Ref](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/entry/src/main/ets/pages/StaBuilderV2Ref.ets) -->

```TypeScript
// entry/src/main/ets/pages/StaBuilderV2Ref.ets
import { Entry, ComponentV2, Column, Button, ClickEvent } from '@ohos.arkui.component';
import { Local } from '@ohos.arkui.stateManagement';
import { overBuilder } from 'dynamic_module';

@Entry
@ComponentV2
struct Index {
  @Local label: string = 'Local Interop';

  build() {
    Column() {
      Column() {
        // 在父组件中调用overBuilder组件时，
        // 把this.label通过引用传递的方式传给overBuilder组件。
        overBuilder({ paramA1: this.label })
        Button('Click me')
          .onClick(() => {
            // 单击Click me后，UI文本从Hello更改为ArkUI。
            this.label = 'ArkUI';
          })
      }
    }
  }
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module",
}
```

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出全局自定义构建函数。

<!-- @[StaBuilderV2RefMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/dynamic_module/src/main/ets/components/MainPage.ets) -->

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

export class Tmp {
  paramA1: string = '';
}

@Builder
export function overBuilder(params: Tmp) {
  Row() {
    Text(`UseStateVarByReference: ${params.paramA1} `)
  }
}
```

<!-- @[StaBuilderV2RefDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/dynamic_module/Index.ets) -->

```TypeScript
// dynamic_module/Index.ets
export { overBuilder } from './src/main/ets/components/MainPage';
```

## ArkTS-Sta使用ArkTS-Dyn状态管理V2互操作自定义组件@BuilderParam成员属性@Builder按引用传递参数

完整示例结构如下图所示：
```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaBuilderV2Param.ets
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

下面的代码示例展示了在ArkTS-Sta中使用ArkTS-Dyn的@Builder，使用V2状态变量驱动刷新。

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn组件。

<!-- @[StaBuilderV2Param](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/entry/src/main/ets/pages/StaBuilderV2Param.ets) -->

```TypeScript
// entry/src/main/ets/pages/StaBuilderV2Param.ets
import { Entry, ComponentV2, Builder, Column, Text, ClickEvent, Color } from '@ohos.arkui.component';
import { Local } from '@ohos.arkui.stateManagement';
import { CustomContainer } from 'dynamic_module';

@Entry
@ComponentV2
struct CustomContainerUser {
  @Local text: string = 'header';

  @Builder
  localBuilder() {
    Text(this.text)
      .onClick((value: ClickEvent) => {
        this.text = 'changeHeader';
      })
  }

  build() {
    Column() {
      // 创建CustomContainer，在创建CustomContainer时，通过其后紧跟一个大括号"{}"形成尾随闭包
      // 作为传递给子组件CustomContainer的@BuilderParam 参数 closer: () => void
      CustomContainer() {
        Column() {
          Text(this.text)
        }
        .backgroundColor(Color.Yellow)
        .onClick((value: ClickEvent) => {
          this.text = 'changeHeader';
        })
      }

      // 通过参数初始化 @BuilderParam 成员。
      CustomContainer({ closer: this.localBuilder })
    }
  }
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module",
}
```

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出自定义组件。

<!-- @[StaBuilderV2ParamMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/dynamic_module/src/main/ets/components/MainPage.ets) -->

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

@ComponentV2
export struct CustomContainer {
  @Builder
  closerBuilder() {
  }

  @BuilderParam closer: () => void = this.closerBuilder;

  build() {
    Column() {
      this.closer()
    }
  }
}
```

<!-- @[StaBuilderV2ParamDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/dynamic_module/Index.ets) -->

```TypeScript
// dynamic_module/Index.ets
export { CustomContainer } from './src/main/ets/components/MainPage';
```

## ArkTS-Sta使用ArkTS-Dyn状态管理V2互操作WrappedBuilder对象@Builder按引用传递参数

完整示例结构如下图所示：
```text
project/
├── entry/          # ArkTS-Sta主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── StaBuilderV2Wrapped.ets
│
└── library/         # ArkTS-Dyn子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets
```

下面的代码示例展示了在ArkTS-Sta中使用ArkTS-Dyn的@Builder，使用V2状态变量驱动刷新。

- 在ArkTS-Sta主模块`entry`中引入ArkTS-Dyn组件。

<!-- @[StaBuilderV2Wrapped](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/entry/src/main/ets/pages/StaBuilderV2Wrapped.ets) -->

```TypeScript
// entry/src/main/ets/pages/StaBuilderV2Wrapped.ets
import { Entry, ComponentV2, Column, Button, ClickEvent, compatibleWrappedBuilder } from '@ohos.arkui.component';
import { Local } from '@ohos.arkui.stateManagement';
import { globalBuilder } from 'dynamic_module';

@Entry
@ComponentV2
struct MainPage {
  @Local stateVar: string = 'Hello World!';

  build() {
    Column() {
      // 无需显式使用占位组件API，框架会自动处理
      let globalBuilderParam = ESValue.instantiateEmptyObject()
      globalBuilderParam.setProperty(ESValue.wrap('content'), ESValue.wrap(this.stateVar))
      compatibleWrappedBuilder(globalBuilder, globalBuilderParam)
      Button('Click me')
        .onClick((e: ClickEvent) => {
          this.stateVar = 'Hello ArkUI!';
        })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
  }
}
```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

```json
// entry/oh-package.json5

"dependencies": {
  "dynamic_module": "file:../dynamic_module",
}
```

- 创建ArkTS-Dyn子模块`dynamic_module`，在`dynamic_module/src/main/ets/components`目录创建并导出自定义组件。

<!-- @[StaBuilderV2WrappedMainPage](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/dynamic_module/src/main/ets/components/MainPage.ets) -->

```TypeScript
// dynamic_module/src/main/ets/components/MainPage.ets

class Message {
  content: string = 'Hello World!';
}

@Builder
function messageBuilder(param: Message) {
  Column() {
    Text(param.content)
  }
}

export const globalBuilder: WrappedBuilder<[Message]> = wrapBuilder(messageBuilder);
```

<!-- @[StaBuilderV2WrappedDynIndex](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/ArkUISample-Sta/StaInteropDynBuilderV2/dynamic_module/Index.ets) -->

```TypeScript
// dynamic_module/Index.ets
export { globalBuilder } from './src/main/ets/components/MainPage';
```





