# isCaptured

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## isCaptured

```TypeScript
function isCaptured(): boolean
```

Checks whether the device's screen content is being captured.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the device's screen content is being captured. **true** is returned when screen content is being captured (including active screen capture, casting, recording, or the creation of a virtual screen that could be captured). **false** is returned when screen content is no longer being captured. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |

**Examples**

```TypeScript
let ret: boolean = false;
// Check whether the screen content is captured.
ret = display.isCaptured();
```

```TypeScript
try {
  const bundleList: Array<string> = ['com.example.app'];
  let ret = display.isCaptured(bundleList);
  console.info(`The screen is captured or not: ${ret}`);
} catch (err) {
  console.error(`Failed to get display isCaptured. Code: ${err.code}, message: ${err.message}`);
}
```


## isCaptured

```TypeScript
function isCaptured(bundleNameList: Array<string>): boolean
```

Check whether the device is captured, projected, or recorded by any app in the bundle name list.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleNameList | Array&lt;string&gt; | Yes | The list of application bundle names that need to be checked. The max size of array is 100. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | true means the device is captured, projected, or recorded by any app in the bundle name list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-parameter-error) | Parameter error. Possible cause: 1.The size of bundleNameList is larger than 100. |

**Examples**

See [isCaptured](#iscaptured)
