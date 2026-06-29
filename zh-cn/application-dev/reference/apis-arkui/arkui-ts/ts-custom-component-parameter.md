# 自定义组件参数
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
> 
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。

## ComponentOptions

自定义组件参数，用于配置是否支持组件冻结和全局复用池。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选     | 说明   |
| ------ | ---- | ---- | ------------ | ------------ |
|freezeWhenInactive|boolean| 否   | 否   |配置自定义组件支持组件冻结。true：开启组件冻结，false：不开启组件冻结。当开发者未指定ComponentOptions时，freezeWhenInactive将使用false作为默认值。<br>从API version 11开始，支持通过此参数配置[@Component](../../../ui/state-management/arkts-create-custom-components.md#component)组件冻结。例子可见[自定义组件冻结](../../../ui/state-management/arkts-custom-components-freeze.md)。<br>从API version 12开始，支持通过此参数配置[@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)组件冻结。例子可见[自定义组件冻结](../../../ui/state-management/arkts-custom-components-freezeV2.md)。<br>**卡片能力（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在ArkTS卡片中使用。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| reusePool | [ReusePoolOwnership](#reusepoolownership) | 否 | 是 | 在自定义组件上配置全局复用池的类型，如果不传入，则全局复用池不会生效。<br>**起始版本：** 26.0.0<br>**卡片能力（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。 |
| poolAccepts | Function[] | 否 | 是 | 自定义组件全局复用池接纳的自定义组件名称，reusePool参数被设置时，poolAccepts必须为非空数组。poolAccepts和reusePool都没有赋值时，全局复用不生效。<br>**起始版本：** 26.0.0<br>**卡片能力（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。<br>**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。 |

## ReusableOptions

可复用自定义组件的参数，用于配置内存优化策略。

**起始版本：** 26.0.0

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选     | 说明   |
| ------ | ---- | ---- | ------------ | ------------ |
| memoryOptimizationStrategy | [ReusableMemOptStrategy](#reusablememoptstrategy) | 否   | 是   | 可复用自定义组件的内存优化策略。该参数在创建可复用自定义组件时设定，不支持动态修改。<br>默认值：[DEFAULT](#reusablememoptstrategy) |

## ReusableMemOptStrategy

可复用自定义组件内存优化策略枚举。

**起始版本：** 26.0.0

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| --- | --- | --- |
| DEFAULT | 0 | 无内存优化策略。 |
| ENABLE_AUTO_CACHE_OPTIMIZATION | 1 << 0 | 自动内存优化策略，当可复用自定义组件内存占用较高时，建议使用此策略以降低内存使用量。<br>当应用退后台时、复用池所在组件不可见时（[visibility](./ts-universal-attributes-visibility.md#visibility)属性设置为[Visible](./ts-appendix-enums.md#visibility)以外的值，或组件面积为0，不考虑遮挡）、整机低内存时（[MemoryLevel](../../apis-ability-kit/js-apis-app-ability-abilityConstant.md#memorylevel)达到MEMORY_LEVEL_LOW或MEMORY_LEVEL_CRITICAL），释放复用池内的所有该类型自定义组件。<br>当复用池中相同ReuseId的该类型自定义组件数量超过8，且5分钟内不再增加时，保留8个组件，释放其余组件。<br>在释放节点时，会触发[自定义组件生命周期](../../../ui/state-management/arkts-page-custom-components-lifecycle.md)。 |

## 示例

### 示例1（使用自动内存优化策略）

以下示例中，可复用自定义组件ReusableComponent通过[ReusableOptions](#reusableoptions)的memoryOptimizationStrategy属性使用了自动内存优化策略。点击Recycle按钮，可触发ReusableComponent组件回收。之后应用退后台，可触发复用池缓存释放。

从API版本26.0.0开始，新增ReusableOptions接口。

```ts
@Reusable({ memoryOptimizationStrategy: ReusableMemOptStrategy.ENABLE_AUTO_CACHE_OPTIMIZATION }) // 使用自动内存优化策略
@Component
struct ReusableComponent {
  aboutToRecycle() {
    console.info('ReusableComponent aboutToRecycle');
  }
  aboutToDisappear() {
    console.info('ReusableComponent aboutToDisappear');
  }
  build() {
    Text('ReusableComponent')
  }
}

@Entry
@Component
struct MemoryOptimizeDemo {
  @State showReusableComponent: boolean = true;
  build() {
    Column() {
      Button('Recycle').onClick(() => { // 点击按钮触发组件回收
        this.showReusableComponent = false;
      })
      if (this.showReusableComponent) {
        ReusableComponent()
      }
    }
  }
}
```

## ReusePoolOwnership

type ReusePoolOwnership = 'shared' | 'perInstance'

全局复用池的持有类型。

**起始版本：** 26.0.0

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型            | 说明                  |
|-------------    | ------------------- |
| 'shared'        | 拥有@Component/@ComponentV2类的所有实例共享单个复用池实例。 |
| 'perInstance'   | 拥有@Component/@ComponentV2的每个实例都有自己的复用池实例。 |
