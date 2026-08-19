# DragAction

监听状态改变，启动拖拽服务的对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-dragController-interface DragAction--><!--Device-dragController-interface DragAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## offStatusChange

```TypeScript
offStatusChange(callback?: Callback<DragAndDropInfo>): void
```

取消注册监听拖拽状态改变事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragAction-offStatusChange(callback?: Callback<DragAndDropInfo>): void--><!--Device-DragAction-offStatusChange(callback?: Callback<DragAndDropInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DragAndDropInfo](arkts-arkui-dragcontroller-draganddropinfo-i.md)&gt; | 否 |  |

## onStatusChange

```TypeScript
onStatusChange(callback: Callback<DragAndDropInfo>): void
```

注册监听拖拽状态改变事件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragAction-onStatusChange(callback: Callback<DragAndDropInfo>): void--><!--Device-DragAction-onStatusChange(callback: Callback<DragAndDropInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DragAndDropInfo](arkts-arkui-dragcontroller-draganddropinfo-i.md)&gt; | 是 |  |

## startDrag

```TypeScript
startDrag(): Promise<void> | null
```

启动拖拽服务。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragAction-startDrag(): Promise<void> | null--><!--Device-DragAction-startDrag(): Promise<void> | null-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal handling failed. |

