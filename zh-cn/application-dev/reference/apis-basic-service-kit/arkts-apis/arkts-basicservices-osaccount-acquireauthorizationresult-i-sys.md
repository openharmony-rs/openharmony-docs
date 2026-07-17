# AcquireAuthorizationResult（系统接口）

表示获取授权的结果。

**起始版本：** 24

<!--Device-osAccount-interface AcquireAuthorizationResult--><!--Device-osAccount-interface AcquireAuthorizationResult-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## isReused

```TypeScript
isReused?: boolean
```

是否为复用的授权结果，默认为undefined。

true：表示是复用的授权结果。false：表示不是复用的授权结果。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationResult-isReused?: boolean--><!--Device-AcquireAuthorizationResult-isReused?: boolean-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## privilege

```TypeScript
privilege: string
```

与授权关联的权限。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationResult-privilege: string--><!--Device-AcquireAuthorizationResult-privilege: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## resultCode

```TypeScript
resultCode: AuthorizationResultCode
```

授权结果码。

**类型：** AuthorizationResultCode

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationResult-resultCode: AuthorizationResultCode--><!--Device-AcquireAuthorizationResult-resultCode: AuthorizationResultCode-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## token

```TypeScript
token?: Uint8Array
```

授权令牌，默认为undefined。

**类型：** Uint8Array

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationResult-token?: Uint8Array--><!--Device-AcquireAuthorizationResult-token?: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## validityPeriod

```TypeScript
validityPeriod?: number
```

授权的有效期，默认值为300，单位为s。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AcquireAuthorizationResult-validityPeriod?: int--><!--Device-AcquireAuthorizationResult-validityPeriod?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

