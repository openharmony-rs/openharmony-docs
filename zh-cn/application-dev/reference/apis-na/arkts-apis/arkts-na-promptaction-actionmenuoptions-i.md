# ActionMenuOptions

操作菜单的选项。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-promptAction-export interface ActionMenuOptions--><!--Device-promptAction-export interface ActionMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## buttons

```TypeScript
buttons: PromptActionSingleButton | PromptActionDoubleButtons | PromptActionTripleButtons |
            PromptActionQuadrupleButtons | PromptActionQuintupleButtons | PromptActionSextupleButtons
```

菜单中菜单项按钮的数组，结构为： {text:'button', color: '#666666'}. 支持1-6个按钮。按钮数量大于6个时，仅显示前6个按钮，之后的按钮不显示。

**类型：** [PromptActionSingleButton](arkts-na-promptaction-promptactionsinglebutton-t.md) \| [PromptActionDoubleButtons](arkts-na-promptaction-promptactiondoublebuttons-t.md) \| [PromptActionTripleButtons](arkts-na-promptaction-promptactiontriplebuttons-t.md) \| [PromptActionQuadrupleButtons](arkts-na-promptaction-promptactionquadruplebuttons-t.md) \| [PromptActionQuintupleButtons](arkts-na-promptaction-promptactionquintuplebuttons-t.md) \| [PromptActionSextupleButtons](arkts-na-promptaction-promptactionsextuplebuttons-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-buttons: PromptActionSingleButton | PromptActionDoubleButtons | PromptActionTripleButtons |            PromptActionQuadrupleButtons | PromptActionQuintupleButtons | PromptActionSextupleButtons--><!--Device-ActionMenuOptions-buttons: PromptActionSingleButton | PromptActionDoubleButtons | PromptActionTripleButtons |            PromptActionQuadrupleButtons | PromptActionQuintupleButtons | PromptActionSextupleButtons-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## immersiveMode

```TypeScript
immersiveMode?: ImmersiveMode
```

设置页面内菜单蒙层效果。&lt;br /&gt;**说明：**&lt;br /&gt;- 默认值：ImmersiveMode.DEFAULT &lt;br /&gt;- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。

**类型：** [ImmersiveMode](arkts-na-promptaction-immersivemode-e.md)

**默认值：** ImmersiveMode.DEFAULT

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-immersiveMode?: ImmersiveMode--><!--Device-ActionMenuOptions-immersiveMode?: ImmersiveMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isModal

```TypeScript
isModal?: boolean
```

菜单是否为模态窗口。值为true表示为模态窗口且有蒙层，不可与菜单周围其他控件进行交互，即蒙层区域无法事件透传。 值为false表示为非模态窗口且无蒙层，可以与菜单周围其他控件进行交互。<br/>默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-isModal?: boolean--><!--Device-ActionMenuOptions-isModal?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

设置菜单显示层级。&lt;br /&gt;**说明：**&lt;br /&gt;- 默认值：LevelMode.OVERLAY &lt;br /&gt;- 当且仅当showInSubWindow属性设置为false时生效。

**类型：** [LevelMode](arkts-na-promptaction-levelmode-e.md)

**默认值：** LevelMode.OVERLAY

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-levelMode?: LevelMode--><!--Device-ActionMenuOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelUniqueId

```TypeScript
levelUniqueId?: int
```

设置页面级菜单需要显示的层级下的节点UniqueID，该ID可以通过[getUniqueId](../../apis-arkui/arkts-apis/arkts-arkui-framenode-c.md#getuniqueid)获取。 取值范围：大于等于0的数字。&lt;br /&gt;**说明：**<br/>- 当且仅当levelMode属性设置为LevelMode.EMBEDDED时生效。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-levelUniqueId?: int--><!--Device-ActionMenuOptions-levelUniqueId?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidAppear

```TypeScript
onDidAppear?: VoidCallback
```

菜单弹出后的事件回调。&lt;br /&gt;**说明：**&lt;br /&gt;1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。 &lt;br /&gt;2.快速点击弹出，关闭菜单时，onWillDisappear在onDidAppear前生效。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-onDidAppear?: VoidCallback--><!--Device-ActionMenuOptions-onDidAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidDisappear

```TypeScript
onDidDisappear?: VoidCallback
```

菜单消失后的事件回调。&lt;br /&gt;**说明：**&lt;br /&gt;1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-onDidDisappear?: VoidCallback--><!--Device-ActionMenuOptions-onDidDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillAppear

```TypeScript
onWillAppear?: VoidCallback
```

菜单显示动效前的事件回调。&lt;br /&gt;**说明：**&lt;br /&gt;1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-onWillAppear?: VoidCallback--><!--Device-ActionMenuOptions-onWillAppear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDisappear

```TypeScript
onWillDisappear?: VoidCallback
```

菜单退出动效前的事件回调。&lt;br /&gt;**说明：**&lt;br /&gt;1.正常时序依次为：onWillAppear>>onDidAppear>>onWillDisappear>>onDidDisappear。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-onWillDisappear?: VoidCallback--><!--Device-ActionMenuOptions-onWillDisappear?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

某操作菜单需要显示在主窗口之外时，是否在子窗口显示此菜单。值为true表示在子窗口显示菜单。 默认值：false，在子窗口不显示菜单。 **说明：** - showInSubWindow为true的菜单无法触发显示另一个showInSubWindow为true的菜单。 - 若在UIExtension中设置showInSubWindow为true, 菜单将基于UIExtension的宿主窗口对齐。

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-showInSubWindow?: boolean--><!--Device-ActionMenuOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: uiMaterial.Material
```

设置弹窗的系统材质。<br/>默认值：ImmersiveOptions的style为ImmersiveStyle.ULTRA_THICK的ImmersiveMaterial对象。 设置undefined时与默认值保持一致。不同的材质具有不同的效果，可以影响弹窗的背景色、边框、阴影等视觉属性。

**类型：** uiMaterial.Material

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-systemMaterial?: uiMaterial.Material--><!--Device-ActionMenuOptions-systemMaterial?: uiMaterial.Material-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string | Resource
```

标题文本。<br/>默认值：undefined，取值为undefined默认不显示标题。

**类型：** string \| Resource

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionMenuOptions-title?: string | Resource--><!--Device-ActionMenuOptions-title?: string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

