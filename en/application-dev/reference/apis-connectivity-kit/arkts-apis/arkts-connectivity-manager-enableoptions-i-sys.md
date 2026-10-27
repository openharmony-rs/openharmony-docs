# EnableOptions (System API)

```TypeScript
interface EnableOptions
```

The options for enabling NearLink.

**Since:** 26.1.0

<!--Device-manager-interface EnableOptions--><!--Device-manager-interface EnableOptions-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## autoConnPolicy

```TypeScript
autoConnPolicy?: AutoConnectPolicy
```

Auto-connection policy to be used when NearLink is enabled. The default value is **AUTO_CONN_GENERAL**.

**Type:** [AutoConnectPolicy](arkts-connectivity-manager-autoconnectpolicy-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-EnableOptions-autoConnPolicy?: AutoConnectPolicy--><!--Device-EnableOptions-autoConnPolicy?: AutoConnectPolicy-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.
