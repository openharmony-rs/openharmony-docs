# @ohos.arkui.advanced.ProgressButtonV2

## Modules to Import

```TypeScript
import { ProgressButtonV2, ProgressButtonV2Color, ProgressButtonV2ColorOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [ProgressButtonV2Color](arkts-arkui-arkui-advanced-progressbuttonv2-progressbuttonv2color-c.md) | Declare ProgressButtonV2 Color. |

### Structs

| Name | Description |
| --- | --- |
| [ProgressButtonV2](arkts-arkui-arkui-advanced-progressbuttonv2-progressbuttonv2-s.md) | Declare Component ProgressButtonV2 |

### Interfaces

| Name | Description |
| --- | --- |
| [ProgressButtonV2ColorOptions](arkts-arkui-arkui-advanced-progressbuttonv2-progressbuttonv2coloroptions-i.md) | Declare Color options interface of the ProgressButtonV2. |

### Types

| Name | Description |
| --- | --- |
| [ClickCallback](arkts-arkui-clickcallback-t.md) | Defines ClickCallback of the ProgressButtonV2. |

## Examples

This example demonstrates how to create a simple download button with a progress indicator that shows the loading status of a text file.

```TypeScript
import { LengthMetrics, ProgressButtonV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local progressIndex: number = 0;
  @Local textState: string = 'Download';
  @Local buttonWidth: LengthMetrics = LengthMetrics.vp(200);
  @Local isRunning: boolean = false;
  @Local enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButtonV2({
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            isEnabled: this.enableState,
            onClicked: () => {
              if (this.textState && !this.isRunning && this.progressIndex < 100) {
                this.textState = 'Continue';
              }
              this.isRunning = !this.isRunning;
              let timer = setInterval(() => {
                if (this.isRunning) {
                  if (this.progressIndex === 100) {
                    clearInterval(timer);
                  } else {
                    this.progressIndex++;
                    if (this.progressIndex === 100) {
                      this.textState = 'Completed';
                      this.enableState = false;
                    }
                  }
                } else {
                  clearInterval(timer);
                }
              }, 20);
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 });
      }
    }
  }
}
```
