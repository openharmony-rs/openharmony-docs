# AutoConnectPolicy (System API)

```TypeScript
enum AutoConnectPolicy
```

Enumerates the auto-connection policies when NearLink is enabled.

**Since:** 26.2.0

<!--Device-manager-enum AutoConnectPolicy--><!--Device-manager-enum AutoConnectPolicy-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

## AUTO_CONN_EXCEPT_AUDIO_DEVICES

```TypeScript
AUTO_CONN_EXCEPT_AUDIO_DEVICES = 1
```

All paired devices except audio devices are automatically reconnected after NearLink is enabled.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-AutoConnectPolicy-AUTO_CONN_EXCEPT_AUDIO_DEVICES = 1--><!--Device-AutoConnectPolicy-AUTO_CONN_EXCEPT_AUDIO_DEVICES = 1-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

## AUTO_CONN_EXCEPT_USER_DISCONNECTED_DEVICES

```TypeScript
AUTO_CONN_EXCEPT_USER_DISCONNECTED_DEVICES = 2
```

All paired devices except those disconnected by the user are automatically reconnected after NearLink is enabled.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-AutoConnectPolicy-AUTO_CONN_EXCEPT_USER_DISCONNECTED_DEVICES = 2--><!--Device-AutoConnectPolicy-AUTO_CONN_EXCEPT_USER_DISCONNECTED_DEVICES = 2-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

## AUTO_CONN_GENERAL

```TypeScript
AUTO_CONN_GENERAL = 0
```

All paired devices are automatically reconnected after NearLink is enabled.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-AutoConnectPolicy-AUTO_CONN_GENERAL = 0--><!--Device-AutoConnectPolicy-AUTO_CONN_GENERAL = 0-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.
