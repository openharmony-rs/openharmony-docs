# DLPProperty（系统接口）

表示授权相关信息。

**起始版本：** 21

<!--Device-dlpPermission-export interface DLPProperty--><!--Device-dlpPermission-export interface DLPProperty-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## allowedOpenCount

```TypeScript
allowedOpenCount?: number
```

表示允许打开的次数，默认为0。无范围限制。

**类型：** number

**起始版本：** 21

<!--Device-DLPProperty-allowedOpenCount?: number--><!--Device-DLPProperty-allowedOpenCount?: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## countdown

```TypeScript
countdown?: number
```

表示文件可被查看的有效时间，超时后打开的文件将自动关闭，默认为0，单位：秒。取值范围大于等于0。无范围限制。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DLPProperty-countdown?: number--><!--Device-DLPProperty-countdown?: number-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## extensionFields

```TypeScript
extensionFields?: Record<string, Object>
```

表示DLP文件的扩展属性，默认为空。

**类型：** Record&lt;string, Object&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DLPProperty-extensionFields?: Record<string, Object>--><!--Device-DLPProperty-extensionFields?: Record<string, Object>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## fileId

```TypeScript
fileId?: string
```

表示文件的标识，默认为空。长度不超过255字节，超出此范围抛出错误码401。

**类型：** string

**起始版本：** 21

<!--Device-DLPProperty-fileId?: string--><!--Device-DLPProperty-fileId?: string-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

## waterMarkConfig

```TypeScript
waterMarkConfig?: boolean
```

表示是否要求添加水印。true表示要求添加水印，false表示不要求添加水印，默认为空。

**类型：** boolean

**起始版本：** 23

<!--Device-DLPProperty-waterMarkConfig?: boolean--><!--Device-DLPProperty-waterMarkConfig?: boolean-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

