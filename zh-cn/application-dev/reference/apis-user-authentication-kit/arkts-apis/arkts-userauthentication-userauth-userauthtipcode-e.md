# UserAuthTipCode

表示身份认证中间状态的枚举。该枚举用于描述认证过程中的各种中间状态，包括认证不通过、超时、冻结状态以及认证界面的加载和释放等。应用可通过[on('authTip')](arkts-userauthentication-userauth-userauthinstance-i.md#on-2)接口订阅这些中间状态，以便在认证过程中提供更精细的用户反馈和状态感知。

**起始版本：** 20

<!--Device-userAuth-enum UserAuthTipCode--><!--Device-userAuth-enum UserAuthTipCode-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## COMPARE_FAILURE

```TypeScript
COMPARE_FAILURE = 1
```

认证不通过。表示当前认证尝试失败，用户特征与已注册凭据比对不匹配。此状态会在每次认证不通过时触发，应用可根据此状态提示用户重新尝试。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthTipCode-COMPARE_FAILURE = 1--><!--Device-UserAuthTipCode-COMPARE_FAILURE = 1-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## TIMEOUT

```TypeScript
TIMEOUT = 2
```

认证超时。表示认证操作超时，通常是由于用户在规定时间内未完成认证交互（如未及时输入密码、未正视摄像头等）导致。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthTipCode-TIMEOUT = 2--><!--Device-UserAuthTipCode-TIMEOUT = 2-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## TEMPORARILY_LOCKED

```TypeScript
TEMPORARILY_LOCKED = 3
```

临时冻结。表示认证器进入临时冻结状态，用户需等待冻结时长结束后才能继续尝试认证。临时冻结通常由连续多次认证失败触发。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthTipCode-TEMPORARILY_LOCKED = 3--><!--Device-UserAuthTipCode-TEMPORARILY_LOCKED = 3-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## PERMANENTLY_LOCKED

```TypeScript
PERMANENTLY_LOCKED = 4
```

永久冻结。表示认证器进入永久冻结状态，用户无法通过等待自动解锁，必须使用PIN认证解锁后才能继续使用该认证类型。永久冻结通常由临时冻结期间继续尝试认证不通过触发。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthTipCode-PERMANENTLY_LOCKED = 4--><!--Device-UserAuthTipCode-PERMANENTLY_LOCKED = 4-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## WIDGET_LOADED

```TypeScript
WIDGET_LOADED = 5
```

身份认证界面加载完毕。表示认证控件已成功加载并显示，用户可以开始进行认证交互。应用可在此状态触发后进行界面相关的初始化操作。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthTipCode-WIDGET_LOADED = 5--><!--Device-UserAuthTipCode-WIDGET_LOADED = 5-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## WIDGET_RELEASED

```TypeScript
WIDGET_RELEASED = 6
```

当前的身份认证界面退出，切换其他认证界面或身份认证控件关闭。表示认证控件已释放，应用可在此状态触发后进行后续操作，如弹出其他窗口等。在PC/2in1设备上使用模应用弹窗方式认证时，建议订阅此状态以确保控件完全释放后再执行其他界面操作。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthTipCode-WIDGET_RELEASED = 6--><!--Device-UserAuthTipCode-WIDGET_RELEASED = 6-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## COMPARE_FAILURE_WITH_FROZEN

```TypeScript
COMPARE_FAILURE_WITH_FROZEN = 7
```

认证不通过并触发了认证冻结。表示当前认证不通过，并且失败次数已达到阈值，认证器进入冻结状态。此状态同时包含认证不通过和冻结两个信息，应用可根据冻结类型（临时或永久）提示用户相应的解锁方式。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-UserAuthTipCode-COMPARE_FAILURE_WITH_FROZEN = 7--><!--Device-UserAuthTipCode-COMPARE_FAILURE_WITH_FROZEN = 7-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

