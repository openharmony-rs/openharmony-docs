# DeviceStateChange

```TypeScript
enum DeviceStateChange
```

Enumerates the device states.

**Since:** 10

<!--Device-distributedDeviceManager-enum DeviceStateChange--><!--Device-distributedDeviceManager-enum DeviceStateChange-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## AVAILABLE

```TypeScript
AVAILABLE = 1
```

The information between devices has been synchronized in the Distributed Data Service (DDS) module, and the device is ready for running distributed services.

**Since:** 10

<!--Device-DeviceStateChange-AVAILABLE = 1--><!--Device-DeviceStateChange-AVAILABLE = 1-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## UNAVAILABLE

```TypeScript
UNAVAILABLE = 2
```

The device goes offline, and the device state is unknown.

**Since:** 10

<!--Device-DeviceStateChange-UNAVAILABLE = 2--><!--Device-DeviceStateChange-UNAVAILABLE = 2-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

The device state is unknown after the device goes online. Before the device state changes to available, distributed services cannot be used.

**Since:** 10

<!--Device-DeviceStateChange-UNKNOWN = 0--><!--Device-DeviceStateChange-UNKNOWN = 0-End-->

**System capability:** SystemCapability.DistributedHardware.DeviceManager
