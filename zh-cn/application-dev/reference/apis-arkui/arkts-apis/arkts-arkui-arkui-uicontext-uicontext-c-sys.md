# UIContext

UIContext实例对象。

> **说明：**

> - 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。  
>  
> - 以下API需要通过对应的UIContext实例调用。获取UIContext分为三种方式，第一种是使用ohos.window中的  
> [getUIContext()](../../../../reference/apis-arkui/arkts-apis-window-Window.md#getuicontext10)方法获取UIContext实例，第二种是通过自定  
> 义组件内置方法[getUIContext()](../../../../reference/apis-arkui/arkui-ts/ts-custom-component-api.md#getuicontext)获取UIContext  
> 实例，第三种是通过UIContext类的静态方法如[getCallingScopeUIContext](arkts-arkui-arkui-uicontext-uicontext-c.md#getcallingscopeuicontext-1)获取UIContext实例。本文中  
> UIContext对象以uiContext表示。

**起始版本：** 10

<!--Device-unnamed-export class UIContext--><!--Device-unnamed-export class UIContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## animateToImmediately

```TypeScript
animateToImmediately(param: AnimateParam, processor: Callback<void>): void
```

通过UIContext对象指定明确的动画主实例上下文，并触发显式动画立即下发。避免由于找不到实例或实例不对，导致的动画不执行或动画结束回调不执行问题。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-UIContext-animateToImmediately(param: AnimateParam, processor: Callback<void>): void--><!--Device-UIContext-animateToImmediately(param: AnimateParam, processor: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [AnimateParam](../arkts-components/arkts-arkui-common-animateparam-i.md) | 是 | 设置动画效果相关参数。 |
| processor | [Callback](../arkts-components/arkts-arkui-common-callback-i.md)<void> | 是 | 回调函数。指定显示动效的闭包函数，在闭包函数中导致的状态变化系统会自动插入过渡动画。 |

## clearResourceCache

```TypeScript
clearResourceCache(): void
```

清除跨模块（[HSP](../../../../quick-start/in-app-hsp.md)包）访问资源时生成的资源对象缓存。清除缓存后，下次访问该模块资源的加载时间会增加。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12 - 12开始，该接口支持在原子化服务API中使用。

<!--Device-UIContext-clearResourceCache(): void--><!--Device-UIContext-clearResourceCache(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application.<br>**适用版本：** 12 - 22 |

**示例：**

```TypeScript
@Entry
@Component
struct MyStateSample {
  build() {
    Column() {
      Button("clearResourceCache")
        .onClick((event: ClickEvent) => {
          this.getUIContext().clearResourceCache()
        })
        .width('100%')
    }
  }
}

```

## freezeUINode

```TypeScript
freezeUINode(id: string, isFrozen: boolean): void
```

通过id设置组件冻结状态，防止组件被标记为脏从而触发布局更新。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIContext-freezeUINode(id: string, isFrozen: boolean): void--><!--Device-UIContext-freezeUINode(id: string, isFrozen: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件的id。 |
| isFrozen | boolean | 是 | 是否设置冻结。<br/>true表示设置冻结，false表示设置不冻结。<br/>默认值为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |

## freezeUINode

```TypeScript
freezeUINode(uniqueId: number, isFrozen: boolean): void
```

通过uniqueId设置组件的冻结状态，防止组件被标记为脏从而触发布局更新。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIContext-freezeUINode(uniqueId: number, isFrozen: boolean): void--><!--Device-UIContext-freezeUINode(uniqueId: number, isFrozen: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | number | 是 | 组件的uniqueId。 |
| isFrozen | boolean | 是 | 是否设置冻结。<br/>true表示设置冻结，false表示设置不冻结。<br/>默认值为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |

## getLuminanceSampler

```TypeScript
getLuminanceSampler(target: TargetInfo): LuminanceSampler | undefined
```

获取[LuminanceSampler](arkts-arkui-uicontext.md)取色对象，通过该对象设置背景亮度取色参数、注册亮度变化监听回调、取消注册监听回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIContext-getLuminanceSampler(target: TargetInfo): LuminanceSampler | undefined--><!--Device-UIContext-getLuminanceSampler(target: TargetInfo): LuminanceSampler | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [TargetInfo](arkts-arkui-arkui-uicontext-targetinfo-i.md) | 是 | 目标组件的标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LuminanceSampler](arkts-arkui-arkui-uicontext-luminancesampler-c-sys.md) | the luminance sampler or undefined. |

**示例：**

参考[offBackgroundLuminanceChange](arkts-apis-uicontext-luminancesampler-sys.md#offbackgroundluminancechange23)接口的示例。

## recycleInvisibleImageMemory

```TypeScript
recycleInvisibleImageMemory(enabled: boolean): void
```

设置不可见Image节点内存回收配置开关，由系统应用配置，默认不开启；开启后，在应用退后台不可见页面下挂载的Image节点会进行内存回收。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIContext-recycleInvisibleImageMemory(enabled: boolean): void--><!--Device-UIContext-recycleInvisibleImageMemory(enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 使能开关项：true开启，false关闭；默认不开启，由系统应用按需开启。<br>默认值：false<br>默认值：false<br>默认值：false<br>默认值：false<br>配置为异常undefined时，恢复为默认值false |

**示例：**

```TypeScript
@Entry
@Component
struct ImageRecycleSample {
  build() {
    Column({ space: 12 }) {
      Button('Enable recycle invisible image memory')
        .onClick(() => {
          this.getUIContext().recycleInvisibleImageMemory(true)
        })

      Button('Disable recycle invisible image memory')
        .onClick(() => {
          this.getUIContext().recycleInvisibleImageMemory(false)
        })
    }
    .width('100%')
    .padding(16)
  }
}

```

## setDynamicDimming

```TypeScript
setDynamicDimming(id: string, value: number): void
```

通过该方法设置组件的压暗程度。

> **说明：**  
>  
> 设置该属性后设置其他效果类属性会导致效果冲突。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIContext-setDynamicDimming(id: string, value: number): void--><!--Device-UIContext-setDynamicDimming(id: string, value: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 组件id。 |
| value | number | 是 | 组件压暗程度取值范围[0,1], 由0到1逐渐变亮。 |

**示例：**

```TypeScript
@Entry
@Component
struct Index {
  @State
  myCount : number = 100

  build() {
    Column(){
      Image($r('app.media.testImage')).width(500).height(800).id("test")
    }.width("100%").height("100%").onClick(()=>{
      this.getUIContext().setDynamicDimming("test",1)
      this.getUIContext()?.animateTo({duration:5000 },()=>{
        this.getUIContext().setDynamicDimming("test",0)
      })
    })
  }
}

```

## setKeyboardAppearanceConfig

```TypeScript
setKeyboardAppearanceConfig(uniqueId: number, config: KeyboardAppearanceConfig): void
```

在输入框绑定输入法前设置键盘样式配置

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIContext-setKeyboardAppearanceConfig(uniqueId: number, config: KeyboardAppearanceConfig): void--><!--Device-UIContext-setKeyboardAppearanceConfig(uniqueId: number, config: KeyboardAppearanceConfig): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | number | 是 | The unique id of the input component. |
| config | [KeyboardAppearanceConfig](arkts-arkui-text-common-keyboardappearanceconfig-i-sys.md) | 是 | The config of keyboard. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |

