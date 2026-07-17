# AppSeniorModeInfo（系统接口）

Indicates the senior mode information of an application.

**起始版本：** 26.0.0

<!--Device-config-interface AppSeniorModeInfo--><!--Device-config-interface AppSeniorModeInfo-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## appIndex

```TypeScript
appIndex?: number
```

Indicates the index of clone app.The value must be an integer greater than or equal to 0. Default value: 0.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppSeniorModeInfo-appIndex?: int--><!--Device-AppSeniorModeInfo-appIndex?: int-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

The bundle name of application.

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppSeniorModeInfo-bundleName: string--><!--Device-AppSeniorModeInfo-bundleName: string-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## seniorModeState

```TypeScript
seniorModeState: boolean
```

The state of senior mode for application.

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppSeniorModeInfo-seniorModeState: boolean--><!--Device-AppSeniorModeInfo-seniorModeState: boolean-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

