# UI接口适配

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## @ohos.arkui.dragController

### executeDrag

ArkTS-Dyn接口声明：[executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo,callback:AsyncCallback\<DragEventParam>): void](../reference/apis-arkui/js-apis-arkui-dragController.md#dragcontrollerexecutedragdeprecated)

替代的ArkTS-Sta接口声明：[executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo, callback: AsyncCallback&lt;dragController.DragEventParam&gt;): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#executedrag11)

ArkTS-Dyn示例：

```typescript
import { dragController } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@ComponentV2
struct DragControllerPage {
  @Local text: string = '';

  @Builder
  DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
        .fontColor(Color.White)
        .fontSize(12)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .margin(10)
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.PlainText();
              text.textContent = 'drag text';
              text.abstract = 'abstract';
              let unifiedData = new unifiedDataChannel.UnifiedData(text);
              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              };
              dragController.executeDrag(() => {
                this.DraggingBuilder()
              }, dragInfo, (err, eve) => {
                // handle drag result
              })
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, ComponentV2, Column, Color, Text, Button, TouchEvent, TouchType, Builder, Local, dragController } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@ComponentV2
struct DragControllerPage {
  @Local text: string = '';

  @Builder
  DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
        .fontColor(Color.White)
        .fontSize(12)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .margin(10)
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.PlainText();
              text.textContent = 'drag text';
              let unifiedData = new unifiedDataChannel.UnifiedData(text);
              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              }
              // 使用UIContext上的同名接口替代
              this.getUIContext().getDragController().executeDrag(() => {
                this.DraggingBuilder()
              }, dragInfo, (err, eve) => {
                // 处理起拖结果
              })
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### executeDrag

ArkTS-Dyn接口声明：[executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo): Promise\<DragEventParam>](../reference/apis-arkui/js-apis-arkui-dragController.md#dragcontrollerexecutedragdeprecated-1)

替代的ArkTS-Sta接口声明：[executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo): Promise&lt;dragController.DragEventParam&gt;](../reference/apis-arkui/js-apis-arkui-UIContext.md#executedrag11-1)

ArkTS-Dyn示例：

```typescript
import { dragController } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@ComponentV2
struct DragControllerPage {
  @Local text: string = '';

  @Builder
  DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
        .fontColor(Color.White)
        .fontSize(12)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .margin(10)
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.PlainText();
              text.textContent = 'drag text';
              text.abstract = 'abstract';
              let unifiedData = new unifiedDataChannel.UnifiedData(text);
              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              }
              dragController.executeDrag(() => {
                this.DraggingBuilder()
              }, dragInfo)
                .then((event) => {
                  // 处理起拖结果
                })
                .catch((err:Error) => {
                  // 处理起拖异常
                })
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, ComponentV2, Column, Color, Text, Button, TouchEvent, TouchType, Builder, Local, dragController } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@ComponentV2
struct DragControllerPage {
  @Local text: string = '';

  @Builder
  DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
        .fontColor(Color.White)
        .fontSize(12)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .margin(10)
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.PlainText();
              text.textContent = 'drag text';
              let unifiedData = new unifiedDataChannel.UnifiedData(text);
              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              }
              // 使用UIContext上的同名接口替代
              this.getUIContext().getDragController().executeDrag(() => {
                this.DraggingBuilder()
              }, dragInfo)
                .then((event) => {
                  // 处理起拖结果
                })
                .catch((err:Error) => {
                  // 处理起拖异常
                })
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### createDragAction

ArkTS-Dyn接口声明：[createDragAction(customArray: Array&lt;CustomBuilder \| DragItemInfo&gt;, dragInfo: DragInfo): DragAction](../reference/apis-arkui/js-apis-arkui-dragController.md#dragcontrollercreatedragactiondeprecated)

替代的ArkTS-Sta接口声明：[createDragAction(customArray: Array&lt;CustomBuilder \| DragItemInfo&gt;, dragInfo: dragController.DragInfo): dragController.DragAction](../reference/apis-arkui/js-apis-arkui-UIContext.md#createdragaction11)

ArkTS-Dyn示例：

```typescript
import { dragController } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@ComponentV2
struct DragControllerPage {
  customBuilders: Array<CustomBuilder | DragItemInfo> = new Array<CustomBuilder | DragItemInfo>();
  private dragAction: dragController.DragAction | null = null;

  @Builder
  DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
        .fontColor(Color.White)
        .fontSize(12)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('使用dragAction发起拖拽')
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              this.customBuilders.splice(0, this.customBuilders.length);
              this.customBuilders.push(() => {this.DraggingBuilder()});
              let text = new unifiedDataChannel.PlainText();
              text.textContent = 'drag text';
              let unifiedData = new unifiedDataChannel.UnifiedData(text);
              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              }
              try {
                this.dragAction = dragController.createDragAction(this.customBuilders, dragInfo)
                if (!this.dragAction) {
                  console.error("listener dragAction is null");
                  return;
                }
                this.dragAction.startDrag().then(() => {
                  // 起拖成功
                }).catch((err: Error) => {
                  // 起拖失败
                })
              } catch (err) {
                // 创建drag action失败
              }
            }
          }
        }).margin({ top: 20 })
    }
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, ComponentV2, Column, Color, Text, Button, TouchEvent, Builder, dragController, CustomBuilder, DragItemInfo, TouchType, Local, CustomBuilder, Margin } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@ComponentV2
struct DragControllerPage {
  customBuilders: Array<CustomBuilder | DragItemInfo> = new Array<CustomBuilder | DragItemInfo>();
  private dragAction: dragController.DragAction | null = null;

  @Builder
  DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
        .fontColor(Color.White)
        .fontSize(12)
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('使用dragAction发起拖拽')
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              this.customBuilders.splice(0, this.customBuilders.length);
              this.customBuilders.push(() => {this.DraggingBuilder()});
              let text = new unifiedDataChannel.PlainText();
              text.textContent = 'drag text';
              let unifiedData = new unifiedDataChannel.UnifiedData(text);
              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              }
              try {
                // 使用UIContext上的同名接口替代
                this.dragAction = this.getUIContext().getDragController().createDragAction(this.customBuilders, dragInfo)
                if (!this.dragAction) {
                  console.error("listener dragAction is null");
                  return;
                }
                (this.dragAction as dragController.DragAction).startDrag().then(() => {
                  // 起拖成功
                }).catch((err: Error) => {
                  // 起拖失败
                })
              } catch (err) {
                // 创建drag action失败
              }
            }
          }
        }).margin({ top: 20 } as Margin)
    }
  }
}
```

### getDragPreview

ArkTS-Dyn接口声明：[getDragPreview(): DragPreview](../reference/apis-arkui/js-apis-arkui-dragController.md#dragcontrollergetdragpreviewdeprecated)

替代的ArkTS-Sta接口声明：[getDragPreview(): dragController.DragPreview](../reference/apis-arkui/js-apis-arkui-UIContext.md#getdragpreview11)

ArkTS-Dyn示例：

```typescript
import { dragController } from "@kit.ArkUI";

@Entry
@ComponentV2
struct DragControllerPage {

 build() {
    Column() {
      // 一个可以支持长按并移动发起拖拽的column组件
      Column().width(100).height(100).backgroundColor(Color.Black)
        .draggable(true)
        .onDragStart(()=>{
          // 此处简化
        })

      Divider().height(10)

      // 一个可以感知拖拽移动的组件
      Column().width(200).height(200).backgroundColor(Color.Blue)
        .onDrop(() => {})
        .onDragEnter(()=> {
          // 当拖拽进入这个组件区域时，为拖拽跟手图添加一个前景色
          dragController.getDragPreview().setForegroundColor(Color.Pink)
        })
        .onDragLeave(()=> {
          // 当拖拽离开这个组件区域时，取消拖拽跟手图前景色
          dragController.getDragPreview().setForegroundColor(Color.Transparent)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, ComponentV2, Column, Color, Divider, DragItemInfo, DropOptions } from '@kit.ArkUI';

@Entry
@ComponentV2
struct DragControllerPage {

 build() {
    Column() {
      // 一个可以支持长按并移动发起拖拽的column组件
      Column().width(100).height(100).backgroundColor(Color.Black)
        .draggable(true)
        .onDragStart(()=>{
          // 此处简化
          return {} as DragItemInfo;
        })

      Divider().height(10)

      // 一个可以感知拖拽移动的组件
      Column().width(200).height(200).backgroundColor(Color.Blue)
        .onDrop(() => {}, {} as DropOptions)
        .onDragEnter(()=> {
          // 使用UIContext上的同名接口替代
          this.getUIContext().getDragController().getDragPreview().setForegroundColor(Color.Pink)
        })
        .onDragLeave(()=> {
          // 使用UIContext上的同名接口替代
          this.getUIContext().getDragController().getDragPreview().setForegroundColor(Color.Transparent)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## @ohos.arkui.componentSnapshot

### get

ArkTS-Dyn接口声明：[get(id: string, callback: AsyncCallback<image.PixelMap>, options?: SnapshotOptions): void](../reference/apis-arkui/js-apis-arkui-componentSnapshot.md#componentsnapshotgetdeprecated)

替代的ArkTS-Sta接口声明：[get(id: string, callback: AsyncCallback<image.PixelMap>, options?: componentSnapshot.SnapshotOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#get12)

ArkTS-Dyn示例：

```typescript
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct SnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined;

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
              console.error("error: " + JSON.stringify(error));
              return;
            }
            this.pixmap = pixmap;
          }, { scale: 2, waitUntilRenderFinished: true })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, ComponentV2, Column, Row, Image, Button, HorizontalAlign, Color, BusinessError, Local, $r } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct SnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined;

  build() {
    Column() {
      Row() {
        // 用来显示截图结果的图片组件
        Image(this.pixmap ? this.pixmap : '').width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
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
          this.getUIContext().getComponentSnapshot().get("snapshot_target", (error: BusinessError<void> | null, pixmap: image.PixelMap | undefined) => {
            if (pixmap) {
              this.pixmap = pixmap;
              return;
            }
            console.error("error: " + JSON.stringify(error));
          }, { scale: 2, waitUntilRenderFinished: true })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

### get

ArkTS-Dyn接口声明：[get(id: string, options?: SnapshotOptions): Promise<image.PixelMap>](../reference/apis-arkui/js-apis-arkui-componentSnapshot.md#componentsnapshotgetdeprecated-1)

替代的ArkTS-Sta接口声明：[get(id: string, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>](../reference/apis-arkui/js-apis-arkui-UIContext.md#get12-1)

ArkTS-Dyn示例：

```typescript
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct SnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined;

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
              this.pixmap = pixmap;
            }).catch((err: Error) => {
            console.log("error: " + err);
          })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, ComponentV2, Column, Row, Image, Button, HorizontalAlign, Color, Local, $r } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@ComponentV2
struct SnapshotExample {
  @Local pixmap: image.PixelMap | undefined = undefined;

  build() {
    Column() {
      Row() {
        // 用来显示截图结果的图片组件
        Image(this.pixmap ? this.pixmap : '').width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
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
              this.pixmap = pixmap;
            }).catch((err: Error) => {
            console.log("error: " + err);
          })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

### createFromBuilder

ArkTS-Dyn接口声明：[createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): void](../reference/apis-arkui/js-apis-arkui-componentSnapshot.md#componentsnapshotcreatefrombuilderdeprecated)

替代的ArkTS-Sta接口声明：[createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#createfrombuilder12)

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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

### createFromBuilder

ArkTS-Dyn接口声明：[createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): Promise<image.PixelMap>](../reference/apis-arkui/js-apis-arkui-componentSnapshot.md#componentsnapshotcreatefrombuilderdeprecated-1)

替代的ArkTS-Sta接口声明：[createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>](../reference/apis-arkui/js-apis-arkui-UIContext.md#createfrombuilder12-1)

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

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
## @ohos.arkui.componentUtils

### get

ArkTS-Dyn接口声明：[getRectangleById(id: string): ComponentInfo](../reference/apis-arkui/js-apis-arkui-componentUtils.md#componentutilsgetrectanglebyiddeprecated)

替代的ArkTS-Sta接口声明：[getRectangleById(id: string): componentUtils.ComponentInfo](../reference/apis-arkui/js-apis-arkui-UIContext.md#getrectanglebyid)

ArkTS-Dyn示例：

```typescript
import { componentUtils, matrix4 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Utils {
  @Local x: number = 120;
  @Local y: number = 10;
  @Local z: number = 100;
  @Local value: string = '';
  private matrix1 = matrix4.identity().translate({ x: this.x, y: this.y, z: this.z });

  build() {
    Column() {
      Image($r("app.media.startIcon"))
        .transform(this.matrix1)
        .translate({ x: 20, y: 20, z: 20 })
        .scale({ x: 0.5, y: 0.5, z: 1 })
        .rotate({
          x: 1,
          y: 1,
          z: 1,
          centerX: '50%',
          centerY: '50%',
          angle: 300
        })
        .width(300)
        .height(100)
        .key("image_01")
      Button('getRectangleById')
        .onClick(() => {
          this.value = JSON.stringify(componentUtils.getRectangleById("image_01"))
        }).margin(10).id('onClick')
      Text(this.value)
        .margin(20)
        .width(300)
        .height(300)
        .borderWidth(2)
    }.margin({ left: 50 })
  }
}
```

ArkTS-Sta示例：

```typescript
import { matrix4 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Utils {
  @Local x: number = 120;
  @Local y: number = 10;
  @Local z: number = 100;
  @Local value: string = '';
  private matrix1 = matrix4.identity().translate({ x: this.x, y: this.y, z: this.z });

  build() {
    Column() {
      Image($r("app.media.startIcon"))
        .transform(this.matrix1)
        .translate({ x: 20, y: 20, z: 20 })
        .scale({ x: 0.5, y: 0.5, z: 1 })
        .rotate({
          x: 1,
          y: 1,
          z: 1,
          centerX: '50%',
          centerY: '50%',
          angle: 300
        })
        .width(300)
        .height(100)
        .key("image_01")
      Button('getRectangleById')
        .onClick(() => {
          // 使用UIContext上的同名接口替代
          this.value = JSON.stringify(this.getUIContext().getComponentUtils().getRectangleById("image_01"))
        }).margin(10).id('onClick')
      Text(this.value)
        .margin(20)
        .width(300)
        .height(300)
        .borderWidth(2)
    }.margin({ left: 50 })
  }
}
```
## 布局回调

### createComponentObserver

ArkTS-Dyn接口声明：[createComponentObserver(id: string): ComponentObserver](../reference/apis-arkui/js-apis-arkui-inspector.md#inspectorcreatecomponentobserverdeprecated)

替代的ArkTS-Sta接口声明：[createComponentObserver(id: string): inspector.ComponentObserver](../reference/apis-arkui/js-apis-arkui-UIContext.md#createcomponentobserver)



ArkTS-Dyn示例：

```ts
// 监听id为COMPONENT_ID的组件回调事件
let listener:inspector.ComponentObserver = inspector.createComponentObserver('COMPONENT_ID');
```

ArkTS-Sta示例：
<!--code_no_check-->
```ts
import { inspector } from '@ohos.arkui.inspector';

// 监听id为COMPONENT_ID的组件回调事件
let listener:inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('COMPONENT_ID');
```