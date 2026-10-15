# SharingCode (System API)

```TypeScript
enum SharingCode
```

Enumerates the error codes for device-cloud sharing.

**Since:** 11

<!--Device-sharing-enum SharingCode--><!--Device-sharing-enum SharingCode-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## CLOUD_DISABLED

```TypeScript
CLOUD_DISABLED = 8
```

Cloud is disabled. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-CLOUD_DISABLED = 8--><!--Device-SharingCode-CLOUD_DISABLED = 8-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## CUSTOM_ERROR

```TypeScript
CUSTOM_ERROR = 1000
```

Customized error. Error codes smaller than **1000** are used to define internal error codes, and error codes greater than **1000** are used to customize error codes. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-CUSTOM_ERROR = 1000--><!--Device-SharingCode-CUSTOM_ERROR = 1000-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## INNER_ERROR

```TypeScript
INNER_ERROR = 10
```

System internal error. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-INNER_ERROR = 10--><!--Device-SharingCode-INNER_ERROR = 10-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## INVALID_ARGS

```TypeScript
INVALID_ARGS = 6
```

Invalid parameter. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-INVALID_ARGS = 6--><!--Device-SharingCode-INVALID_ARGS = 6-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## INVALID_INVITATION

```TypeScript
INVALID_INVITATION = 11
```

Invalid invitation, which means the current invitation has expired or does not exist. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-INVALID_INVITATION = 11--><!--Device-SharingCode-INVALID_INVITATION = 11-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## NETWORK_ERROR

```TypeScript
NETWORK_ERROR = 7
```

Network error. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-NETWORK_ERROR = 7--><!--Device-SharingCode-NETWORK_ERROR = 7-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## NOT_INVITER

```TypeScript
NOT_INVITER = 2
```

The participant is not the inviter of this share. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-NOT_INVITER = 2--><!--Device-SharingCode-NOT_INVITER = 2-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## NOT_INVITER_OR_INVITEE

```TypeScript
NOT_INVITER_OR_INVITEE = 3
```

Invalid participant, which means the participant is neither the inviter nor the invitee. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-NOT_INVITER_OR_INVITEE = 3--><!--Device-SharingCode-NOT_INVITER_OR_INVITEE = 3-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## OVER_QUOTA

```TypeScript
OVER_QUOTA = 4
```

The number of device-cloud sharing times has reached the limit for the current account. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-OVER_QUOTA = 4--><!--Device-SharingCode-OVER_QUOTA = 4-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## RATE_LIMIT

```TypeScript
RATE_LIMIT = 12
```

The amount of data to be synced at a time has reached the limit. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-RATE_LIMIT = 12--><!--Device-SharingCode-RATE_LIMIT = 12-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## REPEATED_REQUEST

```TypeScript
REPEATED_REQUEST = 1
```

Repeated invitation, which means the participant has been invited. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-REPEATED_REQUEST = 1--><!--Device-SharingCode-REPEATED_REQUEST = 1-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## SERVER_ERROR

```TypeScript
SERVER_ERROR = 9
```

Server error. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-SERVER_ERROR = 9--><!--Device-SharingCode-SERVER_ERROR = 9-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## SUCCESS

```TypeScript
SUCCESS = 0
```

Operation successful. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-SUCCESS = 0--><!--Device-SharingCode-SUCCESS = 0-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.

## TOO_MANY_PARTICIPANTS

```TypeScript
TOO_MANY_PARTICIPANTS = 5
```

The number of device-cloud sharing participants has reached the limit. Use the enum name rather than the enum value.

**Since:** 11

<!--Device-SharingCode-TOO_MANY_PARTICIPANTS = 5--><!--Device-SharingCode-TOO_MANY_PARTICIPANTS = 5-End-->

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**System API:** This is a system API.
