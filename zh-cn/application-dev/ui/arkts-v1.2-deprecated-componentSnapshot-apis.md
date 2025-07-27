# @ohos.arkui.componentSnapshot

以下接口在ArkTS1.1中已标记为废弃，并在ArkTS1.2中不再支持。

## get

ArkTS1.1接口声明：[get(id: string, callback: AsyncCallback<image.PixelMap>, options?: SnapshotOptions): void](../reference/apis-arkui/js-apis-arkui-componentSnapshot.md#componentsnapshotgetdeprecated)

替代的ArkTS1.2接口声明：[get(id: string, callback: AsyncCallback<image.PixelMap>, options?: componentSnapshot.SnapshotOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#get12)

ArkTS1.1

```typescript
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct SnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined

  build() {
    Column() {
      Row() {
        // 用来显示截图结果的图片组件
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        // 用来被截图的组件
        Image($r('app.media.startIcon'))
          .autoResize(true)
          .width(200)
          .height(200)
          .margin(5)
          .id("snapshot_target")
      }

      Button("click to generate UI snapshot")
        .onClick(() => {
          componentSnapshot.get("snapshot_target", (error: Error, pixmap: image.PixelMap) => {
            if (error) {
              console.error("error: " + JSON.stringify(error))
              return;
            }
            this.pixmap = pixmap
          }, { scale: 2, waitUntilRenderFinished: true })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

ArkTS1.2

```typescript
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct SnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined

  build() {
    Column() {
      Row() {
        // 用来显示截图结果的图片组件
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        // 用来被截图的组件
        Image($r('app.media.startIcon'))
          .autoResize(true)
          .width(200)
          .height(200)
          .margin(5)
          .id("snapshot_target")
      }

      Button("click to generate UI snapshot")
        .onClick(() => {
          // 使用UIContext中的同名方法替代
          this.getUIContext().getComponentSnapshot().get("snapshot_target", (error: Error, pixmap: image.PixelMap) => {
            if (error) {
              console.error("error: " + JSON.stringify(error))
              return;
            }
            this.pixmap = pixmap
          }, { scale: 2, waitUntilRenderFinished: true })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

## get

ArkTS1.1接口声明：[get(id: string, options?: SnapshotOptions): Promise<image.PixelMap>](../reference/apis-arkui/js-apis-arkui-componentSnapshot.md#componentsnapshotgetdeprecated-1)

替代的ArkTS1.2接口声明：[get(id: string, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>](../reference/apis-arkui/js-apis-arkui-UIContext.md#get12-1)

ArkTS1.1

```typescript
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct SnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined

  build() {
    Column() {
      Row() {
        // 用来显示截图结果的图片组件
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        // 用来被截图的组件
        Image($r('app.media.startIcon'))
          .autoResize(true)
          .width(200)
          .height(200)
          .margin(5)
          .id("snapshot_target")
      }

      Button("click to generate UI snapshot")
        .onClick(() => {
          componentSnapshot.get("snapshot_target", { scale: 2, waitUntilRenderFinished: true })
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap
            }).catch((err: Error) => {
            console.log("error: " + err)
          })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

ArkTS1.2

```typescript
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct SnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined

  build() {
    Column() {
      Row() {
        // 用来显示截图结果的图片组件
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        // 用来被截图的组件
        Image($r('app.media.startIcon'))
          .autoResize(true)
          .width(200)
          .height(200)
          .margin(5)
          .id("snapshot_target")
      }

      Button("click to generate UI snapshot")
        .onClick(() => {
          // 使用UIContext中的同名方法替代
          this.getUIContext().getComponentSnapshot().get("snapshot_target", { scale: 2, waitUntilRenderFinished: true })
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap
            }).catch((err: Error) => {
            console.log("error: " + err)
          })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

## createFromBuilder

ArkTS1.1接口声明：[createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): void](../reference/apis-arkui/js-apis-arkui-componentSnapshot.md#componentsnapshotcreatefrombuilderdeprecated)

替代的ArkTS1.2接口声明：[createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#createfrombuilder12)

ArkTS1.1

```typescript
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct OffscreenSnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined

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
      // 用于显示截图结果的图片组件
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
        .margin(10)
      Button("click to generate offscreen UI snapshot")
        .onClick(() => {
          componentSnapshot.createFromBuilder(this.RandomBuilder,
            (error: Error, pixmap: image.PixelMap) => {
              if (error) {
                console.log("error: " + JSON.stringify(error))
                return;
              }
              this.pixmap = pixmap
            }, 320, true, { scale: 2, waitUntilRenderFinished: true })
        })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```

ArkTS1.2

```typescript
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct OffscreenSnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined

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
      // 用于显示截图结果的图片组件
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
        .margin(10)
      Button("click to generate offscreen UI snapshot")
        .onClick(() => {
          // 使用UIContext同名接口替代
          this.getUIContext().getComponentSnapshot().createFromBuilder(this.RandomBuilder,
            (error: Error, pixmap: image.PixelMap) => {
              if (error) {
                console.log("error: " + JSON.stringify(error))
                return;
              }
              this.pixmap = pixmap
            }, 320, true, { scale: 2, waitUntilRenderFinished: true })
        })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```

## createFromBuilder

ArkTS1.1接口声明：[createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): Promise<image.PixelMap>](../reference/apis-arkui/js-apis-arkui-componentSnapshot.md#componentsnapshotcreatefrombuilderdeprecated-1)

替代的ArkTS1.2接口声明：[createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>](../reference/apis-arkui/js-apis-arkui-UIContext.md#createfrombuilder12-1)

ArkTS1.1

```typescript
import { componentSnapshot } from '@kit.ArkUI'
import { image } from '@kit.ImageKit'

@Entry
@ComponentV2
struct OffscreenSnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined

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
          componentSnapshot.createFromBuilder(this.RandomBuilder, 320, true, { scale: 2, waitUntilRenderFinished: true })
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap
            }).catch((err: Error) => {
            console.log("error: " + err)
          })
        })
      // 显示截图结果的图片组件
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```

ArkTS1.2

```typescript
import { image } from '@kit.ImageKit'

@Entry
@ComponentV2
struct OffscreenSnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined

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
          // 使用UIContext中的同名接口替代
          this.getUIContext()
            .getComponentSnapshot()
            .createFromBuilder(this.RandomBuilder, 320, true, { scale: 2, waitUntilRenderFinished: true })
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap
            })
            .catch((err: Error) => {
              console.log("error: " + err)
            })
        })
      // 显示截图结果的图片组件
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```
