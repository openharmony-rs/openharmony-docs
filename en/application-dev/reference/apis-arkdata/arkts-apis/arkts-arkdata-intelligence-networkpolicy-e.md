# NetworkPolicy

```TypeScript
enum NetworkPolicy
```

Enumerates the network policies for downloading cloud-side models.

**Since:** 26.0.0

<!--Device-intelligence-enum NetworkPolicy--><!--Device-intelligence-enum NetworkPolicy-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## WIFI_AND_CELLULAR

```TypeScript
WIFI_AND_CELLULAR = 1
```

Download the model over both Wi-Fi and cellular networks. This policy applies to scenarios where the model needs to be obtained quickly and mobile data usage is allowed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NetworkPolicy-WIFI_AND_CELLULAR = 1--><!--Device-NetworkPolicy-WIFI_AND_CELLULAR = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## WIFI_ONLY

```TypeScript
WIFI_ONLY = 0
```

Download the model only over Wi-Fi. This policy applies to scenarios where mobile data traffic needs to be saved.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NetworkPolicy-WIFI_ONLY = 0--><!--Device-NetworkPolicy-WIFI_ONLY = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core
