# @Computed

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 12开始，支持该装饰器。

@Computed为方法装饰器，用于状态管理V2中，装饰getter方法。

在ArkTS-Dyn中使用时，开发指南参考：[@Computed装饰器：计算属性（ArkTS-Dyn）](../../../ui/state-management/arkts-new-computed.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Entry
@ComponentV2
  struct Index {
  @Local firstName: string = 'Hua';
  @Local lastName: string = 'Li';

  @Computed
  get fullName() {
    return this.firstName + ' ' + this.lastName;
  }

  build() {
    Column() {
      Text(`${this.fullName}`)
    }
  }
}
```

