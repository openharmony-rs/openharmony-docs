# @Reusable：组件复用
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @maorh-->
<!--Designer: @keerecles-->
<!--Tester: @khq-->
<!--Adviser: @zhang_yixin13-->

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@Reusable装饰[\@Component：自定义组件](./ts-custom-component-decorator-component-static.md)装饰的自定义组件，达成组件复用的效果。开发指南参考：[\@Reusable装饰器：组件复用](../../../ui/state-management/arkts-reusable.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## memoryOptimizationStrategy

组件复用内存优化配置项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型                       | 只读 | 可选 | 说明            |
| ------ | --------------- | ---- | ---- | ------- |
| memoryOptimizationStrategy   | [ReusableMemOptStrategy](#reusablememoptstrategy) | 否 | 是   | 组件复用内存优化策略。不支持动态修改。<br>默认值：DEFAULT |

## ReusableMemOptStrategy

内存优化策略枚举。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 值 | 说明 |
| --- | --- | --- |
| DEFAULT | 0 | 无内存优化策略。 |
| ENABLE_AUTO_CACHE_OPTIMIZATION | 1 | 当可复用自定义组件内存占用较高时，建议使用此策略以降低内存使用量。<br>当应用退后台时、复用池所在组件不可见时（[visibility](./ts-universal-attributes-visibility.md#visibility)属性设置为Visible以外的值，或组件面积为0，不考虑遮挡）、整机低内存时（[MemoryLevel](../../apis-ability-kit/js-apis-app-ability-abilityConstant.md#memorylevel)达到MEMORY_LEVEL_LOW或MEMORY_LEVEL_CRITICAL），释放复用池内的所有该类型自定义组件。<br>当复用池中相同类型自定义组件数量超过8，且5分钟内不再增加时，保留8个组件，释放其余组件。|

**示例：**

```ts
'use static'
import { Entry, Component, Column, Button, FontWeight, Reusable, Text, State, ReusableMemOptStrategy } from '@kit.ArkUI';

class Message {
  value: string | undefined;

  constructor(value: string) {
    this.value = value;
  }
}

@Entry
@Component
struct Index {
  @State toggle: boolean = true;

  build() {
    Column() {
      Button('Hello')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.toggle = !this.toggle;
        })
      if (this.toggle) {
        // 如果只有一个复用的组件，可以不用设置reuseId。
        Child({ message: new Message('Child') })
          .reuseId('Child')
      }
    }
    .height('100%')
    .width('100%')
  }
}

@Reusable({ memoryOptimizationStrategy: ReusableMemOptStrategy.DEFAULT }) // 配置内存优化策略
@Component
struct Child {
  @State message: Message = new Message('AboutToReuse');

  build() {
    Column() {
      Text(this.message.value)
        .fontSize(30)
    }
    .borderWidth(1)
    .height(100)
  }
}
```
