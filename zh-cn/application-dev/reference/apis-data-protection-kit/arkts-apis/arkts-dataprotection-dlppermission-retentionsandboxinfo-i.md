# RetentionSandboxInfo

保留沙箱的沙箱信息。

**起始版本：** 10

<!--Device-dlpPermission-export interface RetentionSandboxInfo--><!--Device-dlpPermission-export interface RetentionSandboxInfo-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## appIndex

```TypeScript
appIndex: number
```

表示DLP沙箱应用索引。取值范围为1001到1100。

**类型：** number

**起始版本：** 10

<!--Device-RetentionSandboxInfo-appIndex: number--><!--Device-RetentionSandboxInfo-appIndex: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## bundleName

```TypeScript
bundleName: string
```

表示应用包名。最小7字节，最大128字节。

**类型：** string

**起始版本：** 10

<!--Device-RetentionSandboxInfo-bundleName: string--><!--Device-RetentionSandboxInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## docUris

```TypeScript
docUris: Array<string>
```

表示DLP文件的URI列表。不对Array长度进行限制，每个string长度不超过4095字节。

**类型：** Array&lt;string&gt;

**起始版本：** 10

<!--Device-RetentionSandboxInfo-docUris: Array<string>--><!--Device-RetentionSandboxInfo-docUris: Array<string>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

