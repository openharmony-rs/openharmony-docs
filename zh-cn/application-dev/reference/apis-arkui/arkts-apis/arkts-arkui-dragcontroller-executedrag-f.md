# executeDrag

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## executeDrag

```TypeScript
function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo,
    callback: AsyncCallback<DragEventParam>): void
```

Execute a drag event.

**起始版本：** 10

**废弃版本：** 18

**替代接口：** executeDrag

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md) | 是 | Object used for prompts displayed when the object is dragged. |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | 是 | Information about the drag event. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md)&gt; | 是 | Callback that contains the drag event information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

**示例**

```TypeScript
> 说明：
> 
> 推荐通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller)方法获取当前UI上下文关联的DragController对象。
```


## executeDrag

```TypeScript
function executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: DragInfo): Promise<DragEventParam>
```

主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。使用Promise异步回调。

> **说明：** 
> 
> 从API version 11开始，可以通过使用[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的
> [getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller)方法获取当前UI
> 上下文关联的[DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md)对象。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** executeDrag

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md) | 是 | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | 是 | 拖拽信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{ event: DragEvent, extraParams: string }&gt; | Promise used to return the result.<br>**适用版本：** 10 - 11 |
| Promise&lt;[DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md)&gt; | A Promise with the drag event information.<br>**适用版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

**示例**

参见 [executeDrag](#executedrag)
