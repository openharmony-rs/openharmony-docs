# Intention

UDMF已经支持的数据通路枚举类型。其主要用途是标识各种UDMF数据通路所面向的不同业务场景。

**起始版本：** 10

<!--Device-unifiedDataChannel-enum Intention--><!--Device-unifiedDataChannel-enum Intention-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DATA_HUB

```TypeScript
DATA_HUB = 'DataHub'
```

公共数据通路。

**适用场景：** 适用于在公共数据共享场景下使用UDMF来跨应用数据共享。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Intention-DATA_HUB = 'DataHub'--><!--Device-Intention-DATA_HUB = 'DataHub'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SYSTEM_SHARE

```TypeScript
SYSTEM_SHARE = 'SystemShare'
```

系统分享类型数据通道。

**适用场景：** 适用于在系统分享场景下使用UDMF来跨应用数据共享。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Intention-SYSTEM_SHARE = 'SystemShare'--><!--Device-Intention-SYSTEM_SHARE = 'SystemShare'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## PICKER

```TypeScript
PICKER = 'Picker'
```

Picker类型数据通道。

**适用场景：** 适用于在Picker选择器场景下使用UDMF来跨应用数据共享。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Intention-PICKER = 'Picker'--><!--Device-Intention-PICKER = 'Picker'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## MENU

```TypeScript
MENU = 'Menu'
```

菜单类型数据通道。

**适用场景：** 适用于在右键菜单场景下使用UDMF来跨应用数据共享。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Intention-MENU = 'Menu'--><!--Device-Intention-MENU = 'Menu'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

