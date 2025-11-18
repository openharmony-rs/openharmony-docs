# \@BuilderParam装饰器：引用\@Builder函数

\@BuilderParam用于装饰指向@Builder方法的变量。开发指南见[\@BuilderParam装饰器：引用\@Builder函数](../../../ui/state-management/arkts-builderparam.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 该装饰器从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

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

  @BuilderParam customBuilderParam: () => void = this.customBuilder;

  build() {
    Column() {
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
      Child({ customBuilderParam: this.componentBuilder })
    }
  }
}
```

  