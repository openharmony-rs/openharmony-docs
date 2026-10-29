# @ohos.arkui.placeholderRegister (滚动占位注册) (ArkTS-Sta)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @wind_-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

本模块提供滚动占位模板的注册、注销和查询能力。快速滚动场景下，当框架预测在剩余帧预算内创建下一个列表项会导致超帧时，可滚动组件（如[List](arkui-ts/ts-container-list.md)）会先为该项显示占位组件，真实列表项在UI线程分帧创建完成后替换占位，以减少丢帧。占位模板经[register](#register)注册后，供[List](arkui-ts/ts-container-list.md)的[scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder)属性按id引用。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块接口仅可在Stage模型下使用。

**起始版本：** 26.1.0

## 导入模块

```ts
import { PlaceholderRegister } from '@kit.ArkUI';
```

## PlaceholderRegister

滚动占位模板的注册表，提供占位模板的注册、注销和查询能力。每个UI实例持有独立的注册表，在一个UI实例中注册的占位模板对其他UI实例不可见。请不要自行构造PlaceholderRegister实例，应通过[getPlaceholderRegister()](./arkts-apis-uicontext-uicontext.md#getplaceholderregister)获取当前UI实例的注册表。

> **说明：**
>
> 以下API需先使用UIContext中的[getPlaceholderRegister()](./arkts-apis-uicontext-uicontext.md#getplaceholderregister)方法获取到PlaceholderRegister对象，再通过该对象调用对应方法。

**起始版本：** 26.1.0

### register

register(id: string, builder: WrappedBuilder\<CustomBuilder\>): void

注册滚动占位模板，将占位builder绑定到指定id，供可滚动组件的[scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder)属性按id引用。

> **说明：**
>
> - 占位模板须为全局、无参的`@Builder({ isPlaceholder: true })`函数，且只做只读静态渲染：不得访问响应式状态，不得注册手势，不得注册业务回调。传入的builder须经过[wrapBuilder](arkui-ts/ts-universal-wrapBuilder-static.md#wrapbuilder)包装，不接受裸builder函数。
>
> - 框架在注册时校验编译产物中携带的受限Builder标记：未在编译期标记`@Builder({ isPlaceholder: true })`的builder（包括通过绕过编译期类型检查的动态方式传入的builder）会被拒绝注册，该id不会注册成功，[scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder)的provider命中该id时使用系统默认占位。
>
> - 重复注册相同id时，会原子地发布新版本的模板；已派发的占位任务在上屏前会先与模板版本做校验。

**ArkTS-Sta起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                 | 必填 | 说明                                       |
| ------- | -------------------- | ---- | ------------------------------------------ |
| id      | string               | 是   | 占位模板的id，[scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder)的[PlaceholderProvider](#placeholderprovider)通过该id引用模板。 |
| builder | [WrappedBuilder](arkui-ts/ts-universal-wrapBuilder-static.md#wrappedbuilder)\<CustomBuilder\> | 是   | 经[wrapBuilder](arkui-ts/ts-universal-wrapBuilder-static.md#wrapbuilder)包装后的全局无参占位builder，不接受裸builder函数。 |

**错误码：**

以下错误码的详细介绍请参见[滚动类组件错误码](./errorcode-scroll.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 100031   | Registration rejected: the builder is not marked with @Builder({ isPlaceholder: true }). The ID is not registered. |

**示例：**

完整示例请参考[示例1（注册滚动占位模板并设置滚动占位）](#示例1注册滚动占位模板并设置滚动占位)。

### unregister

unregister(id: string): void

注销当前UI实例下指定id的占位模板。

> **说明：**
>
> - 模板注销后，该id不再能被匹配：[scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder)的[PlaceholderProvider](#placeholderprovider)命中该id时使用系统默认占位，已为该模板派发的占位任务不会上屏。
>
> - 注销未注册的id时，静默处理，不产生异常。

**ArkTS-Sta起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                             |
| ------ | ------ | ---- | -------------------------------- |
| id     | string | 是   | 需要注销的占位模板的id。           |

**示例：**

完整示例请参考[示例1（注册滚动占位模板并设置滚动占位）](#示例1注册滚动占位模板并设置滚动占位)。

### isRegistered

isRegistered(id: string): boolean

查询当前UI实例下是否已注册指定id的占位模板。

> **说明：**
>
> 该接口为只读查询，不改变注册状态，也不影响后续占位行为。无论框架当前是否为该模板保留预构建的占位实例，模板的注册状态均保持不变。

**ArkTS-Sta起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                             |
| ------ | ------ | ---- | -------------------------------- |
| id     | string | 是   | 需要查询的占位模板的id。           |

**返回值：**

| 类型    | 说明                                                    |
| ------- | ------------------------------------------------------- |
| boolean | 返回当前UI实例下是否已注册指定id的占位模板。true表示已注册，false表示未注册。 |

**示例：**

完整示例请参考[示例1（注册滚动占位模板并设置滚动占位）](#示例1注册滚动占位模板并设置滚动占位)。

## PlaceholderOptions

描述滚动组件单个列表项的占位信息。真实列表项需要分帧创建时，可滚动组件会先显示该项的占位组件。

**ArkTS-Sta起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型                                       | 只读 | 可选 | 说明                                       |
| ------ | ------------------------------------------ | ---- | ---- | ------------------------------------------ |
| id     | string                                     | 否   | 是   | 占位模板的id。注册表通过UIContext的[getPlaceholderRegister()](./arkts-apis-uicontext-uicontext.md#getplaceholderregister)获取，占位builder通过其[register](#register)方法注册。<br/>未设置、设置为空字符串或未注册时，使用系统默认占位。<br/>默认值：undefined |
| size   | [SizeOptions](arkui-ts/ts-types.md#sizeoptions) | 否   | 是   | 占位的建议尺寸，仅影响占位组件的测量，不影响真实列表项的布局。真实列表项创建完成后会按列表项的正常布局约束重新布局，建议尺寸越接近真实列表项的尺寸，替换时的视觉跳动越小。<br/>默认值：undefined。未设置时，不指定建议尺寸，占位组件按组件自身的估算尺寸测量。 |

## PlaceholderProvider

type PlaceholderProvider = (index: int) => PlaceholderOptions | undefined

列表项占位信息的提供函数，供[List](arkui-ts/ts-container-list.md)的[scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder)属性使用。该函数在UI线程滚动过程中同步调用，须为纯计算，不得执行耗时操作。

**ArkTS-Sta起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                       |
| ------ | ------ | ---- | ------------------------------------------ |
| index  | int    | 是   | 即将创建的列表项的索引。<br/>取值范围：[0, +∞)。                     |

**返回值：**

| 类型    | 说明                                       |
| ------- | ------------------------------------------ |
| [PlaceholderOptions](#placeholderoptions) \| undefined | 返回该项的占位信息。返回undefined表示该列表项不需要占位，使用系统默认占位，滚动不中断。 |

## 示例

### 示例1（注册滚动占位模板并设置滚动占位）

该示例通过[register](#register)接口注册占位模板，通过[isRegistered](#isregistered)接口查询注册状态，通过[unregister](#unregister)接口在组件销毁时注销占位模板，并通过[List](arkui-ts/ts-container-list.md)的[scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder)属性设置占位提供者：快速滚动时，帧预算不足的列表项先显示已注册的占位模板，真实列表项分帧创建完成后替换占位，减少丢帧。

从API版本26.1.0开始，新增register、unregister、isRegistered接口及PlaceholderOptions、PlaceholderProvider类型。

<!--code_no_check-->
```ts
// xxx.ets
'use static'
import { Entry, Component, Column, Text, List, ListItem, LazyForEach, IDataSource, DataChangeListener,
  Builder, wrapBuilder, PlaceholderOptions, FlexAlign, TextAlign } from '@kit.ArkUI';

// 占位模板须为全局、无参、只读静态渲染的受限Builder
@Builder({ isPlaceholder: true })
function ItemPlaceholder() {
  Column() {
    Text('加载中...')
      .fontSize(16)
      .fontColor(0x999999)
  }
  .width('100%')
  .height(100)
  .justifyContent(FlexAlign.Center)
}

class ListDataSource implements IDataSource<number> {
  private list: Array<number> = [];

  constructor(list: Array<number>) {
    this.list = list;
  }

  totalCount(): int {
    return this.list.length;
  }

  getData(index: int): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
struct PlaceholderRegisterExample {
  private arr: ListDataSource = new ListDataSource([]);

  aboutToAppear() {
    // 通过UIContext获取当前UI实例的占位注册表，注册结果对其他UI实例不可见
    let placeholderRegister = this.getUIContext().getPlaceholderRegister();
    // 查询该id是否已注册，未注册时注册占位模板，builder经wrapBuilder包装后传入
    if (!placeholderRegister.isRegistered('itemPlaceholder')) {
      placeholderRegister.register('itemPlaceholder', wrapBuilder(ItemPlaceholder));
    }
    let list: Array<number> = [];
    for (let i = 0; i < 100; i++) {
      list.push(i);
    }
    this.arr = new ListDataSource(list);
  }

  aboutToDisappear() {
    this.getUIContext().getPlaceholderRegister().unregister('itemPlaceholder');
  }

  build() {
    Column({ space: 5 }) {
      List({ space: 10 }) {
        LazyForEach(this.arr, (item: number, index: int) => {
          ListItem() {
            Text(item.toString())
              .fontSize(16)
              .width('100%')
              .height(100)
              .textAlign(TextAlign.Center)
          }
        }, (item: number, index: int) => item.toString())
      }
      .width('90%')
      .height(300)
      // id对应已注册的占位模板，size为占位的建议尺寸，与真实列表项高度一致
      .scrollPlaceholder((index: int): PlaceholderOptions | undefined => {
        return { id: 'itemPlaceholder', size: { height: 100 } };
      })
    }.width('100%').padding({ top: 10 }).backgroundColor('#FFDCDCDC')
  }
}
```
