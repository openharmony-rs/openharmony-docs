# DragSpringLoadingConfiguration

定义拖拽的悬停检测配置参数的接口。默认的配置参数通常已能满足需求。可以通过在绑定onDragSpringLoading时指定配置，或者通过在 BEGIN状态期间使用[updateConfiguration](arkts-arkui-dragcontroller-springloadingcontext-c.md#updateconfiguration)方法动态修改的方式以自定义该配置参数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-dragController-export interface DragSpringLoadingConfiguration--><!--Device-dragController-export interface DragSpringLoadingConfiguration-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## stillTimeLimit

```TypeScript
stillTimeLimit?: int
```

进入悬停检测BEGIN状态所需保持静止的时间，单位：ms。取值范围为[0, 2&lt;sup&gt;31&lt;/sup&gt;-1]的整数。输入浮点数时只取整数部分。输入非法值（负数、null、undefined、NaN）时取默认值500。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragSpringLoadingConfiguration-stillTimeLimit?: int--><!--Device-DragSpringLoadingConfiguration-stillTimeLimit?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateInterval

```TypeScript
updateInterval?: int
```

进入悬停检测UPDATE状态后，更新通知的时间间隔，单位：ms。取值范围为[0, 2&lt;sup&gt;31&lt;/sup&gt;-1]的整数。输入浮点数时只取整数部分。输入非法值（负数、null、undefined、NaN）时取默认值100。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragSpringLoadingConfiguration-updateInterval?: int--><!--Device-DragSpringLoadingConfiguration-updateInterval?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateNotifyCount

```TypeScript
updateNotifyCount?: int
```

进入悬停检测UPDATE状态后，更新通知的最大次数。取值范围为[0, 2&lt;sup&gt;31&lt;/sup&gt;-1]的整数。输入浮点数时只取整数部分。输入非法值（负数、null、undefined、NaN）时取默认值3。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragSpringLoadingConfiguration-updateNotifyCount?: int--><!--Device-DragSpringLoadingConfiguration-updateNotifyCount?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## updateToFinishInterval

```TypeScript
updateToFinishInterval?: int
```

从UPDATE状态到END状态的最长等待时间，单位：ms。取值范围为[0, 2&lt;sup&gt;31&lt;/sup&gt;-1]的整数。输入浮点数时只取整数部分。输入非法值（负数、null、undefined、NaN）时取默认值100。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragSpringLoadingConfiguration-updateToFinishInterval?: int--><!--Device-DragSpringLoadingConfiguration-updateToFinishInterval?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

