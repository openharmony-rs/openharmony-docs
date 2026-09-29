# OsAccountSubProfileEventData (System API)

```TypeScript
interface OsAccountSubProfileEventData
```

Defines the data of an OS account sub-profile event.

**Since:** 26.0.0

<!--Device-osAccount-interface OsAccountSubProfileEventData--><!--Device-osAccount-interface OsAccountSubProfileEventData-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## event

```TypeScript
event: OsAccountSubProfileEvent
```

Event that occurs.

**Type:** [OsAccountSubProfileEvent](arkts-basicservices-osaccount-osaccountsubprofileevent-e-sys.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-OsAccountSubProfileEventData-event: OsAccountSubProfileEvent--><!--Device-OsAccountSubProfileEventData-event: OsAccountSubProfileEvent-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## osAccountLocalId

```TypeScript
osAccountLocalId: number
```

Local ID of the OS account. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-OsAccountSubProfileEventData-osAccountLocalId: int--><!--Device-OsAccountSubProfileEventData-osAccountLocalId: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## previousSubProfileId

```TypeScript
previousSubProfileId?: number
```

Previous OS account sub-profile ID. This parameter is valid only in the **SWITCHING** and **SWITCHED** events. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-OsAccountSubProfileEventData-previousSubProfileId?: int--><!--Device-OsAccountSubProfileEventData-previousSubProfileId?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## subProfileId

```TypeScript
subProfileId: number
```

OS account sub-profile ID. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-OsAccountSubProfileEventData-subProfileId: int--><!--Device-OsAccountSubProfileEventData-subProfileId: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
