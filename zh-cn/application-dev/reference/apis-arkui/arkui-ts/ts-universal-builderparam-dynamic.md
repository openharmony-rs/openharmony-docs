# \@BuilderParam装饰器：引用\@Builder函数

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@BuilderParam用于装饰指向[@Builder](./ts-universal-builder-dynamic.md)方法的变量。开发指南见[\@BuilderParam装饰器：引用\@Builder函数](../../../ui/state-management/arkts-builderparam.md)。

> **说明：**
>
> - 该装饰器从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @BuilderParam

const BuilderParam: PropertyDecorator

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**示例：**

```ts
@Component
struct Child {
  @Builder
  customBuilder() {
  }

  // 使用@BuilderParam装饰器声明一个指向@Builder函数的变量
  // 类型为无参无返回值的函数，默认值为子组件内部的customBuilder
  @BuilderParam customBuilderParam: () => void = this.customBuilder;

  build() {
    Column() {
      // 调用@BuilderParam引用的构建函数来渲染UI
      this.customBuilderParam()
    }
  }
}

@Entry
@Component
struct Parent {
  @Builder
  componentBuilder() {
    Text(`Parent builder`)
  }

  build() {
    Column() {
      // 创建子组件Child，将父组件的componentBuilder传入customBuilderParam
      Child({ customBuilderParam: this.componentBuilder })
    }
  }
}
```

  