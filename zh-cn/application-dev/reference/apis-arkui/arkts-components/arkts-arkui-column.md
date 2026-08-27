# Column

沿垂直方向布局的容器。适用于需要将多个子组件按垂直方向依次排列的场景，如列表项、表单项、卡片内容等。支持设置子组件间距、对齐方式等属性，能够快速实现垂直方向的线性布局。
> **说明：** > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > > Column未设置高度或宽度时，在主轴（垂直方向）或交叉轴（水平方向）方向上自适应子组件大小。

## 子组件

可以包含子组件。

## Column

```TypeScript
Column(options?: ColumnOptions)
```

创建垂直方向线性布局容器，可以设置子组件的间距。

> **说明：**
> 
> 在复杂界面中使用多组件嵌套时，若布局组件的嵌套层数过深或嵌套的组件数量过多，将会产生额外开销。建议通过移除冗余节点、利用布局边界减少布局计算、合理采用渲染控制语法及布局组件方法来优化性能。最佳实践请参考布局优化指导。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ColumnOptions](arkts-arkui-columnoptions-i.md) | 否 | Column组件的间距配置选项。通过space属性设置纵向布局元素垂直方向间距。当需要为子组件设置固定垂直间距时传入此参数；省略时不设置子组件间距。 |

## Column

```TypeScript
Column(options?: ColumnOptions | ColumnOptionsV2)
```

创建垂直方向线性布局容器，可以设置子组件的间距。

> **说明：**
> 
> 在复杂界面中使用多组件嵌套时，若布局组件的嵌套层数过深或嵌套的组件数量过多，将会产生额外开销。建议通过移除冗余节点、利用布局边界减少布局计算、合理采用渲染控制语法及布局组件方法来优化性能。最佳实践请参考布局优化指导。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ColumnOptions](arkts-arkui-columnoptions-i.md) \| [ColumnOptionsV2](arkts-arkui-columnoptionsv2-i.md) | 否 | Column组件的间距配置选项。通过space属性设置纵向布局元素垂直方向间距，space支持设置number、 string或Resource类型。当需要为子组件设置固定垂直间距时传入此参数；省略时不设置子组件间距。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColumnOptions](arkts-arkui-columnoptions-i.md) | 设置Column组件的子组件间距属性。 |
| [ColumnOptionsV2](arkts-arkui-columnoptionsv2-i.md) | 设置Column组件的子组件间距属性。间距类型SpaceType支持number、string或Resource类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SpaceType](arkts-arkui-spacetype-t.md) | Column组件构造函数中space支持的数据类型，取值类型为下表类型中的并集。 |

## 示例

本示例展示设置Column组件的布局属性，如间距、对齐方式等属性后的效果。

```TypeScript
// resources/base/element/string.json
{
  "string": [
    {
      "name": "stringSpace",
      "value": "5"
    }
  ]
}
```

```TypeScript
// xxx.ets
@Entry
@Component
struct ColumnExample {
  build() {
    Scroll() {
      Column({ space: 5 }) {
        // 设置子元素垂直方向间距为5
        Text('space').width('90%')
        Column({ space: 5 }) {
          Column().width('100%').height(30).backgroundColor(0xAFEEEE)
          Column().width('100%').height(30).backgroundColor(0x00FFFF)
        }.width('90%').height(100).border({ width: 1 })

        // 通过资源引用方式设置子元素垂直方向间距
        Text('Resource space').width('90%')
        Column({ space: $r('app.string.stringSpace') }) {
          Column().width('100%').height(30).backgroundColor(0xAFEEEE)
          Column().width('100%').height(30).backgroundColor(0x00FFFF)
        }.width('90%').height(100).border({ width: 1 })

        // 设置子元素水平方向对齐方式
        Text('alignItems(Start)').width('90%')
        Column() {
          Column().width('50%').height(30).backgroundColor(0xAFEEEE)
          Column().width('50%').height(30).backgroundColor(0x00FFFF)
        }.alignItems(HorizontalAlign.Start).width('90%').border({ width: 1 })

        Text('alignItems(End)').width('90%')
        Column() {
          Column().width('50%').height(30).backgroundColor(0xAFEEEE)
          Column().width('50%').height(30).backgroundColor(0x00FFFF)
        }.alignItems(HorizontalAlign.End).width('90%').border({ width: 1 })

        Text('alignItems(Center)').width('90%')
        Column() {
          Column().width('50%').height(30).backgroundColor(0xAFEEEE)
          Column().width('50%').height(30).backgroundColor(0x00FFFF)
        }.alignItems(HorizontalAlign.Center).width('90%').border({ width: 1 })

        // 设置子元素垂直方向的对齐方式
        Text('justifyContent(Center)').width('90%')
        Column() {
          Column().width('90%').height(30).backgroundColor(0xAFEEEE)
          Column().width('90%').height(30).backgroundColor(0x00FFFF)
        }.height(100).border({ width: 1 }).justifyContent(FlexAlign.Center)

        Text('justifyContent(End)').width('90%')
        Column() {
          Column().width('90%').height(30).backgroundColor(0xAFEEEE)
          Column().width('90%').height(30).backgroundColor(0x00FFFF)
        }.height(100).border({ width: 1 }).justifyContent(FlexAlign.End)
      }.width('100%').padding({ top: 5 })
    }.width('100%').height('100%')
  }
}
```

本示例展示设置Column组件的reverse属性后的效果。

```TypeScript
@Entry
@Component
struct ColumnReverseSample {
  build() {
    Column() {
      Text("1")
        .width(50)
        .height(100)
        .backgroundColor(0xAFEEEE)

      Text("2")
        .width(50)
        .height(100)
        .backgroundColor(0x00FFFF)
    }
    .height(300)
    .width(100)
    .border({ width: 1 })
    .reverse(true)
  }
}
```
