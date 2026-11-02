# SystemDefinedRecord

```TypeScript
class SystemDefinedRecord extends UnifiedRecord
```

SystemDefinedRecord is a subclass of [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md) and the base class of OpenHarmony system-specific data types. It is used to describe data types that circulate only within the OpenHarmony system. You are advised to use subclasses of SystemDefinedRecord, such as [SystemDefinedForm](arkts-arkdata-unifieddatachannel-systemdefinedform-c.md), [SystemDefinedAppItem](arkts-arkdata-unifieddatachannel-systemdefinedappitem-c.md), and [SystemDefinedPixelMap](arkts-arkdata-unifieddatachannel-systemdefinedpixelmap-c.md), to describe data.

**Inheritance/Implementation:** SystemDefinedRecord extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**Since:** 10

<!--Device-unifiedDataChannel-class SystemDefinedRecord extends UnifiedRecord--><!--Device-unifiedDataChannel-class SystemDefinedRecord extends UnifiedRecord-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, number | string | Uint8Array>
```

A dictionary object whose key is of the string type and whose value can be of the number, string, or Uint8Array (binary byte array) type. This is an optional field, and the default value is an empty dictionary object.

**Type:** Record&lt;string, number &#124; string &#124; Uint8Array&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SystemDefinedRecord-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-SystemDefinedRecord-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
