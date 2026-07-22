# UserAuthResultCode

表示返回码的枚举。该枚举定义了用户认证操作可能返回的所有结果码，包括成功码和各类错误码。应用可根据返回码判断认证结果，并采取相应的处理措施。

**起始版本：** 9

<!--Device-userAuth-enum UserAuthResultCode--><!--Device-userAuth-enum UserAuthResultCode-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## SUCCESS

```TypeScript
SUCCESS = 12500000
```

执行成功。表示用户身份认证通过，认证令牌有效。应用可使用返回的token进行后续的安全操作。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-SUCCESS = 12500000--><!--Device-UserAuthResultCode-SUCCESS = 12500000-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## FAIL

```TypeScript
FAIL = 12500001
```

认证不通过。表示用户特征与已注册凭据比对不匹配，可能是用户输入错误或使用了未注册的凭据。建议提示用户重新尝试。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-FAIL = 12500001--><!--Device-UserAuthResultCode-FAIL = 12500001-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## GENERAL_ERROR

```TypeScript
GENERAL_ERROR = 12500002
```

操作通用错误。表示认证过程中发生未知错误，建议稍后重试或联系系统管理员。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-GENERAL_ERROR = 12500002--><!--Device-UserAuthResultCode-GENERAL_ERROR = 12500002-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## CANCELED

```TypeScript
CANCELED = 12500003
```

认证取消。表示用户主动取消了认证操作或认证被系统取消。应用可根据业务逻辑决定是否重新发起认证。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-CANCELED = 12500003--><!--Device-UserAuthResultCode-CANCELED = 12500003-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## TIMEOUT

```TypeScript
TIMEOUT = 12500004
```

认证超时。表示用户在规定时间内未完成认证交互（如未及时输入密码、未正视摄像头等）。建议提示用户重新尝试并注意操作时限。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-TIMEOUT = 12500004--><!--Device-UserAuthResultCode-TIMEOUT = 12500004-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## TYPE_NOT_SUPPORT

```TypeScript
TYPE_NOT_SUPPORT = 12500005
```

认证类型不支持。表示当前设备不支持指定的认证类型（如设备无指纹传感器却请求指纹认证）。建议检查设备能力或更换认证类型。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-TYPE_NOT_SUPPORT = 12500005--><!--Device-UserAuthResultCode-TYPE_NOT_SUPPORT = 12500005-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## TRUST_LEVEL_NOT_SUPPORT

```TypeScript
TRUST_LEVEL_NOT_SUPPORT = 12500006
```

认证等级不支持。表示指定的认证可信等级高于当前认证类型所能达到的最高等级。建议降低认证等级或使用更安全的认证类型。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-TRUST_LEVEL_NOT_SUPPORT = 12500006--><!--Device-UserAuthResultCode-TRUST_LEVEL_NOT_SUPPORT = 12500006-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## BUSY

```TypeScript
BUSY = 12500007
```

系统繁忙。表示认证服务正忙于处理其他请求，建议稍后重试。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-BUSY = 12500007--><!--Device-UserAuthResultCode-BUSY = 12500007-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 12500008
```

参数校验失败。表示传入的参数不符合要求，如参数类型错误、参数值超出范围等。建议检查参数并重新调用。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-INVALID_PARAMETERS = 12500008--><!--Device-UserAuthResultCode-INVALID_PARAMETERS = 12500008-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## LOCKED

```TypeScript
LOCKED = 12500009
```

认证器已锁定。表示认证器因连续多次认证不通过而进入冻结状态，用户需等待冻结解除或使用PIN解锁后才能继续认证。可通过[getAuthLockState](arkts-userauthentication-userauth-getauthlockstate-f.md#getauthlockstate)查询具体冻结状态。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-LOCKED = 12500009--><!--Device-UserAuthResultCode-LOCKED = 12500009-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## NOT_ENROLLED

```TypeScript
NOT_ENROLLED = 12500010
```

用户未录入指定的系统身份认证凭据。表示用户未注册所请求的认证类型（如请求指纹认证但用户未录入指纹）。建议引导用户先注册相应凭据。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-NOT_ENROLLED = 12500010--><!--Device-UserAuthResultCode-NOT_ENROLLED = 12500010-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## CANCELED_FROM_WIDGET

```TypeScript
CANCELED_FROM_WIDGET = 12500011
```

用户取消了系统认证方式，选择应用自定义认证。表示用户点击了认证界面上的导航按钮，选择使用应用提供的自定义认证方式。应用需拉起自定义认证界面。

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-CANCELED_FROM_WIDGET = 12500011--><!--Device-UserAuthResultCode-CANCELED_FROM_WIDGET = 12500011-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## PIN_EXPIRED

```TypeScript
PIN_EXPIRED = 12500013
```

锁屏密码过期。表示系统锁屏口令已过期（如企业策略要求定期更换密码），用户需更新锁屏密码后才能继续使用认证功能。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthResultCode-PIN_EXPIRED = 12500013--><!--Device-UserAuthResultCode-PIN_EXPIRED = 12500013-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

