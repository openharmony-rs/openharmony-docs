# AccessedDLPFileInfo

表示被打开的DLP文件的信息。

**起始版本：** 10

<!--Device-dlpPermission-export interface AccessedDLPFileInfo--><!--Device-dlpPermission-export interface AccessedDLPFileInfo-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## lastOpenTime

```TypeScript
lastOpenTime: number
```

表示DLP文件最近打开时间。单位：s。

**类型：** number

**起始版本：** 10

<!--Device-AccessedDLPFileInfo-lastOpenTime: number--><!--Device-AccessedDLPFileInfo-lastOpenTime: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## uri

```TypeScript
uri: string
```

表示DLP文件的uri。不超过4095字节。

**类型：** string

**起始版本：** 10

<!--Device-AccessedDLPFileInfo-uri: string--><!--Device-AccessedDLPFileInfo-uri: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

