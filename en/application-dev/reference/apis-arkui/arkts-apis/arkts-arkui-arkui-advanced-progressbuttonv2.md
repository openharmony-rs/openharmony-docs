# @ohos.arkui.advanced.ProgressButtonV2

The **ProgressButtonV2** component is a text-based download button with a progress indicator that shows the download
 progress.

This component is implemented based on
 [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared
 with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1),
 state management V2 delivers enhanced capabilities for deep observation and management of data objects, and is no
 longer limited to the component level. With state management V2, you can control the data and states of the text
 download button more flexibly through this component, achieving more efficient UI refresh.

Device differences: When this API is used on wearable devices, the application runs abnormally, and the exception
 information indicates that the API is not defined. On other devices, this API can be called as normal.

> **NOTE**
 >
 > - If the **ProgressButtonV2** component has [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) or
 > [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) configured, the compiler toolchain automatically
 > generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node
 > rather than the **ProgressButtonV2** component itself. As a result, the configured universal attributes and
 > universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes
 > and events with the **ProgressButtonV2** component.



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
| [ProgressButtonV2](arkts-arkui-arkui-advanced-progressbuttonv2-progressbuttonv2-s.md) | Creates a **ProgressButtonV2** component. |

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
