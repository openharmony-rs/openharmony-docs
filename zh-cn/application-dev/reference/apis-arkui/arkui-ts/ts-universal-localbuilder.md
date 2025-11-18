# \@LocalBuilder装饰器：维持组件关系

@LocalBuilder拥有和局部@Builder相同的功能，且比局部@Builder能够更好的确定组件的父子关系和状态管理的父子关系。开发指南见[\@LocalBuilder装饰器：维持组件关系](../../../ui/state-management/arkts-localBuilder.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 本装饰器首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
class ReferenceType {
  paramString: string = '';
}

@Entry
@Component
struct Parent {
  @State variableValue: string = 'Hello World';

  @LocalBuilder
  citeLocalBuilder(params: ReferenceType) {
    Row() {
      Text(`UseStateVarByReference: ${params.paramString}`)
    }
  };

  build() {
    Column() {
      this.citeLocalBuilder({ paramString: this.variableValue })
      Button('Click me').onClick(() => {
        this.variableValue = 'Hi World';
      })
    }
  }
}
```