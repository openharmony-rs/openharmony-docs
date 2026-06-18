# @Trace：类属性变化观测

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Trace是属性装饰器，用于状态管理V2中。@ObservedV2与@Trace配套使用，装饰类以及类中的属性，使得被装饰的类和属性具有深度观测的能力。

在ArkTS-Dyn中使用时，开发指南参考：[\@ObservedV2装饰器和\@Trace装饰器：类属性变化观测（ArkTS-Dyn）](../../../ui/state-management/arkts-new-observedV2-and-trace.md)。

> **说明：**
>
> 从API version 12开始，支持该装饰器。

## @Trace

const Trace: PropertyDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@ObservedV2
class Son {
  // 使用@Trace属性装饰器标记需要观测的属性，属性变化时触发UI刷新
  @Trace age: number = 100;
}
class Father {
  son: Son = new Son();
}
@Entry
@ComponentV2
struct Index {
  father: Father = new Father();

  build() {
    Column() {
      Text(`${this.father.son.age}`)
        // 点击后age值加1，由于@Trace装饰器，UI会自动刷新
        .onClick(() => {
          this.father.son.age++;
        })
    }
  }
}
```

