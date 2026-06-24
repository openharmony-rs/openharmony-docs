# @Component：自定义组件

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Component装饰器能装饰struct关键字声明的数据结构。struct被\@Component装饰后具备组件化的能力，需要实现build方法描述UI，一个struct只能被一个\@Component装饰。开发指南参考：[创建自定义组件](../../../ui/state-management/arkts-create-custom-components.md)。

> **说明：**
>
> - 本装饰器首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 从API version 11开始，\@Component可以接受一个可选的boolean类型参数。
>
> - 从API版本26.0.0开始，\@Component可以接受可选参数`reusePool`和`poolAccepts`，用于配置全局复用池，开发指南参考：[全局复用：集中化的组件回收与复用](../../../ui/state-management/arkts-global-reuse-pool.md)

## @Component

const Component: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 名称                  | 类型    | 必填  | 说明                                                         |
| --------------------- | ------ | ---- | ------------------------------------------------------------ |
| options<sup>11+</sup> | [ComponentOptions](./ts-custom-component-parameter.md#componentoptions) | 否 | \@Component装饰器选项，缺省时默认关闭组件冻结和全局复用功能。 |


**示例：**

```ts
@Entry
@Component({ freezeWhenInactive: true })
struct MyComponent {
  build() {
    Column() {
      Text('Hello World!')
    }
  }
}
```