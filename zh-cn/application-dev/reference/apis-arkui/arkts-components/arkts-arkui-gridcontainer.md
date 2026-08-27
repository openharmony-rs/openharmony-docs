# GridContainer

纵向排布栅格布局容器，仅在栅格布局场景中使用。栅格布局通过将容器宽度划分为指定列数，实现响应式布局，子组件可占用不同的列数和偏移量。适用于响应式页面布局、多栏目内容展示、仪表盘布局等场景。
> **说明：** > > 从API version 9开始，该组件不再维护，推荐使用新组件GridCol、GridRow。 > > 该组件从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件

可以包含子组件。

## GridContainer

```TypeScript
GridContainer(value?: GridContainerOptions)
```

创建纵向排布栅格布局容器。

> **说明：**
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** grid_col/GridColInterface

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GridContainerOptions](arkts-arkui-gridcontaineroptions-i.md) | 否 | GridContainer配置参数，用于设置栅格布局的列数、设备宽度类型、列间距和两侧间距。不传入时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [GridContainerOptions](arkts-arkui-gridcontaineroptions-i.md) | 栅格栅格布局容器配置参数对象，用于设置GridContainer组件的列数、设备宽度类型、列间距和两侧间距。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SizeType](arkts-arkui-sizetype-e.md) | 设备宽度类型枚举，用于在栅格布局中区分不同宽度的设备类型，实现响应式布局。 |

## 示例

```TypeScript
// xxx.ets
// 栅格布局示例：GridContainer配合useSizeType实现响应式布局
@Entry
@Component
struct GridContainerExample {
  @State sizeType: SizeType = SizeType.XS // 当前设备宽度类型

  build() {
    Column({ space: 5 }) {
      // 配置12列栅格布局，列间距10vp，两侧间距20vp
      GridContainer({ columns: 12, sizeType: this.sizeType, gutter: 10, margin: 20 }) {
        Row() {
          // 子组件通过useSizeType设置不同设备宽度类型下的span（占列数）和offset（偏移列数）
          Text('1')
            .useSizeType({
              xs: { span: 6, offset: 0 },
              sm: { span: 2, offset: 0 },
              md: { span: 2, offset: 0 },
              lg: { span: 2, offset: 0 }
            })
            .height(50).backgroundColor(0x4682B4).textAlign(TextAlign.Center)
          Text('2')
            .useSizeType({
              xs: { span: 2, offset: 6 },
              sm: { span: 6, offset: 2 },
              md: { span: 2, offset: 2 },
              lg: { span: 2, offset: 2 }
            })
            .height(50).backgroundColor(0x00BFFF).textAlign(TextAlign.Center)
          Text('3')
            .useSizeType({
              xs: { span: 2, offset: 8 },
              sm: { span: 2, offset: 8 },
              md: { span: 6, offset: 4 },
              lg: { span: 2, offset: 4 }
            })
            .height(50).backgroundColor(0x4682B4).textAlign(TextAlign.Center)
          Text('4')
            .useSizeType({
              xs: { span: 2, offset: 10 },
              sm: { span: 2, offset: 10 },
              md: { span: 2, offset: 10 },
              lg: { span: 6, offset: 6 }
            })
            .height(50).backgroundColor(0x00BFFF).textAlign(TextAlign.Center)
        }
      }.width('90%')

      Text('Click Simulate to change the device width').fontSize(9).width('90%').fontColor(0xCCCCCC)
      // 点击按钮切换设备宽度类型，观察响应式布局变化
      Row() {
        Button('XS')
          .onClick(() => {
            this.sizeType = SizeType.XS
          }).backgroundColor(0x317aff)
        Button('SM')
          .onClick(() => {
            this.sizeType = SizeType.SM
          }).backgroundColor(0x317aff)
        Button('MD')
          .onClick(() => {
            this.sizeType = SizeType.MD
          }).backgroundColor(0x317aff)
        Button('LG')
          .onClick(() => {
            this.sizeType = SizeType.LG
          }).backgroundColor(0x317aff)
      }
    }.width('100%').margin({ top: 5 })
  }
}
```
