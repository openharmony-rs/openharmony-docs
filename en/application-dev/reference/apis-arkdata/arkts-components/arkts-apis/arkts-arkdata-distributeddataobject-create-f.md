# create

## Modules to Import

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## create

```TypeScript
function create(context: Context, source: object): DataObject
```

Creates a distributed data object. The object properties support basic types (number, Boolean, and string) and complex types (array and nested basic types).

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context. For details about the application context of the FA model, see Context.For details about the application context of the stage model, see Context. |
| source | object | Yes | Properties of the distributed data object. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataObject](arkts-arkdata-distributeddataobject-dataobject-i.md) | Distributed data object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
FA model:
```

```TypeScript
Stage model:
```
