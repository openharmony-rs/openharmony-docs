# @Param

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 12开始，支持该装饰器。

@Param用于状态管理V2中，接收外部输入，实现父子组件之前的单向数据同步。

在ArkTS-Dyn中使用时，开发指南参考：[@Param：组件外部输入（ArkTS-Dyn）](../../../ui/state-management/arkts-new-param.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@ComponentV2
struct Child {
  @Param message: string = '';
  build() {
    Column() {
      Text(`Child message: ${this.message}`)
    }
  }
}
@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello';
  build() {
    Column() {
      Text(`Parent message: ${this.message}`)
      Button('change message')
        .onClick(() => {
          this.message = 'Hello World';
        })
      Child({ message: this.message })
    }
  }
}
```

