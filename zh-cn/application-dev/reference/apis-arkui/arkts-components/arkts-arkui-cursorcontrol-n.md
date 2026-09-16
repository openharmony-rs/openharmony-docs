# cursorControl

控制鼠标光标的显示样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [setCursor](arkts-arkui-cursorcontrol-setcursor-f.md) | 方法语句中可使用的全局接口，调用该接口可更改当前的鼠标光标样式。 |
| [restoreDefault](arkts-arkui-cursorcontrol-restoredefault-f.md) | 方法语句中可使用的全局接口，调用此接口可将鼠标光标恢复成默认箭头样式。 |

## 示例

```TypeScript
该示例主要演示通过foregroundBlurStyle为图片设置内容模糊效果。
```

```TypeScript
### 示例1（半模态设置边缘光效动画）

以下示例通过设置edgeLightMode属性开启边缘光效动画，同时使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的systemMaterial接口实现了半透明材质效果。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增edgeLightMode属性。


```

```TypeScript
### 示例2（半模态设置模糊优化）

以下示例通过设置blurSnapshot属性开启模糊优化。当使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的systemMaterial接口设置材质效果或使用[SheetOptions](ts-universal-attributes-sheet-transition.md#sheetoptions)中的blurStyle接口设置模糊时发现功耗明显增加时，可以尝试开启模糊优化。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增blurSnapshot属性。
```

```TypeScript
属性动画状态下添加运动模糊效果。
```

```TypeScript
### 示例1（设置键盘接续）

该示例通过[onNeedSoftkeyboard](arkts-arkui-commonmethod-c.md#onneedsoftkeyboard)接口，设置按钮需要键盘。在从输入框拉起键盘后，点击按钮使焦点切换到按钮，此时键盘将不会收起，再次点击输入框可继续输入。

从API version 24开始，新增[onNeedSoftkeyboard](arkts-arkui-commonmethod-c.md#onneedsoftkeyboard)接口。
```

```TypeScript
该示例通过setCursor实现了鼠标光标样式的设置。
```

```TypeScript
该示例实现了组件注册表冠事件，并上报接收到的表冠事件数据内容。
```

```TypeScript
### 示例1（List使用OnMove进行拖拽）

以下示例展示了ForEach在List组件内使用时的拖拽效果。
```

```TypeScript
### 示例2（List使用OnMove进行拖拽，并设置拖拽事件回调）

从API version 20开始，以下示例展示了ForEach在List组件设置拖拽效果后触发的回调事件。
```

```TypeScript
### 示例3（Grid规则布局使用ForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了ForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里全是规则的GridItem。


```

```TypeScript
### 示例4（Grid不规则布局使用ForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了ForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过[irregularIndexes](ts-container-grid.md#gridlayoutoptions10对象说明)设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。


```

```TypeScript
### 示例5（Grid不规则布局使用LazyForEach的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了LazyForEach在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过irregularIndexes设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。
```

```TypeScript

```

```TypeScript
### 示例6（Grid不规则布局使用Repeat的onMove进行拖拽，并设置拖拽事件回调）

从API版本26.0.0开始，以下示例展示了Repeat在Grid组件设置拖拽效果后触发的回调事件，Grid里存在不规则的GridItem。应用可通过irregularIndexes设置哪些索引是不规则节点，通过修改对应索引的rectSize调整该GridItem所占的行列数。
```

```TypeScript
该示例分别使用了不传参@Preview和传参的@Preview。
```

```TypeScript
### 示例1（触摸测试模式为Block和Transparent的触摸测试效果）

该示例通过设置不同的[HitTestMode](./ts-appendix-enums.md#hittestmode9)值演示了Block和Transparent的触摸测试效果。
```

```TypeScript
### 示例2（触摸测试类型为BLOCK_HIERARCHY时的触摸测试效果）

从API version 20开始，该示例演示了设置触摸测试模式为BLOCK_HIERARCHY时的触摸测试效果。
```

```TypeScript
### 示例3（触摸测试类型为BLOCK_DESCENDANTS时的触摸测试效果）

从API version 20开始，该示例演示了设置触摸测试模式为BLOCK_DESCENDANTS时的触摸测试效果。
```

```TypeScript
### 示例4（Stack组件中多节点重合时的触摸测试效果）

该示例演示了在Stack组件中存在多节点触摸区域重叠时的触摸测试效果。此时设置[HitTestMode](./ts-appendix-enums.md#hittestmode9)为None时，重叠的背景区域无法响应触摸测试；只有设置为Transparent时，背景区域才能响应触摸测试。
```

```TypeScript
### 示例1（使用全屏模态转场）

该示例主要演示通过bindContentCover来实现全屏模态转场。


```

```TypeScript
### 示例2（自定义转场动画）

全屏模态无动画转场模式下，自定义转场动画。


```

```TypeScript
### 示例3（上下切换转场）

全屏模态上下切换转场。


```

```TypeScript
### 示例4（透明度渐变转场）

全屏模态透明度渐变转场。


```

```TypeScript
### 示例5（设置不同效果的自定义转场）

该示例主要演示全屏模态旋转、平移等自定义转场。


```

```TypeScript
### 示例6（设置全屏模态适配安全区）

从API version 20开始，该示例主要演示设置enableSafeArea为true后全屏模态适配安全区的内容效果。全屏模态容器的背景色为浅蓝色，内容颜色为灰色，内容在安全区内布局。
```

```TypeScript
### 示例1（设置组件获焦和走焦的效果）

该示例通过配置[defaultFocus](#defaultfocus9)可以使绑定的组件成为[层级页面](../../../ui/arkts-common-events-focus-event.md#基础概念)创建后首次获焦的焦点，配置[groupDefaultFocus](arkts-arkui-commonmethod-c.md#groupdefaultfocus)可以使绑定的组件成为tabIndex容器创建后首次获焦的焦点，配置[focusOnTouch](arkts-arkui-commonmethod-c.md#focusontouch)可以使绑定的组件点击后立即获焦。

示意图：

首次进入时，焦点默认在defaultFocus绑定的TextInput组件上：



首次按Tab键，焦点切换到tabIndex(1)的容器上，且自动走焦到内部第一个可获焦组件上：



第二次按Tab键，焦点切换到tabIndex(2)的容器上，且自动走焦到其内部的groupDefaultFocus绑定的组件上：



第三次按Tab键，焦点切换到tabIndex(3)的容器上，且自动走焦到内部配置了defaultFocus的组件上：



点击绑定了focusOnTouch的组件，组件自身获焦，焦点框被清除，再按下Tab键后，显示焦点框：


```

```TypeScript
### 示例2（设置指定组件获焦）

该示例通过配置[focusControl.requestFocus](#requestfocus9)使指定组件获取焦点。

示意图：

按下Tab键，激活焦点态显示。

申请不存在的组件获焦：



申请不可获焦的组件获焦：



申请存在且可获焦的组件获焦：


```

```TypeScript
### 示例3（设置焦点框样式）

该示例通过配置[focusBox](#focusbox12)修改组件的焦点框样式。


```

```TypeScript
### 示例4（设置焦点组走焦）

该示例通过配置[focusScopePriority](arkts-arkui-commonmethod-c.md#focusscopepriority)，可以使绑定的组件在所属容器首次获焦时成为焦点，配置[focusScopeId](arkts-arkui-commonmethod-c.md#focusscopeid)，可以使绑定的容器组件成为焦点组。

示意图：

首次按下Tab键时，焦点转移到容器1中绑定focusScopePriority的组件上。



继续按下Tab键，焦点转移到容器1下一个组件上。



再次按下Tab键，焦点转移到容器1下一个组件上。



继续按下Tab键，焦点转移到容器2中配置了focusScopePriority的组件上。



继续按下Tab键，焦点转移到容器1中名为Group1的组件上。


```

```TypeScript
### 示例5（设置Tab走焦停留）

该示例通过配置[tabStop](arkts-arkui-commonmethod-c.md#tabstop)实现使用Tab走焦停留在组件上。

示意图：

连续按下两次Tab键，焦点转移到button2上。



接着按下Tab键，焦点转移到配置了tabStop的组件。



再按下Enter键，焦点转移至内部button3上。



再按下ESC键，焦点转移到配置了tabStop的组件上。



再按下Tab键，焦点循环走焦到button1上。


```

```TypeScript
### 示例6（设置自定义走焦）

从API version 18开始，该示例通过配置[nextFocus](arkts-arkui-commonmethod-c.md#nextfocus)实现自定义走焦规则。

如果不配置[nextFocus](arkts-arkui-commonmethod-c.md#nextfocus)，默认的按下Tab键的走焦顺序为：M->A->B->C->D->E->F；配置了[nextFocus](arkts-arkui-commonmethod-c.md#nextfocus)以后，走焦顺序变更为：M->D->F->B->C。
```

```TypeScript
该示例通过Text组件设置组件尺寸变化事件，当Text尺寸变化时可以触发onSizeChange事件，获取oldValue和newValue参数。
```

```TypeScript
### 示例1（使用onAreaChange监听区域变化）

该示例通过Text组件设置组件区域变化事件，当Text布局变化时可以触发onAreaChange事件，获取相关参数。


```

```TypeScript
### 示例2（使用onAreaChange自定义间隔监听区域变化）

该示例通过设置[expectedUpdateInterval](arkts-arkui-areachangeoptions-i.md)，当Text布局变化时可以触发[onAreaChange](#onareachange-1)事件，达到间隔回调的效果。

从API版本26.0.0开始，新增[onAreaChange](#onareachange-1)、[AreaChangeCallback](arkts-arkui-areachangecallback-t.md)和[AreaChangeOptions](arkts-arkui-areachangeoptions-i.md)。
```

```TypeScript
### 示例1（使用外描边属性）

该示例主要演示如何通过[outline](arkts-arkui-commonmethod-c.md#outline)来实现组件外描边。


```

```TypeScript
### 示例2（使用LocalizedEdgeColors类型）

该示例将[outline](arkts-arkui-commonmethod-c.md#outline)属性中的color属性值设置为[LocalizedEdgeColors](ts-types.md#localizededgecolors12)类型。
```

```TypeScript
### 示例1（系统组件设置自定义属性）

在[Column](ts-container-column.md)组件上设置自定义属性，并在其对应的FrameNode上获取所设置的自定义属性。
```

```TypeScript
### 示例2（自定义组件设置自定义属性）

从API版本26.0.0开始，自定义组件支持通过[customProperty](#customproperty)接口设置自定义属性。本示例以[自定义组件的自定义布局](../../../ui/state-management/arkts-page-custom-components-layout.md)场景为例，在自定义组件上设置自定义属性，并在其[onMeasureSize](ts-custom-component-layout.md#onmeasuresize10)回调中获取所设置的自定义属性。
```

```TypeScript
### 示例1（组件绑定Modifier切换背景颜色）

该示例通过Button绑定Modifier实现了点击切换背景颜色的效果。


```

```TypeScript
### 示例2（组件绑定Modifier实现按压态效果）

该示例通过Button绑定Modifier实现了按压态的效果。如果配合状态管理V2使用，详情见：[Modifier与makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#modifier)。


```

```TypeScript
### 示例3（自定义Modifier不支持感知@State装饰的状态数据变化）

该示例通过状态数据设置自定义Modifier的宽度，自定义Modifier不支持感知@State装饰的状态数据变化，点击按钮后宽度不发生改变。


```

```TypeScript
### 示例4（Modifier和自定义Modifier的属性同时生效）

该示例通过自定义Modifier设置了width、height和margin，点击按钮时设置[borderStyle](ts-appendix-enums.md#borderstyle)和[borderWidth](ts-universal-attributes-border.md#borderwidth)，点击后5个属性同时生效。


```

```TypeScript
### 示例5（组件绑定Modifier获焦样式）

该示例通过Button绑定Modifier实现了组件在获得焦点时的样式效果。点击Button2后，Button会显示获得焦点后的样式。


```

```TypeScript
### 示例6（组件绑定Modifier禁用状态的样式）

该示例通过Button绑定Modifier实现了组件禁用时的样式效果。点击Button2后，Button会显示禁用状态的样式。


```

```TypeScript
### 示例7（组件绑定Modifier选中状态样式）

该示例通过Radio绑定Modifier实现了组件选中时的样式效果。


```

```TypeScript
### 示例8（自定义组件绑定Modifier实现按压态效果）

该示例通过Common（自定义）绑定Modifier实现了按压态的效果。


```

```TypeScript
### 示例9（组件绑定Modifier实现鼠标悬浮态效果）

该示例通过Button绑定Modifier实现了鼠标悬浮态的效果。当鼠标移动到Button上时，Button的背景颜色变为红色，此时为悬浮态效果；当鼠标离开Button时，Button的背景颜色变为黑色，此时为普通态效果；同时通过[applyHoveredAttribute](arkts-arkui-attributemodifier-i.md#applyhoveredattribute)接口设置悬浮态样式。

从API版本26.0.0开始，新增[applyHoveredAttribute](arkts-arkui-attributemodifier-i.md#applyhoveredattribute)接口。
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Example {
  build() {
    Column() {
      Flex({ wrap: FlexWrap.Wrap }) {
        Column() {
          Text('width(220)')
            .width(220)
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width('220px')")
            .width('220px')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
        }.margin(5)

        Column() {
          Text("width('220vp')")
            .width('220vp')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width('220lpx') designWidth:720")
            .width('220lpx')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("width(getUIContext().vp2px(220) + 'px')")
            .width(this.getUIContext().vp2px(220) + 'px')
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12vp')
        }.margin(5)

        Column() {
          Text("fontSize('12fp')")
            .width(220)
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12fp')
        }.margin(5)

        Column() {
          Text('width(px2vp(220))')
            .width(this.getUIContext().px2vp(220))
            .height(40)
            .backgroundColor(0xF9CF93)
            .textAlign(TextAlign.Center)
            .fontColor(Color.White)
            .fontSize('12fp')
        }.margin(5)
      }.width('100%')
    }
  }
}
```

```TypeScript
### 示例1（使用onHover）

该示例通过按钮设置了悬浮事件[onHover](#onhover)，鼠标悬浮可触发该事件修改按钮颜色。

示意图：

未悬浮时的文本内容与背景颜色：



手写笔悬浮时改变文本内容与背景颜色：


```

```TypeScript
### 示例2（使用onHoverMove）

从API version 15开始，该示例设置了按钮的[onHoverMove](arkts-arkui-commonmethod-c.md#onhovermove)事件。当手写笔悬浮在按钮上时，UI会显示手写笔当前悬浮的位置。
```

```TypeScript
### 示例1（设置组件提亮）

该示例主要通过advancedBlendMode给组件添加提亮效果。

效果图如下：


```

```TypeScript
### 示例2（设置节点组剔除属性）

该示例演示在组件的属性动画场景下，如何通过使用节点组剔除属性[excludeFromRenderGroup](arkts-arkui-commonmethod-c-sys.md#excludefromrendergroup)，避免节点组缓存反复失效。

从API version 22开始，新增[excludeFromRenderGroup](arkts-arkui-commonmethod-c-sys.md#excludefromrendergroup)属性。


```

```TypeScript
### 示例3（设置组件提亮并渐隐）

从API version 23开始，该示例主要演示如何通过advancedBlendMode给组件同时添加提亮和渐隐效果。


```

```TypeScript
### 示例4（设置组件边缘流光效果）

该示例主要演示如何通过[edgeLight](#edgelight)给组件添加边缘流光效果。

从API版本26.0.0开始，新增edgeLight方法。
```

```TypeScript
该示例展示了组件获焦和失焦的情况，按钮获焦和失焦时会改变按钮的颜色。
```

```TypeScript
### 示例1（悬浮气泡的显示和消失）

此示例为bindTips通过绑定Button产生悬浮气泡。


```

```TypeScript
### 示例2（多个悬浮气泡的显示和消失）

此示例展示了如何使用bindTips配置多个悬浮气泡依次显示和消失。


```

```TypeScript
### 示例3（设置悬浮气泡的沉浸光感视效）

该示例通过[TipsOptions](#tipsoptions类型说明)中的systemMaterial属性设置组件的系统材质，实现了bindTips的沉浸光感视效。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在TipsOptions中新增了systemMaterial属性。
```

```TypeScript
### 示例1（动态绑定手势）

该示例通过gestureModifier动态设置组件绑定的手势。


```

```TypeScript
### 示例2（动态绑定手势组）

该示例通过gestureModifier动态设置组件绑定的手势组。
```

```TypeScript
### 示例1（自定义手势判定）

该示例通过配置[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin)实现了对长按、快滑、滑动、捏合和拖动手势的自定义判定。从API version 21开始，支持通过[BaseEvent](ts-universal-events-click.md#baseevent8)的axisPinch属性获取双指缩放比例。


```

```TypeScript
### 示例2（自定义区域手势判定）

该示例通过配置onGestureJudgeBegin，根据触发位置所在区域决定长按手势和拖动手势是否响应。


```

```TypeScript
### 示例3（实时监测参与手势的有效触点的数量及其简要信息）

该示例通过配置onGestureJudgeBegin回调，读取fingerInfos实时检测参与手势的有效触点数量、各个触点ID及其坐标。
```

```TypeScript
### 示例1 (使用onVisibleAreaChange来监听区域变化)

该示例对组件设置[onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange)事件，当组件完全显示或者完全消失时触发回调。
```

```TypeScript
### 示例2 (使用onVisibleAreaApproximateChange来监听区域变化)

从API version 17开始，该示例对组件设置[onVisibleAreaApproximateChange](arkts-arkui-commonmethod-c.md#onvisibleareaapproximatechange)事件，当组件完全显示或者完全消失时触发回调。


```

```TypeScript
### 示例3 (设置measureFromViewport计算子组件超出父组件显示时的可见区域)

从API version 22开始，该示例展示onVisibleAreaChange事件设置measureFromViewport参数后的效果对比，主要差异体现在回调返回的组件可见比例（currentRatio）上。设置measureFromViewport为true时，返回的组件可见比例（currentRatio）更符合实际效果。由于不同设备的屏幕像素密度不同，可见区域变化事件的计算过程涉及小数取整，currentRatio可能存在微小差异。
```

```TypeScript
该示例通过hoverEffect设置组件的鼠标悬浮态显示效果。
```

```TypeScript
该示例演示通过foregroundEffect接口设置前景属性。
```

```TypeScript
### 示例1（使用自动内存优化策略）

以下示例中，可复用自定义组件ReusableComponent通过[ReusableOptions](arkts-arkui-reusableoptions-i.md)的memoryOptimizationStrategy属性使用了自动内存优化策略。点击Recycle按钮，可触发ReusableComponent组件回收。之后应用退后台，可触发复用池缓存释放。

从API版本26.0.0开始，新增ReusableOptions接口。
```

```TypeScript
该示例主要演示如何通过keyframeAnimateTo来设置关键帧动画，包括delay延迟、onFinish播放完成回调以及各关键帧的curve曲线配置。
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State lightIntensity: number = 0;
  @State bloomValue: number = 0;

  build() {
    Row({ space: 20 }) {
      Flex()
        .pointLight({ illuminated: IlluminatedType.BORDER })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)

      Flex()
        .pointLight({
          lightSource: {
            intensity: this.lightIntensity,
            positionX: '50%',
            positionY: '50%',
            positionZ: 80
          },
          bloom: this.bloomValue
        })
        .animation({ duration: 333 })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)
        .onTouch((event: TouchEvent) => {
          // 按下时增强光源强度和发光强度，松开或取消时恢复默认效果。
          if (event.type === TouchType.Down) {
            this.lightIntensity = 1;
            this.bloomValue = 1;
          } else if (event.type === TouchType.Up || event.type === TouchType.Cancel) {
            this.lightIntensity = 0;
            this.bloomValue = 0;
          }
        })

      Flex()
        .pointLight({ illuminated: IlluminatedType.BORDER_CONTENT })
        .backgroundColor(0x307af7)
        .size({ width: 50, height: 50 })
        .borderRadius(25)
    }
    .justifyContent(FlexAlign.Center)
    .backgroundColor(Color.Black)
    .size({ width: '100%', height: '100%' })
  }
}
```

```TypeScript
### 示例1（使用不同裁剪属性）

该示例通过[clipShape](arkts-arkui-commonmethod-c.md#clipshape)、[clip](#clip12)、[maskShape](arkts-arkui-commonmethod-c.md#maskshape)实现图片的裁剪和遮罩。


```

```TypeScript
### 示例2（实现组件遮罩）

该示例通过[mask](#mask12)实现图片的遮罩。
```

```TypeScript
### 示例1（禁用默认点击音效）

该示例通过配置enableClickSoundEffect属性，实现组件禁用默认点击音效，开发者可以在onClick回调中调用音频相关接口自定义发音。自定义发音可参考[SoundPool播放短音频指南](../../../media/media/using-soundpool-for-playback.md)。

从API version 24开始，新增[enableClickSoundEffect](arkts-arkui-commonmethod-c.md#enableclicksoundeffect)属性。
```

```TypeScript
### 示例1（通过DrawModifier进行自定义绘制）

通过DrawModifier对[Text](ts-basic-components-text.md)组件进行自定义绘制。


```

```TypeScript
### 示例2（通过DrawModifier对容器的前景进行自定义绘制）

通过DrawModifier对[Column](ts-container-column.md)容器的前景进行自定义绘制。
```

```TypeScript
该示例主要演示前景滤镜、背景滤镜和合成滤镜的模糊效果。
```

```TypeScript
### 示例1（设置组件快捷键）

该示例通过设置组件的快捷键，同时按控制键+对应的字符可以触发组件响应快捷键，并触发onClick事件或自定义事件。


```

```TypeScript
### 示例2（快捷键的绑定和解除绑定）

该示例演示了如何实现快捷键的绑定和解除绑定。
```

```TypeScript
### 示例1（设置无障碍文本和无障碍说明）

该示例主要演示accessibilityText无障碍文本和accessibilityDescription无障碍说明的播报内容。
```

```TypeScript
### 示例2（设置无障碍组）

该示例主要演示优先使用子组件的无障碍文本进行朗读。
```

```TypeScript
### 示例3（设置首焦点和组件的下一个焦点）

该示例主要演示accessibilityDefaultFocus屏幕朗读当前页默认首焦点和accessibilityNextFocusId走焦过程中组件的下一个焦点。
```

```TypeScript
### 示例4（设置无障碍组件类型和文本提示信息）

该示例主要演示accessibilityRole无障碍组件类型和accessibilityTextHint设置组件的文本提示信息（仅在与车机交互的场景下供车机的无障碍服务监听并响应）。
```

```TypeScript
### 示例5（设置无障碍屏幕朗读滚动和焦点绿框绘制）

该示例主要演示accessibilityScrollTriggerable设置无障碍节点是否支持屏幕朗读滚动、accessibilityFocusDrawLevel设置无障碍焦点绿框的绘制层级和accessibilityUseSamePage为跨进程嵌入式显示的组件（如[EmbeddedComponent](ts-container-embedded-component.md)）设置同page模式。


```

```TypeScript
### 示例6（设置无障碍聚合功能下的子组件状态和操作接管功能）

该示例主要演示使用accessibilityGroup的可选参数stateControllerRoleType或者stateControllerId来选择一个特定子组件接管其无障碍状态信息，可选参数actionControllerRoleType或者actionControllerId来选择一个特定子组件接管其无障碍控制操作。
```

```TypeScript
### 示例7（设置无障碍组件状态播报信息）

该示例主要通过[accessibilityStateDescription](#accessibilitystatedescription23)接口修改组件的状态播报。在开启无障碍功能后，组件发生聚焦或者点击后，屏幕朗读进行组件的状态信息播报。

从API version 23开始，新增accessibilityStateDescription接口。
```

```TypeScript
### 示例8（设置无障碍操作选项修改组件滑动步数）

本示例主要演示如何通过[accessibilityActionOptions](ts-types.md#accessibilityactionoptions23对象说明)中的scrollStep参数，自定义组件的滑动步数。以下将以slider组件在屏幕朗读场景下滑动距离变化为例进行说明。

从API version 23开始，新增AccessibilityActionOptions。
```

```TypeScript
### 示例9（设置自定义无障碍操作）

本示例主要演示如何使用[accessibilityCustomActions](arkts-arkui-commonmethod-c.md#accessibilitycustomactions)为组件设置自定义无障碍操作。开发者可以按操作名为组件进行自定义操作的回调绑定。

从API版本26.0.0开始，新增accessibilityCustomActions。
```

```TypeScript
### 示例1（设置Text多态样式）

该示例展示了[stateStyles](#statestyles)设置状态为hovered、pressed和disabled时Text组件的样式变化。

从API版本26.0.0开始，[stateStyles](#statestyles)新增hovered属性。


```

```TypeScript
### 示例2（设置Radio多态样式）

该示例展示了状态为selected时Radio组件的样式变化。


```

```TypeScript
### 示例3（设置Builder多态样式）

该示例展示了状态为pressed时@Builder中自定义组件的样式变化。
```

```TypeScript
该示例主要展示如何通过组件标识接口，获取特定id组件的属性，以及如何向该id的组件触发事件。
```

```TypeScript
该示例通过animation实现了组件的属性动画。
```

```TypeScript
### 示例1（不同高度的半模态弹窗）

该示例通过height设置不同高度的半模态弹窗。


```

```TypeScript
### 示例2（设置三个不同高度的挡位）

使用bindSheet的detents属性设置三个不同高度的挡位。

dragBar控制条只在多个挡位高度时生效；

区别于height属性在不同时刻设置不同挡位的能力，多挡位能力有手势切换挡位高度的效果，且更适合固定高度区间的场景；

若高度范围不确定，且可能存在大于3个不同高度的场景，不建议使用detents属性。


```

```TypeScript
### 示例3（使用边框宽度和颜色）

bindSheet属性的borderWidth、borderColor属性值使用LocalizedEdgeWidths类型和LocalizedEdgeColors类型。

从左至右显示语言模式示例图



从右至左显示语言模式示例图


```

```TypeScript
### 示例4（使用关闭回调函数）

bindSheet注册onWillDismiss与onWillSpringBackWhenDismiss。


```

```TypeScript
### 示例5（设置内容区刷新时机）

ScrollSizeMode.CONTINUOUS持续更新内容适合detents多挡位切换场景。

建议在builder内减少UI加载耗时的操作，滑动时内容实时刷新对性能要求较高。

跟手触发挡位切换时，松手才触发面板内容高度刷新。



跟手触发挡位切换时，跟手时期就会触发面板内容高度刷新。


```

```TypeScript
### 示例6（设置压缩模态内容）

通过设置SheetKeyboardAvoidMode为RESIZE_ONLY，当键盘高度变化时，根据高度变化实现滚动组件的滚动。


```

```TypeScript
### 示例7（镜像场景下如何设置圆角属性）

此示例为说明镜像场景而设置了不同的圆角半径，通常不建议开发者设置不同的值，会造成视觉体验不佳。

其中，从API version 15开始，半模态的radius属性值使用LocalizedBorderRadiuses类型。

从左至右显示语言模式示例图



从右至左显示语言模式示例图


```

```TypeScript
### 示例8（半模态Side侧边样式）

从API version 20开始，此示例实现半模态侧边样式。


```

```TypeScript
### 示例9（半模态ContentCover全屏样式）

从API version 20开始，此示例实现半模态的全屏显示效果。


```

```TypeScript
### 示例10（半模态设置系统材质）

该示例通过半模态systemMaterial属性设置系统材质。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增systemMaterial属性。


```

```TypeScript
### 示例11（半模态自定义按钮材质）

该示例通过closeButtonMaterial属性自定义半模态关闭按钮的材质效果，对比未设置（使用systemMaterial内置材质）、关闭材质、自定义材质三种状态。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增closeButtonMaterial属性。

未设置closeButtonMaterial时，关闭按钮使用systemMaterial带来的内置材质效果。



设置closeButtonMaterial为uiMaterial.Material.empty时，关闭按钮无材质效果。



设置closeButtonMaterial为自定义材质时，关闭按钮使用自定义材质效果。


```

```TypeScript
### 示例12（半模态标题栏背景模糊）

该示例通过titleBarBackgroundBlur属性设置半模态标题栏背景渐变模糊效果。同时配合titleBarHoverMode设置为STACK堆叠模式，使标题栏悬浮于内容区上方时模糊效果可见。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增titleBarBackgroundBlur属性。


```

```TypeScript
### 示例13（半模态标题栏悬浮模式）

该示例通过titleBarHoverMode属性设置半模态标题栏为STACK堆叠模式，标题栏悬浮在内容区上方。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增titleBarHoverMode属性。


```

```TypeScript
### 示例14（半模态滚动条状态）

该示例通过scrollBarState属性设置半模态内容区滚动条的显示状态，点击按钮在[BarState](ts-appendix-enums.md#barstate)的Off、On、Auto和未设置之间切换。

从API版本26.1.0开始，[SheetOptions](arkts-arkui-sheetoptions-i.md)新增scrollBarState属性。
```

```TypeScript
### 示例1（支持滚动手势）

该示例通过设置[enableScrollInteraction](#enablescrollinteraction11)属性，实现了使用手势滚动纵向列表，并在当前显示界面发生改变时回调索引。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。


```

```TypeScript
### 示例2（设置边缘渐隐）

该示例通过设置[fadingEdge](#fadingedge14)属性，实现了[List](ts-container-list.md)组件开启边缘渐隐效果并设置边缘渐隐长度。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。


```

```TypeScript
### 示例3（设置裁剪区域）

该示例通过设置[clipContent](arkts-arkui-scrollablecommonmethod-c.md#clipcontent)属性，改变组件的内容层裁剪区域。


```

```TypeScript
### 示例4（设置滚动条边距）

从API version 20开始，该示例通过设置[scrollBarMargin](#scrollbarmargin20)属性，调整滚动组件的滚动条边距。

ListDataSource说明及完整代码参考[示例1（添加滚动事件）](./ts-container-list.md#示例1添加滚动事件)。
```

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  @State isShow: boolean = false

  build() {
    Stack({ alignContent: Alignment.Center }) {
      if (this.isShow) {
        Image($r('app.media.pic'))
          .autoResize(false)
          .clip(true)
          .width(300)
          .height(400)
          .offset({ y: 100 })
          .geometryTransition("picture", { hierarchyStrategy: TransitionHierarchyStrategy.ADAPTIVE })
          .transition(TransitionEffect.OPACITY)
      } else {
        // geometryTransition此处绑定的是容器，那么容器内的子组件需设为相对布局跟随父容器变化，
        // 套多层容器为了说明相对布局约束传递
        Column() {
          Column() {
            Image($r('app.media.icon'))
              .width('100%').height('100%')
          }.width('100%').height('100%')
        }
        .width(80)
        .height(80)
        // geometryTransition会同步圆角，但仅限于geometryTransition绑定处，此处绑定的是容器
        // 则对容器本身有圆角同步而不会操作容器内部子组件的borderRadius
        .borderRadius(20)
        .clip(true)
        .geometryTransition("picture", { hierarchyStrategy: TransitionHierarchyStrategy.ADAPTIVE })
        // transition保证组件离场不被立即析构，可设置其他转场效果
        .transition(TransitionEffect.OPACITY)
      }
    }
    .onClick(() => {
      this.getUIContext()?.animateTo({ duration: 1000 }, () => {
        this.isShow = !this.isShow;
      })
    })
  }
}
```

```TypeScript
### 示例1（弹出不同类型的气泡）

该示例通过配置[PopupOptions](#popupoptions类型说明)或[CustomPopupOptions](#custompopupoptions8类型说明)中的keyboardAvoidMode属性，设置气泡是否避让软键盘。

从API version 15开始，分别在PopupOptions和CustomPopupOptions中新增了keyboardAvoidMode属性。


```

```TypeScript
### 示例2（设置气泡的文本样式）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的messageOptions属性，实现了弹出自定义文本样式的气泡。


```

```TypeScript
### 示例3（设置气泡的样式）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的arrowHeight、arrowWidth、radius、shadow和popupColor属性，实现了气泡箭头以及气泡本身的样式。


```

```TypeScript
### 示例4（设置气泡的动效）

该示例通过配置[PopupOptions](#popupoptions类型说明)或[CustomPopupOptions](#custompopupoptions8类型说明)中的transition属性，实现了气泡显示以及退出的动效。


```

```TypeScript
### 示例5（为气泡添加事件）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的onWillDismiss属性，实现了当气泡退出时，拦截退出事件并执行回调函数。


```

```TypeScript
### 示例6（为气泡拦截退出事件）

该示例将[PopupOptions](#popupoptions类型说明)的onWillDismiss属性设为false，使气泡不响应退出事件。同时，配置[PopupOptions](#popupoptions类型说明)的followTransformOfTarget属性，设置气泡是否跟随宿主组件变换。


```

```TypeScript
### 示例7（为气泡内外描边设置线性渐变）

该示例通过配置[PopupOptions](#popupoptions类型说明)中的outlineWidth、borderWidth、outlineLinearGradient、borderLinearGradient属性，为气泡设置内外描边线性渐变的颜色和方向。

从API version 20开始，在PopupOptions中新增了outlineWidth、borderWidth、outlineLinearGradient、borderLinearGradient属性。


```

```TypeScript
### 示例8（设置气泡避让绑定的组件模式）

该示例通过配置[PopupOptions](#popupoptions类型说明)的avoidTarget属性，实现气泡对其绑定组件的避让。

从API version 20开始，在PopupOptions中新增了avoidTarget属性。


```

```TypeScript
### 示例9（设置Popup的沉浸光感视觉效果）

该示例通过[PopupOptions](#popupoptions类型说明)中的systemMaterial属性设置组件的系统材质，实现了Popup的沉浸光感视效。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在PopupOptions中新增了systemMaterial属性。

未设置系统材质时：



设置系统材质后：


```

```TypeScript
### 示例10（自定义气泡背景效果参数）

该示例通过配置[PopupOptions](#popupoptions类型说明)的backgroundBlurStyleOptions和backgroundEffect属性，实现自定义气泡背景效果。

从API版本26.0.0开始，在PopupOptions中新增了backgroundBlurStyleOptions和backgroundEffect属性。


```

```TypeScript
### 示例11（设置气泡的显示层级模式）

该示例通过配置[PopupOptions](#popupoptions类型说明)的levelMode属性，实现气泡在页面内嵌入显示。点击按钮后页面级的气泡不会显示在下一个路由页面中。

从API版本26.0.0开始，在PopupOptions中新增了levelMode属性。
```

```TypeScript
PageTwo页面：
```

```TypeScript
### 示例1（获取轴事件相关参数）

该示例中，对按钮设置轴事件，通过滚动鼠标滚轮可获取轴事件的相关参数。从API version 21开始，该示例通过[BaseEvent](./ts-universal-events-click.md#baseevent8)的属性和[getPinchAxisScaleValue](arkts-arkui-axisevent-i.md#getpinchaxisscalevalue)获取双指缩放比例；从API version 22开始，该示例通过[hasAxis](arkts-arkui-axisevent-i.md#hasaxis)判断轴事件是否包含指定的轴类型。

鼠标滚轮滚动时：


```

```TypeScript
### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取鼠标光标位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
### 示例1（设置组件宽高比）

通过aspectRatio设置不同的宽高比。

图1 竖屏显示

图2 横屏显示
```

```TypeScript
### 示例2（设置组件显示优先级）

使用displayPriority为子组件设置显示优先级。
```

```TypeScript
### 示例1（触发onKeyEvent回调）

该示例为按钮设置按键事件。按钮获焦时，按下按键可触发onKeyEvent回调。按键事件触发的流程和具体时机参考[按键事件数据流](../../../ui/arkts-interaction-development-guide-keyboard.md#按键事件数据流)。


```

```TypeScript
### 示例2（获取Unicode码值）

该示例通过按键事件获取所按按键的Unicode码值。


```

```TypeScript
### 示例3（触发onKeyPreIme回调）

该示例使用onKeyPreIme屏蔽输入框中的方向左键。
```

```TypeScript
### 示例4（使用stopPropagation阻止冒泡）

该示例使用stopPropagation阻止事件冒泡。即，通过在Button的onKeyEvent回调中加入event.stopPropagation()方法，达到“仅Button响应键盘事件，Column不响应”的效果。

> 说明：
> 
> onKeyEvent事件默认是冒泡的。
> 
> 事件冒泡：在一个树形结构中，当子节点处理完一个事件后，再将该事件交给它的父节点处理。
> 
> 可以在[onKeyEvent15+](#onkeyevent15)中，通过返回true消费按键事件阻止冒泡，效果等同于stopPropagation。
```

```TypeScript
### 示例1（设置onAccessibilityActionIntercept拦截点击事件）

该示例演示在无障碍模式下，通过onAccessibilityActionIntercept事件在Toggle组件点击事件触发前进行拦截，并弹出确认对话框由用户确认是否放行该点击事件。
```

```TypeScript
### 示例2（设置onAccessibilityFocus回调函数）

从API version 18开始，当获焦、失焦状态发生变化时，触发该回调函数。本示例展示了[onAccessibilityFocus](arkts-arkui-commonmethod-c.md#onaccessibilityfocus)的基本用法，聚焦到"onAccessibilityFocus takes effect"时，会打印"[testingTag] isFocus current is true"，当聚焦到"onAccessibilityFocus takes effect"以外的位置时，会打印"[testingTag] isFocus current is false"。
```

```TypeScript
该示例通过onTouchIntercept修改组件的HitTestMode属性。
```

```TypeScript
### 示例1（基本样式用法）

设置边框的宽度、颜色、圆角半径以及点、线样式。


```

```TypeScript
### 示例2（边框宽度、圆角半径和颜色类型）

border属性的width、radius、color属性值分别使用LocalizedEdgeWidths类型、LocalizedBorderRadiuses类型和LocalizedEdgeColors类型。

从左至右（LTR）显示语言示例图



从右至左（RTL）显示语言示例图


```

```TypeScript
### 示例3（设置离屏圆角）

从API version 22开始，该示例支持设置组件绘制圆角的模式。

快速绘制模式（RenderStrategy.FAST）通过GPU硬件加速进行实时绘制，适用于普通圆角场景；离屏绘制模式（RenderStrategy.OFFSCREEN）将组件先绘制到离屏缓冲区再合成，适用于包含模糊、滚动等复杂内容的圆角场景，可避免圆角裁剪异常。设置在线绘制模式（上方）以及离屏绘制模式（下方）的示例图如下：


```

```TypeScript
### 示例4（设置异形圆角）

该示例通过[borderRadius](#borderradius)设置四个不同圆角值。当其中一个圆角值超过高度或宽度最小值的一半时，按值的比例绘制异形圆角。
```

```TypeScript
### 示例1（设置组件堆叠顺序）

该示例通过zIndex设置组件堆叠顺序。

Stack容器内子组件不设置zIndex时，默认按照声明顺序显示，后声明的组件会覆盖在先声明的组件上方。



Stack容器子组件设置zIndex后的效果。


```

```TypeScript
### 示例2（动态修改zIndex属性）

该示例使用Button组件动态修改zIndex属性。

不点击Button修改zIndex值的效果。



点击Button动态修改zIndex，使Text1和Text2的zIndex相等，因为在点击Button前的层级顺序上根据zIndex进行稳定排序，层级顺序不发生改变。



点击Button动态修改zIndex，使Text2的zIndex大于Text1，层级顺序发生改变。


```

```TypeScript
### 示例3（设置不同容器内组件的zIndex属性）

该示例在不同容器内设置zIndex属性。其中，Text1、Text2在同一个Stack容器内，Text3在另一个Stack容器内。虽然Text3的zIndex值最小，但Text1、Text2仍无法根据zIndex值显示在Text3的上方。
```

```TypeScript
### 示例1（设置组件的宽高和边距）

设置组件的宽度、高度、内边距及外边距。


```

```TypeScript
### 示例2（LocalizedPadding和LocalizedMargin类型的使用）

使用LocalizedPadding类型和LocalizedMargin类型定义padding和margin属性。

从左至右显示语言示例图



从右至左显示语言示例图


```

```TypeScript
### 示例3（设置组件级安全区）

对容器设置组件级安全区。


```

```TypeScript
### 示例4（使用attributeModifier动态设置安全区）

使用attributeModifier对容器设置组件级安全区。


```

```TypeScript
### 示例5（设置布局策略）

对容器大小设置布局策略。


```

```TypeScript
### 示例6（子组件单方向设置matchParent效果）

该示例展示Column组件自适应子组件且子组件仅单方向设置matchParent时的布局效果。从API版本26.0.0开始，Column组件高度自适应第一个和第二个子组件，宽度自适应第一个和第三个子组件。
```

```TypeScript
### 示例1（逐帧布局的效果）

以下示例通过改变Text组件宽度实现逐帧布局的效果。


```

```TypeScript
### 示例2（折线的动画效果）

以下示例实现折线的动画效果。
```

```TypeScript
### 示例1（对齐方式和主轴方向上的布局）

设置内容在元素内的对齐方式和子元素在父组件主轴方向上的布局。


```

```TypeScript
### 示例2（位置偏移）

基于父组件、相对定位、锚点作出位置偏移。


```

```TypeScript
### 示例3（绝对定位和相对偏移）

使用position设置绝对定位，确定子组件相对父组件的位置。使用offset设置相对偏移，组件相对原本的布局位置进行偏移。


```

```TypeScript
### 示例4（镜像效果）

通用布局属性支持[使用镜像能力](./../../../ui/arkts-internationalization.md#使用镜像能力)。下述示例从上到下依次通过[position](#position)、[offset](#offset)和[markAnchor](#markanchor)实现镜像效果，为对比镜像前后的差异，浅蓝色对应镜像前效果，深蓝色对应镜像后效果。

镜像前效果：



镜像后效果如下，镜像生效条件请参考[使用镜像能力](./../../../ui/arkts-internationalization.md#使用镜像能力)：


```

```TypeScript
### 示例5（align属性适配镜像特性）

设置内容在元素内的对齐方式和子元素在父组件主轴方向上的布局。


```

```TypeScript
### 示例6（layoutGravity属性单独设置Stack组件中子组件的对齐规则）

更改Stack中Text的位置。
```

```TypeScript
该示例主要显示通过[opacity](#opacity)设置组件的不透明度。
```

```TypeScript
该示例通过为[Navigation](ts-basic-components-navigation.md)下的[Button](ts-basic-components-button.md)组件绑定toolbar通用属性，为标题栏NavBar分栏开头位置添加包含两个[Button](ts-basic-components-button.md)组件的工具栏项。为[NavDestination](ts-basic-components-navdestination.md)下的[Text](ts-basic-components-text.md)组件绑定toolbar通用属性，为标题栏NavDestination分栏末尾位置添加两个工具栏项，分别包含一个滑动条组件和一个搜索框组件。
```

```TypeScript
### 示例1（允许拖拽和落入）

示例1通过配置[allowDrop](arkts-arkui-commonmethod-c.md#allowdrop)设置组件是否可落入，通过配置[draggable](#draggable)设置组件是否可拖拽。


```

```TypeScript
### 示例2（设置预览图）

示例2通过配置[dragPreview](#dragpreview11)设置拖拽过程的预览图。


```

```TypeScript
### 示例3（设置背板图样式）

示例3通过配置[dragPreviewOptions](#dragpreviewoptions11)为ENABLE_DEFAULT_SHADOW、ENABLE_DEFAULT_RADIUS设置默认阴影和统一圆角效果。从API version 18开始，通过配置[dragPreviewOptions](#dragpreviewoptions11)为ENABLE_DRAG_ITEM_GRAY_EFFECT设置灰显效果。


```

```TypeScript
### 示例4（设置多选拖拽）

示例4通过配置[isMultiSelectionEnabled](arkts-arkui-draginteractionoptions-i.md)实现Grid组件的多选拖拽效果。


```

```TypeScript
### 示例5（设置默认点按效果）

示例5通过配置[defaultAnimationBeforeLifting](arkts-arkui-draginteractionoptions-i.md)实现Grid组件的默认点按效果。


```

```TypeScript
### 示例6（自定义背板图样式）

示例6通过配置[ImageModifier](arkts-arkui-imagemodifier-t.md)实现Image组件的自定义背板图样式。


```

```TypeScript
### 示例7（图片拖拽设置）

示例7展示了不同图片（在线图片资源、本地图片资源和PixelMap）在拖拽时组件的设置。

使用网络图片时，需要申请权限ohos.permission.INTERNET。具体申请方式请参考[声明权限](../../../security/AccessToken/declare-permissions.md)。


```

```TypeScript
### 示例8（设置图片拖拽震动）

从API version 18开始，示例8通过设置[enableHapticFeedback](arkts-arkui-draginteractionoptions-i.md)实现图片拖拽的震动效果。
```

```TypeScript
### 示例9（自定义预览图）

从API version 15开始，示例9通过配置[onlyForLifting](./ts-universal-events-drag-drop.md#previewconfiguration15)实现自定义预览图，仅用于浮起效果以及配置[isLiftingDisabled](arkts-arkui-draginteractionoptions-i.md)实现禁用浮起效果。

自定义预览图用于浮起效果。



自定义预览图禁用浮起效果。


```

```TypeScript
### 示例10（以拖拽预览图初始尺寸计算跟手点位置）

从API version 19开始，示例10通过配置[DragPreviewMode](#dragpreviewmode11枚举说明)为ENABLE_TOUCH_POINT_CALCULATION_BASED_ON_FINAL_PREVIEW实现基于最终拖拽预览图的原始尺寸来计算拖拽过程中跟手点位置。当设置[DragPreviewMode](#dragpreviewmode11枚举说明)为ENABLE_MULTI_TILE_EFFECT时，该属性不生效。


```

```TypeScript
### 示例11（长按浮起预览图与拖拽预览图过渡动效）

从API version 19开始，示例11通过配置[DraggingSizeChangeEffect](#draggingsizechangeeffect19枚举说明)实现不同拖拽过渡效果。


```

```TypeScript
### 示例12（设置自定义组件落入）

从API version 23开始，示例12通过组件的[onDragStart](ts-universal-events-drag-drop.md#ondragstart)接口传递其类型，并在目标组件的[allowDrop](arkts-arkui-commonmethod-c.md#allowdrop)属性中设置允许该类型落入，即可实现自定义组件的拖拽落入功能。


```

```TypeScript
### 示例13（设置背板图材质效果）

该示例通过配置[ImageModifier](arkts-arkui-imagemodifier-t.md)中的[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)属性，设置拖拽背板的材质效果。

从API版本26.0.0开始，[DragPreviewOptions](#dragpreviewoptions11-1)接口中的modifier参数新增支持[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)属性。
```

```TypeScript
### 示例1（if else范式下的共享元素实现）

该示例主要演示if else范式下的共享元素效果集成。


```

```TypeScript
### 示例2（if范式下使用follow实现跟随效果）

该示例主要演示if范式下使用follow参数实现不下树的组件的跟随效果。
```

```TypeScript
该示例通过按钮控制组件的挂载和卸载，触发onAttach和onDetach事件。
```

```TypeScript
### 示例1（使用前景色设置）

该示例主要演示通过foregroundColor设置前景色。


```

```TypeScript
### 示例2（设置前景色为组件背景色反色）

该示例通过[ColoringStrategy](ts-appendix-enums.md#coloringstrategy10).INVERT将前景色设置为背景色反色。


```

```TypeScript
### 示例3（前景色未继承父组件）

该示例主要演示组件同时设置前景色和背景色与只设置背景色的效果对比。
```

```TypeScript
### 示例1（通过responseRegion接口设置触摸热区）

该示例通过responseRegion设置按钮的触摸热区以响应点击事件。


```

```TypeScript
### 示例2（通过responseRegionList接口设置触摸热区）

该示例通过[responseRegionList](arkts-arkui-commonmethod-c.md#responseregionlist)设置按钮的触摸热区以响应点击事件。

从API version 22开始，新增responseRegionList接口。


```

```TypeScript
### 示例3（设置鼠标的触摸热区以响应点击事件）

该示例通过[mouseResponseRegion](arkts-arkui-commonmethod-c.md#mouseresponseregion)设置鼠标的触摸热区以响应点击事件。
```

```TypeScript
该示例通过obscured对Text、Image组件实现了隐私遮罩效果。
```

```TypeScript
设置不同设备类型下的栅格配置。gridSpan和gridOffset用于设置默认占用列数和偏移列数，仅在useSizeType未配置对应尺寸时生效。示例中useSizeType配置了sm尺寸的值（span: 2, offset: 1），若要在其他未配置的尺寸下实现相同的栅格效果，可通过gridSpan和gridOffset设置默认值。

> 说明：
> 
> 本示例展示的是已废弃接口的用法。建议使用新组件[GridCol](ts-container-gridcol.md)、[GridRow](ts-container-gridrow.md)来实现栅格布局。
```

```TypeScript
该示例主要演示不同组件的点击回弹效果。
```

```TypeScript
### 示例1（为组件添加图形变换效果）

该示例通过[rotate](#rotate)、[translate](#translate)、[scale](#scale)、[transform](#transform)为组件添加旋转、平移、缩放、变换矩阵效果。


```

```TypeScript
### 示例2（设置旋转视距）

该示例通过[perspective](#rotateoptions对象说明)为组件添加视距效果。


```

```TypeScript
### 示例3（按中心点旋转）

该示例通过设置[rotate](#rotate)和[transform](#transform)为不同的参数实现相同的旋转效果。


```

```TypeScript
### 示例4（通过transform3D实现图形变换）

从API version 20开始，该示例通过设置[transform3D](arkts-arkui-commonmethod-c.md#transform3d)实现图形变换效果。


```

```TypeScript
### 示例5（按各轴旋转角的方式实现旋转）

从API version 20开始，该示例通过设置rotate的[RotateAngleOptions](#rotateangleoptions20对象说明)参数实现旋转效果。
```

```TypeScript
示例代码为点击图片所在区域跳转页面时，显示共享元素图片的自定义转场动效。
```

```TypeScript
// PageB.ets
@Entry
@Component
struct PageBExample {
  build() {
    Stack() {
      // $r('app.media.ic_health_heart')需要替换为开发者所需的图像资源文件。
      Image($r('app.media.ic_health_heart')).width(150).height(150)
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 })
    }.width('100%').height('100%')
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

```TypeScript
### 示例1（实现沉浸式效果）

该示例通过设置expandSafeArea属性向顶部和底部扩展安全区实现沉浸式效果。


```

```TypeScript
### 示例2（同时设置固定宽高和expandSafeArea属性）

该示例展示了同时设置固定宽高和expandSafeArea属性的效果。

如下图：Column组件扩展至了顶部状态栏[SafeAreaEdge.TOP]，未扩展至底部导航条[SafeAreaEdge.BOTTOM]，扩展后的组件高度维持设置值不变。


```

```TypeScript
### 示例3（键盘避让时固定背景图位置）

该示例通过为背景图组件设置expandSafeArea属性，来实现拉起键盘进行避让时，背景图保持不动的效果。


```

```TypeScript
### 示例4（设置键盘避让模式为压缩）

该示例通过调用setKeyboardAvoidMode设置键盘避让模式为RESIZE模式，实现键盘抬起时page的压缩效果。
```

```TypeScript

```

```TypeScript
### 示例5（设置键盘避让模式为上抬）

该示例通过调用setKeyboardAvoidMode设置键盘避让模式为OFFSET模式，实现键盘抬起时page的上抬效果。但当输入光标距离屏幕底部的高度大于键盘高度时，page不会抬起，如本例中所示。
```

```TypeScript

```

```TypeScript
### 示例6（切换避让模式）

该示例通过调用setKeyboardAvoidMode来实现OFFSET、RESIZE和NONE模式之间的切换，实现三种不同的键盘避让效果。


```

```TypeScript
### 示例7（滚动类容器扩展安全区）

该示例通过在滚动类容器内调用expandSafeArea属性实现沉浸式效果，Scroll内的Swiper可以延伸到状态栏上。


```

```TypeScript
### 示例8（ignoreLayoutSafeArea延伸组件布局范围）

该示例利用[ignoreLayoutSafeArea](#ignorelayoutsafearea20)改变组件位置。相比未使用该属性，配置ignoreLayoutSafeArea后，Row组件基于Stack内容区、Stack组件级安全区、系统状态栏共同组成的范围，取其左上部分，作左上对齐。


```

```TypeScript
### 示例9（ignoreLayoutSafeArea配合LayoutPolicy.matchParent延伸组件布局范围）

该示例利用[ignoreLayoutSafeArea](#ignorelayoutsafearea20)和[LayoutPolicy.matchParent](ts-universal-attributes-size.md#layoutpolicy15)同时改变组件大小和位置。相比未使用该属性，配置ignoreLayoutSafeArea后，Row组件基于Stack内容区、Stack组件级安全区，取其右下部分并撑满可用空间。


```

```TypeScript
### 示例10（expandSafeArea与ignoreLayoutSafeArea的区别）

该示例展示了容器分别设置了expandSafeArea和ignoreLayoutSafeArea的布局效果和各自对子组件布局效果的影响。两种设置下，容器都可见地进行了延伸，但前者的子组件不受延伸影响，后者的子组件因父容器的延伸改变了位置。
```

```TypeScript
该示例通过enabled设置按钮是否可交互。
```

```TypeScript
### 示例1（设置渐变色边框）

通过[borderImage](arkts-arkui-commonmethod-c.md#borderimage)接口为组件设置渐变色边框。


```

```TypeScript
### 示例2（动态调整属性值）

通过[Slider](../../apis-arkui/arkui-js/js-components-basic-slider.md)接口动态调整[borderImage](arkts-arkui-commonmethod-c.md#borderimage)接口中属性值。


```

```TypeScript
### 示例3（使用LocalizedEdgeWidths类型值）

通过[borderImage](arkts-arkui-commonmethod-c.md#borderimage)接口中的slice、width和outset属性值使用[LocalizedEdgeWidths](ts-types.md#localizededgewidths12)类型。
```

```TypeScript
### 示例1（父组件优先识别手势和父子组件同时触发手势）

该示例通过配置priorityGesture和parallelGesture分别实现了父组件优先识别手势和父子组件同时触发手势。


```

```TypeScript
### 示例2（实时监测参与滑动手势的有效触点数量）

该示例通过读取fingerInfos实时监测参与滑动手势的有效触点数量。
```

```TypeScript
### 示例1 (使用onAccessibilityHover事件)

该示例主要演示使用onAccessibilityHover事件，对无障碍模式下的按钮进行设置。
```

```TypeScript
### 示例2 (捕获无法无障碍聚焦的组件的触摸事件)

该示例代码在无障碍模式下通过onAccessibilityHoverTransparent接口捕获无法无障碍聚焦的组件的触摸事件，最后再将事件信息显示在组件下方的文本中。

从API version 20开始，新增了[onAccessibilityHoverTransparent](arkts-arkui-commonmethod-c.md#onaccessibilityhovertransparent)接口。
```

```TypeScript
### 示例1（设置背景基础样式）

该示例通过配置backgroundColor、backgroundImage、backgroundImageSize和backgroundImagePosition设置背景的基础样式。


```

```TypeScript
### 示例2（设置背景模糊样式）

该示例通过backgroundBlurStyle设置背景模糊样式。


```

```TypeScript
### 示例3（设置组件背景）

该示例通过background设置组件背景。


```

```TypeScript
### 示例4（设置组件背景提亮效果）

该示例通过backgroundBrightness设置组件背景提亮效果。

效果图如下：

rate和lightUpDegree参数值为0.5,0.5：



修改rate和lightUpDegree参数值为0.5,-0.1：



去掉backgroundBrightness的设置，效果如下：


```

```TypeScript
### 示例5（设置模糊属性）

该示例提供了模糊属性的实现方法。通过blur设置内容模糊，通过backdropBlur设置背景模糊。


```

```TypeScript
### 示例6（设置文字异形模糊效果）

该示例通过[blendMode](ts-universal-attributes-image-effect.md#blendmode11)和backgroundEffect实现文字异形模糊效果。如果出现漏线问题，开发者应首先确保两个blendMode所在组件大小严格相同。如果确认相同，可能是组件边界落在浮点数坐标上导致，可尝试设置[pixelRound](ts-universal-attributes-pixelRoundForComponent.md#pixelround)通用属性，使产生的白线、暗线两侧的组件边界对齐到整数像素坐标上。


```

```TypeScript
### 示例7（模糊效果对比）

该示例对比了[backgroundEffect11+](#backgroundeffect11)、[backdropBlur](arkts-arkui-commonmethod-c.md#backdropblur)和[backgroundBlurStyle9+](#backgroundblurstyle9)三种不同的模糊效果。


```

```TypeScript
### 示例8（设置P3色域背景效果）

从API version 20开始，该示例通过[backgroundColor](#backgroundcolor20)设置P3色域背景效果。


```

```TypeScript
### 示例9（设置组件背景扩展）

从API version 20开始，该示例通过[background](#background10)实现组件背景扩展到父组件的安全区。
```

```TypeScript
该示例主要演示通过renderFit设置宽高动画过程中的组件内容不同填充方式。
```

```TypeScript
该示例演示背景模糊等特效的绘制合并。
```

```TypeScript
该示例通过reuseId标识自定义组件的复用组。
```

```TypeScript
### 示例1（弹出普通菜单）

该示例为bindMenu通过配置[MenuElement](arkts-arkui-menuelement-i.md)弹出普通菜单。


```

```TypeScript
### 示例2（弹出自定义菜单）

该示例为bindMenu通过配置CustomBuilder弹出自定义菜单。同时，从API version 18开始支持通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的hapticFeedbackMode属性实现菜单弹出时的振动效果。


```

```TypeScript
### 示例3（长按弹出菜单）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress弹出菜单。


```

```TypeScript
### 示例4（右键弹出指向型菜单）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).RightClick和[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的enableArrow属性弹出指向型菜单。同时，从API version 18开始支持通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的hapticFeedbackMode属性实现菜单弹出时的振动效果。


```

```TypeScript
### 示例5（长按弹出菜单的截图预览样式）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress和[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中preview属性的[MenuPreviewMode](arkts-arkui-menupreviewmode-e.md)类型弹出菜单预览样式。


```

```TypeScript
### 示例6（长按弹出菜单的自定义预览样式）

该示例为bindContextMenu通过配置[responseType](ts-appendix-enums.md#responsetype8).LongPress和[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中preview属性的[CustomBuilder](ts-types.md#custombuilder8)类型弹出菜单自定义预览样式。


```

```TypeScript
### 示例7（设置状态变量弹出菜单）

该示例为[bindContextMenu](arkts-arkui-commonmethod-c.md#bindcontextmenu)通过配置isShown弹出菜单预览样式。


```

```TypeScript
### 示例8（设置菜单和预览的动效）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的transition属性，实现自定义菜单以及菜单预览时的显示和退出动效。


```

```TypeScript
### 示例9（设置symbol类型图标）

该示例为bindMenu通过配置[MenuElement](arkts-arkui-menuelement-i.md)的symbolIcon弹出菜单。


```

```TypeScript
### 示例10（设置一镜到底动效）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中previewAnimationOptions属性的hoverScale，实现组件截图到自定义预览图的一镜到底过渡动效。


```

```TypeScript
### 示例11（自定义背景模糊效果参数）

该示例为bindMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的backgroundBlurStyleOptions属性，实现了自定义菜单背景模糊效果。

从API version 18开始，在ContextMenuOptions中新增了backgroundBlurStyleOptions属性。


```

```TypeScript
### 示例12（自定义背景效果参数）

该示例为bindMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的backgroundEffect属性，实现了自定义菜单背景效果。

从API version 18开始，在ContextMenuOptions中新增了backgroundEffect属性。


```

```TypeScript
### 示例13（设置一镜到底动效支持抬手打断）

该示例通过为bindContextMenu配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的previewAnimationOptions属性实现了一镜到底过渡动效的同时，再配置hoverScaleInterruption控制是否允许长按抬手取消菜单弹出。

从API version 20开始，在previewAnimationOptions的类型[ContextMenuAnimationOptions](arkts-arkui-contextmenuanimationoptions-i.md)中新增了hoverScaleInterruption属性。


```

```TypeScript
### 示例14（设置预览图边框圆角半径）

该示例通过bindContextMenu配置[responseType](ts-appendix-enums.md#responsetype8).LongPress来实现功能。同时，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中配置preview属性的[MenuPreviewMode](arkts-arkui-menupreviewmode-e.md)类型来设置菜单预览样式。最后，通过设置previewBorderRadius来实现预览图边框的圆角半径。

从API version 19开始，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了previewBorderRadius属性。


```

```TypeScript
### 示例15（bindMenu配置生命周期回调）

该示例为bindMenu11+配置生命周期回调。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了onWillAppear、onDidAppear、onWillDisappear和onDidDisappear属性。


```

```TypeScript
### 示例16（设置菜单蒙层）

该示例为bindMenu通过配置mask属性设置菜单蒙层。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了mask属性。


```

```TypeScript
### 示例17（bindMenu设置下拉菜单外描边样式）

该示例为bindMenu通过配置outlineWidth和outlineColor属性设置下拉菜单外描边样式。

从API version 20开始，在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了outlineWidth和outlineColor属性。


```

```TypeScript
### 示例18（bindMenu传入带参数的CustomBuilder）

该示例通过在bindMenu中传入带参数的CustomBuilder来配置菜单的具体属性。


```

```TypeScript
### 示例19（根据触发方式弹出不同内容的菜单）

该示例通过在[bindContextMenuWithResponse](arkts-arkui-commonmethod-c.md#bindcontextmenuwithresponse)中传入CustomBuilderT<ResponseType>给目标组件绑定菜单，组件会在UI函数中返回弹出菜单的触发方式，开发者可根据返回的触发方式实现差异化显示。

从API version 23开始，新增了bindContextMenuWithResponse的接口。


```

```TypeScript
### 示例20（设置菜单避让软键盘）

该示例通过在bindMenu中配置keyboardAvoidMode设置菜单避让软键盘，通过minKeyboardAvoidDistance设置菜单避让软键盘的最小距离。

从API version 23开始，[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增keyboardAvoidMode、minKeyboardAvoidDistance属性。


```

```TypeScript
### 示例21（设置菜单相对于绑定组件左上角的弹出位置）

该示例通过设置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的anchorPosition属性，实现了菜单相对于绑定组件左上角弹出的效果。

从API version 20开始，在ContextMenuOptions中新增了anchorPosition属性。


```

```TypeScript
### 示例22（设置菜单的最大高度）

该示例为bindContextMenu通过配置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的maxHeight属性，设置菜单的最大高度。

未设置maxHeight属性时，默认按照菜单的最大高度（可用高度的80%），可展示全部列表项，通过设置最大高度为窗口可用高度的50%时，仅能显示8个列表项。

从API版本26.0.0开始，在ContextMenuOptions中新增了maxHeight属性。


```

```TypeScript
### 示例23（设置菜单与目标组件间距）

该示例通过设置[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的targetSpace属性，介绍如何增加菜单与目标组件之间的间距。

从API版本26.0.0开始，在ContextMenuOptions中新增了targetSpace属性。


```

```TypeScript
### 示例24（设置菜单的沉浸光感）

该示例通过[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中的systemMaterial属性设置组件的系统材质，实现了菜单的沉浸光感视效。设置系统材质后，Menu弹出过程中会有非线性形变和边缘流光。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，在ContextMenuOptions中新增了systemMaterial属性。

未设置系统材质时：



设置系统材质后：


```

```TypeScript
### 示例25（使用gridStyle设置栅格菜单）

该示例展示了如何在[bindContextMenuByIsShow](arkts-arkui-commonmethod-c.md#bindcontextmenubyisshow)中使用gridStyle设置栅格菜单样式。通过设置count、horizontalSize和position属性，可以自定义菜单的栅格布局。

从API版本26.0.0开始，新增了[bindContextMenuByIsShow](arkts-arkui-commonmethod-c.md#bindcontextmenubyisshow)的接口；在[ContextMenuOptions](arkts-arkui-contextmenuoptions-i.md)中新增了gridStyle属性。
```

```TypeScript
### 示例1（获取鼠标事件相关参数）

该示例通过按钮设置了鼠标事件，通过鼠标点击按钮可以触发[onMouse](#onmouse)事件，获取鼠标事件相关参数。从API version 15开始，可以获取鼠标事件[MouseEvent](#mouseevent对象说明)的targetDisplayId、rawDeltaX、rawDeltaY、pressedButtons等参数。

鼠标滚轮的处理请参考[轴事件示例](ts-universal-events-axis.md#示例)。

示意图：

鼠标点击时：


```

```TypeScript
### 示例2（获取当前帧历史点）

该示例通过调用[getHistoricalPoints](#gethistoricalpoints)接口，获取当前帧的历史点，可以用来实现更平滑的绘制等操作。

从API版本26.0.0开始，新增getHistoricalPoints接口。
```

```TypeScript
### 示例3（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取鼠标位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
该示例通过配置visibility的不同值，实现不同的显隐控制效果。
```

```TypeScript
### 示例1（设置事件派发策略为FORWARD_COMPETITION）

在该示例中，点击List下方空白区域后拖动，可使List滑动。点击Button按钮时，Button会响应onClick事件。


```

```TypeScript
### 示例2（设置事件派发策略为FORWARD）

点击List下方空白区域后拖动，可以滑动List。点击Button按钮时，Button不会响应onClick事件。


```

```TypeScript
### 示例3（设置事件派发策略为DEFAULT）

点击List下方空白区域后拖动，List不会滑动。点击Button按钮时，Button会响应onClick事件。
```

```TypeScript
// xxx.ets
@Entry
@Component
struct TouchableExample {
  @State text1: string = '';
  @State text2: string = '';

  build() {
    Stack() {
      Rect()
        .fill(Color.Gray).width(150).height(150)
        .onClick(() => {
          console.info(this.text1 = 'Rect Clicked');
        })
        .overlay(this.text1, { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
      Ellipse()
        .fill(Color.Pink).width(150).height(80)
        .touchable(false) // 点击Ellipse区域，不会打印 “Ellipse Clicked”
        .onClick(() => {
          console.info(this.text2 = 'Ellipse Clicked');
        })
        .overlay(this.text2, { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
    }.margin(100);
  }
}
```

```TypeScript
该示例通过restoreId设置了List组件的分布式迁移标识。
```

```TypeScript
该示例主要演示使用[animateToImmediately](#animatetoimmediately)接口实现显式动画立即下发。
```

```TypeScript
该示例主要演示如何设置组件进行位移动画时的运动路径。此方法仅配置运动路径参数，需配合animateTo等动画触发方法及组件属性状态变化才能产生实际的位移动画效果，单独设置motionPath不会触发动画。
```

```TypeScript
### 示例1（获取点击事件相关参数）

该示例通过按钮设置点击事件[ClickEvent](arkts-arkui-clickevent-i.md)，点击按钮可获取点击事件的相关参数。


```

```TypeScript
### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取当前组件基于其实时位置的左上角坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
当父组件出现1px的缝隙时，应利用pixelRound来指导布局调整。
```

```TypeScript
### 示例1（获取指定范围的文本内容）

该示例主要演示如何通过[TextAreaController](ts-basic-components-textarea.md#textareacontroller8)控制器调用[getText](#gettext19)接口，获取输入框中指定范围内的文本内容。

从API version 19开始，新增getText接口。
```

```TypeScript
### 示例1（使用同一接口实现图片出现消失）

该示例主要演示如何通过同一[TransitionEffect](#transitioneffect10对象说明)来实现图片的出现与消失，出现和消失互为逆过程。

示意图：
```

```TypeScript
### 示例2（使用不同接口实现图片出现消失）

该示例主要演示使用不同[TransitionEffect](#transitioneffect10对象说明)来实现图片的出现和消失。

示意图：
```

```TypeScript
### 示例3（设置父子组件为transition）

该示例主要演示通过父子组件都配置[transition](#transition)来实现图片的出现和消失。

示意图：
```

```TypeScript
### 示例4（visibility切换时的双动画复合效果）

该示例演示当[visibility](ts-universal-attributes-visibility.md#visibility)在Visibility.Visible与Visibility.None之间切换时，[transition](#transition)动画与布局动画叠加形成双动画复合表现的效果。
```

```TypeScript
### 示例1（嵌套滚动）

该示例通过shouldBuiltInRecognizerParallelWith和onGestureRecognizerJudgeBegin实现了嵌套滚动的功能。内部组件优先响应滑动手势，当内部组件滑动至顶部或底部时，外部组件能够接替滑动。


```

```TypeScript
### 示例2（嵌套场景下拦截内部容器手势）

本示例通过将参数exposeInnerGesture设置为true，实现了一级Tabs容器在嵌套二级Tabs的场景下，能够屏蔽二级Tabs内置Swiper的滑动手势，从而触发一级Tabs内置Swiper滑动手势的功能。

开发者自行定义变量记录内层Tabs的索引值，并通过该索引值判断滑动是否达到内层Tabs的边界。达到边界时，触发回调返回拒绝结果，屏蔽内层Tabs的滑动手势，使外层Tabs产生滑动手势。


```

```TypeScript
### 示例3（拦截手势获取属性）

该示例通过配置onGestureRecognizerJudgeBegin判定手势，获取手势的距离、手指数、是否限制手指数、重复触发状态、持续时间、点击次数、旋转角度、滑动方向和速度阈值等属性参数。


```

```TypeScript
### 示例4（手势触发成功时取消子组件上的Touch事件）

该示例通过配置onGestureRecognizerJudgeBegin判定手势，在父容器手势触发成功时，调用cancelTouch()强制取消子组件上的Touch事件，实现父子组件手势控制的精准切换。


```

```TypeScript
### 示例5（自定义手势识别器是否参与手势处理）

从API version 20开始，该示例通过配置[onTouchTestDone](arkts-arkui-commonmethod-c.md#ontouchtestdone)指定手势识别器不参与后续手势处理，触发回调时，调用[preventBegin](./ts-gesture-common.md#preventbegin20)阻止手势识别器参与后续处理。点击Tap2和Tap1的重合区域，不调用preventBegin时，触发Tap2对应的手势；调用preventBegin阻止Tap2时，触发Tap1对应的手势。


```

```TypeScript
### 示例6（自定义干预事件和手势的收集结果）

该示例通过配置[onGestureCollectIntercept](arkts-arkui-commonmethod-c.md#ongesturecollectintercept)指定手势识别器或者触摸识别器是否透传到其他节点。点击button2时，不透传触摸事件到Column。点击button1时，透传触摸事件到Column，Column变色。

从API版本26.0.0开始，新增onGestureCollectIntercept接口。
```

```TypeScript


示例对应的组件树如下图所示。
```

```TypeScript
### 示例7（非内置手势嵌套滚动）

该示例通过[shouldRecognizerParallelWith](arkts-arkui-commonmethod-c.md#shouldrecognizerparallelwith)和[onGestureRecognizerJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturerecognizerjudgebegin)实现了嵌套滚动的功能。内部组件优先响应滑动手势，当内部组件滑动至顶部或底部时，外部组件能够接替滑动。

从API版本26.0.0开始，新增shouldRecognizerParallelWith接口。
```

```TypeScript
### 示例1（设置跟手变形拖拽动画）

该示例通过设置[dragAnimationType](#cursorcontrol)为FOLLOW_HAND_MORPH实现跟手变形拖拽动画效果，并在拖拽结束时通过[executeFollowHandMorphDropAnimation](arkts-arkui-dragevent-i-sys.md#executefollowhandmorphdropanimation)执行自定义落位动效。

从API版本26.0.0开始，新增[dragAnimationType](#cursorcontrol)属性、[executeFollowHandMorphDropAnimation](arkts-arkui-dragevent-i-sys.md#executefollowhandmorphdropanimation)方法、[interruptFollowHandMorphDropAnimation](../arkts-apis/arkts-arkui-arkui-uicontext-dragcontroller-c-sys.md#interruptfollowhandmorphdropanimation)方法。
```

```TypeScript
### 示例1（获取触摸事件相关参数）

该示例中，按钮设置触摸事件，在点击按钮时可获取事件的相关参数。


```

```TypeScript
### 示例2（获取组件实时位置）

该示例通过[getCurrentLocalPosition](#getcurrentlocalposition)方法获取触摸位置相对于当前组件实时位置左上角的坐标。

从API版本26.0.0开始，新增支持getCurrentLocalPosition接口。
```

```TypeScript
### 示例1（颜色线性渐变）

该示例通过[linearGradient](#lineargradient)来实现组件的颜色线性渐变。


```

```TypeScript
### 示例2（颜色按旋转角度渐变）

该示例通过[sweepGradient](arkts-arkui-commonmethod-c.md#sweepgradient)来实现组件颜色旋转角度渐变。


```

```TypeScript
### 示例3（颜色按径向渐变）

该示例通过[radialGradient](arkts-arkui-commonmethod-c.md#radialgradient)来实现组件颜色径向渐变。
```

```TypeScript
@Entry
@ComponentV2
struct Index {
  build() {
    Column() {
      ReusableV2Component()
        .reuse({reuseId: () => 'reuseComponent'}) // 使用'reuseComponent'作为reuseId
      ReusableV2Component()
        .reuse({reuseId: () => ''}) // 使用空字符串将默认使用组件名'ReusableV2Component'作为reuseId
      ReusableV2Component() // 未指定reuseId将默认使用组件名'ReusableV2Component'作为reuseId
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  build() {
    Text('content')
  }
}
```

```TypeScript
### 示例1（通过string设置浮层）

该示例通过传入string设置浮层。


```

```TypeScript
### 示例2（通过builder设置浮层）

该示例通过传入builder设置浮层。


```

```TypeScript
### 示例3（通过ComponentContent设置浮层）

该示例通过overlay传入ComponentContent，并通过update方法更新ComponentContent参数，使backgroundColor不断发生变化。
```

```TypeScript
### 示例1（在组件出现时创建动画）

> 说明：
> 
> 直接使用animateTo可能导致[UI上下文不明确](../../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](../arkts-apis-uicontext-uicontext.md)实例，并使用[animateTo](../arkts-apis-uicontext-uicontext.md#animateto)调用绑定实例的animateTo。

该示例通过在onAppear方法中创建组件出现时的动画效果。


```

```TypeScript
### 示例2（动画执行结束后组件消失）

该示例主要演示如何实现在动画执行结束后组件消失。
```

```TypeScript
通过配置flexBasis/flexGrow/flexShrink/alignSelf属性设置Flex布局。
```

```TypeScript
### 示例1（设置图片不同属性效果）

设置图片的效果，包括阴影、灰度、高光、饱和度、对比度、图像反转、叠色、色相旋转等。


```

```TypeScript
### 示例2（设置组件线性渐变模糊效果）

该示例主要演示通过[linearGradientBlur](arkts-arkui-commonmethod-c.md#lineargradientblur)设置组件的内容线性渐变模糊效果。


```

```TypeScript
### 示例3（设置离屏渲染效果）

该示例主要演示通过[renderGroup](arkts-arkui-commonmethod-c.md#rendergroup)来设置组件是否先整体离屏渲染绘制后，再与父组件融合绘制。


```

```TypeScript
### 示例4（当前组件内容与下方画布内容混合）

该示例主要演示通过[blendMode](#blendmode11)将当前组件内容与下方画布内容混合。


```

```TypeScript
### 示例5（前景智能取反色）

该示例主要通过[InvertOptions](#invertoptions11对象说明)来实现前景智能取反色。


```

```TypeScript
### 示例6（设置同层阴影不重叠效果）

该示例主要通过[useShadowBatching](arkts-arkui-commonmethod-c.md#useshadowbatching)搭配[shadow](#shadow)实现同层阴影不重叠效果。


```

```TypeScript
### 示例7（设置组件图像球面效果）

该示例主要演示通过[sphericalEffect](arkts-arkui-commonmethod-c.md#sphericaleffect)设置组件的图像球面效果。

效果图如下：



去掉sphericalEffect的设置，效果如下：


```

```TypeScript
### 示例8（设置组件图像渐亮效果）

该示例主要演示通过[lightUpEffect](arkts-arkui-commonmethod-c.md#lightupeffect)设置组件的图像渐亮效果。

效果图如下：



修改lightUpEffect参数值为0.2：



去掉lightUpEffect的设置，效果如下：


```

```TypeScript
### 示例9（设置组件图像边缘像素扩展效果）

该示例主要演示通过[pixelStretchEffect](arkts-arkui-commonmethod-c.md#pixelstretcheffect)设置组件的图像边缘像素扩展效果。

效果图如下：



去掉pixelStretchEffect的设置，原图效果如下：


```

```TypeScript
### 示例10（系统导航条智能反色）

该示例主要演示通过[systemBarEffect](arkts-arkui-commonmethod-c.md#systembareffect)来实现系统导航条智能反色。

效果图如下：


```

```TypeScript
### 示例11（设置组件是否双面绘制）

该示例主要演示通过[doubleSided](arkts-arkui-commonmethod-c.md#doublesided)来设置组件是否双面绘制。

从API版本26.0.0开始，新增doubleSided方法。
```

```TypeScript
通过ContentModifier实现自定义复选框样式的功能，用一个五边形复选框替换原本Checkbox的样式。如果选中，内部会出现红色三角图案，标题会显示选中字样；如果取消选中，红色三角图案消失，标题会显示非选中字样。
```

```TypeScript
// 组件添加allowForceDark(false)属性后，说明对当前组件及其所有子组件均不使用反色相关能力。
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Column() {
        Text("Hello World")
          .fontSize(20)
          .fontColor(Color.Blue)
          .onClick(() => {
            console.info(`Text is clicked`);
          })
      }
      .allowForceDark(false) // Column及其子组件Text不使用反色能力，不受父组件Column使用反色能力的影响。

      Row() {
        Button('BUTTON')
          .backgroundColor(Color.Grey)
          .allowForceDark(true)
          .onClick(() => {
            console.info(`Button is clicked`);
          })
      }
      .allowForceDark(false) // Row及其子组件Button不使用反色能力，不受父组件Column使用反色能力的影响。
    }
    .allowForceDark(true)
    .width('100%')
    .height('100%')
  }
}
```

```TypeScript
该示例演示如何通过配置monopolizeEvents设置组件是否独占事件。
```

```TypeScript
### 示例1（设置组件拖拽和落入）

示例1展示了部分组件（如Image和Text等）拖拽和可落入区域的设置。


```

```TypeScript
### 示例2（自定义落位动效）

从API version 18开始，示例2展示了通过[executeDropAnimation](arkts-arkui-dragevent-i.md#executedropanimation)接口，实现自定义落位动效。


```

```TypeScript
### 示例3（拖拽异步获取数据）

从API version 15开始，示例3展示了通过[startDataLoading](arkts-arkui-dragevent-i.md#startdataloading)实现拖拽异步获取数据。
```

```TypeScript
### 示例4（获取当前拖拽的屏幕ID）

从API version 20开始，示例4展示了通过onDragXXX（不支持onDragEnd）接口获取拖拽事件，并调用拖拽事件的[getDisplayId](#getdisplayid20)接口获取屏幕ID。


```

```TypeScript
### 示例5（获取包名和是否是跨设备）

从API version 20开始，示例5展示了通过onDragXXX接口获取拖拽事件，调用拖拽事件的[getDragSource](arkts-arkui-dragevent-i.md#getdragsource)接口获取包名，调用isRemote接口判断是否为跨设备拖拽。


```

```TypeScript
### 示例6（拖拽支持悬停检测）

从API version 20开始，示例6展示了通过[onDragSpringLoading](arkts-arkui-commonmethod-c.md#ondragspringloading)接口注册回调，并通过回调中的[SpringLoadingContext](#springloadingcontext20)获取上下文信息（当前状态、通知序列）。


```

```TypeScript
### 示例7（拖起方延迟提供数据）

从API version 20开始，示例7展示了在[onDragStart](#ondragstart)中调用[setDataLoadParams](arkts-arkui-dragevent-i.md#setdataloadparams)延迟提供数据接口，并在[onDrop](#ondrop)中调用[startDataLoading](arkts-arkui-dragevent-i.md#startdataloading)异步获取数据接口。


```

```TypeScript
### 示例8（拖拽自动隐藏指定组件）

该示例通过DragEvent的[autoHideComponentUniqueIds](#cursorcontrol)属性，在拖拽成功发起后自动隐藏指定组件。

从API版本26.0.0开始，DragEvent新增autoHideComponentUniqueIds属性。
```

```TypeScript
### 示例1（自定义布局代码示例）

自定义布局代码示例。


```

```TypeScript
### 示例2（判断是否参与布局计算）

通过组件的位置灵活判断是否参与布局计算。


```

```TypeScript
### 示例3（获取子组件FrameNode并设置相关属性）

通过uniqueId获取子组件的FrameNode，并调用FrameNode的API接口修改尺寸、背景颜色。


```

```TypeScript
### 示例4（子组件超过父组件大小约束）

在自定义布局的自定义组件中，为子组件设置了[LayoutPolicy](./ts-universal-attributes-size.md#layoutpolicy15)对象的fixAtIdealSize属性。
```
