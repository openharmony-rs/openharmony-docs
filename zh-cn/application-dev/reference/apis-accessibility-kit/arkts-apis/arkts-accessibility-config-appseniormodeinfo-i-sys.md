# AppSeniorModeInfo（系统接口）

“长辈模式”在应用中的状态信息。

**起始版本：** 26.0.0

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

应用包的分身索引标识。取值大于等于0的整数，缺省时默认为0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用包名，用于标识应用，格式如：'com.example.myapplication'。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## seniorModeState

```TypeScript
seniorModeState: boolean
```

应用“长辈模式”启用状态，true表示已启用，false表示未启用。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。
