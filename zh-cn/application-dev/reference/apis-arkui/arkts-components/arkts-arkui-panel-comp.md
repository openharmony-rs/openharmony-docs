# Panel

可滑动面板，提供一种轻量的内容展示窗口，方便在不同尺寸中切换。

> **说明：** > > 从API version 12开始，该组件不再维护，推荐使用通用属性[bindSheet](arkts-arkui-commonmethod-c.md#bindsheet)。

## Panel

```TypeScript
Panel(show: boolean)
```

滑动面板组件。

> **说明：** 
> 
> 从API version 7开始支持，从API version 12开始废弃。

**起始版本：** 7

**废弃版本：** 12

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| show | boolean | 是 | 控制Panel显示或隐藏，true表示显示面板，false表示隐藏面板。<br>**说明：** <br>如果设置为false时，则不占位隐藏。Visibility.None或show之间有一个生效时，都会生效不占位隐藏。<br>属性show的优先级高于此参数，当属性show被设置时，本参数可能不生效。 |

## 汇总

### 枚举

| 名称 | 说明 |
| --- | --- |
| [PanelHeight](arkts-arkui-panelheight-e.md) | 设置可滑动面板的高度。 |
| [PanelMode](arkts-arkui-panelmode-e.md) | 设置可滑动面板的初始状态 |
| [PanelType](arkts-arkui-paneltype-e.md) | 设置可滑动面板的类型 |

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
