# DragAction

监听状态改变，启动拖拽服务的对象。

**起始版本：** 11

<!--Device-dragController-interface DragAction--><!--Device-dragController-interface DragAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## off('statusChange')

```TypeScript
off(type: 'statusChange', callback?: Callback<DragAndDropInfo>): void
```

取消注册监听拖拽状态改变事件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragAction-off(type: 'statusChange', callback?: Callback<DragAndDropInfo>): void--><!--Device-DragAction-off(type: 'statusChange', callback?: Callback<DragAndDropInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'statusChange' | 是 | for status changing |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<DragAndDropInfo> | 否 | with drag event and status information |

## on('statusChange')

```TypeScript
on(type: 'statusChange', callback: Callback<DragAndDropInfo>): void
```

注册监听拖拽状态改变事件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragAction-on(type: 'statusChange', callback: Callback<DragAndDropInfo>): void--><!--Device-DragAction-on(type: 'statusChange', callback: Callback<DragAndDropInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'statusChange' | 是 | for status changing |
| callback | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<DragAndDropInfo> | 是 | with drag event and status information |

## startDrag

```TypeScript
startDrag(): Promise<void>
```

启动拖拽服务。使用Promise异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DragAction-startDrag(): Promise<void>--><!--Device-DragAction-startDrag(): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

