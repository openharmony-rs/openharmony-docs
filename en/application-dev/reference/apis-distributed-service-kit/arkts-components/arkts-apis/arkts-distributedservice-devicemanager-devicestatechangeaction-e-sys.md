# DeviceStateChangeAction (System API)

Enumerates the device states.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [DeviceStateChange](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## ONLINE

```TypeScript
ONLINE = 0
```

The device is physically online.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [UNKNOWN](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md#unknown)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## READY

```TypeScript
READY = 1
```

The information between devices has been synchronized in the Distributed Data Service (DDS) module, and the device is ready for running distributed services.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [AVAILABLE](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md#available)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## OFFLINE

```TypeScript
OFFLINE = 2
```

The device is physically offline.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [UNAVAILABLE](arkts-distributedservice-distributeddevicemanager-devicestatechange-e.md#unavailable)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## CHANGE

```TypeScript
CHANGE = 3
```

The device information is changed.

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
