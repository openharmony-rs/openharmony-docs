# @ReusableV2：组件复用V2
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @maorh-->
<!--Designer: @keerecles-->
<!--Tester: @khq-->
<!--Adviser: @zhang_yixin13-->

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@ReusableV2装饰[\@ComponentV2](./ts-custom-component-decorator-componentv2-static.md#componentv2)装饰的自定义组件，达成组件复用的效果。开发指南参考：[\@ReusableV2装饰器：组件复用](../../../ui/state-management-static/arkts-static-new-reusableV2.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @ReusableV2

@interface ReusableV2

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

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
import { Entry, ComponentV2, Local, Column, Button, ReusableV2, Text, ReusableMemOptStrategy } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('回收/复用')
        .onClick(() => {
          this.condition = !this.condition;
        }) // 点击切换回收/复用状态
      if (this.condition) {
        ReusableV2Component()
      }
    }
  }
}
@ReusableV2({ memoryOptimizationStrategy: ReusableMemOptStrategy.DEFAULT }) // 配置内存优化策略
@ComponentV2
struct ReusableV2Component {
  @Local message: string = 'Hello World';
  aboutToRecycle() {
    console.info('ReusableV2Component aboutToRecycle'); // 回收时被调用
  }
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse'); // 复用时被调用
  }
  build() {
    Column() {
      Text(this.message)
    }
  }
}
```
