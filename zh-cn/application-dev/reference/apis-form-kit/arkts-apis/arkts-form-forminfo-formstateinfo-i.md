# FormStateInfo

卡片状态信息。

**起始版本：** 23

<!--Device-formInfo-interface FormStateInfo--><!--Device-formInfo-interface FormStateInfo-End-->

**系统能力：** SystemCapability.Ability.Form

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## formState

```TypeScript
formState: FormState
```

卡片状态，用于标识卡片当前状态（如未知、默认、就绪）。

**类型：** FormState

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormStateInfo-formState: FormState--><!--Device-FormStateInfo-formState: FormState-End-->

**系统能力：** SystemCapability.Ability.Form

## want

```TypeScript
want: Want
```

Want对象，用于承载卡片状态切换时的意图信息。

**类型：** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-FormStateInfo-want: Want--><!--Device-FormStateInfo-want: Want-End-->

**系统能力：** SystemCapability.Ability.Form

