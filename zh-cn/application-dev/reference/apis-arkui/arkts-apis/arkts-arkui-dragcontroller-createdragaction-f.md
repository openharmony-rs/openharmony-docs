# createDragAction

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## createDragAction

```TypeScript
function createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: DragInfo): DragAction
```

创建拖拽的Action对象，需要显式指定拖拽背板图（可多个），以及拖拽的数据，跟手点等信息；当通过一个已创建的 Action 对象发起的拖拽未结束时，无法再次创建新的 Action 对象，接口会抛出异常；当Action对象的生命周期结束后，注册在该对象上的回调函数会失效，因此需要在一个尽量长的作用域下持有该对象，并在每次发起拖拽前通过createDragAction返回新的对象覆盖旧值。

> **说明：** 
> 
> - 从API version 11开始，可以通过使用[UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)中的[getDragController](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller)方法获取当前UI 上下文关联的[DragController](arkts-arkui-arkui-uicontext-dragcontroller-c.md)对象。
> 
> - 建议控制传递的拖拽背板数量，传递过多容易导致拖起的效率问题。

**起始版本：** 11

**废弃版本：** 18

**替代接口：** createDragAction

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| customArray | Array&lt;[CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md)&gt; | 是 | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | 是 | 拖拽信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DragAction](arkts-arkui-dragcontroller-dragaction-i.md) | 创建拖拽Action对象，主要用于后面实现注册监听拖拽状态改变事件和启动拖拽服务。 |

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
