# \@Type装饰器：标记类属性的类型
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zzq212050299-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

为了实现序列化类时不丢失属性的复杂类型，开发者可以使用\@Type装饰器装饰类属性。

\@Type的目的是标记类属性，配合PersistenceV2使用，防止序列化时类丢失。在阅读本文档前，建议提前阅读：[PersistenceV2](./arkts-new-persistencev2.md)。

>**说明：**
>
>\@Type从API version 12开始支持。
>

## 概述

\@Type标记类属性，使得类属性序列化时不丢失类型信息，便于类的反序列化。

## 装饰器说明

| \@Type装饰器 | 说明 |
| ------------------- | ------------------------------------------------------------ |
| 装饰器参数 | type：类型。 |
| 可装饰的类型 | Object class以及Array、Date、Map、Set等内嵌类型。 |

## 使用限制

1. 只能用在[\@ObservedV2](./arkts-new-observedV2-and-trace.md)装饰的类中，不能用在自定义组件中。

    ```ts
    class Sample {
      data: number = 0;
    }
    @ObservedV2
    class Info {
      @Type(Sample)
      @Trace sample: Sample = new Sample(); // 正确用法
    }
    @Observed
    class Info2 {
      @Type(Sample)
      sample: Sample = new Sample(); // 错误用法，不能用在@Observed装饰的类中，编译时报错
    }
    @ComponentV2
    struct Index {
      @Type(Sample)
      sample: Sample = new Sample(); // 错误用法，不能用在自定义组件中
      build() {
      }
    }
    ```

2. 不支持collections.Set、collections.Map等类型。

3. 不支持非buildin类型。如PixelMap、NativePointer、ArrayList等Native类型。

4. 不支持简单类型。如string、number、boolean等。

5. 不支持构造函数含参的类。

## 使用场景

### 持久化数据

```ts
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace childNumber: number = 1;
}

@ObservedV2
class Sample {
  // 对于复杂对象需要@Type修饰，确保反序列化成功，去掉@Type会反序列化值失败。
  @Type(SampleChild)
  // 对于没有初值的类属性，经过@Type修饰后，需要手动保存，否则持久化失败。
  // 无法使用@Type修饰的类属性，必须要有初值才能持久化。
  @Trace sampleChild?: SampleChild = undefined;
}

@Entry
@ComponentV2
struct TestCase {
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
