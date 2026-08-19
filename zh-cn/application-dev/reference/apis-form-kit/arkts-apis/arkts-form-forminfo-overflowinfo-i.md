# OverflowInfo

互动卡片动效信息。

**起始版本：** 23

<!--Device-formInfo-interface OverflowInfo--><!--Device-formInfo-interface OverflowInfo-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## area

```TypeScript
area: Rect
```

描述互动卡片动效区域范围，以卡片左上角为原点。

**类型：** Rect

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OverflowInfo-area: Rect--><!--Device-OverflowInfo-area: Rect-End-->

**系统能力：** SystemCapability.Ability.Form

## duration

```TypeScript
duration: int
```

互动卡片动效持续时长，单位ms。取值为大于0的整数，<!--Del-->针对三方应用，<!--DelEnd-->取值要求不大于3500<!--Del-->，系统应用无此限制<!--DelEnd-->。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OverflowInfo-duration: int--><!--Device-OverflowInfo-duration: int-End-->

**系统能力：** SystemCapability.Ability.Form

## useDefaultAnimation

```TypeScript
useDefaultAnimation?: boolean
```

互动卡片状态切换时是否启动系统提供的默认动效，默认为true。 - true：表示系统提供默认切换动效。 - false：表示系统不提供切换动效，画面直接切换，适合切换时非激活态和激活态UI完全一致的场景。

**类型：** boolean

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-OverflowInfo-useDefaultAnimation?: boolean--><!--Device-OverflowInfo-useDefaultAnimation?: boolean-End-->

**系统能力：** SystemCapability.Ability.Form

