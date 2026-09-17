# Participant (System API)

Represents information about a participant of device-cloud sharing.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## attachInfo

```TypeScript
attachInfo?: string
```

Additional information, such as the verification code used for participant identity verification. The default value is an empty string.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## identity

```TypeScript
identity: string
```

ID of the participant.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## privilege

```TypeScript
privilege?: Privilege
```

Permissions on the shared data. The Privilege defaults are used by default.

**Type:** [Privilege](arkts-arkdata-sharing-privilege-i-sys.md)

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## role

```TypeScript
role?: Role
```

Role of the participant, inviter or invitee. The default value is undefined.

**Type:** [Role](arkts-arkdata-sharing-role-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## state

```TypeScript
state?: State
```

State of the device-cloud sharing. The default value is undefined.

**Type:** [State](arkts-arkdata-sharing-state-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.
