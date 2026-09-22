# SettingsForDevice

```TypeScript
enum SettingsForDevice
```

Enumerates device setting items.

**Since:** 26.0.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SET_APN

```TypeScript
SET_APN = 0
```

APN configuration, currently supported only on phones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## POWER_LONG_PRESS

```TypeScript
POWER_LONG_PRESS = 1
```

Opens the power menu by long-pressing the power button. Currently, this item is supported only on phones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SET_ETHERNET_IP

```TypeScript
SET_ETHERNET_IP = 2
```

Changes the Ethernet IP address. Currently, this item is supported only on PCs/2-in-1 devices.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SET_DEVICE_NAME

```TypeScript
SET_DEVICE_NAME = 3
```

Changes the device name configuration. Currently, this item is supported only on PCs/2-in-1 devices, phones, and tablets. When it is disabled, the device name cannot be modified in the following settings: **About**, **Bluetooth**, and **More connectivity options**  
> **NearLink** on PCs/2-in-1 devices, and **About**, **Bluetooth**, and **Personal hotspot** on smartphones and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## SET_BIOMETRICS_AND_SCREEN_LOCK

```TypeScript
SET_BIOMETRICS_AND_SCREEN_LOCK = 4
```

Changes the screen lock password. Currently, this item is supported only on PCs/2-in-1 devices, phones, and tablets.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
