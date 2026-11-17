# HibernateCallback (System API)

```TypeScript
interface HibernateCallback
```

Defines the hibernation event callback interface.

**Since:** 26.1.0

<!--Device-power-interface HibernateCallback--><!--Device-power-interface HibernateCallback-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## onHibernate

```TypeScript
onHibernate(): Promise<void>
```

Called when the device is entering hibernation.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-HibernateCallback-onHibernate(): Promise<void>--><!--Device-HibernateCallback-onHibernate(): Promise<void>-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## onWakeup

```TypeScript
onWakeup(hibernateResult: boolean): Promise<void>
```

Called when the device is exiting hibernation.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-HibernateCallback-onWakeup(hibernateResult: boolean): Promise<void>--><!--Device-HibernateCallback-onWakeup(hibernateResult: boolean): Promise<void>-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hibernateResult | boolean | Yes | Indicates whether the hibernation succeeded. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
