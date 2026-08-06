# AuthParam

用户认证相关参数。该接口用于配置用户认证的各项参数，包括挑战值、认证类型列表、认证信任等级、认证结果复用配置等。通过合理配置这些参数，可以满足不同业务场景下的认证需求。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-userAuth-interface AuthParam--><!--Device-userAuth-interface AuthParam-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## credentialIdList

```TypeScript
credentialIdList?: Uint8Array[]
```

凭据ID列表，用于指定需要认证的凭据。当需要只认证特定凭据而非用户的所有凭据时传入此参数；若不传入或传入空数组，则默认认证该用户的所有凭据。

**类型：** Uint8Array[]

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuthParam-credentialIdList?: Uint8Array[]--><!--Device-AuthParam-credentialIdList?: Uint8Array[]-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: int
```

待认证的目标用户ID，用于指定需要认证的用户。当需要认证特定用户而非当前登录用户时传入此参数；若不传入则默认使用当前登录用户的ID。取值为非负整数。

**类型：** int

**默认值：** The ID of the current user. The value is a positive integer greater than or equal to 0.

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-AuthParam-userId?: int--><!--Device-AuthParam-userId?: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

