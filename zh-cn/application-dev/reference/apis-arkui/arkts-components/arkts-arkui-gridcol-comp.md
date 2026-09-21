# GridCol

栅格布局系统中的列组件，必须作为栅格容器组件([GridRow](arkts-arkui-gridrow-comp.md#grid_row))的子组件使用。适用于响应式布局、多设备适配等需要动态调整列宽的场景。支持响应式断点配置、跨列布局、偏移和排序功能。使用GridCol组件可以快速实现响应式布局，简化多设备适配的开发工作。

> **说明：** > > 该组件从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 子组件

可以包含单个子组件。

## GridCol

```TypeScript
GridCol(option?: GridColOptions)
```

栅格列布局组件。创建成功后，可根据配置的span、offset、order属性进行栅格布局，作为GridRow的子组件参与栅格系统的布局计算。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| option | [GridColOptions](arkts-arkui-gridcol-comp-gridcoloptions-i.md) | 否 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md) | 用于自定义指定在不同宽度设备类型上，栅格子组件占据的栅格数量单位。 |
| [GridColOptions](arkts-arkui-gridcol-comp-gridcoloptions-i.md) | 设置栅格列布局组件布局选项。 |

## 示例

GridCol的基本用法示例。

```TypeScript
// xxx.ets
@Entry
@Component
struct GridColExample {
  @State bgColors: Color[] =
    [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Pink, Color.Grey, Color.Blue, Color.Brown]
  @State currentBp: string = 'unknown'

  build() {
    Column() {
      // 创建栅格容器，配置列数、间距和响应式断点
      GridRow({
        columns: 5,
        gutter: { x: 5, y: 10 },
        // 设置响应式断点，基于窗口尺寸判断
        breakpoints: {
          value: ['400vp', '600vp', '800vp'],
          reference: BreakpointsReference.WindowSize
        },
        direction: GridRowDirection.Row
      }) {
        ForEach(this.bgColors, (color: Color) => {
          // 配置不同断点下的span值，实现响应式布局
          GridCol({
            span: { xs: 1, sm: 2, md: 3, lg: 4 },
            offset: 0,
            order: 0
          }) {
            Row().width('100%').height('20vp')
          }.borderColor(color).borderWidth(2)
        })
      }.width('100%').height('100%')
      .onBreakpointChange((breakpoint) => {
        this.currentBp = breakpoint
      })
    }.width('80%').margin({ left: 10, top: 5, bottom: 5 }).height(200)
    .border({ color: '#880606', width: 2 })
  }
}
```
