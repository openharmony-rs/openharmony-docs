# Panel

Defines Panel Component.

## Panel

```TypeScript
Panel(show: boolean)
```

Called when the panel slidable panel pops up.

**Since:** 7

**Deprecated since:** 12

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| show | boolean | Yes |  |

## Summary

### Enums

| Name | Description |
| --- | --- |
| [PanelHeight](arkts-arkui-panelheight-e.md) | Enum for custom content display area. |
| [PanelMode](arkts-arkui-panelmode-e.md) | Sets the initial state of the slidable panel. |
| [PanelType](arkts-arkui-paneltype-e.md) | Sets the type of sliding panel. |

## Examples

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
      Panel(this.show) { // Display calendar events.
        Column() {
          Text('Today Calendar')
          Divider()
          Text('1. afternoon 4:00 The project meeting')
        }
      }
      .type(PanelType.Foldable)
      .mode(PanelMode.Half)
      .dragBar(true) // The drag bar is enabled by default.
      .halfHeight(500) // Set the half height to 500. The default value is half of the main axis size of the current component.
      .showCloseIcon(true) // Display the close icon.
      .onChange((width: number, height: number, mode: PanelMode) => {
        console.info(`width:${width},height:${height},mode:${mode}`);
      })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```
