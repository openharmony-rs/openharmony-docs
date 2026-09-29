# EthEapConfig

```TypeScript
interface EthEapConfig
```

Represents the 802.1X Ethernet EAP configuration, including the EAP profile and feature toggles.

**Since:** 26.2.0

<!--Device-eap-interface EthEapConfig--><!--Device-eap-interface EthEapConfig-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## autoAuth

```TypeScript
autoAuth: boolean
```

Whether to automatically initiate authentication when the network cable is connected or on boot.

**Type:** boolean

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapConfig-autoAuth: boolean--><!--Device-EthEapConfig-autoAuth: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## enabled

```TypeScript
enabled: boolean
```

Whether the 802.1X feature is enabled.

**Type:** boolean

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapConfig-enabled: boolean--><!--Device-EthEapConfig-enabled: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## locked

```TypeScript
locked: boolean
```

Whether the configuration is locked. When locked, modifications are denied except for unlocking.

**Type:** boolean

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapConfig-locked: boolean--><!--Device-EthEapConfig-locked: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap

## profile

```TypeScript
profile: EthEapProfile
```

EAP profile information.

**Type:** [EthEapProfile](arkts-network-eap-etheapprofile-i.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EthEapConfig-profile: EthEapProfile--><!--Device-EthEapConfig-profile: EthEapProfile-End-->

**System capability:** SystemCapability.Communication.NetManager.Eap
