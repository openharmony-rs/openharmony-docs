# ProgressButton
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fengluochenai-->
<!--Designer: @YanSanzo-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->


The **ProgressButton** component is a text-based download button with a progress indicator that shows the download progress.


> **NOTE**
>
> - This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - If the **ProgressButton** component has [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) configured, the compiler toolchain automatically generates an additional **__Common__** node and mounts the universal attributes and universal events on this node rather than the **ProgressButton** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **ProgressButton** component.


## Modules to Import

```
import { ProgressButton } from '@kit.ArkUI';
```

## ProgressButton

ProgressButton({progress: number, content: ResourceStr, progressButtonWidth?: Length, clickCallback: () => void, enable:
boolean, colorOptions?: ProgressButtonColorOptions, progressButtonRadius?: LengthMetrics})

**Decorator**: @Component


**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name                               | Type                                                           | Mandatory| Decorator | Description                                                                                                                                     |
|-----------------------------------|---------------------------------------------------------------|---|--------|-----------------------------------------------------------------------------------------------------------------------------------------|
| progress                          | number                                                        | Yes| \@Prop | Current download progress.<br>The value ranges from 0 to 100. Values less than 0 are adjusted to **0**, and values greater than 100 are capped at **100**.<br>Default value: **0**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.               |
| content                           | [ResourceStr](ts-types.md#resourcestr)                        | Yes| \@Prop | Button text.<br>The default value is an empty string.<br>Note: The text is truncated with an ellipsis (...) if it exceeds the maximum display width of the component. The Resource type is supported since API version 20.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| progressButtonWidth               | [Length](ts-types.md#length)                                  | No| -      | Button width, in vp.<br>The value must be greater than or equal to 44 vp.<br>The default value is **44vp**. If the provided value is not of the Resource type and is either less than the default value or invalid, the system will automatically use the default value. If the provided value is of the Resource type but is less than the default value, the system will automatically use the default value. If the provided value is invalid, the button width will be 100% of the container width.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                     |
| clickCallback                     | () => void                                                 | Yes| -      | Callback invoked when the button is clicked.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                         |
| enable                            | boolean                                                       | Yes| \@Prop | Whether the button can be clicked.<br> **true**: The button can be clicked.<br> **false**: The button cannot be clicked.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                     |
| colorOptions<sup>18+<sup>         | [ProgressButtonColorOptions](#progressbuttoncoloroptions18)   | No| \@Prop | Color options of the button.<br>**Atomic service API**: This API can be used in atomic services since API version 18.                                                                            |
| progressButtonRadius<sup>18+<sup> | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No| \@Prop | Corner radius of the button. It cannot be set in percentage.<br>Value range: [0, height/2]<br>Default value: height/2<br>If the value is less than 0, the value **0** is used. If the value is invalid, the default value is used. If the input parameter is **undefined**, the default value is used. When using LengthMetrics.vp, you are advised to provide a specific numeric value. Passing **null** or **undefined** will result in an exception.<br>**Atomic service API**: This API can be used in atomic services since API version 18.   |

## ProgressButtonColorOptions<sup>18+<sup>

Defines the color options for the download button.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name             | Type                                    | Read-Only| Optional| Description                                                              |
|-----------------|----------------------------------------|---|---|------------------------------------------------------------------|
| progressColor   | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Color of the progress indicator.<br>Default value: **#330A59F7**                                        |
| borderColor     | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Border color of the button.<br>Default value: **#330A59F7**                                       |
| textColor       | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Text color of the button.<br>Default value: system default value **#CE000000**                                |
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Background color of the button.<br>Default value: **\$r('sys.color.ohos_id_color_foreground_contrary')**|

## Events
The [universal events](ts-component-general-events.md) are not supported.

## Example

### Example 1: Creating a Download Button with a Progress Indicator
This example demonstrates how to create a simple download button with a progress indicator that shows the loading status of a text file.
```ts
import { ProgressButton } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State progressIndex: number = 0;
  @State textState: string = 'Download';
  @State buttonWidth: number = 200;
  @State isRunning: boolean = false;
  @State enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButton({
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            enable: this.enableState,
            clickCallback: () => {
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
              }, 20)
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 })
      }
    }
  }
}
```


![img.png](./figures/img.png)

### Example 2: Implementing a Download Button with Custom Colors
This example shows how to implement a download button with custom colors.
```ts
import { ProgressButton } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State progressIndex: number = 0;
  @State textState: string = 'Download';
  @State buttonWidth: number = 200;
  @State isRunning: boolean = false;
  @State enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButton({
            // Set the color options of the download button.
            colorOptions: {
              progressColor: Color.Orange,
              borderColor: Color.Black,
              textColor: Color.Blue,
              backgroundColor: Color.Pink
            },
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            enable: this.enableState,
            clickCallback: () => {
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
              }, 20)
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 })
      }
    }
  }
}
```
![en-us_image_progressbutton_example02](figures/en-us_image_progressbutton_example02.png)

### Example 3: Implementing a Download Button with Custom Corner Radius
This example shows how to implement a download button with custom corner radius.
```ts
import { ProgressButton, LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State progressIndex: number = 0;
  @State textState: string = 'Download';
  @State buttonWidth: number = 200;
  @State isRunning: boolean = false;
  @State enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButton({
            progressButtonRadius: LengthMetrics.vp (8), // Set the custom corner radius to 8 vp.
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            enable: this.enableState,
            clickCallback: () => {
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
              }, 20)
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 })
      }
    }
  }
}
```
![en-us_image_progressbutton_example03](figures/en-us_image_progressbutton_example03.png)
