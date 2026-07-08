# @Provide：与后代组件双向同步

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Provide和\@Consume配套使用，用于状态管理V1，实现跨组件层级的双向同步，适用于需要跨越多层组件传递状态、避免逐层传递的场景，能够解决组件层级较深时状态传递繁琐的问题。\@Provide装饰的变量作为数据源，通过别名或变量名与\@Consume装饰的变量建立双向绑定关系。当\@Provide或\@Consume装饰的变量发生变化时，变化会自动同步到对方。

开发指南参考：[\@Provide装饰器和\@Consume装饰器：与后代组件双向同步](../../../ui/state-management/arkts-provide-and-consume.md)。

> **说明：**
>
> 本装饰器从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @Provide

const Provide: PropertyDecorator & ((value: string | ProvideOptions) => PropertyDecorator)

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                        | 必填 | 说明                         |
| ------ | ------------------------------------------------- | ---- | ---------------------------- |
| value  | string \| [ProvideOptions](#provideoptions11) | 否   | 用于设置别名及允许重写的别名。<br/>ProvideOptions用于设置allowOverride参数，指定允许重写的别名。<br>缺省时默认别名为变量名，不允许重写。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PropertyDecorator | 属性装饰器，开发者无需关注该返回值。 |

## ProvideOptions<sup>11+</sup>

ProvideOptions是\@Provide的选项。允许在同一组件树下通过allowOverride重写同名的\@Provide。

**卡片能力：** 从API version 11开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**属性**：

| 名称 | 类型     | 只读 | 可选 | 说明                                                         |
| ------ | -------- | ---- | ---- | ------------------------------------------------------------ |
| allowOverride  | string   | 否   | 是   | 允许\@Provide重写的别名。允许在同一组件树下通过allowOverride重写同名的@Provide。如果开发者未写allowOverride，定义同名的\@Provide，运行时会报错。<br/>默认值：undefined，表示\@Provide不允许重写。 |

**示例：**

```ts
@Entry
@Component
struct Index {
  @Provide message: string = 'aaa'; // @Provide提供数据，变量名'message'作为别名

  build() {
    Column() {
      Text(`provide: ${this.message}`)
      Child()
    }
  }
}

@Component
struct Child {
  @Consume message: string; // @Consume消费数据，通过相同的变量名'message'与@Provide建立配对关系

  build() {
    Column() {
      Text(`consume: ${this.message}`)
    }
  }
}
```

