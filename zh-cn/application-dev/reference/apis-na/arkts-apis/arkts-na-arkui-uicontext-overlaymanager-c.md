# OverlayManager

提供绘制浮层的能力。 > **说明：** > > - 本Class首批接口从API version 12开始支持。 > - 以下API需先使用UIContext中的[getOverlayManager()](arkts-na-arkui-uicontext-uicontext-c.md#getoverlaymanager)方法获取到 > OverlayManager对象，再通过该对象调用对应方法。 > > - OverlayManager上节点的层级在Page页面层级之上，在Dialog、Popup、Menu、BindSheet、BindContentCover和Toast等之下。 > > - OverlayManager上节点安全区域内外的绘制方式与Page一致，键盘避让方式与Page一致。 > > - 与OverlayManager相关的属性推荐采用AppStorage来进行应用全局存储，以免切换页面后属性值发生变化从而导致业务错误。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class OverlayManager--><!--Device-unnamed-export declare class OverlayManager-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## addComponentContent

```TypeScript
addComponentContent<T>(content: ComponentContent<T>, index?: int): void
```

在OverlayManager上新增指定节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManager-addComponentContent<T>(content: ComponentContent<T>, index?: int): void--><!--Device-OverlayManager-addComponentContent<T>(content: ComponentContent<T>, index?: int): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | 在OverlayManager的指定节点上添加此content。 <br>**说明：** <br/> 新增的节点默认处于页面居中，按层级堆叠。 |
| index | int | 否 |  |

## addComponentContentWithOrder

```TypeScript
addComponentContentWithOrder<T>(content: ComponentContent<T>, levelOrder?: LevelOrder): void
```

创建浮层节点时，指定显示顺序。 支持在浮层节点创建时指定显示的顺序。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManager-addComponentContentWithOrder<T>(content: ComponentContent<T>, levelOrder?: LevelOrder): void--><!--Device-OverlayManager-addComponentContentWithOrder<T>(content: ComponentContent<T>, levelOrder?: LevelOrder): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | 在OverlayManager的指定节点上添加此content。 <br>**说明：** <br/> 新增的节点默认处于页面居中位置，按层级堆叠。 |
| levelOrder | [LevelOrder](arkts-na-promptaction-levelorder-c.md) | 否 |  |

## hideAllComponentContents

```TypeScript
hideAllComponentContents(): void
```

隐藏OverlayManager上的所有ComponentContent。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManager-hideAllComponentContents(): void--><!--Device-OverlayManager-hideAllComponentContents(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hideComponentContent

```TypeScript
hideComponentContent<T>(content: ComponentContent<T>): void
```

隐藏OverlayManager上的指定节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManager-hideComponentContent<T>(content: ComponentContent<T>): void--><!--Device-OverlayManager-hideComponentContent<T>(content: ComponentContent<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | 在OverlayManager上隐藏此content。 |

## openOrderOverlay

```TypeScript
openOrderOverlay(content: ComponentContent<Object>, options?: OrderOverlayOptions): Promise<void>
```

打开具有指定ComponentContent和选项的浮层。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManager-openOrderOverlay(content: ComponentContent<Object>, options?: OrderOverlayOptions): Promise<void>--><!--Device-OverlayManager-openOrderOverlay(content: ComponentContent<Object>, options?: OrderOverlayOptions): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;Object&gt; | 是 | 该内容将被添加到OverlayManager中。 |
| options | [OrderOverlayOptions](arkts-na-arkui-uicontext-orderoverlayoptions-i.md) | 否 | Options for the overlay. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103307](../../apis-arkui/errorcode-promptAction.md#103307-系统弹出窗口导致无法打开浮层) | The overlay cannot be opened due to the system pop-up window. |

## removeComponentContent

```TypeScript
removeComponentContent<T>(content: ComponentContent<T>): void
```

删除overlay上的指定节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManager-removeComponentContent<T>(content: ComponentContent<T>): void--><!--Device-OverlayManager-removeComponentContent<T>(content: ComponentContent<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | 在OverlayManager上删除此content。 |

## showAllComponentContents

```TypeScript
showAllComponentContents(): void
```

显示OverlayManager上所有的ComponentContent。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManager-showAllComponentContents(): void--><!--Device-OverlayManager-showAllComponentContents(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showComponentContent

```TypeScript
showComponentContent<T>(content: ComponentContent<T>): void
```

在OverlayManager上显示指定节点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OverlayManager-showComponentContent<T>(content: ComponentContent<T>): void--><!--Device-OverlayManager-showComponentContent<T>(content: ComponentContent<T>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | 在OverlayManager上显示此content。 |

