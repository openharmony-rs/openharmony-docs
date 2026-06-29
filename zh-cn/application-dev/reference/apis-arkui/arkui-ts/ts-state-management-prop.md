# @Prop：父子单向同步

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Prop用于状态管理V1中，接收外部传入值，并与父组件建立单向同步关系。开发指南参考：[@Prop装饰器：父子单向同步](../../../ui/state-management/arkts-prop.md)。

> **说明：**
>
> 从API version 7开始，支持该装饰器。

## @Prop

const Prop: PropertyDecorator

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Component
struct Child {
  // 使用@Prop装饰器接收父组件传入的值，与父组件建立单向同步关系
  // 父组件数据变化会同步到子组件，但子组件修改不会同步回父组件
  @Prop message: string = 'Hi';

  build() {
    Column() {
      Text(this.message)
    }
  }
}

@Entry
@Component
struct Index {
  // 使用@State声明状态变量，作为@Prop的数据源
  @State message: string = 'Hello';

  build() {
    Column() {
      // 创建子组件Child，将message单向绑定到子组件的@Prop变量
      Child({ message: this.message })
    }
  }
}
```

