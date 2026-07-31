# \@Require装饰器：校验构造传参

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Require装饰器用于校验[\@Prop](../../../ui/state-management/arkts-prop.md)、[\@State](../../../ui/state-management/arkts-state.md)、[\@Provide](../../../ui/state-management/arkts-provide-and-consume.md)、[\@BuilderParam](../../../ui/state-management/arkts-builderparam.md)、[\@Param](../../../ui/state-management/arkts-new-param.md)和普通变量（无状态装饰器装饰的变量）是否需要构造传参。使用该装饰器装饰的变量，要求父组件在构造子组件时必须传入对应参数，否则在编译阶段报错，从而避免因参数缺失导致的运行时异常，适用于需要确保自定义组件必需参数被正确初始化的场景。

开发指南参考：[\@Require装饰器：校验构造传参](../../../ui/state-management/arkts-require.md)。

> **说明：**
>
> - 从API version 11开始支持该装饰器。
>
> - 从API version 11开始对\@Prop/\@BuilderParam进行校验。
>
> - 从API version 12开始对\@State/\@Provide/\@Param/普通变量（无状态装饰器装饰的变量）进行校验。

## @Require

const Require: PropertyDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API version 11开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
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
        regularValue: this.message,
        stateValue: this.message,
        provideValue: this.message,
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

  @Require regularValue: string = 'Hello';
  @Require @State stateValue: string = 'Hello';
  @Require @Provide provideValue: string = 'Hello';
  @Require @BuilderParam buildTest: () => void;
  @Require @BuilderParam initBuildTest: () => void = this.buildFunction;
  @Require @Prop initMessage: string = 'Hello';
  @Require @Prop message: string;

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