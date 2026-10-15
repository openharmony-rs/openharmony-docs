# EthEapState

```TypeScript
enum EthEapState
```

Enumerates the 802.1X EAP authentication states.

**Since:** 26.2.0

<!--Device-eap-enum EthEapState--><!--Device-eap-enum EthEapState-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## STATE_AUTHENTICATED

```TypeScript
STATE_AUTHENTICATED = 2
```

Authenticated: authentication succeeded.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapState-STATE_AUTHENTICATED = 2--><!--Device-EthEapState-STATE_AUTHENTICATED = 2-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## STATE_AUTHENTICATING

```TypeScript
STATE_AUTHENTICATING = 1
```

Authenticating: 802.1X authentication is in progress.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapState-STATE_AUTHENTICATING = 1--><!--Device-EthEapState-STATE_AUTHENTICATING = 1-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## STATE_FAILED

```TypeScript
STATE_FAILED = 3
```

Failed: maximum retry count reached.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapState-STATE_FAILED = 3--><!--Device-EthEapState-STATE_FAILED = 3-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## STATE_IDLE

```TypeScript
STATE_IDLE = 0
```

Idle: no authentication has been initiated.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapState-STATE_IDLE = 0--><!--Device-EthEapState-STATE_IDLE = 0-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## STATE_RETRYING

```TypeScript
STATE_RETRYING = 4
```

Retrying: waiting before the next retry attempt.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapState-STATE_RETRYING = 4--><!--Device-EthEapState-STATE_RETRYING = 4-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap
