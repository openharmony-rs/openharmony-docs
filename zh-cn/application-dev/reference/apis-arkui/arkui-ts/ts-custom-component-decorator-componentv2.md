# @ComponentV2：自定义组件V2

@ComponentV2主要配合状态管理V2使用。除非特别说明，@ComponentV2装饰的自定义组件将与@Component装饰的自定义组件保持相同的行为。开发指南参考：[创建自定义组件](../../../ui/state-management/arkts-create-custom-components.md#componentv2)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 本装饰器首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @ComponentV2

const ComponentV2: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)

**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 名称                  | 类型    | 必填  | 说明                                                         |
| --------------------- | ------ | ---- | ------------------------------------------------------------ |
| options               | [ComponentOptions](./ts-custom-component-decorator-component.md#componentoptions11) | 否 | \@ComponentV2装饰器选项。 |

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