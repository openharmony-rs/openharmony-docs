# @ohos.arkui.dragController

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## executeDrag

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

## executeDrag

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

## createDragAction

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

## getDragPreview

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