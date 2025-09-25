# @Track

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 11开始，支持该装饰器。

@Track用于状态管理V1中，观测class对象的属性级更新。

在ArkTS-Dyn中使用时，开发指南参考：[@Track装饰器：class对象属性级更新（ArkTS-Dyn）](../../../ui/state-management/arkts-track.md)。

**卡片能力：** 从API version 11开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
class Info {
  @Track id: number;

  constructor(id: number) {
    this.id = id;
  }
}

@Entry
@Component
struct Index {
  @State info: Info = new Info(1);

  build() {
    Column() {
      Text(`id: ${this.info.id}`)
      Button('change')
        .onClick(() => {
          this.info.id++;
        })
    }
  }
}
```