# WindowAnimationTarget（系统接口）

动画目标窗口，用来实现动画。

**起始版本：** 9

<!--Device-windowAnimationManager-export interface WindowAnimationTarget--><!--Device-windowAnimationManager-export interface WindowAnimationTarget-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { windowAnimationManager } from '@kit.ArkUI';
```

## abilityName

```TypeScript
readonly abilityName: string
```

/* 动画目标窗口所对应的Ability名称。

**类型：** string

**起始版本：** 9

<!--Device-WindowAnimationTarget-readonly abilityName: string--><!--Device-WindowAnimationTarget-readonly abilityName: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
readonly bundleName: string
```

动画目标窗口所对应的包名。

**类型：** string

**起始版本：** 9

<!--Device-WindowAnimationTarget-readonly bundleName: string--><!--Device-WindowAnimationTarget-readonly bundleName: string-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## missionId

```TypeScript
readonly missionId: number
```

/* 任务ID，多任务中用于与ability进行匹配。

**类型：** number

**起始版本：** 9

<!--Device-WindowAnimationTarget-readonly missionId: int--><!--Device-WindowAnimationTarget-readonly missionId: int-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

## windowBounds

```TypeScript
readonly windowBounds: RRect
```

/* 动画目标窗口所对应的实际大小。

**类型：** RRect

**起始版本：** 9

<!--Device-WindowAnimationTarget-readonly windowBounds: RRect--><!--Device-WindowAnimationTarget-readonly windowBounds: RRect-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

