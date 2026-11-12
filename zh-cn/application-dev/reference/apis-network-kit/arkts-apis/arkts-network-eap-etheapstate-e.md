# EthEapState

```TypeScript
enum EthEapState
```

枚举802.1X EAP身份验证状态。

**起始版本：** 26.0.1

<!--Device-eap-enum EthEapState--><!--Device-eap-enum EthEapState-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## STATE_AUTHENTICATED

```TypeScript
STATE_AUTHENTICATED = 2
```

Authenticated：鉴权成功。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapState-STATE_AUTHENTICATED = 2--><!--Device-EthEapState-STATE_AUTHENTICATED = 2-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## STATE_AUTHENTICATING

```TypeScript
STATE_AUTHENTICATING = 1
```

正在认证：802.1X认证正在进行中。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapState-STATE_AUTHENTICATING = 1--><!--Device-EthEapState-STATE_AUTHENTICATING = 1-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## STATE_FAILED

```TypeScript
STATE_FAILED = 3
```

失败：已达到最大重试计数。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapState-STATE_FAILED = 3--><!--Device-EthEapState-STATE_FAILED = 3-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## STATE_IDLE

```TypeScript
STATE_IDLE = 0
```

空闲：未发起鉴权。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapState-STATE_IDLE = 0--><!--Device-EthEapState-STATE_IDLE = 0-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap

## STATE_RETRYING

```TypeScript
STATE_RETRYING = 4
```

重试：等待下一次重试。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EthEapState-STATE_RETRYING = 4--><!--Device-EthEapState-STATE_RETRYING = 4-End-->

**系统能力：** SystemCapability.Communication.NetManager.Eap
