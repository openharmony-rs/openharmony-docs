# TypeDecorator

```TypeScript
export declare type TypeDecorator = <T>(type: TypeConstructor<T>) => PropertyDecorator
```

属性装饰器，用于装饰嵌套类中属于自定义class类的属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [TypeConstructor](arkts-arkui-arkui-statemanagement-typeconstructor-i.md)&lt;T&gt; | 是 | 标记类属性的类型，仅支持自定义class类型，传入其他类型会导致持久化失败。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PropertyDecorator | 属性装饰器，用于装饰嵌套类中属于自定义class类的属性。 |

**示例**

```TypeScript
import { PersistenceV2, Type } from '@kit.ArkUI';

@ObservedV2
class SampleChild {
  @Trace id: number = 0;
  count: number = 10;
}

@ObservedV2
export class Sample {
  // 对于复杂对象需要@Type修饰，确保序列化成功
  // TypeDecorator 指的是 @Type
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

在使用@Type装饰嵌套类属性时，仅支持自定义class类型，传入其他类型会持久化失败。

```TypeScript
@ObservedV2
class SampleChild {
  @Trace id: number = 0;
  count: number = 10;
}

@ObservedV2
class Sample {
  // 建议用法，装饰自定义Sample类中的sampleChild属性，其类型为SampleChild类型
  @Type(SampleChild)
  @Trace sampleChild: SampleChild = new SampleChild();

  // 不建议用法，装饰的嵌套类属性类型是Array<number>
  @Type(Array<number>)
  @Trace value: Array<Array<number>> = new Array();
}
```
