# ArkTS-Dyn部分特性使用ArkTS-Sta开发

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lixingchi1-->
<!--Designer: @lixingchi1-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->


## 概述

在实际开发场景中，需要在ArkTS-Dyn项目中集成ArkTS-Sta开发的特性。本文档将详细介绍两者互操作的项目环境准备步骤，以及路由交互、UI数据交互等常见场景的实现方案。


## 环境准备

- 创建ArkTS-Dyn项目，具体步骤请参考[ArkTS-Dyn项目创建](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-tools-overview)。

- 在ArkTS-Dyn项目根目录`build-profile.json5`配置文件中，将`app.products`节点下的`arkTSVersion`字段指定为`1.2`。

  ```json
  {
    "app": {
      "products": [
        {
          "name": "default",
          "arkTSVersion": "1.2"  // 需显式配置为1.2以支持互操作
        }
      ]
    }
  }
  ```


## 使用场景

### ArkTS-Dyn页面与ArkTS-Sta页面的路由交互

示例结构如下：

```text
project/
├── entry/                           # ArkTS-Dyn主模块
│   └── src/
│       └── main/
│           └── ets/
│               └── pages/
│                   └── Index.ets    # ArkTS-Dyn主页面（发起路由跳转）
│
└── library/                         # ArkTS-Sta子模块
    └── src/
        └── main/
            └── ets/
                └── components/
                    └── MainPage.ets # ArkTS-Sta目标页面（被跳转页面）
```

以下代码示例展示了在ArkTS-Dyn项目中与ArkTS-Sta页面进行路由交互。

- 创建ArkTS-Sta子模块`library`，在`library/src/main/ets/components`目录创建并导出页面。

  ```TypeScript
  'use static'
  // library/src/main/ets/components/MainPage.ets
  import { Component, NavDestination, Text } from '@ohos.arkui.component';

  @Component
  export struct PageOne {  // 导出ArkTS-Sta页面组件
    build() {
      NavDestination() {
        Text('this is PageOne')
          .fontSize(28)
          .fontWeight(700)
      }
    }
  }
  ```

  ```TypeScript
  'use static'
  //library/index.ets
  export { PageOne } from './src/main/ets/components/MainPage';
  ```

- 在主模块`entry`的`oh-package.json5`文件中配置子模块依赖。

  ```json
  // entry/oh-package.json5

  "dependencies": {
      'library': 'file:../library',
  }
  ```

- 在ArkTS-Dyn主模块中引入ArkTS-Sta模块的页面。

  ```TypeScript
  // entry/src/main/ets/pages/Index.ets
  import { PageOne } from 'library';

  let pathStack: NavPathStack = new NavPathStack();

  @Entry
  @Component
  struct Index {
    @Builder
    PageBuilder(name: string, param: Object | null | undefined) {
      if (name === 'PageOne') {
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
              let info: NavPathInfo = new NavPathInfo('PageOne', new Object())
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


### ArkTS-Dyn页面与ArkTS-Sta UI组件的数据交互

示例结构如下：

```text
project/
└── entry/                              # ArkTS-Dyn模块
    └── src/
        └── main/
            └── ets/
                └── pages/
                    └── Index.ets        # ArkTS-Dyn主页面（传递数据）  
                    └── StaFeature.ets   # ArkTS-Sta组件文件（接收并处理数据）
```

以下代码示例展示了在ArkTS-Dyn中使用ArkTS-Sta组件进行数据交互。

- 在ArkTS-Dyn模块`entry`中引入ArkTS-Sta组件`StaComp`。

```TypeScript
// entry/src/main/ets/pages/Index.ets
import { StaComp } from './StaFeature';

@Entry
@Component
struct DynComp {
  @State message: string = 'Hello Interop';
  @Provide message5: string = 'Provide Interop';

  build() {
    Column() {
      Button(this.message)
        .onClick((e: ClickEvent) => {
          this.message += '~';
        })
      StaComp({ // 使用ArkTS-Sta组件，并传递数据
        message1: this.message,
        message2: this.message,
        message3: this.message,
        message4: this.message,
      })
    }
    .width('100%')
    .height('100%')
    .backgroundColor('#F1F3F5')
  }
}
```

- 在`entry/src/main/ets/pages`目录下，创建ArkTS-Sta文件`StaFeature.ets`，并导出自定义组件`StaComp`。

```TypeScript
'use static'

// entry/src/main/ets/pages/StaFeature.ets
import { Component, Column, Text, ClickEvent } from '@ohos.arkui.component';
import { State, Link, PropRef, Provide, Consume } from '@ohos.arkui.stateManagement';

@Component
export struct StaComp {
  @State message1: string = 'static State';
  @Link message2: string;
  @PropRef message3: string = 'static Prop';
  @Provide message4: string = 'static Provide';
  @Consume message5: string;

  build() {
    Column() {
      Text(this.message1)
        .fontSize(30)
        .onClick((e: ClickEvent) => {
          this.message1 += '!';
        })
      Text(this.message2)
        .fontSize(30)
        .onClick((e: ClickEvent) => {
          this.message2 += '!';
        })
      Text(this.message3)
        .fontSize(30)
        .onClick((e: ClickEvent) => {
          this.message3 += '!';
        })
      Text(this.message4)
        .fontSize(30)
        .onClick((e: ClickEvent) => {
          this.message4 += '!';
        })
      Text(this.message5)
        .fontSize(30)
        .onClick((e: ClickEvent) => {
          this.message5 += '!';
        })
    }
    .padding(20)
  }
}
```


## 常见问题

### ArkTS-Dyn与ArkTS-Sta范式差异的互操作适配

当ArkTS-Dyn与ArkTS-Sta对同一类型的定义存在差异（如[WrappedBuilder](./state-management/arkts-v1.2-wrapBuilder.md)），需通过修改ArkTS-Sta的互操作声明文件适配编译。

下面的代码示例展示了`WrappedBuilder`在ArkTS-Dyn与ArkTS-Sta用法中的差异。

```TypeScript  
// ArkTS-Dyn范式
const globalDynamicBuilder: WrappedBuilder<[string, number]>[] = [wrapBuilder(MyBuilder)];

// ArkTS-Sta范式
const globalStaticBuilder: Array<WrappedBuilder<@Builder (value: string, size: number) => void>> = [wrapBuilder(MyBuilder)];

// MyBuilder定义
@Builder
function MyBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}
```

针对上述差异，找到主模块编译产物目录`build/intermediates/declgen/default/declgenV1`下对应的ArkTS-Sta的互操作声明文件，将`WrappedBuilder`的类型从`Array<WrappedBuilder<@Builder (value: string, size: number) => void>>`修改为`WrappedBuilder<[string, number]>[]`，以支持ArkTS-Dyn的用法。


### ArkTS-Dyn与ArkTS-Sta系统对象类型互操作适配

针对[ComponentContent](../reference/apis-arkui/js-apis-arkui-ComponentContent-static.md)、[TypedFrameNode](../reference/apis-arkui/js-apis-arkui-frameNode.md#typedframenode12)、[BuilderNode](../reference/apis-arkui/js-apis-arkui-builderNode-static.md)等ArkUI系统对象，可以通过[@ohos.transfer](../reference/apis-arkts/js-apis-transfer.md)模块实现转换：

- `transferStatic`：从ArkTS-Dyn系统对象转换为ArkTS-Sta系统对象；

- `transferDynamic`：从ArkTS-Sta系统对象转换为ArkTS-Dyn系统对象。

详细使用方法可参考[使用ArkTS-Dyn的自定义节点对象](./arkts-sta-interop-dyn-node.md)。
