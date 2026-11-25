# 自定义组件异步加载
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @shiyu_huang_plus-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

页面转场、首帧渲染等对帧率敏感的场景下，构建耗时较长的自定义组件同步构建（[build函数](./arkts-create-custom-components.md#build函数)执行）会占据主线程的帧内时间，导致丢帧卡顿。自定义组件异步加载（[enableAsyncLoad](../../reference/apis-arkui/js-apis-stateManagement.md#enableasyncload)）将组件实际内容的构建从首个渲染帧推迟到之后的空闲时段执行，页面其余部分正常渲染，转场更流畅；加载完成前可显示占位组件，超时未完成时由框架通过强制加载进行兜底。

在阅读本文档之前，建议先阅读[创建自定义组件](./arkts-create-custom-components.md)和[自定义组件生命周期（推荐）](./arkts-custom-components-new-lifecycle.md)。配置占位组件时，须先了解[\@ohos.arkui.placeholderRegister (滚动占位注册)](../../reference/apis-arkui/arkts-apis-placeholderregister.md)。

>**说明：**
>
> 自定义组件异步加载功能从API版本26.1.0开始支持。
>
> 从API版本26.1.0开始，支持在原子化服务中使用。

## 概述

自定义组件默认同步加载：组件创建后，其[build函数](./arkts-create-custom-components.md#build函数)在首个渲染帧内执行，实际内容与页面其余部分同帧构建呈现。当build函数构建耗时较长（如深层嵌套、大量子组件）时，会挤占帧内渲染预算，在页面转场等场景引起丢帧。

启用异步加载后，组件的实际内容构建被推迟，其工作方式如下：

- **首帧不构建**：首个渲染帧不执行该组件的build函数，页面其余部分正常渲染；组件位置显示占位组件（已配置且可找到时）或不显示内容。
- **空闲分片构建**：实际内容在后续帧的空闲时段（IDLE）构建，以帧剩余时间为预算分片执行，不占用帧内渲染预算；页面持续空闲时，框架会自动调度后续空闲时段直至构建完成。
- **超时强制兜底**：超过超时阈值（默认1000 ms）仍未完成时，框架在后续帧强制加载该组件（单帧强制加载的组件数量有上限），保证组件最终呈现。
- **自动替换**：加载完成后，占位组件自动替换为实际内容，框架自动触发渲染更新，无需开发者干预。

## 基本概念

**异步加载**：组件实际内容的构建推迟至首个渲染帧之后的空闲时段执行的加载方式。启用后，组件生命周期回调时序相应推迟（详见[约束与限制](#约束与限制)）。

**占位组件**：异步加载期间显示的临时组件，通过[PlaceholderOptions](../../reference/apis-arkui/arkts-apis-placeholderregister.md#placeholderoptions)配置：id指向经[getPlaceholderRegister()](../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getplaceholderregister)注册的占位模板，size为布局建议尺寸（数字单位为vp，越接近实际内容尺寸，替换时视觉跳动越小）。未配置占位时，加载完成前组件位置不显示内容。

**超时强制加载**：超时阈值到期后仍未完成加载的组件，由框架在后续帧强制加载的兜底机制。timeout取正数（默认1000 ms）时在阈值内等待空闲完成、到期后强制加载，取0表示不等待，取负数（含正/负无穷大）表示永不超时；取值语义详见[CustomComponentAsyncLoadOptions](../../reference/apis-arkui/js-apis-stateManagement.md#customcomponentasyncloadoptions)。

## 接口说明

| 接口 | 说明 |
| ---- | ---- |
| [enableAsyncLoad](../../reference/apis-arkui/js-apis-stateManagement.md#enableasyncload)(options?: [CustomComponentAsyncLoadOptions](../../reference/apis-arkui/js-apis-stateManagement.md#customcomponentasyncloadoptions)): void | 将当前自定义组件置为异步加载。options不传时，加载完成前不显示占位组件，超时阈值取默认值1000ms。 |

配置项**placeholder**（占位组件）与**timeout**（超时阈值）的取值语义在[CustomComponentAsyncLoadOptions](../../reference/apis-arkui/js-apis-stateManagement.md#customcomponentasyncloadoptions)中声明。

## 约束与限制

- **调用时机与作用范围**：仅在组件构造期调用生效，即[\@ComponentInit](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentinit)装饰的函数内（组件构造函数尾部执行）；仅对当前自定义组件实例生效，未调用enableAsyncLoad的组件保持既有同步加载行为。
- **构造期外调用无效**：其余时机（含[aboutToAppear](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#abouttoappear)、build执行中、组件已显示后）调用时无异步效果：调用正常返回、不抛异常，也无错误日志等可观测的失败信号，组件按既有同步方式完成加载显示。
- **仅首次生效**：同一组件重复调用enableAsyncLoad无效，仅首次调用生效；重复调用会记录维测告警日志（可观察于hilog）。
- **嵌套规则**：祖先自定义组件异步构建过程中创建的子组件，其enableAsyncLoad调用不生效——子组件随父组件同步构建，父组件的异步加载预算与超时兜底已覆盖其构建。
- **占位模板要求**：占位模板须先通过[getPlaceholderRegister()](../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getplaceholderregister)注册，且builder须为全局、无参、只读静态渲染的[\@Builder](./arkts-builder.md)({ isPlaceholder: true })函数（不得访问响应式状态、注册手势/动画/回调；动画组件如LoadingProgress不可用于占位模板），受限Builder要求详见[\@ohos.arkui.placeholderRegister (滚动占位注册)](../../reference/apis-arkui/arkts-apis-placeholderregister.md)；占位模板注册表按UI实例隔离，注册结果对其他UI实例不可见。
- **生命周期时序变化**：启用异步加载后，aboutToAppear/[\@ComponentAppear](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentappear)不在首个渲染帧触发，推迟至实际内容构建所在的帧（先于该帧内内容构建）触发；[\@ComponentBuilt](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentbuilt)、[onDidBuild](../../reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#ondidbuild)、[onWillApplyTheme](../../reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#onwillapplytheme12)的触发时机与顺序为：onWillApplyTheme → \@ComponentBuilt → onDidBuild（onWillApplyTheme 先于内容构建，后两者在构建完成后依次触发，与同步加载场景一致）；每个回调仍恰好触发一次。
- **测量回调**：[onMeasureSize](../../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#onmeasuresize10)/[onPlaceChildren](../../reference/apis-arkui/arkui-ts/ts-custom-component-layout.md#onplacechildren10)首次触发于加载完成后，占位期间不触发，占位子树不作为LayoutChild暴露。
- **失败处理**：当前版本不处理异步加载失败场景，由超时强制加载机制兜底。

## 使用场景

### 页面转场时避免重型组件阻塞首帧

构建耗时较长的自定义组件启用异步加载后，页面首个渲染帧仅构建页面其余部分，组件内容在后续空闲时段完成，转场不丢帧。

<!-- @[AsyncLoadBasic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AsyncLoad/entry/src/main/ets/pages/AsyncLoadBasic.ets) -->

```ts
import { UIUtils, ComponentInit } from '@kit.ArkUI';

// 构建耗时较长的自定义组件
@ComponentV2
struct HeavyComponent {
  @ComponentInit
  init() {
    // 仅构造期调用生效：组件进入异步加载，首个渲染帧不构建实际内容
    UIUtils.getCustomComponentContext(this).enableAsyncLoad();
  }

  build() {
    // build推迟至后续空闲时段分片执行
    Column() {
      Text('实际内容')
        .fontSize(24)
      // ...更多构建耗时较长的内容
    }
  }
}

@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      Text('页面其余内容首个渲染帧正常呈现')
      HeavyComponent()
    }
  }
}
```

### 配置占位组件，降低加载完成前的视觉空白

未配置占位时，异步加载完成前组件位置不显示内容。配置占位组件后，加载期间显示占位（如加载提示、骨架样式等静态渲染内容），加载完成后自动替换为实际内容。

<!-- @[AsyncLoadPlaceholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AsyncLoad/entry/src/main/ets/pages/AsyncLoadPlaceholder.ets) -->

```ts
import { UIUtils, ComponentInit } from '@kit.ArkUI';

// 占位模板须为全局、无参、只读静态渲染的受限Builder：
// 只能包含静态渲染内容，不得访问响应式状态、注册手势/动画/回调——
// 动画组件（如LoadingProgress）不可用，违反约束的模板无法注册成功
@Builder({ isPlaceholder: true })
function HeavyPlaceholder() {
  Column() {
    Text('加载中...')
      .fontSize(14)
      .fontColor(0x999999)
  }
  .width('100%')
  .height(120)
  .justifyContent(FlexAlign.Center)
}

@ComponentV2
struct HeavyComponent {
  @ComponentInit
  init() {
    // 占位id须与注册的模板id一致；size为占位建议尺寸，数字单位为vp，
    // 越接近实际内容尺寸，占位替换为实际内容时视觉跳动越小
    UIUtils.getCustomComponentContext(this).enableAsyncLoad({
      placeholder: {
        id: 'heavyPlaceholder',
        size: { height: 120 }
      }
    });
  }

  build() {
    Column() {
      Text('实际内容')
        .fontSize(24)
    }
    .width('100%')
    .height(120)
    .justifyContent(FlexAlign.Center)
  }
}

@Entry
@ComponentV2
struct Index {
  aboutToAppear() {
    // 先注册占位模板（注册表经getPlaceholderRegister获取，按UI实例隔离）
    this.getUIContext().getPlaceholderRegister()
      .register('heavyPlaceholder', wrapBuilder(HeavyPlaceholder));
  }

  aboutToDisappear() {
    this.getUIContext().getPlaceholderRegister().unregister('heavyPlaceholder');
  }

  build() {
    Column() {
      Text('页面其余内容首个渲染帧正常呈现')
      HeavyComponent()
    }
  }
}
```

### 按内容特点选择超时策略

超时阈值决定“空闲等待”与“强制完成”的平衡，按组件内容特点选择。超时计时自异步加载生效（组件在首个渲染帧注册异步加载）起算，至实际内容构建完成：

- **默认1000 ms**：适合大多数场景，兼顾转场流畅与呈现及时性。
- **较小的正值**：内容较轻、希望尽快稳定呈现的组件，可适当调小。
- **0**：不等待空闲，组件在后续帧中被强制加载——适合内容轻但对呈现时机敏感的场景，此时异步加载主要收益是避开首个渲染帧。
- **负数（含正/负无穷大）**：永不超时，持续等待空闲完成——适合配合占位组件做长时间加载呈现（如骨架屏）的耗时较长的内容。等待持续至加载完成或组件销毁（如用户离开页面）为止：销毁时若仍未完成，框架取消后续构建并清理状态，不再继续加载、无残留显示。

<!-- @[AsyncLoadTimeout](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/AsyncLoad/entry/src/main/ets/pages/AsyncLoadTimeout.ets) -->

```ts
import { UIUtils, ComponentInit } from '@kit.ArkUI';

@ComponentV2
struct HeavyComponent {
  @ComponentInit
  init() {
    // 3秒兜底：3秒内等待空闲分片构建，到期后强制加载
    UIUtils.getCustomComponentContext(this).enableAsyncLoad({ timeout: 3000 });
    // 不等待：组件在后续帧中被强制加载
    // UIUtils.getCustomComponentContext(this).enableAsyncLoad({ timeout: 0 });
    // 永不超时：持续等待空闲完成，配合占位组件呈现
    // UIUtils.getCustomComponentContext(this).enableAsyncLoad({ timeout: -1 });
  }

  build() {
    Text('实际内容')
  }
}

@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      HeavyComponent()
    }
  }
}
```

