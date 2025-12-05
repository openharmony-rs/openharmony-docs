# @Type

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 12开始，支持该装饰器。

@Type装饰类属性，用于状态管理V1中，可以实现序列化类时不丢失属性的复杂类型。

在ArkTS-Dyn中使用时，开发指南参考：[@Type装饰器：标记类属性的类型（ArkTS-Dyn）](../../../ui/state-management/arkts-new-type.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型               | 必填 | 说明               |
| ------ | ------------------ | ---- | ------------------ |
| type   | [TypeConstructor<T>](../js-apis-stateManagement.md#typeconstructort) | 是   | 标记类属性的类型。 |

**示例：**

```ts
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace childNumber: number = 1;
}

@ObservedV2
class Sample {
  @Type(SampleChild)
  @Trace sampleChild?: SampleChild = undefined;
}

@Entry
@ComponentV2
struct Index {
  @Local sample: Sample = PersistenceV2.connect(Sample, () => new Sample)!;

  build() {
    Column() {
      Text('childNumber value:' + this.sample.sampleChild?.childNumber)
        .onClick(() => {
          this.sample.sampleChild = new SampleChild();
          this.sample.sampleChild.childNumber = 2;
          PersistenceV2.save(Sample);
        })
        .fontSize(30)
    }
  }
}
```

