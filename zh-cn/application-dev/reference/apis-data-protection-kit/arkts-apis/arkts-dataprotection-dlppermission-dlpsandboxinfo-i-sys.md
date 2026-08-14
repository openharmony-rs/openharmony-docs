# DLPSandboxInfo（系统接口）

表示DLP沙箱的信息。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-dlpPermission-export interface DLPSandboxInfo--><!--Device-dlpPermission-export interface DLPSandboxInfo-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
appIndex: number
```

表示DLP沙箱应用索引。

**类型：** number

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-DLPSandboxInfo-tokenID: number--><!--Device-DLPSandboxInfo-tokenID: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

