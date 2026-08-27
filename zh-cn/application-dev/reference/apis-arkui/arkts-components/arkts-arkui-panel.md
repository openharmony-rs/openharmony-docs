# Panel

可滑动面板，提供一种轻量的内容展示窗口，方便在不同尺寸中切换。

## Panel

```TypeScript
Panel(show: boolean)
```

滑动面板组件。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | 控制Panel显示或隐藏，true表示显示面板，false表示隐藏面板。 |

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PanelHeight](arkts-arkui-panelheight-e.md) | 自定义内容显示区域的枚举。 |
| [PanelMode](arkts-arkui-panelmode-e.md) | 设置滑动面板的初始状态 |
| [PanelType](arkts-arkui-paneltype-e.md) | 设置滑动面板的类型 |

## 示例

```TypeScript
// xxx.ets
@Entry
@Component
struct PanelExample {
  @State show: boolean = false

  build() {
    Column() {
      Text('2021-09-30    Today Calendar: 1.afternoon......Click for details')
        .width('90%')
        .height(50)
        .borderRadius(10)
        .backgroundColor(0xFFFFFF)
        .padding({ left: 20 })
        .onClick(() => {
          this.show = !this.show;
        })
      Panel(this.show) { // 展示日程
        Column() {
          Text('Today Calendar')
          Divider()
          Text('1. afternoon 4:00 The project meeting')
        }
      }
      .type(PanelType.Foldable)
      .mode(PanelMode.Half)
      .dragBar(true) // 默认开启
      .halfHeight(500) // 设置半屏高度为500，默认为当前组件主轴大小的一半
      .showCloseIcon(true) // 显示关闭图标
      .onChange((width: number, height: number, mode: PanelMode) => {
        console.info(`width:${width},height:${height},mode:${mode}`);
      })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```
