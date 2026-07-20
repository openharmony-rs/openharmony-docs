# VersionDigestInfo（系统接口）

版本摘要。

**起始版本：** 9

<!--Device-update-export interface VersionDigestInfo--><!--Device-update-export interface VersionDigestInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## versionDigest

```TypeScript
versionDigest: string
```

版本摘要。长度范围[1，128]，单位：字符。从版本检查结果中获取，用于标识具体版本。超出范围时抛出异常。

**类型：** string

**起始版本：** 9

<!--Device-VersionDigestInfo-versionDigest: string--><!--Device-VersionDigestInfo-versionDigest: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

