# AuthParam

用户认证相关参数。该接口用于配置用户认证的各项参数，包括挑战值、认证类型列表、认证信任等级、认证结果复用配置等。通过合理配置这些参数，可以满足不同业务场景下的认证需求。

**起始版本：** 10

<!--Device-userAuth-interface AuthParam--><!--Device-userAuth-interface AuthParam-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## credentialIdList

```TypeScript
credentialIdList?: Uint8Array[]
```

凭据ID列表。若凭据ID列表不为空，则会认证指定的凭据ID，而非用户的所有凭据。适用于需要精确控制认证凭据的场景。

**类型：** Uint8Array[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthParam-credentialIdList?: Uint8Array[]--><!--Device-AuthParam-credentialIdList?: Uint8Array[]-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

待认证的目标用户ID。值为非负整数，用于指定需要认证的用户。默认值为当前用户的ID。

**类型：** number

**默认值：** The ID of the current user. The value is a positive integer greater than or equal to 0.

**起始版本：** 18

<!--Device-AuthParam-userId?: int--><!--Device-AuthParam-userId?: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

