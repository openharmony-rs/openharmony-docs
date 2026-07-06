# @Link：父子双向同步

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Link用于状态管理V1中，接收外部传入值，并与父组件中的数据源建立双向数据绑定。

在ArkTS-Dyn中使用时，开发指南参考：[@Link装饰器：父子双向同步（ArkTS-Dyn）](../../../ui/state-management/arkts-link.md)。

> **说明：**
>
> 从API version 7开始，支持该装饰器。

## @Link

const Link: PropertyDecorator

**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Component
struct Child {
  // 使用@Link装饰器声明双向绑定变量，与父组件数据源建立双向同步
  @Link msg: string;

  build() {
    Column() {
      Text(this.msg)
      Button('change')
        .onClick(() => {
          // 修改会同步到父组件
          this.msg += '~';
        })
    }
  }
}

@Entry
@Component
struct LinkExample {
  // 使用@State声明状态变量，作为@Link的数据源
  @State message: string = 'Hello';

  build() {
    Column() {
      // 创建子组件Child，通过@Link将message双向绑定到子组件的msg
      Child({msg: this.message})
    }
  }
}
```

