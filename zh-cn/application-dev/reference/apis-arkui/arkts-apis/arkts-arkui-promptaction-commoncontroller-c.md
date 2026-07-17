# CommonController

公共控制器，可以控制promptAction相关组件。

**起始版本：** 18

<!--Device-promptAction-class CommonController--><!--Device-promptAction-class CommonController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## close

```TypeScript
close(): void
```

关闭显示的自定义弹窗，若已关闭，则不生效。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonController-close(): void--><!--Device-CommonController-close(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

控制器的构造函数。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CommonController-constructor()--><!--Device-CommonController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getState

```TypeScript
getState(): CommonState
```

获取自定义弹窗的状态。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-CommonController-getState(): CommonState--><!--Device-CommonController-getState(): CommonState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CommonState](arkts-arkui-promptaction-commonstate-e.md) | 返回对应的弹窗状态。 |

