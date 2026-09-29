# StandbyResourceType

```TypeScript
enum StandbyResourceType
```

Enumerates the standby resource types. These types represent resources that can be exempted from device standby restrictions. When a device enters standby mode, the system restricts network access and other resources for background applications. By applying for standby resource exemptions, specified applications can continue to use these resources even when the device is in standby mode.

**Since:** 26.0.1

<!--Device-applicationManager-enum StandbyResourceType--><!--Device-applicationManager-enum StandbyResourceType-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## NETWORK

```TypeScript
NETWORK = 1
```

Network access resource. When applied, the specified application can continue to access the network during device standby.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-StandbyResourceType-NETWORK = 1--><!--Device-StandbyResourceType-NETWORK = 1-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
