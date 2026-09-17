# SyncType

Enumerates the sync types supported by an asset.

**Since:** 11

**System capability:** SystemCapability.Security.Asset

## NEVER

```TypeScript
NEVER = 0
```

Asset sync is not allowed.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## THIS_DEVICE

```TypeScript
THIS_DEVICE = 1 << 0
```

Asset sync is allowed only on the local device, for example, in data restore on the local device.

**Note:**  This field is reserved for future use and is not supported currently.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## TRUSTED_DEVICE

```TypeScript
TRUSTED_DEVICE = 1 << 1
```

Asset sync is allowed only between trusted devices, for example, in the case of cloning.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset

## TRUSTED_ACCOUNT

```TypeScript
TRUSTED_ACCOUNT = 1 << 2
```

Asset sync is allowed only between the devices that are logged in with trusted accounts, for example, in cloud sync scenarios.

**Note:**  This field is reserved for future use and is not supported currently.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Security.Asset
