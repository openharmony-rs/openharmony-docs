# Sendable对象改造实践
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

## 简介

本文介绍AI for Sendable skills，`@hadss/turbo-trans-json`（下文简称 **turbotransJSON**）与`@hadss/turbo-trans-protobuf`（下文简称 **turbotransProtobuf**）在ArkTS中操作Sendable对象的典型用法：

- 使用**turbotransJSON**将JSON字符串反序列化为对象，并转换为**Sendable 对象**在并发实例间传递。
- 使用**turbotransProtobuf**通过`.proto`生成**@Sendable**的消息类，并进行编码/解码。
- 将ArkTS中的非共享类型改造为Sendable共享类型，使其可以跨线程传递。

### 总体思路

建议按以下顺序阅读本文：

- 如果关注普通对象如何转换为Sendable对象，可先阅读[使用turbotransJSON序列化/反序列化并生成 Sendable 对象](#使用turbotransjson序列化反序列化并生成-sendable-对象)。
- 如果关注消息对象的生成与编解码，可先阅读[使用turbotransProtobuf生成 Sendable 对象并编解码](#使用turbotransprotobuf生成-sendable-对象并编解码)。
- 如果关注AI SKILL将ArkTS类改造为Sendable类型，可先阅读[使用AI将ArkTS类改造为Sendable对象](#使用ai将arkts类改造为sendable对象)。
- 三条路径得到的Sendable结果，都可以继续进入后文[使用makeObserved将 Sendable 对象转换成可观察对象](#使用makeobserved将-sendable-对象转换成可观察对象)章节，通过并发任务返回并绑定到 UI。

## 使用TurboTrans三方库操作Sendable对象指南

#### turbotransJSON：普通对象 ⇄ Sendable对象

1. 用`@Serializable({ generateSendable: true })`声明模型，并用`@SerialName`映射字段名。
2. 使用`TJSON.fromString<Model>(jsonStr, Model)`从JSON字符串反序列化为**普通对象**。
3. 对普通对象调用`toSendable()`，得到对应的**Sendable 对象**。
4. 如有需要，可继续通过`toOrigin()`还原为普通对象。
5. 可用`ArkTSUtils.isSendable(obj)`进行校验。

#### turbotransProtobuf：从proto生成Sendable消息类

1. 编写`.proto`原型文件。
2. 构建时生成相应的消息类，其中消息类会带`@Sendable`（可直接跨并发实例引用传递）。
3. 使用生成类提供的`encode/decode`完成二进制序列化/反序列化。
4. 解码得到的消息对象仍可继续作为Sendable对象向后传递。

### 使用turbotransJSON序列化/反序列化并生成Sendable对象

#### 定义可序列化模型（开启Sendable生成）

在工程中，自定义`Layout`模型如下（位置：`entry/src/main/ets/turbotrans_JSON/layout.ets`）：

<!-- @[tranferabledObject_Layout ](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/turbotrans_JSON/layout.ets) -->

``` TypeScript
import { Serializable, SerialName } from '@hadss/turbo-trans-core';
// ...

@Serializable({ generateSendable: true})
export class Layout {
  @SerialName({ name: 'type'})
  public type: string = '';
  @SerialName({ name: 'arr'})
  public arr: number[] = [];
}
```

其中：

- `@Serializable({ generateSendable: true })`：表示需要生成与该模型对应的Sendable类型与转换方法。
- `@SerialName({ name: 'xxx' })`：将类属性与JSON字段名绑定。

本文涉及的几个类型在JSON路径中的角色如下：

- `Layout`：普通模型，用于接收JSON反序列化结果。
- `LayoutS`：示例工程中在业务侧直接使用的Sendable类型。
- `SendableLayout`：构建生成的Sendable类型实现，用于展示`toSendable()`/`toOrigin()`的转换落点。

#### 从JSON字符串反序列化为普通对象（TJSON.fromString）

工程示例（位置：`entry/src/main/ets/turbotrans_JSON/test1.ets`）演示了两种输入来源，并在反序列化后继续将普通对象转换为Sendable对象，形成“JSON 字符串 -> `Layout` -> Sendable 对象”的前半段链路：

- 对象`JSON.stringify()`得到的字符串。
- 手写JSON字符串。

  <!-- @[tranferabledObject_testJSON ](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/turbotrans_JSON/test1.ets) -->
  
  ``` TypeScript
  import { TJSON } from '@hadss/turbo-trans-json';
  import { Layout, LayoutS } from 'entry/ets/turbotrans_JSON/layout'
  import { ArkTSUtils } from '@kit.ArkTS';
  
  export function testJSON1(): LayoutS {
    let obj = new Layout();
    obj.type = 'Test';
    obj.arr = [3, 4];
    let str = JSON.stringify(obj);
    let layoutNormal = TJSON.fromString<Layout>(str, Layout);
    console.info('111 layout arr: ' + layoutNormal.arr);
    let layoutS = layoutNormal.toSendable() as LayoutS;
    if (ArkTSUtils.isSendable(layoutS)) {
      console.info('expect layout from JSON string is Sendable');
    } else {
      console.error('test occur error');
    }
    return layoutS;
  }
  
  export function testJSON2(): LayoutS {
    let layoutStr = '{"type":"Text","arr":[3,4],}';
    let layoutNormal = TJSON.fromString<Layout>(layoutStr, Layout);
    console.info('222 layout arr: ' + layoutNormal.arr);
    let layoutS = layoutNormal.toSendable() as LayoutS;
    if (ArkTSUtils.isSendable(layoutS)) {
      console.info('expect layout from simple string is Sendable');
    } else {
      console.error('test occur error');
    }
    return layoutS;
  }
  
  export function testJSON() {
    testJSON1();
    testJSON2();
  }
  ```

#### 将普通对象转换为Sendable对象（toSendable）

当`generateSendable: true`生效后，构建产物中会生成`toSendable()`，将普通对象转换为Sendable对象（位置：`entry/src/generated/ets/turbotrans_JSON/layout.ets`）。其关键点在于会做必要的容器转换，例如把`number[]`转换为`collections.Array<number>`：

<!-- @[tranferabledObject_SendableLayout ](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/generated/ets/turbotrans_JSON/layout.ets) -->

```ts
toSendable(): SendableLayout {
  const sendable = new SendableLayout();

  // 非构造函数属性赋值
  sendable.type = this.type;
  sendable.arr = new collections.Array(...this.arr);

  return sendable;
}
```

同时，生成的Sendable类型（位置：`entry/src/generated/ets/sendableModel/SendableLayout.ets`）通常会提供 `toOrigin()`，用于在需要继续按普通对象处理、复用原有逻辑或重新序列化时，将Sendable对象还原出普通对象：

<!-- @[tranferabledObject_SendableLayout_toOrigin ](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/generated/ets/sendableModel/SendableLayout.ets) -->

``` TypeScript
@Sendable
export class SendableLayout implements lang.ISendable {
  public type: string = '';
  public arr: collections.Array<number> = new collections.Array();

  toOrigin(): Layout {
    const origin = new Layout();
    origin.type = this.type;
    origin.arr = new Array(...this.arr);
    return origin;
  }
```

这样，JSON路径就形成了完整闭环：

`JSON 字符串` -> `TJSON.fromString()` -> 普通对象 `Layout` -> `toSendable()` -> Sendable 对象 `LayoutS/SendableLayout` -> `toOrigin()` -> 普通对象 `Layout`。

### 使用turbotransProtobuf生成Sendable对象并编解码

> **说明：**
>
> 此章节暂无sample仓示例代码。

#### 编写proto文件

工程中 `.proto` 位于 `entry/protobuf/test_pb.proto`：

```proto
syntax = "proto3";

message test_pb {
    int32 value_int32 = 1;
    int64 value_int64 = 2;
    uint32 value_uint32 = 3;
    uint64 value_uint64 = 4;
    sint32 value_sint32 = 5;
    sint64 value_sint64 = 6;
    fixed32 value_fixed32 = 7;
    fixed64 value_fixed64 = 8;
    sfixed32 value_sfixed32 = 9;
    sfixed64 value_sfixed64 = 10;
    float value_float = 11;
    double value_double = 12;
    bool value_bool = 13;
    string value_string = 14;
    bytes value_bytes = 15;
}
```

#### 生成的消息类可直接参与Sendable传输与编解码

构建后会生成ArkTS文件 `entry/src/main/ets/protobuf/test_pb.ets`。生成的`test_pb`类 `@Sendable`，因此既可以作为消息对象进行编解码，也可以直接作为Sendable对象跨并发实例传递。围绕同一个`test_pb`类型，示例中的数据流如下：

- `test_pb.create()`：创建实例。
- `test_pb.encode(message)`：将实例编码为`ArrayBuffer`。
- `test_pb.decode(buffer)`：将二进制数据解码回`test_pb`。

也就是说，Protobuf路径不是“生成类后只做一次编码”，而是：

`test_pb.create()`创建 Sendable 消息对象 -> `encode()` 编码为`ArrayBuffer` -> `decode()`解码回`test_pb` -> 解码后的结果仍然可以作为Sendable对象继续传递或绑定到后续UI。

#### 创建Sendable消息对象、编码、解码

工程示例（位置：`entry/src/main/ets/turbotrans_protobuf/test1.ets`）如下。示例先创建`test_pb`实例，再编码为二进制，最后解码回`test_pb`并校验其仍为Sendable：

```ts
import { test_pb } from '../protobuf/test_pb'
import { ArkTSUtils, collections } from '@kit.ArkTS';

function testCreate() {
  const obj = test_pb.create();
  obj.value_int32 = 1;
  obj.value_int64 = 2;
  obj.value_uint32 = 3;
  obj.value_uint64 = 4;
  obj.value_sint32 = 5;
  obj.value_sint64 = 6;
  obj.value_fixed32 = 7;
  obj.value_fixed64 = 8;
  obj.value_sfixed32 = 9;
  obj.value_sfixed64 = 10;
  obj.value_float = 11;
  obj.value_double = 12;
  obj.value_bool = true;
  obj.value_string = "TestProtobuf_Success";
  obj.value_bytes?.fill(13);

  if (ArkTSUtils.isSendable(obj)) {
    console.info("create a sendable object");
  }

  return obj;
}

function testencode(obj: test_pb) {
  return test_pb.encode(obj);
}

function testdecode(data: ArrayBuffer | collections.ArrayBuffer) {
  let obj = test_pb.decode(data);
  console.info("expect value_int32 " + obj?.value_int32 + " = 1");
  console.info("expect value_double " + obj?.value_double + " = 12");
  if (ArkTSUtils.isSendable(obj)) {
    console.info("decode a sendable object");
  }
}

export function testProtobuf() {
  let obj = testCreate();
  let buf = testencode(obj);
  if (buf) {
    testdecode(buf);
  }
}
```

`test_pb`经过编解码后仍然保留Sendabl 特性，因此也可以像JSON路径生成的Sendable对象一样，继续作为并发任务的返回值进入UI绑定流程。

## 使用AI将ArkTS类改造为Sendable对象

使用AI将ArkTS类改造为Sendable对象，请阅读[ArkTS Sendable 改造技能完整使用指南](https://gitcode.com/openharmony-skills/arkts-sendable-transformer/blob/master/Wiki.md)。

## 使用makeObserved将Sendable对象转换成可观察对象

### 创建UI组件实时观察Sendable对象属性变化

`Index.ets` 中通过 `@Local` 状态保存任务返回值，再由 `Text` 组件绑定 `pb.value_string` 和 `layout.type`。其中，`pb` 存储的是 `observeProtobuf` 返回的 Sendable 对象（`test_pb` 类型），`layout` 存储的是 `observeJSON1` 返回的 Sendable 对象（`LayoutS` 类型）。

工程示例（位置：`entry/src/main/ets/pages/Index.ets`）如下：

<!-- @[tranferabledObject_Text ](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/pages/Index.ets) -->

```ts
@Entry
@ComponentV2
struct Index {
  @Local layout: LayoutS = new LayoutS();
  @Local pb: test_pb = test_pb.create();

  build() {
    Column() {
      Button('运行TaskPool测试')
        .onClick(() => {
          this.runTests();
        })

      Scroll() {
        Column() {
          Text(`TestProtobuf: ${this.pb.value_string}`)
            .fontSize(14)
            .textAlign(TextAlign.Start)
            .backgroundColor(Color.White)
            .padding(10)
            .borderRadius(8)
            .margin({ bottom: 10 })
            .width('100%')

          Text(this.layout.type)
            .fontSize(14)
            .textAlign(TextAlign.Start)
            .backgroundColor(Color.White)
            .padding(10)
            .borderRadius(8)
            .margin({ bottom: 10 })
            .width('100%')
        }
        .width('100%')
        .padding(10)
      }
      .height('60%')
      .width('100%')
    }
    .height('100%')
    .width('100%')
  }
}
```

### 通过taskpool执行异步任务并将Sendable对象转换为可观察对象

`runTests()`中通过`taskpool.execute()`执行并发任务，拿到返回的Sendable对象后，再用`UIUtils.makeObserved()`包装为可观察对象并写回 UI 状态。这样数据链路就变成了“并发任务返回 -> 转换为可观察对象 -> 组件自动刷新”。

同一个`Index`页面中的任务执行代码如下：

<!-- @[tranferabledObject_makeObserved ](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/TurboTrans/entry/src/main/ets/pages/Index.ets) -->

```ts
runTests() {
  taskpool.execute(observeProtobuf).then((res: test_pb) => {
    this.pb = UIUtils.makeObserved(res)
  })
  taskpool.execute(observeJSON1).then((res) => {
    this.layout = UIUtils.makeObserved(res as LayoutS)
  })
}
```

### 小结

- 使用`taskpool.execute()`获取并发任务返回的Sendable对象，再通`UIUtils.makeObserved()`转为可观察对象。
- 当可观察对象的属性发生变化时，绑定的UI组件会自动刷新显示。