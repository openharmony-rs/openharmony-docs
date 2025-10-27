# @Prop

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 7开始，支持该装饰器。
>

@Prop用于状态管理V1中，接收外部传入值，并与父组件建立单向同步关系。

在ArkTS-Dyn中使用时，开发指南参考：[@Prop装饰器：父子单向同步（ArkTS-Dyn）](../../../ui/state-management/arkts-prop.md)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Component
struct Child {
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
  @State message: string = 'Hello';

  build() {
    Column() {
      Child({ message: this.message })
    }
  }
}
```

