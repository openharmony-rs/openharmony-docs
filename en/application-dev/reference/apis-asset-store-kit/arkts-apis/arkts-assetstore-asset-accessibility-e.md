# Accessibility

```TypeScript
enum Accessibility
```

Enumerates the types of access control based on the lock screen status.

**Since:** 11

<!--Device-asset-enum Accessibility--><!--Device-asset-enum Accessibility-End-->

**System capability:** SystemCapability.Security.Asset

## DEVICE_FIRST_UNLOCKED

```TypeScript
DEVICE_FIRST_UNLOCKED = 1
```

The asset can be accessed only after the device is unlocked for the first time.

**Note:**  If no lock screen password is set, this option is equivalent to **DEVICE_POWERED_ON**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-Accessibility-DEVICE_FIRST_UNLOCKED = 1--><!--Device-Accessibility-DEVICE_FIRST_UNLOCKED = 1-End-->

**System capability:** SystemCapability.Security.Asset

## DEVICE_POWERED_ON

```TypeScript
DEVICE_POWERED_ON = 0
```

The asset can be accessed after the device is powered on.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-Accessibility-DEVICE_POWERED_ON = 0--><!--Device-Accessibility-DEVICE_POWERED_ON = 0-End-->

**System capability:** SystemCapability.Security.Asset

## DEVICE_UNLOCKED

```TypeScript
DEVICE_UNLOCKED = 2
```

The asset can be accessed only when the device is unlocked.

**Note:**  If no lock screen password is set, this option is equivalent to **DEVICE_POWERED_ON**.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-Accessibility-DEVICE_UNLOCKED = 2--><!--Device-Accessibility-DEVICE_UNLOCKED = 2-End-->

**System capability:** SystemCapability.Security.Asset
