# DLPSandboxInfo（系统接口）

表示DLP沙箱的信息。

**起始版本：** 10

<!--Device-dlpPermission-export interface DLPSandboxInfo--><!--Device-dlpPermission-export interface DLPSandboxInfo-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## appIndex

```TypeScript
appIndex: number
```

表示DLP沙箱应用索引。

**类型：** number

**起始版本：** 10

<!--Device-DLPSandboxInfo-appIndex: number--><!--Device-DLPSandboxInfo-appIndex: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## bindAppIndex

```TypeScript
bindAppIndex?: number
```

表示被绑定的DLP沙箱应用的应用索引。默认不返回，仅当沙箱应用是预览时返回。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DLPSandboxInfo-bindAppIndex?: number--><!--Device-DLPSandboxInfo-bindAppIndex?: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## tokenID

```TypeScript
tokenID: number
```

表示DLP沙箱应用的tokenID。

**类型：** number

**起始版本：** 10

<!--Device-DLPSandboxInfo-tokenID: number--><!--Device-DLPSandboxInfo-tokenID: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

