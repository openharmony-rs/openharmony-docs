# SubscribeInfo (System API)

Defines subscription information.

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## capability

```TypeScript
capability: SubscribeCap
```

Discovery capability.

**Type:** [SubscribeCap](arkts-distributedservice-devicemanager-subscribecap-e-sys.md)

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## freq

```TypeScript
freq: ExchangeFreq
```

Frequency of device discovery.

**Type:** [ExchangeFreq](arkts-distributedservice-devicemanager-exchangefreq-e-sys.md)

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## isSameAccount

```TypeScript
isSameAccount: boolean
```

Whether the account is the same as the current account. The value **true** indicates the same account and the value **false** indicates a different account.

**Type:** boolean

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## isWakeRemote

```TypeScript
isWakeRemote: boolean
```

Whether to wake up the device. The value **true** means to wake up the device and the value **false** means the opposite.

**Type:** boolean

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## medium

```TypeScript
medium: ExchangeMedium
```

Medium used for device discovery.

**Type:** [ExchangeMedium](arkts-distributedservice-devicemanager-exchangemedium-e-sys.md)

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## mode

```TypeScript
mode: DiscoverMode
```

Device discovery mode.

**Type:** [DiscoverMode](arkts-distributedservice-devicemanager-discovermode-e-sys.md)

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

## subscribeId

```TypeScript
subscribeId: number
```

Subscription ID, used to identify a device discovery period. The value ranges from 1 to 65535.

**Type:** number

**Since:** 7

**Deprecated since:** 11

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.
