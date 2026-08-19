# ChangeSceneAnimationStateRequest（系统接口）

互动卡片状态切换请求信息。互动卡片状态分为激活态和非激活态，非激活态下，互动卡片同普通卡片一致；激活态下，互动卡片支持拉起卡片提供方所开发的LiveFormExtensionAbility进程，实现互动卡片动效。

**起始版本：** 23

<!--Device-formInfo-interface ChangeSceneAnimationStateRequest--><!--Device-formInfo-interface ChangeSceneAnimationStateRequest-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## formId

```TypeScript
formId: string
```

卡片id。

**类型：** string

**起始版本：** 23

<!--Device-ChangeSceneAnimationStateRequest-formId: string--><!--Device-ChangeSceneAnimationStateRequest-formId: string-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: int
```

状态切换请求类型标记：1 表示请求切换为激活态，0 表示请求切换为非激活态。

**类型：** int

**起始版本：** 23

<!--Device-ChangeSceneAnimationStateRequest-state: int--><!--Device-ChangeSceneAnimationStateRequest-state: int-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

