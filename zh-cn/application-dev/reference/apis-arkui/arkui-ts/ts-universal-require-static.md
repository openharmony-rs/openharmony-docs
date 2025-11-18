# \@Require装饰器：校验构造传参

\@Require是校验[\@Prop](../../../ui/state-management/arkts-prop.md)、[\@State](../../../ui/state-management/arkts-state.md)、[\@Provide](../../../ui/state-management/arkts-provide-and-consume.md)、[\@BuilderParam](../../../ui/state-management/arkts-builderparam.md)、[\@Param](../../../ui/state-management/arkts-new-param.md)和普通变量(无状态装饰器修饰的变量)是否需要构造传参的一个装饰器。开发指南见[\@Require装饰器：校验构造传参](../../../ui/state-management/arkts-require.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 该装饰器从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'

import { Entry, Component, Builder, Text, Column, Row, BuilderParam, State, Require, Provide, PropRef } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  @Builder
  buildTest() {
    Row() {
      Text('Hello, world')
        .fontSize(30)
    }
  }

  build() {
    Row() {
      // 构造Child时需传入所有@Require对应参数，否则编译失败。
      Child({
        regular_value: this.message,
        state_value: this.message,
        provide_value: this.message,
        initMessage: this.message,
        message: this.message,
        buildTest: this.buildTest,
        initBuildTest: this.buildTest
      })
    }
  }
}

@Component
struct Child {
  @Builder
  buildFunction() {
    Column() {
      Text('initBuilderParam')
        .fontSize(30)
    }
  }

  @Require regular_value: string = 'Hello';
  @Require @State state_value: string = 'Hello';
  @Require @Provide provide_value: string = 'Hello';
  @Require @BuilderParam buildTest: () => void;
  @Require @BuilderParam initBuildTest: () => void = this.buildFunction;
  @Require @PropRef initMessage: string = 'Hello';
  @Require @PropRef message: string;

  build() {
    Column() {
      Text(this.initMessage)
        .fontSize(30)
      Text(this.message)
        .fontSize(30)
      this.initBuildTest()
      this.buildTest()
    }
    .width('100%')
    .height('100%')
  }
}
```