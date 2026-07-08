# @ComponentV2：自定义组件V2

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@ComponentV2主要配合状态管理V2使用。除非特别说明，@ComponentV2装饰的自定义组件将与[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)装饰的自定义组件保持相同的行为。开发指南参考：[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 本装饰器首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 从API版本26.0.0开始，\@ComponentV2的[ComponentOptions](./ts-custom-component-parameter.md#componentoptions)参数支持可选属性`reusePool`和`poolAccepts`，用于配置全局复用池，开发指南参考：[全局复用：集中化的组件回收与复用](../../../ui/state-management/arkts-global-reuse-pool.md)。

## @ComponentV2

const ComponentV2: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)

**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 名称                  | 类型    | 必填  | 说明                                                         |
| --------------------- | ------ | ---- | ------------------------------------------------------------ |
| options               | [ComponentOptions](./ts-custom-component-parameter.md#componentoptions) | 否 | \@ComponentV2装饰器选项。当需要开启组件冻结或全局复用功能时传入此参数进行自定义配置；缺省时关闭组件冻结和全局复用功能。 |

**示例：**

```ts
@Entry
@ComponentV2({ freezeWhenInactive: true })
struct MyComponent {
  build() {
    Column() {
      Text('Hello World!')
    }
  }
}
```