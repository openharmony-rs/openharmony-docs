# 常量

## MAX_ALLOWABLE_REUSE_DURATION

```TypeScript
const MAX_ALLOWABLE_REUSE_DURATION: 300000
```

复用解锁认证结果最大有效时长，值为300000毫秒（5分钟）。用于限制认证结果复用的最大时长，防止长时间复用过期的认证结果带来的安全风险。该常量可作为[ReuseUnlockResult](arkts-userauthentication-userauth-reuseunlockresult-i.md)中reuseDuration参数的最大值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-userAuth-const MAX_ALLOWABLE_REUSE_DURATION: 300000--><!--Device-userAuth-const MAX_ALLOWABLE_REUSE_DURATION: 300000-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## PERMANENT_LOCKOUT_DURATION

```TypeScript
const PERMANENT_LOCKOUT_DURATION: number = 0x7fffffff
```

永久冻结时间，值为0x7fffffff毫秒。当认证不通过次数达到上限后，认证器将进入永久冻结状态，此时需要通过PIN认证才能解锁。该值用于标识认证器的永久冻结状态，可通过[AuthLockState](arkts-userauthentication-userauth-authlockstate-i.md)的lockoutDuration字段返回。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-userAuth-const PERMANENT_LOCKOUT_DURATION: int = 0x7fffffff--><!--Device-userAuth-const PERMANENT_LOCKOUT_DURATION: int = 0x7fffffff-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

