# SpringLoadingContext

定义回调上下文信息的类，用于在悬停检测回调中传递给应用程序，使其能访问拖拽状态、动态刷新UI效果以及访问拖拽数据以确定是否处理拖拽操作。

**起始版本：** 20

<!--Device-dragController-class SpringLoadingContext--><!--Device-dragController-class SpringLoadingContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

<a id="abort"></a>
## abort

```TypeScript
abort(): void
```

终止后续的悬停检测。本方法不会触发CANCEL状态通知，应用程序需要在执行本方法时进行状态清理。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SpringLoadingContext-abort(): void--><!--Device-SpringLoadingContext-abort(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="updateconfiguration"></a>
## updateConfiguration

```TypeScript
updateConfiguration(config: DragSpringLoadingConfiguration): void
```

更新悬停检测的配置，仅在悬停检测状态为BEGIN时生效。应用程序通常在绑定[onDragSpringLoading](../arkts-components/arkts-arkui-commonmethod-c.md#ondragspringloading-1)时设置悬停检测配置或使用默认配置。该方法不会修改绑定时的原始配置，而是在后续悬停检测中更新动态的配置信息。请谨慎使用本方法，因为不同的拖拽数据类型可能需要不同的UX时间。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SpringLoadingContext-updateConfiguration(config: DragSpringLoadingConfiguration): void--><!--Device-SpringLoadingContext-updateConfiguration(config: DragSpringLoadingConfiguration): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [DragSpringLoadingConfiguration](../arkts-components/arkts-arkui-dragspringloadingconfiguration-t.md) | 是 | 悬停检测配置。 |

## currentConfig

```TypeScript
currentConfig?: DragSpringLoadingConfiguration
```

当前回调中的配置信息，当悬停检测状态为CANCEL时缺失，为undefined时取[DragSpringLoadingConfiguration](arkts-arkui-dragcontroller-dragspringloadingconfiguration-i.md)默认值。

**类型：** DragSpringLoadingConfiguration

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SpringLoadingContext-currentConfig?: DragSpringLoadingConfiguration--><!--Device-SpringLoadingContext-currentConfig?: DragSpringLoadingConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentNotifySequence

```TypeScript
currentNotifySequence: number
```

在一次悬停检测流转中的回调通知次数，从0开始。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SpringLoadingContext-currentNotifySequence: number--><!--Device-SpringLoadingContext-currentNotifySequence: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dragInfos

```TypeScript
dragInfos?: SpringLoadingDragInfos
```

拖拽信息，当悬停检测状态为CANCEL时缺失，为undefined时取[SpringLoadingDragInfos](arkts-arkui-dragcontroller-springloadingdraginfos-i.md)默认值。

**类型：** SpringLoadingDragInfos

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SpringLoadingContext-dragInfos?: SpringLoadingDragInfos--><!--Device-SpringLoadingContext-dragInfos?: SpringLoadingDragInfos-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## state

```TypeScript
state: DragSpringLoadingState
```

当前悬停检测的状态。

**类型：** DragSpringLoadingState

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SpringLoadingContext-state: DragSpringLoadingState--><!--Device-SpringLoadingContext-state: DragSpringLoadingState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

