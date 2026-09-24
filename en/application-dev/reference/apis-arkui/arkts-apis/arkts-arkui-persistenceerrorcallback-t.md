# PersistenceErrorCallback

```TypeScript
export declare type PersistenceErrorCallback = (key: string, reason: 'quota' | 'serialization' | 'unknown', 
    message: string, oldValue?: string) => void
```

Defines a callback used to return the cause of the persistence failure.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the error. |
| reason | 'quota' &#124; 'serialization' &#124; 'unknown' | Yes | Reason of the error. |
| message | string | Yes | Extra information about the error. |
| oldValue | string | No | Old serialized data stored on the disk when deserialization fails. |

**Examples**

```TypeScript
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace id: number = 0;
  count: number = 10;
}

@ObservedV2
export class Sample {
  // For complex objects, use the @Type decorator to ensure successful serialization.
  @Type(SampleChild)
  @Trace sampleChild: SampleChild = new SampleChild();
}

// Callback used to receive persistence errors.
// PersistenceErrorCallback refers to (key: string, reason: string, msg: string, oldValue?: string) => {console.error(`error key: ${key}, reason: ${reason}, message: ${msg}, oldValue: ${oldValue}`);}.
PersistenceV2.notifyOnError((key: string, reason: string, msg: string, oldValue?: string) => {
  console.error(`error key: ${key}, reason: ${reason}, message: ${msg}, oldValue: ${oldValue}`);
});

@Entry
@ComponentV2
struct Index {
  // Create a KV pair whose key is Sample in PersistenceV2 (if the key exists, the data in PersistenceV2 is returned) and associate it with data.
  // Add @Local to decorate the data attribute that needs to change the connected object. (Changing the connected object is not recommended.)
  @Local data: Sample = PersistenceV2.connect(Sample, () => new Sample())!;

  build() {
    Text(`Index add 1 to data.id: ${this.data.sampleChild.id}`)
      .fontSize(30)
      .onClick(() => {
        this.data.sampleChild.id++;
      })
  }
}
```
