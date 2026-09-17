# showSystemApnSettings

## Modules to Import

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## showSystemApnSettings

```TypeScript
function showSystemApnSettings(context: Context): Promise<void>
```

Open the system APN selection menu, which is presented in a semi-modal form and can be used to select a specific APN. This API uses a promise to return the result. If there is no SIM card or the device does not support the APN menu, the menu cannot be displayed.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Telephony.CellularData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Indicates Context instance. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
