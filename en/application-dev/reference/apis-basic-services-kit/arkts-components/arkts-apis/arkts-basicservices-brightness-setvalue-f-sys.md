# setValue (System API)

## Modules to Import

```TypeScript
import { brightness } from '@kit.BasicServicesKit';
```

## setValue

```TypeScript
function setValue(value: number): void
```

Sets the screen brightness.

**Since:** 7

**System capability:** SystemCapability.PowerManager.DisplayPowerManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Brightness value. Value range: 0 to 255. The value of this parameter must be a number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; |
| [4700101](../errorcode-brightness.md#4700101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
try {
    brightness.setValue(128);
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```

```TypeScript
try {
    brightness.setValue(128, true);
} catch(err) {
    console.error('set brightness failed, err: ' + err);
}
```


## setValue

```TypeScript
function setValue(value: number, continuous: boolean): void
```

Sets the screen brightness. This API is used for continuous brightness adjustment. To achieve a better performance, set **continuous** to **true** when you start, and set it to **false** after you finish.

**Since:** 11

**System capability:** SystemCapability.PowerManager.DisplayPowerManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Brightness value. Value range: [0, 255] |
| continuous | boolean | Yes | Whether the brightness adjustment is continuous. The value **true** indicates that the brightness adjustment is continuous; **false** indicates the opposite. Default value: **false** |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameter types; |
| [4700101](../errorcode-brightness.md#4700101-service-connection-failure) | Failed to connect to the service. |

**Examples**

See [setValue](#setvalue)
