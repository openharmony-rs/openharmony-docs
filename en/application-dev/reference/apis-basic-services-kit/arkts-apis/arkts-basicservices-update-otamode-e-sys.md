# OtaMode (System API)

Enumerates the update modes.

**Since:** 20

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## REGULAR_OTA

```TypeScript
REGULAR_OTA = 0
```

Regular OTA. In this mode, download the complete upgrade package to the local device and then install the package. This mode applies to most regular upgrade scenarios.

**Since:** 20

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## STREAM_OTA

```TypeScript
STREAM_OTA = 1
```

Streaming OTA. In this mode, the upgrade is performed while the package is being downloaded. This mode applies to scenarios where the storage space is limited or a quick upgrade is required. For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md)

**Since:** 20

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## AB_REGULAR_OTA

```TypeScript
AB_REGULAR_OTA = 2
```

Regular A/B OTA. This mode applies to devices with A/B partitions. For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md)

**Since:** 20

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## AB_STREAM_OTA

```TypeScript
AB_STREAM_OTA = 3
```

Streaming A/B OTA. This mode applies to devices with A/B partitions. For details, see [Upgrading Service Terms](../../../basic-services/update/update-kit-term.md)

**Since:** 20

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
