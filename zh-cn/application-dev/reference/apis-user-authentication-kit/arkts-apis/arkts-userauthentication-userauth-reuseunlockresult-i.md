# ReuseUnlockResult

复用解锁认证结果。该接口用于配置认证结果复用的相关参数，包括复用模式和有效时长。通过合理配置认证结果复用，可以在保证安全性的前提下提升用户体验，避免用户频繁重复认证。
> **说明：**  
>  
> 如果身份认证解锁（包括设备解锁）后，在有效时间内凭据发生了变化，身份认证的结果依然可以复用，认证结果中返回当前实际的EnrolledState。若复用认证结果时，之前认证时所使用的身份认证凭据已经被删除：  
>  
> - 如果删除的是人脸、指纹，则认证结果依然可以复用，只是返回的EnrolledState中credentialCount和credentialDigest均为0。  
>  
> - 如果删除的是锁屏口令，则此次复用会失败。

**起始版本：** 12

<!--Device-userAuth-interface ReuseUnlockResult--><!--Device-userAuth-interface ReuseUnlockResult-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## 导入模块

```TypeScript
import { userAuth } from '@kit.UserAuthenticationKit';
```

## reuseDuration

```TypeScript
reuseDuration: number
```

允许复用解锁认证结果的有效时长，单位为毫秒。有效时长的值应大于0，最大值为[MAX_ALLOWABLE_REUSE_DURATION](arkts-userauthentication-userauth-con.md#max_allowable_reuse_duration)，（300000毫秒，即5分钟）。建议根据业务场景设置合理的时长：

- 高安全场景（如支付）：建议设置较短时长（如30秒至1分钟）。  
- 中等安全场景（如应用登录）：建议设置中等时长（如2至3分钟）。  
- 低安全场景（如数据查询）：可使用最大时长。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ReuseUnlockResult-reuseDuration: int--><!--Device-ReuseUnlockResult-reuseDuration: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## reuseMode

```TypeScript
reuseMode: ReuseMode
```

复用解锁认证结果的模式。根据业务场景的安全需求选择合适的复用模式：

- AUTH_TYPE_RELEVANT(1)：仅复用匹配认证类型的设备解锁结果，安全性最高。  
- AUTH_TYPE_IRRELEVANT(2)：复用任意类型的设备解锁结果，适用于中等安全场景。  
- CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT(3)：复用匹配认证类型的任意认证结果，适用于跨应用场景。  
- CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT(4)：复用任意认证结果，安全性最低但体验最优。

**类型：** ReuseMode

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ReuseUnlockResult-reuseMode: ReuseMode--><!--Device-ReuseUnlockResult-reuseMode: ReuseMode-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

