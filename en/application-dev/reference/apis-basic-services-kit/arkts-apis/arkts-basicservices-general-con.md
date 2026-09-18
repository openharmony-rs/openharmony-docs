# Constants

## ACCELEROMETER_ROTATION_STATUS

```TypeScript
const ACCELEROMETER_ROTATION_STATUS: string
```

Specifies whether the accelerometer is used to change screen orientation, that is, whether auto-rotation is enabled.

<p>The value `1` indicates that the accelerometer is enabled by default, and `0` indicates that the accelerometer is disabled by default.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## ACCESSIBILITY_STATUS

```TypeScript
const ACCESSIBILITY_STATUS: string
```

Specifies whether any accessibility feature is enabled.

<p>If the value is `1`, the accessibility feature is enabled. If the value is `0`, the accessibility feature is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## ACTIVATED_ACCESSIBILITY_SERVICES

```TypeScript
const ACTIVATED_ACCESSIBILITY_SERVICES: string
```

Indicates the list of accessibility features that have been activated.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## AIRPLANE_MODE_STATUS

```TypeScript
const AIRPLANE_MODE_STATUS: string
```

Specifies whether airplane mode is enabled.

<p>If the value is `1`, airplane mode is enabled. If the value is `0`, airplane mode is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## BOOT_COUNTING

```TypeScript
const BOOT_COUNTING: string
```

Indicates the number of boot operations after the device is powered on.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## CONTACT_METADATA_SYNC_STATUS

```TypeScript
const CONTACT_METADATA_SYNC_STATUS: string
```

Specifies whether contact metadata synchronization is enabled.

<p>If the value is `true`, synchronization is enabled. If the value is `false`, synchronization is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DEBUG_APP_PACKAGE

```TypeScript
const DEBUG_APP_PACKAGE: string
```

Indicates the bundle name of the application to debug.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DEBUGGER_WAITING

```TypeScript
const DEBUGGER_WAITING: string
```

Specifies whether the device waits for the debugger when starting an application to debug.

<p>If the value is `1`, the device waits for the debugger. If the value is `0`, the system does not wait for the debugger, and so the application runs normally.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DEVELOPMENT_SETTINGS_STATUS

```TypeScript
const DEVELOPMENT_SETTINGS_STATUS: string
```

Specifies whether developer options are enabled.

<p>If the value is `true`, developer options are enabled. If the value is `false`, developer options are disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DEVICE_NAME

```TypeScript
const DEVICE_NAME: string
```

Indicates the device name.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## DEVICE_PROVISION_STATUS

```TypeScript
const DEVICE_PROVISION_STATUS: string
```

Specifies whether the device is provisioned.

<p>On a multi-user device with a single system user, the screen may be locked when the value is `true`. In addition, other abilities cannot be started on the system user unless they are marked to display over the screen lock.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## END_BUTTON_ACTION

```TypeScript
const END_BUTTON_ACTION: string
```

Specifies what happens after the user presses the call end button if the user is not in a call.

&lt;ul&gt; &lt;li&gt;`0` - Nothing happens. &lt;li&gt;`1` - The home screen is displayed. &lt;li&gt;`2` - The device enters the sleep state and the screen is locked. &lt;li&gt;`3` - The home screen is displayed. If the user is already on the home screen, the device enters the sleep state. &lt;/ul&gt;

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## GEOLOCATION_ORIGINS_ALLOWED

```TypeScript
const GEOLOCATION_ORIGINS_ALLOWED: string
```

Indicates the default geographical location that can be used by the browser. Multiple geographical locations are separated by spaces.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## HDC_STATUS

```TypeScript
const HDC_STATUS: string
```

Specifies whether the hard disk controller (HDC) on USB devices is enabled.

<p>If the value is `true`, the HDC is enabled. If the value is `false`, the HDC is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## SETUP_WIZARD_FINISHED

```TypeScript
const SETUP_WIZARD_FINISHED: string
```

Specifies whether the startup wizard has been run.

<p>If the value is `0`, the startup wizard has not been run. If the value is not `0`, the startup wizard has been run.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## SKIP_USE_HINTS

```TypeScript
const SKIP_USE_HINTS: string
```

Specifies whether an application should attempt to skip all introductory hints at the first startup. This is intended for temporary users or users who are familiar with the environment.

<p>If the value is `1`, the application attempts to skip all introductory hints at the first startup. If the value is `0`, the application does not skip introductory hints at the first startup.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## TOUCH_EXPLORATION_STATUS

```TypeScript
const TOUCH_EXPLORATION_STATUS: string
```

Indicates whether touch exploration is enabled.

<p>If the value is `1`, touch exploration is enabled. If the value is `0`, touch exploration is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## USB_STORAGE_STATUS

```TypeScript
const USB_STORAGE_STATUS: string
```

Specifies whether USB mass storage is enabled.

<p>If the value is `true`, USB mass storage is enabled. If the value is `false`, USB mass storage is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core
