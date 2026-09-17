# DeliveryMode

Enumerates the asset delivery modes.

These modes are used for segmented photo or video delivery. If the device does not support segmentation, the three delivery modes below work the same way and just return the requested image or video directly. The request result is returned through the [onDataPrepared](arkts-medialibrary-photoaccesshelper-mediaassetdatahandler-i.md#ondataprepared) callback.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## FAST_MODE

```TypeScript
FAST_MODE = 0
```

Fast mode.

For segmented photo or video delivery, if a high-quality version is available, it quickly returns the callback for that high-quality version. If only a low-quality version is available, it returns the callback for the low- quality version right away.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## HIGH_QUALITY_MODE

```TypeScript
HIGH_QUALITY_MODE = 1
```

High-quality mode.

For segmented photo or video delivery, if a high-quality version is available, it quickly returns the callback for that high-quality version. If only a low-quality version is available, it starts a task to generate a high- quality version and returns the callback for the high-quality version once that version is ready.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## BALANCE_MODE

```TypeScript
BALANCE_MODE = 2
```

Balance mode.

- For segmented photo delivery, if a high-quality version is available, it quickly returns the callback for that  
high-quality version. If only a low-quality version is available, it returns the callback for the low-quality version, starts a task to generate a high-quality version, and returns the callback for the high-quality version once that version is ready.  
- For segmented video delivery, if a high-quality version is available, it quickly returns the callback for that  
high-quality version. If only a low-quality version is available, it returns the callback for the low-quality version right away.

**Since:** 11

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core
