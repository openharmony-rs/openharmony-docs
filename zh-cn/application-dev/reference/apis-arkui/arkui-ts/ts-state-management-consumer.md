# @Consumer：跨组件层级双向同步

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[@Provider](./ts-state-management-provider.md)和@Consumer搭配使用，用于[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)中，实现跨组件层级的数据双向同步。@Consumer装饰数据消费方，从数据源获取数据，适用于多层嵌套组件间需要共享和同步状态的场景，可避免通过多层组件逐级传递数据的繁琐操作，简化跨组件层级状态管理。如果@Consumer在组件树中未找到别名匹配的@Provider，将使用自身初始值，不进行数据同步。

在ArkTS-Dyn中使用时，开发指南参考：[@Provider装饰器和@Consumer装饰器：跨组件层级双向同步（ArkTS-Dyn）](../../../ui/state-management/arkts-new-provider-and-consumer.md)。

> **说明：**
>
> 从API version 12开始，支持该装饰器。

## @Consumer

const Consumer: (aliasName?: string) => PropertyDecorator

用于状态管理V2中，需与@Provider搭配使用，实现跨组件层级的数据双向同步；装饰数据消费方，从数据源获取数据。如果@Consumer在组件树中未找到别名匹配的@Provider，将使用自身初始值，不进行数据同步。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**卡片能力（仅ArkTS-Dyn）：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型   | 必填 | 说明                               |
| --------- | ------ | ---- | ---------------------------------- |
| aliasName | string | 否   | 用于设置别名，作为@Consumer与@Provider匹配的标识，需与@Provider的别名一致；缺省时为变量名。 |

**返回值：**

| 类型 | 说明 |
| --------- | ------ |
| PropertyDecorator | 属性装饰器。开发者无需关注该返回值。 |

**示例：**

```ts
@Entry
@ComponentV2
struct Index {
  // @Provider提供数据
  @Provider() str: string = 'aaa';

  build() {
    Column() {
      Child()
    }
  }
}

@ComponentV2
struct Child {
  // @Consumer消费数据
  @Consumer() str: string = '';

  build() {
    Column() {
      Text(`${this.str}`)
    }
  }
}
```

