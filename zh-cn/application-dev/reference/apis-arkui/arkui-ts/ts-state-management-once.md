# @Once

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 12开始，支持该装饰器。

@Once作为辅助装饰器，用于状态管理V2中，需要搭配@Param一起使用，适用于仅从外部初始化一次且不接受后续同步变化的场景。

在ArkTS-Dyn中使用时，开发指南参考：[@Once：初始化同步一次（ArkTS-Dyn）](../../../ui/state-management/arkts-new-once.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@ComponentV2
struct Child {
  @Param @Once onceParam: string = '';
  build() {
    Column() {
      Text(`onceParam: ${this.onceParam}`)
      Button('change onceParam')
        .onClick((e: ClickEvent) => {
          this.onceParam = 'child';
        })
    }
  }
}
@Entry
@ComponentV2
struct Index {
  @Local message: string = 'Hello World';
  build() {
    Column() {
      Text(`Parent message: ${this.message}`)
      Button('change message')
        .onClick((e: ClickEvent) => {
          this.message = 'parent';
        })
      Child({ onceParam: this.message })
    }
  }
}
```

