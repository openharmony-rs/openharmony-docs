# createFromBuilder

## Modules to Import

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## createFromBuilder

```TypeScript
function createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>,
    delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): void
```

Renders a custom component in the application background and outputs its snapshot. This API uses an asynchronous callback to return the result. The coordinates and size of the offscreen component's drawing area can be obtained through the callback.

> **NOTE:** 
> 
> - Since API version 12, you can use the [getComponentSnapshot](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentsnapshot)API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md)object associated with the current UI context.
> 
> - To account for the time spent in awaiting component building and rendering, the callback of offscreen snapshots has a delay of less than 500 ms.
> 
> - Components in the builder do not support the setting of animation-related attributes, such as transition.
> 
> - If a component is on a time-consuming task, for example, an [Image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) or Web component that is loading online images, its loading may be still in progress when this API is called. In this case, the output snapshot does not represent the component in the way it looks when the loading is successfully completed.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** createFromBuilder

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) | Yes | Builder of the custom component.<br>Note: The global builder is not supported.<br>If the root component of the builder has a width or height of zero, the snapshot operation will fail with error code 100001. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the result. The coordinates and size of the offscreen component's drawing area can be obtained through the callback. |
| delay | number | No | Delay time for triggering the screenshot command. When the layout includes an image component, it is necessary to set a delay time to allow the system to decode the image resources. The decoding time is subject to the resource size. In light of this, whenever possible, use pixel map resources that do not require decoding.<br> When pixel map resources are used or when **syncLoad** to **true** for the **Image** component, you can set **delay** to **0** to forcibly capture snapshots without waiting. This delay time does not refer to the time from the API call to the return: As the system needs to temporarily construct the passed- in **builder** offscreen, the return time is usually longer than this delay.<br>Note: In the **builder** passed in, state variables should not be used to control the construction of child components. If they are used, they should not change when the API is called, so as to avoid unexpected snapshot results.<br> Default value: **300**<br> Unit: ms<br> Value range: [0, +∞). If the value is less than 0, the default value is used.<br>**Since:** 12 |
| checkImageStatus | boolean | No | Whether to verify the image decoding status before taking a snapshot.<br> **true**: Check whether all Image components have been decoded. <br>**false**: Skip verification. If the verification is not completed, snapshot capture will be canceled and an exception will be returned.<br>Default value: **false**<br>**Since:** 12 |
| options | [SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The builder is not a valid build function. |
| [160001](../errorcode-snapshot.md#160001-image-loading-error) | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct OffscreenSnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined

  @Builder
  RandomBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Test menu item 1')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('Test menu item 2')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
    }
    .width(100)
    .id("builder")
  }

  build() {
    Column() {
      Button("click to generate offscreen UI snapshot")
        .onClick(() => {
          // You are advised to use this.getUIContext().getComponentSnapshot().createFromBuilder().
          componentSnapshot.createFromBuilder(() => {
            this.RandomBuilder()
          },
            (error: Error, pixmap: image.PixelMap) => {
              if (error) {
                console.error(`error:${JSON.stringify(error)}`)
                return;
              }
              this.pixmap = pixmap
              // Save the pixmap to a file.
              // ....
              // Obtain the component size and position.
              let info = this.getUIContext().getComponentUtils().getRectangleById("builder")
              console.info(info.size.width + ' ' + info.size.height + ' ' + info.localOffset.x + ' ' +
              info.localOffset.y + ' ' + info.windowOffset.x + ' ' + info.windowOffset.y)
            }, 320, true, { scale: 2, waitUntilRenderFinished: true })
        })
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```

```TypeScript
import { componentSnapshot } from '@kit.ArkUI'
import { image } from '@kit.ImageKit'

@Entry
@Component
struct OffscreenSnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined

  @Builder
  RandomBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Test menu item 1')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('Test menu item 2')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
    }
    .width(100)
    .id("builder")
  }

  build() {
    Column() {
      Button("click to generate offscreen UI snapshot")
        .onClick(() => {
          // You are advised to use this.getUIContext().getComponentSnapshot().createFromBuilder().
          componentSnapshot.createFromBuilder(() => {
            this.RandomBuilder()
          }, 320, true, { scale: 2, waitUntilRenderFinished: true })
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap
              // Save the pixmap to a file.
              // ....
              // Obtain the component size and position.
              let info = this.getUIContext().getComponentUtils().getRectangleById("builder")
              console.info(`${info.size.width} ${info.size.height} ${info.localOffset.x} ${
              info.localOffset.y} ${info.windowOffset.x} ${info.windowOffset.y}`)
            }).catch((err: Error) => {
            console.error(`error:${err}`)
          })
        })
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```


## createFromBuilder

```TypeScript
function createFromBuilder(builder: CustomBuilder, delay?: number,
    checkImageStatus?: boolean, options?: SnapshotOptions): Promise<image.PixelMap>
```

Renders a custom component in the application background and outputs its snapshot. This API uses a promise to return the result. The coordinates and size of the offscreen component's drawing area can be obtained through the callback.

> **NOTE:** 
> 
> - Since API version 12, you can use the [getComponentSnapshot](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentsnapshot)API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md)object associated with the current UI context.
> 
> - To account for the time spent in awaiting component building and rendering, the callback of offscreen snapshots has a delay of less than 500 ms.
> 
> - Components in the builder do not support the setting of animation-related attributes, such as transition.
> 
> - If a component is on a time-consuming task, for example, an [Image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) or Web component that is loading online images, its loading may be still in progress when this API is called. In this case, the output snapshot does not represent the component in the way it looks when the loading is successfully completed.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** createFromBuilder

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) | Yes | Builder of the custom component.<br>Note: The global builder is not supported.<br>If the root component of the builder has a width or height of zero, the snapshot operation will fail with error code 100001. |
| delay | number | No | Delay time for triggering the screenshot command. When the layout includes an image component, it is necessary to set a delay time to allow the system to decode the image resources. The decoding time is subject to the resource size. In light of this, whenever possible, use pixel map resources that do not require decoding.<br> When pixel map resources are used or when **syncLoad** to **true** for the **Image** component, you can set **delay** to **0** to forcibly capture snapshots without waiting. This delay time does not refer to the time from the API call to the return: As the system needs to temporarily construct the passed- in **builder** offscreen, the return time is usually longer than this delay.<br>Note: In the **builder** passed in, state variables should not be used to control the construction of child components. If they are used, they should not change when the API is called, so as to avoid unexpected snapshot results.<br> Default value: **300**<br> Unit: ms<br>**Since:** 12 |
| checkImageStatus | boolean | No | Whether to verify the image decoding status before taking a snapshot.<br> **true**: Check whether all Image components have been decoded. <br>**false**: Skip verification. If the verification is not completed, snapshot capture will be canceled and an exception will be returned.<br>Default value: **false**<br>**Since:** 12 |
| options | [SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | No | Custom settings of the snapshot.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | The builder is not a valid build function. |
| [160001](../errorcode-snapshot.md#160001-image-loading-error) | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled.<br>**Applicable version:** 12 and later |

**Examples**

See [createFromBuilder](#createfrombuilder)
