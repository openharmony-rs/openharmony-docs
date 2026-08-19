# NetworkPolicy(智慧数据平台)

下载云侧模型的网络策略枚举。

**起始版本：** 26.0.0

<!--Device-intelligence-enum NetworkPolicy--><!--Device-intelligence-enum NetworkPolicy-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## WIFI_ONLY

```TypeScript
WIFI_ONLY = 0
```

仅在Wi-Fi状态下下载模型，适用于需要节省移动数据流量的场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NetworkPolicy-WIFI_ONLY = 0--><!--Device-NetworkPolicy-WIFI_ONLY = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## WIFI_AND_CELLULAR

```TypeScript
WIFI_AND_CELLULAR = 1
```

在Wi-Fi和蜂窝网络状态下下载模型，适用于需要快速获取模型且允许使用移动数据的场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NetworkPolicy-WIFI_AND_CELLULAR = 1--><!--Device-NetworkPolicy-WIFI_AND_CELLULAR = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

