# ReuseMode

复用解锁认证结果的模式。该枚举定义了认证结果复用的四种模式，用于控制何种认证结果可以在何种条件下被复用。应用可根据业务场景选择合适的复用模式，以在安全性和用户体验之间取得平衡。

**起始版本：** 12

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## AUTH_TYPE_RELEVANT

```TypeScript
AUTH_TYPE_RELEVANT = 1
```

与认证类型相关，只有当设备解锁认证结果在有效时间内，并且设备解锁的认证类型匹配上本次认证指定认证类型之一时，可以复用该结果。

例如：用户使用人脸解锁设备后，在有效时间内发起需要人脸认证的业务操作，可直接复用解锁结果；但如果发起需要指纹认证的业务操作，则无法复用。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## AUTH_TYPE_IRRELEVANT

```TypeScript
AUTH_TYPE_IRRELEVANT = 2
```

与认证类型无关，设备解锁认证结果在有效时间内，可以重复使用。

例如：用户使用人脸解锁设备后，在有效时间内发起需要指纹或PIN认证的业务操作，均可直接复用解锁结果，无需再次认证。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT

```TypeScript
CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT = 3
```

与认证类型相关，任意身份认证（包括设备解锁）结果在有效时间内，并且身份认证的认证类型匹配上本次认证指定认证类型之一时，可以复用该结果。

例如：用户在某应用中使用人脸认证完成支付后，在有效时间内另一应用发起需要人脸认证的操作，可复用之前的认证结果；但如果发起需要指纹认证的操作，则无法复用。

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT

```TypeScript
CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT = 4
```

与认证类型无关，任意身份认证（包括设备解锁）结果在有效时间内，可以重复使用。

例如：用户在某应用中使用人脸认证完成操作后，在有效时间内另一应用发起任意类型的认证操作，均可复用之前的认证结果。

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

