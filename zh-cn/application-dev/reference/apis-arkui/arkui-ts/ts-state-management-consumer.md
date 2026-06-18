# @Consumer：跨组件层级双向同步

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Provider和@Consumer搭配使用，用于状态管理V2中，实现跨组件层级的数据双向同步。@Consumer修饰数据消费方，获取数据源数据。

开发指南参考：[\@Provider装饰器和\@Consumer装饰器：跨组件层级双向同步](../../../ui/state-management/arkts-new-provider-and-consumer.md)。

> **说明：**
>
> 从API version 12开始，支持该装饰器。

## @Consumer 

const Consumer: (aliasName?: string) => PropertyDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名    | 类型   | 必填 | 说明                               |
| --------- | ------ | ---- | ---------------------------------- |
| aliasName | string | 否   | 用于设置别名，缺省时默认为变量名。 |

**示例：**

```ts
@Entry
@ComponentV2
struct Index {
  @Provider() str: string = 'aaa'; // @Provider提供数据
  build() {
    Column() {
      Child()
    }
  }
}

@ComponentV2
struct Child {
  @Consumer() str: string = '';  // @Consumer消费数据
  build() {
    Column() {
      Text(`${this.str}`)
    }
  }
}
```

