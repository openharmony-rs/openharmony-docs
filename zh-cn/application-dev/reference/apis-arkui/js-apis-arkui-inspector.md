# @ohos.arkui.inspector (布局回调)

提供注册组件布局和组件绘制送显完成回调通知的能力。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 导入模块

<!--deprecated_code_no_check-->
```ts
import { inspector } from '@kit.ArkUI';
```

## inspector.createComponentObserver<sup>(deprecated)</sup>

createComponentObserver(id: string): ComponentObserver

绑定指定组件，返回对应的监听句柄。

> **说明：**
> 
> 从API version 18开始废弃，建议使用[UIContext](js-apis-arkui-UIContext.md#uicontext)中的[getUIInspector](js-apis-arkui-UIContext.md#getuiinspector)获取[UIInspector](js-apis-arkui-UIContext.md#uiinspector)实例，再通过此实例调用替代方法[createComponentObserver](js-apis-arkui-UIContext.md#createcomponentobserver)。
>
> 从API version 10开始，可以通过使用[UIContext](js-apis-arkui-UIContext.md#uicontext)中的[getUIInspector](js-apis-arkui-UIContext.md#getuiinspector)方法获取当前UI上下文关联的[UIInspector](js-apis-arkui-UIContext.md#uiinspector)对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| id     | string | 是   | 指定组件id，该id通过通用属性[id](./arkui-ts/ts-universal-attributes-component-id.md#id)或者[key](./arkui-ts/ts-universal-attributes-component-id.md#key12)设置。 |

**返回值：** 

| 类型              | 说明                                             |
| ----------------- | ------------------------------------------------ |
|[ComponentObserver](#componentobserver)| 组件回调事件监听句柄，用于注册和取消注册监听回调。 |

**示例：** 

```ts
let listener:inspector.ComponentObserver = inspector.createComponentObserver('COMPONENT_ID'); //监听id为COMPONENT_ID的组件回调事件
```

## ComponentObserver

组件布局和组件绘制送显完成回调的句柄，包含了申请句柄时的首次查询结果。

> **说明：**
>
> 该接口不支持设置空值、null/undefined以及其他非法值。若输入非法值会导致编译报错。

### on('layout')

ArkTS-Dyn: on(type: 'layout', callback: () => void): void

通过句柄向对应的查询条件注册回调，当组件布局完成时会触发该回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[onLayout<sup>23+</sup>](#onlayout23)。

**ArkTS-Dyn起始版本：** 10

**参数：** 

| 参数名   | 类型   | 必填 | 说明|
| -------- | ------ | ---- | -------------------------------------|
| type     | string | 是   | 必须填写字符串'layout'。<br>layout: 组件布局完成。|
| callback | () => void  | 是   | 监听layout的回调。|

### onLayout<sup>23+</sup>

onLayout(callback: VoidCallback): void

通过句柄向对应的查询条件注册回调，当组件布局完成时会触发该回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[on('layout')](#onlayout)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名   | 类型   | 必填 | 说明|
| -------- | ------ | ---- | -------------------------------------|
| callback | [VoidCallback](arkui-ts/ts-types.md#voidcallback12)  | 是   | 监听layout的回调。|

### off('layout')

ArkTS-Dyn: off(type: 'layout', callback?: () => void): void

通过句柄向对应的查询条件取消注册回调，当组件布局完成时不再触发指定的回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[offLayout<sup>23+</sup>](#offlayout23)。

**ArkTS-Dyn起始版本：** 10

**参数：** 

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ------ | ---- | -------------------------------------------- |
| type     | string | 是   | 必须填写字符串'layout'。<br>layout: 组件布局完成。|
| callback | () => void  | 否   | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和[on('layout')](#onlayout)方法中的callback为相同对象时才能取消回调成功。|

### offLayout<sup>23+</sup>

offLayout(callback?: VoidCallback): void

通过句柄向对应的查询条件取消注册回调，当组件布局完成时不再触发指定的回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[off('layout')](#offlayout)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ------ | ---- | -------------------------------------------- |
| callback | [VoidCallback](arkui-ts/ts-types.md#voidcallback12)  | 否   | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和[onLayout](#onlayout23)方法中的callback为相同对象时才能取消回调成功。|

### on('draw')

ArkTS-Dyn: on(type: 'draw', callback: () => void): void

通过句柄向对应的查询条件注册回调，当组件绘制送显完成时会触发该回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[onDraw<sup>23+</sup>](#ondraw23)。

**ArkTS-Dyn起始版本：** 10

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 必须填写字符串'draw'。<br>draw: 组件绘制送显完成。|
| callback | () => void  | 是   | 监听draw的回调。                                     |

### onDraw<sup>23+</sup>

onDraw(callback: VoidCallback): void

通过句柄向对应的查询条件注册回调，当组件绘制送显完成时会触发该回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[on('draw')](#ondraw)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [VoidCallback](arkui-ts/ts-types.md#voidcallback12)  | 是   | 监听draw的回调。                                     |

### off('draw')

ArkTS-Dyn: off(type: 'draw', callback?: () => void): void

通过句柄向对应的查询条件取消注册回调，当组件绘制送显完成时不再触发指定的回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[offDraw<sup>23+</sup>](#offdraw23)。

**ArkTS-Dyn起始版本：** 10

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 必须填写字符串'draw'。<br>draw: 组件绘制送显完成。|
| callback | () => void   | 否   | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和[on('draw')](#ondraw)方法中的callback为相同对象时才能取消回调成功。 |

### offDraw<sup>23+</sup>

offDraw(callback?: VoidCallback): void

通过句柄向对应的查询条件取消注册回调，当组件绘制送显完成时不再触发指定的回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[off('draw')](#offdraw)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [VoidCallback](arkui-ts/ts-types.md#voidcallback12)   | 否   | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和[onDraw](#ondraw23)方法中的callback为相同对象时才能取消回调成功。 |

### on('drawChildren')<sup>20+</sup>

ArkTS-Dyn: on(type: 'drawChildren', callback: Callback\<void\>): void

通过[ComponentObserver](#componentobserver)注册drawChildren事件回调方法，当组件的子组件绘制送显完成时会触发该回调方法。如果组件树中存在多个drawChildren事件回调，只会触发在最顶层的drawChildren事件回调。取消最顶层的回调后，其余drawChildren事件回调也无法生效。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[onDrawChildren<sup>23+</sup>](#ondrawchildren23)。

**ArkTS-Dyn起始版本：** 20

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 必须填写字符串'drawChildren'。<br>drawChildren: 子组件绘制送显完成。|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)\<void>  | 是   | 监听drawChildren的回调。                                     |

### onDrawChildren<sup>23+</sup>

onDrawChildren(callback: VoidCallback): void

通过[ComponentObserver](#componentobserver)注册drawChildren事件回调方法，当组件的子组件绘制送显完成时会触发该回调方法。如果组件树中存在多个drawChildren事件回调，只会触发在最顶层的drawChildren事件回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[on('drawChildren')](#ondrawchildren20)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [VoidCallback](arkui-ts/ts-types.md#voidcallback12)  | 是   | 监听drawChildren的回调。                                     |

### off('drawChildren')<sup>20+</sup>

ArkTS-Dyn: off(type: 'drawChildren', callback?: Callback\<void\>): void

通过句柄向对应的查询条件取消注册回调，当组件绘制送显完成时不再触发指定的回调。

**原子化服务API：** 从API version 20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta的接口是[offDrawChildren<sup>23+</sup>](#offdrawchildren23)。

**ArkTS-Dyn起始版本：** 20

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 必须填写字符串'drawChildren'。<br>drawChildren: 子组件绘制送显完成。|
| callback | [Callback](../apis-basic-services-kit/js-apis-base.md#callback)\<void>   | 否   | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和[on('drawChildren')](#ondrawchildren20)方法中的callback为相同对象时才能取消回调成功。 |

### offDrawChildren<sup>23+</sup>

offDrawChildren(callback?: VoidCallback): void

通过句柄向对应的查询条件取消注册回调，当组件绘制送显完成时不再触发指定的回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn的接口是[off('drawChildren')](#offdrawchildren20)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [VoidCallback](arkui-ts/ts-types.md#voidcallback12)   | 否   | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和[onDrawChildren](#ondrawchildren23)方法中的callback为相同对象时才能取消回调成功。 |

**示例：**

> **说明：**
>
> 推荐通过使用[UIContext](./js-apis-arkui-UIContext.md#uicontext)中的[getUIInspector](./js-apis-arkui-UIContext.md#getuiinspector)方法获取当前UI上下文关联的[UIInspector](./js-apis-arkui-UIContext.md#uiinspector)对象。

### onLayoutChildren<sup>23+</sup>

ArkTS-Dyn: onLayoutChildren(callback: Callback\<void\>): void

ArkTS-Sta: onLayoutChildren(callback: VoidCallback): void

通过[ComponentObserver](#componentobserver)注册layoutChildren事件回调方法，当组件的子组件布局完成时会触发该回调方法。如果组件树中存在多个layoutChildren事件回调，只会触发在最顶层的layoutChildren事件回调。使用callback异步回调。取消最顶层的回调后，其余layoutChildren事件回调也无法生效。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: Callback\<void\><br/>ArkTS-Sta: [VoidCallback](arkui-ts/ts-types.md#voidcallback12)  | 是   | 监听layoutChildren的回调。                                     |

### offLayoutChildren<sup>23+</sup>

ArkTS-Dyn: offLayoutChildren(callback?: Callback\<void\>): void

ArkTS-Sta: offLayoutChildren(callback?: VoidCallback): void

通过句柄向对应的查询条件取消注册回调，当组件的子组件布局完成时不再触发指定的回调。使用callback异步回调。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: Callback\<void\><br/>ArkTS-Sta: [VoidCallback](arkui-ts/ts-types.md#voidcallback12)   | 否   | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和[onLayoutChildren](#onlayoutchildren23)方法中的callback为相同对象时才能取消回调成功。 |

**示例：**

以下示例展示了inspector注册组件布局和组件绘制送显完成回调通知能力的基本用法。同时，通过[onLayoutChildren<sup>23+</sup>](#onlayoutchildren23)接口监听子树中的节点完成布局时的回调事件。

ArkTS-Dyn示例：

```ts
import { inspector } from '@kit.ArkUI'

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  listenerForImage: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('IMAGE_ID')
  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID')

  aboutToAppear() {
    let onLayoutComplete: () => void = (): void => {
      // 根据需要补充实现代码
    }
    let onDrawComplete: () => void = (): void => {
      // 根据需要补充实现代码
    }
    let onDrawChildrenComplete: () => void = (): void => {
      // 根据需要补充实现代码
    }
    let onLayoutChildrenComplete: () => void = (): void => {
      // 根据需要补充实现代码
    }
    let FuncLayout = onLayoutComplete // 绑定当前js实例
    let FuncDraw = onDrawComplete
    let FuncDrawChildren = onDrawChildrenComplete
    let FuncLayoutChildren = onLayoutChildrenComplete
    let OffFuncLayout = onLayoutComplete
    let OffFuncDraw = onDrawComplete
    let OffFuncDrawChildren = onDrawChildrenComplete
    let OffFuncLayoutChildren = onLayoutChildrenComplete

    this.listenerForImage.on('layout', FuncLayout)
    this.listenerForImage.on('draw', FuncDraw)
    this.listenerForRow.on('drawChildren', FuncDrawChildren)
    this.listenerForRow.onLayoutChildren(FuncLayoutChildren)

    // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用
    // this.listenerForImage.off('layout', OffFuncLayout)
    // this.listenerForImage.off('draw', OffFuncDraw)
    // this.listenerForRow.off('drawChildren', OffFuncDrawChildren)
    // this.listenerForRow.offLayoutChildren(OffFuncLayoutChildren)
  }
}
```

ArkTS-Sta示例：

```ts
import inspector from '@ohos.arkui.inspector';
import { Column, Row, Image, Flex, FlexDirection, ItemAlign, $r, Text, Component, Entry} from '@ohos.arkui.component';

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360)
  }

  listenerForImage:inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('IMAGE_ID') as inspector.ComponentObserver
  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID') as inspector.ComponentObserver

  aboutToAppear() {
    let onLayoutComplete:()=>void=():void=>{
      // 用户自定义回调函数
    }
    let onDrawComplete:()=>void=():void=>{
      // 用户自定义回调函数
    }
    let onDrawChildrenComplete:()=>void=():void=>{
      // 用户自定义回调函数
    }
    let FuncLayout = onLayoutComplete // 绑定当前js对象
    let FuncDraw = onDrawComplete // 绑定当前js对象
    let FuncDrawChildren = onDrawChildrenComplete // 绑定当前js对象
    let OffFuncLayout = onLayoutComplete // 绑定当前js对象
    let OffFuncDraw = onDrawComplete // 绑定当前js对象
    let OffFuncDrawChildren = onDrawChildrenComplete // 绑定当前js对象

    this.listenerForImage.onLayout(FuncLayout)
    this.listenerForImage.onDraw(FuncDraw)
    this.listenerForRow.onDrawChildren(FuncDrawChildren)

    // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用。
    // this.listener.offLayout(OffFuncLayout)
    // this.listener.offDraw(OffFuncDraw)
    // this.listener.offDrawChildren(OffFuncDrawChildren)
  }
}
```

### onDrawChildren<sup>24+</sup>

ArkTS-Dyn: onDrawChildren(callback: Callback\<int[]\>): void

ArkTS-Sta: onDrawChildren(callback: Callback\<int[]\>): void

通过[ComponentObserver](#componentobserver)注册drawChildren事件回调。使用callback异步回调。

把当前注册监听的节点作为根节点，组件的子组件绘制送显完成时，会触发该回调。如果组件树中存在多个drawChildren事件回调，只会触发在最顶层的drawChildren事件回调。取消最顶层的回调后，其余drawChildren事件回调也无法生效。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: Callback\<int[]\> <br/>ArkTS-Sta: Callback\<int[]\> | 是   | 监听drawChildren的回调。                              |

**示例：**

以下示例展示了inspector注册组件布局和组件绘制送显完成回调通知能力的基本用法。监听子树内节点完成渲染后，通过[onDrawChildren<sup>24+</sup>](#ondrawchildren24)接口，回调返回该节点的uniqueId信息。

ArkTS-Dyn示例：

```ts
import { inspector } from '@kit.ArkUI'

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID')

  aboutToAppear() {
    let onDrawChildrenComplete_uniqueId: (childIds: Array<number>) => void = (childIds: Array<number>): void => {
      // 从API version 24开始，新增onDrawChildren接口。监听到DrawChildren事件后，用户可以自定义实现逻辑。
    }

    this.listenerForRow.onDrawChildren(onDrawChildrenComplete_uniqueId)
  }
}
```

ArkTS-Sta示例：

```ts
import inspector from '@ohos.arkui.inspector';
import { Column, Row, Image, Flex, FlexDirection, ItemAlign, $r, Text, Component, Entry} from '@ohos.arkui.component';

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360)
  }

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID') as inspector.ComponentObserver

  aboutToAppear() {
    let onDrawChildrenComplete_uniqueId:(childIds: Array<number>)=>void = (childIds: Array<number>) : void => {
      // 监听到DrawChildren事件后，用户可以自定义实现逻辑。
    }

    this.listenerForRow.onDrawChildren(onDrawChildrenComplete_uniqueId)
  }
}
```

### offDrawChildren<sup>24+</sup>

ArkTS-Dyn: offDrawChildren(callback?: Callback\<int[]\>): void

ArkTS-Sta: offDrawChildren(callback?: Callback\<int[]\>): void

取消注册offDrawChildren事件回调。使用callback异步回调。

要实现在子组件布局完成后停止触发特定回调，只需通过其句柄，在对应的查询条件上取消注册该回调即可。

**原子化服务API：** 从API version 24开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: Callback\<int[]\> <br/>ArkTS-Sta: Callback\<int[]\>   | 否   | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和[onDrawChildren24+](#ondrawchildren24)方法中的callback为相同对象时才能取消回调成功。 |

**示例：**

以下示例展示了inspector注册组件布局和组件绘制送显完成回调通知能力的基本用法。同时，通过[onLayoutChildren](#onlayoutchildren23)接口监听子树中的节点完成布局时的回调事件；监听子树内节点完成渲染后，通过[onDrawChildren](#ondrawchildren24)接口，回调返回该节点的uniqueId信息。

从API version 23开始，新增onLayoutChildren接口；从API version 24开始，新增onDrawChildren接口。

ArkTS-Dyn示例：

```ts
import { inspector } from '@kit.ArkUI'

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID')

  aboutToAppear() {
    let onDrawChildrenComplete_uniqueId: (childIds: Array<number>) => void = (childIds: Array<number>): void => {
      // 从API version 24开始，新增onDrawChildren接口。监听到DrawChildren事件后，用户可以自定义实现逻辑。
    }

    this.listenerForRow.onDrawChildren(onDrawChildrenComplete_uniqueId)

    // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用
    // this.listenerForRow.offDrawChildren(onDrawChildrenComplete_uniqueId)
  }
}
```

ArkTS-Sta示例：

```ts
import inspector from '@ohos.arkui.inspector';
import { Column, Row, Image, Flex, FlexDirection, ItemAlign, $r, Text, Component, Entry} from '@ohos.arkui.component';

@Entry
@Component
struct ImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          Image($r('app.media.startIcon'))
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('IMAGE_ID')
        }
        .id('ROW_ID')
      }
    }.height(320).width(360)
  }

  listenerForRow: inspector.ComponentObserver = this.getUIContext().getUIInspector().createComponentObserver('ROW_ID') as inspector.ComponentObserver

  aboutToAppear() {
    let onDrawChildrenComplete_uniqueId:(childIds: Array<number>)=>void = (childIds: Array<number>) : void => {
      // 监听到DrawChildren事件后，用户可以自定义实现逻辑。
    }

    this.listenerForRow.onDrawChildren(onDrawChildrenComplete_uniqueId)

    // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用。
    // this.listenerForRow.offDrawChildren(onDrawChildrenComplete_uniqueId)
  }
}
```