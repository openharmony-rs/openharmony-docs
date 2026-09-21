# TypeDecorator

```TypeScript
export declare type TypeDecorator = <T>(type: TypeConstructor<T>) => PropertyDecorator
```

Defines the attribute decorator, which is used to decorate attributes of the custom class in a nested class.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [TypeConstructor](arkts-arkui-arkui-statemanagement-typeconstructor-i.md)&lt;T&gt; | Yes | Type of the class property. |

**Return value:**

| Type | Description |
| --- | --- |
| [PropertyDecorator](../../apis-default/arkts-apis/arkts-propertydecorator-t.md) | Property decorator. |

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
  // TypeDecorator refers to @Type.
  @Type(SampleChild)
  @Trace sampleChild: SampleChild = new SampleChild();
}

@Entry
@ComponentV2
struct Index {
  data: Sample = PersistenceV2.connect(Sample, () => new Sample())!;

  build() {
    Column() {
      Text(`Index add 1 to data.id: ${this.data.sampleChild.id}`)
        .fontSize(30)
        .onClick(() => {
          this.data.sampleChild.id++;
        })
    }
  }
}
```

When @Type is used to decorate attributes of a nested class, only the custom class type is supported. If other class types are transferred, the persistence will fail.

```TypeScript
@ObservedV2
class SampleChild {
  @Trace id: number = 0;
  count: number = 10;
}

@ObservedV2
class Sample {
  // Recommended method: Decorate the sampleChild attribute of the custom Sample class, whose type is SampleChild.
  @Type(SampleChild)
  @Trace sampleChild: SampleChild = new SampleChild();

  // Not recommended. The type of the nested class of the decorated attributes is Array<number>.
  @Type(Array<number>)
  @Trace value: Array<Array<number>> = new Array();
}
```
