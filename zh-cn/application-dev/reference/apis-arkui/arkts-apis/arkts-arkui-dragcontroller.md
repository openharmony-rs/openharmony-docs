# @ohos.arkui.dragController

本模块提供发起主动拖拽的能力，当应用接收到触摸或长按等事件时可以主动发起拖拽的动作，并在其中携带拖拽信息。

> **说明：**  
>  
> - 本模块功能依赖UI的执行上下文，不可在[UI上下文不明确](../../../../ui/arkts-global-interface.md#ui上下文不明确)的地方使用，参见  
> [UIContext](arkts-arkui-uicontext.md)说明。  
>  
> - 示例效果请以真机运行为准，当前 DevEco Studio预览器不支持。

**起始版本：** 10

<!--Device-unnamed-declare namespace dragController--><!--Device-unnamed-declare namespace dragController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createDragAction](arkts-arkui-dragcontroller-createdragaction-f.md#createdragaction-1) | 创建拖拽的Action对象，需要显式指定拖拽背板图（可多个），以及拖拽的数据，跟手点等信息；当通过一个已创建的 Action 对象发起的拖拽未结束时，无法再次创建新的 Action 对象，接口会抛出异常；当Action对象的生命周期结束后，注册在该对象上的回调函数会失效，因此需要在一个尽量长的作用域下持有该对象，并在每次发起拖拽前通过createDragAction返回新的对象覆盖旧值。 |
| [executeDrag](arkts-arkui-dragcontroller-executedrag-f.md#executedrag-1) | Execute a drag event. |
| [executeDrag](arkts-arkui-dragcontroller-executedrag-f.md#executedrag-2) | 主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。使用Promise异步回调。 |
| [getDragPreview](arkts-arkui-dragcontroller-getdragpreview-f.md#getdragpreview-1) | 返回一个代表拖拽背板的对象。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [DragPreview](arkts-arkui-dragcontroller-dragpreview-c.md) | 拖拽背板的对象，在OnDrop和OnDragEnd回调中使用不生效。 |
| [SpringLoadingContext](arkts-arkui-dragcontroller-springloadingcontext-c.md) | 定义回调上下文信息的类，用于在悬停检测回调中传递给应用程序，使其能访问拖拽状态、动态刷新UI效果以及访问拖拽数据以确定是否处理拖拽操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AnimationOptions](arkts-arkui-dragcontroller-animationoptions-i.md) | 拖拽相关的动效参数。 |
| [DragAction](arkts-arkui-dragcontroller-dragaction-i.md) | 监听状态改变，启动拖拽服务的对象。 |
| [DragAndDropInfo](arkts-arkui-dragcontroller-draganddropinfo-i.md) | 拖拽过程中监听到status改变时上报的数据。 |
| [DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md) | 拖拽结束返回结果的回调。 |
| [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | 发起拖拽所需要的属性和拖拽时携带的信息。 |
| [DragSpringLoadingConfiguration](arkts-arkui-dragcontroller-dragspringloadingconfiguration-i.md) | 定义拖拽的悬停检测配置参数的接口。默认的配置参数通常已能满足需求。可以通过在绑定[onDragSpringLoading](../arkts-components/arkts-arkui-common-commonmethod-c.md#ondragspringloading-1)时指定配置，或者通过在BEGIN状态期间使用[updateConfiguration](arkts-arkui-dragcontroller-springloadingcontext-c.md#updateconfiguration-1)方法动态修改的方式以自定义该配置参数。 |
| [SpringLoadingDragInfos](arkts-arkui-dragcontroller-springloadingdraginfos-i.md) | 定义触发悬停检测时拖拽事件信息的接口。该接口提供了拖拽数据摘要和拖拽事件额外信息，应用程序可以据此决定是否响应悬停检测回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DragSpringLoadingState](arkts-arkui-dragcontroller-dragspringloadingstate-e.md) | 定义拖拽的悬停检测状态的枚举类型。默认系统配置下，如果没有触发CANCEL，状态报告如下：保持Hover--&gt;500ms--&gt;BEGIN--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;END |
| [DragStartRequestStatus](arkts-arkui-dragcontroller-dragstartrequeststatus-e.md) | 定义应用是否可以发起拖拽的枚举类型。仅在[onDragStart](../arkts-components/arkts-arkui-common-commonmethod-c.md#ondragstart-1)调用时有效。 |
| [DragStatus](arkts-arkui-dragcontroller-dragstatus-e.md) | 拖拽开始和结束状态。 |

