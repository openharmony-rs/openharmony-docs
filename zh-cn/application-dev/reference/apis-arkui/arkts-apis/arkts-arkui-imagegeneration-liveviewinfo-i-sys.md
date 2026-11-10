# LiveViewInfo（系统接口）

```TypeScript
interface LiveViewInfo
```

AI图像生成中实况窗的选项。

**起始版本：** 26.0.0

<!--Device-imageGeneration-interface LiveViewInfo--><!--Device-imageGeneration-interface LiveViewInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## getLongTermTaskId

```TypeScript
getLongTermTaskId(): number
```

获取实况窗的长时任务ID。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiveViewInfo-getLongTermTaskId(): int--><!--Device-LiveViewInfo-getLongTermTaskId(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回长时任务ID |

## getWant

```TypeScript
getWant(): Want
```

获取实况窗的Want对象。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiveViewInfo-getWant(): Want--><!--Device-LiveViewInfo-getWant(): Want-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 返回Want对象。 |

## isLiveViewNeeded

```TypeScript
isLiveViewNeeded(): boolean
```

是否需要实况窗。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiveViewInfo-isLiveViewNeeded(): boolean--><!--Device-LiveViewInfo-isLiveViewNeeded(): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true-需要显示实况窗，false-不显示 |
