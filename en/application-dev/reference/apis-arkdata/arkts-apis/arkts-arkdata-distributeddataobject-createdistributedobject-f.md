# createDistributedObject

## Modules to Import

```TypeScript
import { distributedDataObject } from '@kit.ArkData';
```

## createDistributedObject

```TypeScript
function createDistributedObject(source: object): DistributedObject
```

Creates a distributed data object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [create](arkts-arkdata-distributeddataobject-create-f.md)

**System capability:** SystemCapability.DistributedDataManager.DataObject.DistributedObject

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | object | Yes | Properties of the distributed data object. |

**Return value:**

| Type | Description |
| --- | --- |
| [DistributedObject](arkts-arkdata-distributeddataobject-distributedobject-i.md) | Distributed data object created. |

**Examples**

```TypeScript
class SourceObject {
  name: string
  age: number
  isVis: boolean

  constructor(name: string, age: number, isVis: boolean) {
    this.name = name;
    this.age = age;
    this.isVis = isVis;
  }
}

let source: SourceObject = new SourceObject('jack', 18, false);
let g_object: distributedDataObject.DistributedObject = distributedDataObject.createDistributedObject(source);
```
