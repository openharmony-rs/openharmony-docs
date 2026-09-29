# RegState

```TypeScript
export enum RegState
```

Defines the network registration status of the device.

**Since:** 6

<!--Device-radio-export enum RegState--><!--Device-radio-export enum RegState-End-->

**System capability:** SystemCapability.Telephony.CoreService

## REG_STATE_NO_SERVICE

```TypeScript
REG_STATE_NO_SERVICE = 0
```

The device cannot use any services, including data, SMS, and call services.

**Since:** 6

<!--Device-RegState-REG_STATE_NO_SERVICE = 0--><!--Device-RegState-REG_STATE_NO_SERVICE = 0-End-->

**System capability:** SystemCapability.Telephony.CoreService

## REG_STATE_IN_SERVICE

```TypeScript
REG_STATE_IN_SERVICE = 1
```

The device can use services properly, including data, SMS, and call services.

**Since:** 6

<!--Device-RegState-REG_STATE_IN_SERVICE = 1--><!--Device-RegState-REG_STATE_IN_SERVICE = 1-End-->

**System capability:** SystemCapability.Telephony.CoreService

## REG_STATE_EMERGENCY_CALL_ONLY

```TypeScript
REG_STATE_EMERGENCY_CALL_ONLY = 2
```

The device can use only the emergency call service.

**Since:** 6

<!--Device-RegState-REG_STATE_EMERGENCY_CALL_ONLY = 2--><!--Device-RegState-REG_STATE_EMERGENCY_CALL_ONLY = 2-End-->

**System capability:** SystemCapability.Telephony.CoreService

## REG_STATE_POWER_OFF

```TypeScript
REG_STATE_POWER_OFF = 3
```

The device cannot communicate with the network because the cellular radio service is disabled or the modem is powered off.

**Since:** 6

<!--Device-RegState-REG_STATE_POWER_OFF = 3--><!--Device-RegState-REG_STATE_POWER_OFF = 3-End-->

**System capability:** SystemCapability.Telephony.CoreService
