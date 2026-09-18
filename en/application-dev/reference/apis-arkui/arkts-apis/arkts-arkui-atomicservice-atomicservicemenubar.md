# @ohos.atomicservice.AtomicServiceMenuBar(System API)

## Child Components

Not supported

## Attributes

The universal attributes are not supported.

## Modules to Import

```TypeScript
import { AtomicServiceMenuBar } from '@kit.ArkUI';
```

## Summary

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [AtomicServiceMenuBar](arkts-arkui-atomicservice-atomicservicemenubar-atomicservicemenubar-c-sys.md) | Creates an **AtomicServiceMenuBar** object based on the context of the current atomic service. The object is used to control the display of the menu function capsule in the upper right corner. |
<!--DelEnd-->

## Examples

```TypeScript
import { AtomicServiceMenuBar } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private menuBar: AtomicServiceMenuBar = new AtomicServiceMenuBar(this.getUIContext());

  @Builder
  private menuCapsuleShow(title: string, text: string, event?: () => void) {
    Column() {
      if (typeof event === 'function') {
        Button(title)
          .width(300)
          .height(50)
          .fontSize(16)
          .borderRadius(25)
          .onClick(() => {
            event();
          })
      }
      Text(`Expected result: ${text}`)
        .width(300)
        .textAlign(TextAlign.Start)
        .fontSize(12)
        .margin({ top: 5, bottom: 15})
    }
  }

  build() {
    Column() {
      this.menuCapsuleShow('Display menu function capsule', 'Clicking this button will display the menu function capsule.', () => {
        this.menuBar.setVisible(true);
      });
      this.menuCapsuleShow('Hide menu function capsule', 'Clicking this button will hide the menu function capsule.', () => {
        this.menuBar.setVisible(false);
      });
    }
    .width('100%')
    .height('100%')
    .padding({ top: 100 })
  }
}
```
