# @Provider

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 12开始，支持该装饰器。

@Provider和@Consumer搭配使用，用于状态管理V2中，实现跨组件层级的数据双向同步。@Provider修饰数据提供方，为子组件提供数据。

在ArkTS-Dyn中使用时，开发指南参考：[\@Provider装饰器和\@Consumer装饰器：跨组件层级双向同步（ArkTS-Dyn）](../../../ui/state-management/arkts-new-provider-and-consumer.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                               |
| ------ | ------ | ---- | ---------------------------------- |
| aliasName  | string | 否   | 用于设置别名，缺省时默认为变量名。 |

**示例：**

```ts
@Entry
@ComponentV2
struct Index {
  @Provider() str: string = 'aaa';
  build() {
    Column() {
      Text(`parent: ${this.str}`)
      Child()
    }
  }
}

@ComponentV2
struct Child {
  @Consumer() str: string = '';
  build() {
    Column() {
      Text(`child: ${this.str}`)
    }
  }
}
```

