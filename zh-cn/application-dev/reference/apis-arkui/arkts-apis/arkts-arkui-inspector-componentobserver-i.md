# ComponentObserver

组件布局和组件绘制送显完成回调的句柄，通过该句柄可调用以下方法。

**起始版本：** 10

<!--Device-inspector-interface ComponentObserver--><!--Device-inspector-interface ComponentObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { inspector } from '@kit.ArkUI';
```

## offDrawChildren

```TypeScript
offDrawChildren(callback?: Callback<int[]>): void
```

取消注册drawChildren事件回调。要实现在子组件绘制送显完成后停止触发特定回调，只需通过ComponentObserver句柄，取消注册该回调即可。 如果组件树中存在多个drawChildren事件回调，取消最顶层的回调后，其余drawChildren事件回调也无法生效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-offDrawChildren(callback?: Callback<int[]>): void--><!--Device-ComponentObserver-offDrawChildren(callback?: Callback<int[]>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int[]&gt; | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。 callback需要和onDrawChildren方法中的callback为相同对象时才能取消回调成功。 |

**示例**

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

取消注册layoutChildren事件回调。要实现在子组件布局完成后停止触发特定回调，只需通过ComponentObserver句柄，取消注册该回调即可。 如果组件树中存在多个layoutChildren事件回调，取消最顶层的回调后，其余layoutChildren事件回调也无法生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-offLayoutChildren(callback?: Callback<void>): void--><!--Device-ComponentObserver-offLayoutChildren(callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。 callback需要和onLayoutChildren方法中的callback为相同对象时才能取消回调成功。 |

**示例**

以下示例展示了inspector注册组件布局和组件绘制送显完成回调通知能力的基本用法。同时，通过[onLayoutChildren23+](#onlayoutchildren)接口监听子树中的节点完成布局时的回调事件。

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

## off('draw')

```TypeScript
off(type: 'draw', callback?: () => void): void
```

通过句柄取消注册回调，当组件绘制送显完成时不再触发指定的回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-off(type: 'draw', callback?: () => void): void--><!--Device-ComponentObserver-off(type: 'draw', callback?: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'draw' | 是 | 必须填写字符串'draw'。<br/>draw：组件绘制送显完成。<br>**起始版本：** 12 |
| callback | () =&gt; void | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和on('draw')方法中的callback为相同对象时才能取消回调成功。<br>**起始版本：** 12 |

## off('drawChildren')

```TypeScript
off(type: 'drawChildren', callback?: Callback<void>): void
```

通过句柄取消注册回调，当组件的子组件绘制送显完成时不再触发指定的回调。如果组件树中存在多个drawChildren事件回调，取消最顶层的回调后，其余drawChildren事件回调也无法生效。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-off(type: 'drawChildren', callback?: Callback<void>): void--><!--Device-ComponentObserver-off(type: 'drawChildren', callback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'drawChildren' | 是 | 必须填写字符串'drawChildren'。<br/>drawChildren：子组件绘制送显完成。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。 callback需要和on('drawChildren')方法中的callback为相同对象时才能取消回调成功。 |

## off('layout')

```TypeScript
off(type: 'layout', callback?: () => void): void
```

通过句柄取消注册回调，当组件布局完成时不再触发指定的回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-off(type: 'layout', callback?: () => void): void--><!--Device-ComponentObserver-off(type: 'layout', callback?: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'layout' | 是 | 必须填写字符串'layout'。<br/>layout：组件布局完成。<br>**起始版本：** 12 |
| callback | () =&gt; void | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和on('layout')方法中的callback为相同对象时才能取消回调成功。<br>**起始版本：** 12 |

## onDrawChildren

```TypeScript
onDrawChildren(callback: Callback<int[]>): void
```

通过ComponentObserver注册drawChildren事件回调。使用callback异步回调。 与on('drawChildren')相比，本方法在回调中额外返回子组件的uniqueId信息（Callback&lt;number[]&gt;），便于开发者定位具体子组件。 如需获取子组件标识，建议使用本方法；若不需要子组件信息，两者均可使用。以当前注册事件回调的节点为根节点，当组件的子组件位于UI组件主树中且绘制送显完成时，会触发该回调。 如果组件树中存在多个drawChildren事件回调，只会触发最顶层的drawChildren事件回调。取消最顶层的回调后，其余drawChildren事件回调也无法生效。 当前节点注册事件回调后，不支持修改其在UI组件主树中的层级位置。如需调整，请先取消事件回调，再重新注册事件回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-onDrawChildren(callback: Callback<int[]>): void--><!--Device-ComponentObserver-onDrawChildren(callback: Callback<int[]>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int[]&gt; | 是 | 监听drawChildren的回调，回调参数为子组件uniqueId数组，表示绘制送显完成的子组件的唯一标识列表。 |

**示例**

以下示例展示了inspector注册组件绘制送显完成回调通知能力的基本用法。通过[onDrawChildren24+](#ondrawchildren)接口注册回调，当子树内节点完成渲染时，回调返回该节点的uniqueId信息。

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

通过ComponentObserver注册layoutChildren事件回调。使用callback异步回调。以当前注册事件回调的节点为根节点，当子树中的节点位于UI组件主树中且完成布局时，会触发该回调。 如果组件树中存在多个layoutChildren事件回调，只会触发最顶层的layoutChildren事件回调。通过offLayoutChildren取消最顶层的回调后，其余layoutChildren事件回调也无法生效。 当前节点注册回调后，不支持修改其在UI组件主树中的层级位置。如需调整，请先取消事件回调，再重新注册事件回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-onLayoutChildren(callback: Callback<void>): void--><!--Device-ComponentObserver-onLayoutChildren(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 监听layoutChildren的回调。 |

## on('draw')

```TypeScript
on(type: 'draw', callback: () => void): void
```

通过句柄注册回调，当组件绘制送显完成时会触发该回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-on(type: 'draw', callback: () => void): void--><!--Device-ComponentObserver-on(type: 'draw', callback: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'draw' | 是 | 必须填写字符串'draw'。<br/>draw：组件绘制送显完成。<br>**起始版本：** 12 |
| callback | () =&gt; void | 是 | 监听draw的回调。<br>**起始版本：** 12 |

## on('drawChildren')

```TypeScript
on(type: 'drawChildren', callback: Callback<void>): void
```

通过ComponentObserver注册drawChildren事件回调方法。当组件的子组件位于UI组件主树中且绘制送显完成时，会触发该回调方法。 如果组件树中存在多个drawChildren事件回调，只会触发最顶层的drawChildren事件回调。取消最顶层的回调后，其余drawChildren事件回调也无法生效。 当前节点注册回调后，不支持修改其在UI组件主树中的层级位置。如需调整，请先取消事件回调，再重新注册事件回调。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-on(type: 'drawChildren', callback: Callback<void>): void--><!--Device-ComponentObserver-on(type: 'drawChildren', callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'drawChildren' | 是 | 必须填写字符串'drawChildren'。<br/>drawChildren：子组件绘制送显完成。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;void&gt; | 是 | 监听drawChildren的回调。 |

## on('layout')

```TypeScript
on(type: 'layout', callback: () => void): void
```

通过句柄向对应的查询条件注册回调，当组件布局完成时会触发该回调。请注意，该接口无法监听窗口尺寸变化，相关需求请参考on('windowSizeChange')。此外，布局回调和窗口尺寸变化回调之间不存在确定的执行顺序依赖。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentObserver-on(type: 'layout', callback: () => void): void--><!--Device-ComponentObserver-on(type: 'layout', callback: () => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'layout' | 是 | 必须填写字符串'layout'。<br/>layout：组件布局完成。<br>**起始版本：** 12 |
| callback | () =&gt; void | 是 | 监听layout的回调。<br>**起始版本：** 12 |

