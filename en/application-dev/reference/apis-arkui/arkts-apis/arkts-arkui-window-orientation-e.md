# Orientation

```TypeScript
enum Orientation
```

Enumerates the window orientations. <!--Del-->For details of the differences between different enumerated values, see [What is the difference between orientation values 8 to 10 or 12 and values 13 to 16 (API version 9)](../../../faqs/faqs-window-manager.md#what-is-the-difference-between-orientation-values-8-to-10-or-12-and-values-13-to-16-api-version-9).<!--DelEnd-->

**Since:** 9

<!--Device-window-enum Orientation--><!--Device-window-enum Orientation-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

Unspecified. The orientation is determined by the system.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-UNSPECIFIED = 0--><!--Device-Orientation-UNSPECIFIED = 0-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## PORTRAIT

```TypeScript
PORTRAIT = 1
```

Portrait.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Orientation-PORTRAIT = 1--><!--Device-Orientation-PORTRAIT = 1-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## LANDSCAPE

```TypeScript
LANDSCAPE = 2
```

Landscape.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-LANDSCAPE = 2--><!--Device-Orientation-LANDSCAPE = 2-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## PORTRAIT_INVERTED

```TypeScript
PORTRAIT_INVERTED = 3
```

Reverse portrait.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-PORTRAIT_INVERTED = 3--><!--Device-Orientation-PORTRAIT_INVERTED = 3-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## LANDSCAPE_INVERTED

```TypeScript
LANDSCAPE_INVERTED = 4
```

Reverse landscape.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-LANDSCAPE_INVERTED = 4--><!--Device-Orientation-LANDSCAPE_INVERTED = 4-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION

```TypeScript
AUTO_ROTATION = 5
```

Automatically rotates with the sensor to four orientations: portrait, landscape, reverse portrait, and reverse landscape. This rotation is not controlled by the rotation switch in Control Panel.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Orientation-AUTO_ROTATION = 5--><!--Device-Orientation-AUTO_ROTATION = 5-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_PORTRAIT

```TypeScript
AUTO_ROTATION_PORTRAIT = 6
```

Automatically rotates with the sensor to two orientations: portrait and reverse portrait. This rotation is not controlled by the rotation switch in Control Panel.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-AUTO_ROTATION_PORTRAIT = 6--><!--Device-Orientation-AUTO_ROTATION_PORTRAIT = 6-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_LANDSCAPE

```TypeScript
AUTO_ROTATION_LANDSCAPE = 7
```

Automatically rotates with the sensor to two orientations: landscape and reverse landscape. This rotation is not controlled by the rotation switch in Control Panel.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-AUTO_ROTATION_LANDSCAPE = 7--><!--Device-Orientation-AUTO_ROTATION_LANDSCAPE = 7-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_RESTRICTED

```TypeScript
AUTO_ROTATION_RESTRICTED = 8
```

Automatically rotates with the sensor to four orientations: portrait, landscape, reverse portrait, and reverse landscape. This rotation is controlled by the rotation switch in Control Panel.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-AUTO_ROTATION_RESTRICTED = 8--><!--Device-Orientation-AUTO_ROTATION_RESTRICTED = 8-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_PORTRAIT_RESTRICTED

```TypeScript
AUTO_ROTATION_PORTRAIT_RESTRICTED = 9
```

Automatically rotates with the sensor to two orientations: portrait and reverse portrait. This rotation is controlled by the rotation switch in Control Panel.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-AUTO_ROTATION_PORTRAIT_RESTRICTED = 9--><!--Device-Orientation-AUTO_ROTATION_PORTRAIT_RESTRICTED = 9-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_LANDSCAPE_RESTRICTED

```TypeScript
AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10
```

Automatically rotates with the sensor to two orientations: landscape and reverse landscape. This rotation is controlled by the rotation switch in Control Panel.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10--><!--Device-Orientation-AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## LOCKED

```TypeScript
LOCKED = 11
```

Locked mode, where the window orientation is consistent with the current screen orientation.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-LOCKED = 11--><!--Device-Orientation-LOCKED = 11-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## AUTO_ROTATION_UNSPECIFIED

```TypeScript
AUTO_ROTATION_UNSPECIFIED = 12
```

Automatically rotates with the sensor, under the restriction of the rotation switch in Control Panel. The orientation that can be rotated to is determined by the system. For example, the window can rotate to portrait, landscape, or reverse landscape, but not reverse portrait, on a certain device.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-AUTO_ROTATION_UNSPECIFIED = 12--><!--Device-Orientation-AUTO_ROTATION_UNSPECIFIED = 12-End-->

**System capability:** SystemCapability.Window.SessionManager

## USER_ROTATION_PORTRAIT

```TypeScript
USER_ROTATION_PORTRAIT = 13
```

Temporarily rotates to portrait mode, and then automatically rotates with the sensor, under the restriction of the rotation switch in Control Panel. The orientation that can be rotated to is determined by the system.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-USER_ROTATION_PORTRAIT = 13--><!--Device-Orientation-USER_ROTATION_PORTRAIT = 13-End-->

**System capability:** SystemCapability.Window.SessionManager

## USER_ROTATION_LANDSCAPE

```TypeScript
USER_ROTATION_LANDSCAPE = 14
```

Temporarily rotates to landscape mode, and then automatically rotates with the sensor, under the restriction of the rotation switch in Control Panel. The orientation that can be rotated to is determined by the system.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-USER_ROTATION_LANDSCAPE = 14--><!--Device-Orientation-USER_ROTATION_LANDSCAPE = 14-End-->

**System capability:** SystemCapability.Window.SessionManager

## USER_ROTATION_PORTRAIT_INVERTED

```TypeScript
USER_ROTATION_PORTRAIT_INVERTED = 15
```

Temporarily rotates to reverse portrait mode, and then automatically rotates with the sensor, under the restriction of the rotation switch in Control Panel. The orientation that can be rotated to is determined by the system.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-USER_ROTATION_PORTRAIT_INVERTED = 15--><!--Device-Orientation-USER_ROTATION_PORTRAIT_INVERTED = 15-End-->

**System capability:** SystemCapability.Window.SessionManager

## USER_ROTATION_LANDSCAPE_INVERTED

```TypeScript
USER_ROTATION_LANDSCAPE_INVERTED = 16
```

Temporarily rotates to reverse landscape mode, and then automatically rotates with the sensor, under the restriction of the rotation switch in Control Panel. The orientation that can be rotated to is determined by the system.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-USER_ROTATION_LANDSCAPE_INVERTED = 16--><!--Device-Orientation-USER_ROTATION_LANDSCAPE_INVERTED = 16-End-->

**System capability:** SystemCapability.Window.SessionManager

## FOLLOW_DESKTOP

```TypeScript
FOLLOW_DESKTOP = 17
```

Follows the orientation of the home screen, where the window will rotate if the home screen rotates and will not rotate if the home screen does not.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Orientation-FOLLOW_DESKTOP = 17--><!--Device-Orientation-FOLLOW_DESKTOP = 17-End-->

**System capability:** SystemCapability.Window.SessionManager
