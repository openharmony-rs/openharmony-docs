# ComponentObserver

ComponentObserver用于监听布局和绘制事件。

**起始版本：** 10

<!--Device-inspector-interface ComponentObserver--><!--Device-inspector-interface ComponentObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { inspector } from '@kit.ArkUI';
```

## off('layout')

```TypeScript
off(type: 'layout', callback?: () => void): void
```

使用句柄注销具有相应查询条件的回调。当组件布局完成时不再触发此回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-off(type: 'layout', callback?: () => void): void--><!--Device-ComponentObserver-off(type: 'layout', callback?: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'layout' | 是 | 监听事件的类型。<br>**起始版本：** 12 |
| callback | () =&gt; void | 否 | 监听事件的回调。<br>**起始版本：** 12 |

## off('draw')

```TypeScript
off(type: 'draw', callback?: () => void): void
```

使用句柄注销具有相应查询条件的回调。当组件绘制完成时不再触发此回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-off(type: 'draw', callback?: () => void): void--><!--Device-ComponentObserver-off(type: 'draw', callback?: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'draw' | 是 | 监听事件的类型。<br>**起始版本：** 12 |
| callback | () =&gt; void | 否 | 监听事件的回调。<br>**起始版本：** 12 |

## off('drawChildren')

```TypeScript
off(type: 'drawChildren', callback?: Callback<void>): void
```

使用句柄注销具有相应查询条件的回调。当组件的子级绘制完成时，不会触发此回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-off(type: 'drawChildren', callback?: Callback<void>): void--><!--Device-ComponentObserver-off(type: 'drawChildren', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'drawChildren' | 是 | 监听事件的类型。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | 监听事件的回调。 |

## offDrawChildren

```TypeScript
offDrawChildren(callback?: Callback<number[]>): void
```

使用监听句柄取消注册指定事件的回调函数，当组件的任一子节点绘制送显完成时不再触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-offDrawChildren(callback?: Callback<int[]>): void--><!--Device-ComponentObserver-offDrawChildren(callback?: Callback<int[]>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;number[]&gt; | 否 | 监听事件的回调函数。 |

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

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID');

  aboutToAppear() {
    let onDrawChildrenCompleteUniqueId: (childIds: number[]) => void = (childIds: number[]): void => {
      // 从API version 24开始，新增onDrawChildren接口。监听到DrawChildren事件后，用户可以自定义实现逻辑。
    };

    this.listenerForRow.onDrawChildren(onDrawChildrenCompleteUniqueId);
  }
  // 通过句柄取消注册回调，由开发者自行决定在何时调用。
  // this.listenerForRow.offDrawChildren(onDrawChildrenCompleteUniqueId)
}

```

## offLayoutChildren

```TypeScript
offLayoutChildren(callback?: Callback<void>): void
```

使用监听句柄取消注册指定事件的回调函数，当组件的任一子节点布局完成时不再触发回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-offLayoutChildren(callback?: Callback<void>): void--><!--Device-ComponentObserver-offLayoutChildren(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | 监听事件的回调。 |

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

  listenerForImage: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('IMAGE_ID');
  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID');

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      // 根据需要补充实现代码
    };
    let onDrawComplete: () => void = (): void => {
      // 根据需要补充实现代码
    };
    let onDrawChildrenComplete: () => void = (): void => {
      // 根据需要补充实现代码
    };
    // 绑定当前js实例
    let funcLayout = onLayoutComplete;
    let funcDraw = onDrawComplete;
    let funcDrawChildren = onDrawChildrenComplete;
    let offFuncLayout = onLayoutComplete;
    let offFuncDraw = onDrawComplete;
    let offFuncDrawChildren = onDrawChildrenComplete;

    this.listenerForImage.on('layout', funcLayout);
    this.listenerForImage.on('draw', funcDraw);
    this.listenerForRow.on('drawChildren', funcDrawChildren);

    // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用。
    // this.listenerForImage.off('layout', offFuncLayout)
    // this.listenerForImage.off('draw', offFuncDraw)
    // this.listenerForRow.off('drawChildren', offFuncDrawChildren)

    let onLayoutChildrenComplete: () => void = (): void => {
      // 监听到LayoutChildren事件后，用户可以自定义实现逻辑。
    };

    let uniqueId: number = this.getUniqueId();
    let listenerForUniqueId: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver(uniqueId.toString());
    listenerForUniqueId.onLayoutChildren(onLayoutChildrenComplete);
  }

  // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用。
  // listenerForUniqueId.offLayoutChildren(onLayoutChildrenComplete)
}

```

## on('layout')

```TypeScript
on(type: 'layout', callback: () => void): void
```

使用句柄注册具有相应查询条件的回调。当组件布局完成时会触发此回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-on(type: 'layout', callback: () => void): void--><!--Device-ComponentObserver-on(type: 'layout', callback: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'layout' | 是 | 监听事件的类型。<br>**起始版本：** 12 |
| callback | () =&gt; void | 是 | 监听事件的回调。<br>**起始版本：** 12 |

## on('draw')

```TypeScript
on(type: 'draw', callback: () => void): void
```

使用句柄注册具有相应查询条件的回调。当组件绘制完成时会触发此回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-on(type: 'draw', callback: () => void): void--><!--Device-ComponentObserver-on(type: 'draw', callback: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'draw' | 是 | 监听事件的类型。<br>**起始版本：** 12 |
| callback | () =&gt; void | 是 | 监听事件的回调。<br>**起始版本：** 12 |

## on('drawChildren')

```TypeScript
on(type: 'drawChildren', callback: Callback<void>): void
```

使用句柄注册具有相应查询条件的回调。当组件的子级绘制完成时，会触发此回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-on(type: 'drawChildren', callback: Callback<void>): void--><!--Device-ComponentObserver-on(type: 'drawChildren', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'drawChildren' | 是 | 监听事件的类型。 |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 监听事件的回调。 |

## onDrawChildren

```TypeScript
onDrawChildren(callback: Callback<number[]>): void
```

使用监听句柄注册指定事件的回调函数，当组件的任一子节点绘制送显完成时会触发回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-onDrawChildren(callback: Callback<int[]>): void--><!--Device-ComponentObserver-onDrawChildren(callback: Callback<int[]>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;number[]&gt; | 是 | 监听事件的回调函数，回调函数的参数为发生绘制送显节点的UniqueId。 |

**示例：**

以下示例展示了inspector注册组件绘制送显完成回调通知能力的基本用法。通过[onDrawChildren24+](#ondrawchildren24)接口注册回调，当子树内节点完成渲染时，回调返回该节点的uniqueId信息。

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

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID');

  aboutToAppear() {
    let onDrawChildrenCompleteUniqueId: (childIds: number[]) => void = (childIds: number[]): void => {
      // 从API version 24开始，新增onDrawChildren接口。监听到DrawChildren事件后，用户可以自定义实现逻辑。
    };

    this.listenerForRow.onDrawChildren(onDrawChildrenCompleteUniqueId);
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

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-onLayoutChildren(callback: Callback<void>): void--><!--Device-ComponentObserver-onLayoutChildren(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 事件触发时的回调方法。 |

