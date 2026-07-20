# DragSpringLoadingConfiguration

定义拖拽的悬停检测配置参数的接口。默认的配置参数通常已能满足需求。可以通过在绑定[onDragSpringLoading](../arkts-components/arkts-arkui-commonmethod-c.md#ondragspringloading-1)时指定配置，或者通过在BEGIN状态期间使用[updateConfiguration](arkts-arkui-dragcontroller-springloadingcontext-c.md#updateconfiguration-1)方法动态修改的方式以自定义该配置参数。

**起始版本：** 20

<!--Device-dragController-interface DragSpringLoadingConfiguration--><!--Device-dragController-interface DragSpringLoadingConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## stillTimeLimit

```TypeScript
stillTimeLimit?: number
```

进入悬停检测BEGIN状态所需保持静止的时间，单位：ms。取值范围为[0, 2<sup>31</sup>-1]的整数。输入浮点数时只取整数部分。输入非法值（负数、null、undefined、NaN）时取默认值500。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragSpringLoadingConfiguration-stillTimeLimit?: number--><!--Device-DragSpringLoadingConfiguration-stillTimeLimit?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateInterval

```TypeScript
updateInterval?: number
```

进入悬停检测UPDATE状态后，更新通知的时间间隔，单位：ms。取值范围为[0, 2<sup>31</sup>-1]的整数。输入浮点数时只取整数部分。输入非法值（负数、null、undefined、NaN）时取默认值100。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragSpringLoadingConfiguration-updateInterval?: number--><!--Device-DragSpringLoadingConfiguration-updateInterval?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateNotifyCount

```TypeScript
updateNotifyCount?: number
```

进入悬停检测UPDATE状态后，更新通知的最大次数。取值范围为[0, 2<sup>31</sup>-1]的整数。输入浮点数时只取整数部分。输入非法值（负数、null、undefined、NaN）时取默认值3。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragSpringLoadingConfiguration-updateNotifyCount?: number--><!--Device-DragSpringLoadingConfiguration-updateNotifyCount?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateToFinishInterval

```TypeScript
updateToFinishInterval?: number
```

从UPDATE状态到END状态的最长等待时间，单位：ms。取值范围为[0, 2<sup>31</sup>-1]的整数。输入浮点数时只取整数部分。输入非法值（负数、null、undefined、NaN）时取默认值100。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-DragSpringLoadingConfiguration-updateToFinishInterval?: number--><!--Device-DragSpringLoadingConfiguration-updateToFinishInterval?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

