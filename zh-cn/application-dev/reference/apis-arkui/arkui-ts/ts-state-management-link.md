# @Link

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 7开始，支持该装饰器。
>

@Link用于状态管理V1中，接收外部传入值，并与父组件中的数据源建立双向数据绑定。

在ArkTS-Dyn中使用时，开发指南参考：[@Link装饰器：父子双向同步（ArkTS-Dyn）](../../../ui/state-management/arkts-link.md)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Component
struct Child {
  @Link msg: string;

  build() {
    Column() {
      Text(this.msg)
      Button('change')
        .onClick(() => {
          this.msg += '~';
        })
    }
  }
}

@Entry
@Component
struct LinkExample {
  @State message: string = 'Hello';

  build() {
    Column() {
      Child({msg: this.message})
    }
  }
}
```

