# DragAndDropInfo

拖拽过程中监听到status改变时上报的数据。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-dragController-interface DragAndDropInfo--><!--Device-dragController-interface DragAndDropInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## event

```TypeScript
event: DragEvent
```

当前状态所对应的拖拽事件。通过dragController发起的dragEvent仅支持获取result和behavior，且用于拖拽结束状态。

**类型：** DragEvent

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragAndDropInfo-event: DragEvent--><!--Device-DragAndDropInfo-event: DragEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraParams

```TypeScript
extraParams?: string
```

设置拖拽事件额外信息，具体功能暂未实现。 默认值：空

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragAndDropInfo-extraParams?: string--><!--Device-DragAndDropInfo-extraParams?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## status

```TypeScript
status: DragStatus
```

当前拖拽状态（启动和结束）。

**类型：** [DragStatus](arkts-arkui-dragcontroller-dragstatus-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragAndDropInfo-status: DragStatus--><!--Device-DragAndDropInfo-status: DragStatus-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

