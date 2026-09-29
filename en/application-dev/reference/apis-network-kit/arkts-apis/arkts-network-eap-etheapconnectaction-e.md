# EthEapConnectAction

```TypeScript
enum EthEapConnectAction
```

Enumerates the manual connect actions for the 802.1X EAP authentication of Ethernet.

**Since:** 26.2.0

<!--Device-eap-enum EthEapConnectAction--><!--Device-eap-enum EthEapConnectAction-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## ACTION_CONNECT

```TypeScript
ACTION_CONNECT = 0
```

Re-triggers authentication with the saved configuration.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapConnectAction-ACTION_CONNECT = 0--><!--Device-EthEapConnectAction-ACTION_CONNECT = 0-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## ACTION_DISCONNECT

```TypeScript
ACTION_DISCONNECT = 1
```

Stops auto authentication and logs off the underlying 802.1X authentication.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapConnectAction-ACTION_DISCONNECT = 1--><!--Device-EthEapConnectAction-ACTION_DISCONNECT = 1-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap
