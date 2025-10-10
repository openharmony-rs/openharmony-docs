# 交互事件字段

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## TouchObject.screenX/Y

ArkTS-Dyn接口声明：[TouchObject.screenX/Y](../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#touchobject对象说明)

替代的ArkTS-Sta接口声明：[TouchObject.windowX/Y](../reference/apis-arkui/arkui-ts/ts-universal-events-touch.md#touchobject对象说明)

ArkTS-Dyn示例：

```typescript
@Entry
@ComponentV2
struct TouchExample {
  build() {
    Column() {
      Button('Touch').height(40).width(100)
        .onTouch((event?: TouchEvent) => {
          // 输出触摸事件触点相对于窗口坐标
          let screenX = event?.changedTouches[0].screenX
          let screenY = event?.changedTouches[0].screenY
          console.info('touching on window[' + screenX + ', ' + screenY + ']')
        })
    }.width('100%').padding(30)
  }
}
```

ArkTS-Sta示例：

```typescript
@Entry
@ComponentV2
struct TouchExample {
  build() {
    Column() {
      Button('Touch').height(40).width(100)
        .onTouch((event?: TouchEvent) => {
          // 输出触摸事件触点相对于窗口坐标
          let windowX = event?.changedTouches[0].windowX
          let windowY = event?.changedTouches[0].windowY
          console.info('touching on window[' + windowX + ', ' + windowY + ']')
        })
    }.width('100%').padding(30)
  }
}
```

## MouseEvent.screenX/Y

ArkTS-Dyn接口声明：[MouseEvent.screenX/Y](../reference/apis-arkui/arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)

替代的ArkTS-Sta接口声明：[MouseEvent.windowX/Y](../reference/apis-arkui/arkui-ts/ts-universal-mouse-key.md#mouseevent对象说明)

ArkTS-Dyn示例：

```typescript
@Entry
@ComponentV2
struct MouseExample {
  build() {
    Column() {
      Button('Mouse').height(40).width(100)
        .onMouse((event?: MouseEvent) => {
          // 输出鼠标事件相对于窗口坐标
          let screenX = event?.screenX
          let screenY = event?.screenY
          console.info('mouse on window[' + screenX + ', ' + screenY + ']')
        })
    }.width('100%').padding(30)
  }
}
```

ArkTS-Sta示例：

```typescript
@Entry
@ComponentV2
struct MouseExample {
  build() {
    Column() {
      Button('Mouse').height(40).width(100)
        .onMouse((event?: MouseEvent) => {
          // 输出鼠标事件相对于窗口坐标
          let windowX = event?.windowX
          let windowY = event?.windowY
          console.info('mouse on window[' + windowX + ', ' + windowY + ']')
        })
    }.width('100%').padding(30)
  }
}
```


## ClickEvent.screenX/Y

ArkTS-Dyn接口声明：[ClickEvent.screenX/Y](../reference/apis-arkui/arkui-ts/ts-universal-events-click.md#clickevent对象说明)

替代的ArkTS-Sta接口声明：[ClickEvent.windowX/Y](../reference/apis-arkui/arkui-ts/ts-universal-events-click.md#clickevent对象说明)

ArkTS-Dyn示例：

```typescript
@Entry
@ComponentV2
struct ClickExample {
  build() {
    Column() {
      Button('Click').height(40).width(100)
        .onClick((event?: ClickEvent) => {
          // 输出点击事件相对于窗口坐标
          let screenX = event?.screenX;
          let screenY = event?.screenY;
          console.info('clicking on window[' + screenX + ', ' + screenY + ']');
        })
    }.width('100%').padding(30)
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, ComponentV2, Column, Button, ClickEvent } from '@kit.ArkUI';

@Entry
@ComponentV2
struct ClickExample {
  build() {
    Column() {
      Button('Click').height(40).width(100)
        .onClick((event?: ClickEvent) => {
          // 输出点击事件相对于窗口坐标
          let windowX = event?.windowX;
          let windowY = event?.windowY;
          console.info('clicking on window[' + windowX + ', ' + windowY + ']');
        })
    }.width('100%').padding(30)
  }
}
```


## DragEvent.getX/Y

ArkTS-Dyn接口声明：[DragEvent.getX](../reference/apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#getxdeprecated), [DragEvent.getY](../reference/apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#getydeprecated)

替代的ArkTS-Sta接口声明：[DragEvent.getWindowX](../reference/apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#getwindowx10), [DragEvent.getWindowY](../reference/apis-arkui/arkui-ts/ts-universal-events-drag-drop.md#getwindowy10)

ArkTS-Dyn示例：

```typescript
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
        .onDragMove((event: DragEvent)=> {
          // 输出拖拽事件相对于窗口的坐标
          let x = event.getX();
          let y = event.getY();
          console.info('drag moving on window[' + x + ', ' + y + ']');
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

ArkTS-Sta示例：

```typescript
import { Entry, ComponentV2, Column, Divider, Color, DragItemInfo, DragEvent, DropOptions } from '@kit.ArkUI';

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
        .onDragMove((event: DragEvent)=> {
          // 输出拖拽事件相对于窗口的坐标
          let windowX = event.getWindowX();
          let windowY = event.getWindowY();
          console.info('drag moving on window[' + windowX + ', ' + windowY + ']');
        })
        .onDrop(() => {}, {} as DropOptions)
    }
    .width('100%')
    .height('100%')
  }
}
```

## touchable

ArkTS-Dyn接口声明：[touchable](../reference/apis-arkui/arkui-ts/ts-universal-attributes-click.md#点击控制)

替代的ArkTS-Sta接口声明：[hitbehavior](../reference/apis-arkui/arkui-ts/ts-universal-attributes-hit-test-behavior.md#hittestbehavior)

ArkTS-Dyn示例：

```typescript
@Entry
@ComponentV2
struct InteractionExample {
  @Local message: string = "ready"

  build() {
    Column() {
      Text(this.message).margin(10)
      Text("click me")
        .touchable(false)
        .onClick(() => {
          this.message = "clicked"
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
import { Entry, ComponentV2, Column, Text, Button, HitTestMode, HorizontalAlign, Local } from '@kit.ArkUI';

@Entry
@ComponentV2
struct InteractionExample {
  @Local message: string = "ready";

  build() {
    Column() {
      Text(this.message).margin(10)
      Button("click me")
        .hitTestBehavior(HitTestMode.None)
        .onClick(() => {
          this.message = "clicked";
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```