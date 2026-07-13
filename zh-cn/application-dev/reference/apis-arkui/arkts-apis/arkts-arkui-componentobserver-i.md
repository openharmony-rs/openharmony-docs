# ComponentObserver

The ComponentObserver is used to listen for layout and draw events.

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## off('layout')

```TypeScript
off(type: 'layout', callback?: () => void): void
```

Deregisters a callback with the corresponding query condition by using the handle.
This callback is not triggered when the component layout complete.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'layout' | 是 | type of the listened event.<br>**起始版本：** 12 |
| callback | () =&gt; void | 否 | callback of the listened event.<br>**起始版本：** 12 |

## off('draw')

```TypeScript
off(type: 'draw', callback?: () => void): void
```

Deregisters a callback with the corresponding query condition by using the handle.
This callback is not triggered when the component draw complete.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'draw' | 是 | type of the listened event.<br>**起始版本：** 12 |
| callback | () =&gt; void | 否 | callback of the listened event.<br>**起始版本：** 12 |

## off('drawChildren')

```TypeScript
off(type: 'drawChildren', callback?: Callback<void>): void
```

使用句柄注销具有相应查询条件的回调。
当组件的子级绘制完成时，不会触发此回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'drawChildren' | 是 | 监听事件的类型。 |
| callback | Callback&lt;void&gt; | 否 | 监听事件的回调。 |

## offDrawChildren

```TypeScript
offDrawChildren(callback?: Callback<number[]>): void
```

使用监听句柄取消注册指定事件的回调函数，当组件的任一子节点绘制送显完成时不再触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;number[]&gt; | 否 | 监听事件的回调函数。 |

**示例：**

```TypeScript
import { inspector } from '@kit.ArkUI';

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID')

  aboutToAppear() {
    let onDrawChildrenComplete_uniqueId:(childIds: number[])=>void = (childIds: number[]) : void => {
      // 从API version 24开始，新增onDrawChildren接口。监听到DrawChildren事件后，用户可以自定义实现逻辑。
    }

    let uniqueId: number = this.getUniqueId();
    this.listenerForRow.onDrawChildren(onDrawChildrenComplete_uniqueId)
  }
  // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用。
  // this.listenerForRow.offDrawChildren(onDrawChildrenComplete_uniqueId)
}

```

## offLayoutChildren

```TypeScript
offLayoutChildren(callback?: Callback<void>): void
```

使用监听句柄取消注册指定事件的回调函数，当组件的任一子节点布局完成时不再触发回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 否 | callback of the listened event. |

**示例：**

以下示例展示了inspector注册组件布局和组件绘制送显完成回调通知能力的基本用法。同时，通过[onLayoutChildren23+](#onlayoutchildren23)接口监听子树中的节点完成布局时的回调事件。

```TypeScript
import { inspector } from '@kit.ArkUI';

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  listenerForImage: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('IMAGE_ID')
  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID')

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      // 根据需要补充实现代码
    }
    let onDrawComplete: () => void = (): void => {
      // 根据需要补充实现代码
    }
    let onDrawChildrenComplete: () => void = (): void => {
      // 根据需要补充实现代码
    }
    // 绑定当前js实例
    let FuncLayout = onLayoutComplete
    let FuncDraw = onDrawComplete
    let FuncDrawChildren = onDrawChildrenComplete
    let OffFuncLayout = onLayoutComplete
    let OffFuncDraw = onDrawComplete
    let OffFuncDrawChildren = onDrawChildrenComplete

    this.listenerForImage.on('layout', FuncLayout)
    this.listenerForImage.on('draw', FuncDraw)
    this.listenerForRow.on('drawChildren', FuncDrawChildren)

    // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用。
    // this.listenerForImage.off('layout', OffFuncLayout)
    // this.listenerForImage.off('draw', OffFuncDraw)
    // this.listenerForRow.off('drawChildren', OffFuncDrawChildren)

    let onLayoutChildrenComplete: () => void = (): void => {
      // 监听到LayoutChildren事件后，用户可以自定义实现逻辑。
    }

    let uniqueId: number = this.getUniqueId();
    let listenerForUniqueId: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver(uniqueId.toString())
    listenerForUniqueId.onLayoutChildren(onLayoutChildrenComplete)
  }

  // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用。
  // listenerForUniqueId.offLayoutChildren(onLayoutChildrenComplete)
}

```

## on('layout')

```TypeScript
on(type: 'layout', callback: () => void): void
```

Registers a callback with the corresponding query condition by using the handle.
This callback is triggered when the component layout complete.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'layout' | 是 | type of the listened event.<br>**起始版本：** 12 |
| callback | () =&gt; void | 是 | callback of the listened event.<br>**起始版本：** 12 |

## on('draw')

```TypeScript
on(type: 'draw', callback: () => void): void
```

Registers a callback with the corresponding query condition by using the handle.
This callback is triggered when the component draw complete.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'draw' | 是 | type of the listened event.<br>**起始版本：** 12 |
| callback | () =&gt; void | 是 | callback of the listened event.<br>**起始版本：** 12 |

## on('drawChildren')

```TypeScript
on(type: 'drawChildren', callback: Callback<void>): void
```

使用句柄注册具有相应查询条件的回调。
当组件的子级绘制完成时，会触发此回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'drawChildren' | 是 | 监听事件的类型。 |
| callback | Callback&lt;void&gt; | 是 | 监听事件的回调。 |

## onDrawChildren

```TypeScript
onDrawChildren(callback: Callback<number[]>): void
```

使用监听句柄注册指定事件的回调函数，当组件的任一子节点绘制送显完成时会触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;number[]&gt; | 是 | 监听事件的回调函数，回调函数的参数为发生绘制送显节点的UniqueId。 |

**示例：**

以下示例展示了inspector注册组件布局和组件绘制送显完成回调通知能力的基本用法。监听子树内节点完成渲染后，通过[onDrawChildren24+](#ondrawchildren24)接口，回调返回该节点的uniqueId信息。

```TypeScript
import { inspector } from '@kit.ArkUI';

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID')

  aboutToAppear() {
    let onDrawChildrenComplete_uniqueId:(childIds: number[])=>void = (childIds: number[]) : void => {
      // 从API version 24开始，新增onDrawChildren接口。监听到DrawChildren事件后，用户可以自定义实现逻辑。
    }

    let uniqueId: number = this.getUniqueId();
    this.listenerForRow.onDrawChildren(onDrawChildrenComplete_uniqueId)
  }
}

```

## onLayoutChildren

```TypeScript
onLayoutChildren(callback: Callback<void>): void
```

使用监听句柄注册指定事件的回调函数，当组件的任一子节点布局完成时会触发回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | 是 | 事件触发时的回调方法。 |

