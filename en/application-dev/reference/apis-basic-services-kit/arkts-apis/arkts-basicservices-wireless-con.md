# Constants

## AIRPLANE_MODE_RADIOS

```TypeScript
const AIRPLANE_MODE_RADIOS: string
```

Indicates the list of radio signals to be disabled when airplane mode is enabled. Multiple radio signals are separated by commas (,).

&lt;ul&gt; &lt;li&gt;`BLUETOOTH_RADIO` - Bluetooth is disabled in airplane mode. &lt;li&gt;`CELL_RADIO` - Cellular radio is disabled in airplane mode. &lt;li&gt;`NFC_RADIO` - NFC is disabled in airplane mode. &lt;li&gt;`WIFI_RADIO` - Wi-Fi is disabled in airplane mode. &lt;/ul&gt;

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## BLUETOOTH_DISCOVER_ABILITY_STATUS

```TypeScript
const BLUETOOTH_DISCOVER_ABILITY_STATUS: string
```

Specifies whether the device can be discovered or connected by other devices through Bluetooth.

If the value is `0`, the device cannot be connected or discovered. If the value is `1`, the device can be connected but cannot be discovered. If the value is `2`, the device can be connected and discovered.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## BLUETOOTH_DISCOVER_TIMEOUT

```TypeScript
const BLUETOOTH_DISCOVER_TIMEOUT: string
```

Indicates the duration (in seconds) that the device can be discovered through Bluetooth.

<p>After the duration expires, the device cannot be discovered through Bluetooth.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## BLUETOOTH_RADIO

```TypeScript
const BLUETOOTH_RADIO: string
```

A constant of `AIRPLANE_MODE_RADIOS` to indicate that Bluetooth is disabled in airplane mode.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## BLUETOOTH_STATUS

```TypeScript
const BLUETOOTH_STATUS: string
```

Specifies whether Bluetooth is enabled.

<p>If the value is `true`, Bluetooth is enabled. If the value is `false`, Bluetooth is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## CELL_RADIO

```TypeScript
const CELL_RADIO: string
```

A constant of `AIRPLANE_MODE_RADIOS` to indicate that cellular radio is disabled in airplane mode.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## NFC_RADIO

```TypeScript
const NFC_RADIO: string
```

A constant of `AIRPLANE_MODE_RADIOS` to indicate that NFC is disabled in airplane mode.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## OWNER_LOCKDOWN_WIFI_CFG

```TypeScript
const OWNER_LOCKDOWN_WIFI_CFG: string
```

Specifies whether the Wi-Fi configuration created by the application of the device owner should be locked down.

<p>If the value is `true`, the Wi-Fi configuration should be locked down. If the value is `false`, the Wi-Fi configuration should not be locked down.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## WIFI_DHCP_MAX_RETRY_COUNT

```TypeScript
const WIFI_DHCP_MAX_RETRY_COUNT: string
```

Indicates the maximum number of attempts to obtain an IP address from the DHCP server.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## WIFI_RADIO

```TypeScript
const WIFI_RADIO: string
```

A constant of `AIRPLANE_MODE_RADIOS` to indicate that Wi-Fi is disabled in airplane mode.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## WIFI_STATUS

```TypeScript
const WIFI_STATUS: string
```

Specifies whether Wi-Fi is enabled.

<p>If the value is `true`, Wi-Fi is enabled. If the value is `false`, Wi-Fi is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## WIFI_TO_MOBILE_DATA_AWAKE_TIMEOUT

```TypeScript
const WIFI_TO_MOBILE_DATA_AWAKE_TIMEOUT: string
```

Indicates the maximum duration to hold a wake lock when waiting for the mobile data connection to establish after the Wi-Fi connection is disconnected.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## WIFI_WATCHDOG_STATUS

```TypeScript
const WIFI_WATCHDOG_STATUS: string
```

Specifies whether Wi-Fi watchdog is enabled.

<p>If the value is `true`, Wi-Fi watchdog is enabled. If the value is `false`, Wi-Fi watchdog is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core
