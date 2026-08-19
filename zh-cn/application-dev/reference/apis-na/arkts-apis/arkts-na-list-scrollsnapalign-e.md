# ScrollSnapAlign

设置列表项滚动结束对齐效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ScrollSnapAlign--><!--Device-unnamed-export declare enum ScrollSnapAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

默认无项目滚动对齐效果。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapAlign-NONE = 0--><!--Device-ScrollSnapAlign-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## START

```TypeScript
START = 1
```

视图中的第一项将在列表的开头对齐。 &lt;p&gt;&lt;strong&gt;说明&lt;/strong&gt; <br>当列表位移至末端，需要将末端的item完整显示，可能出现开头不对齐的情况。 &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapAlign-START = 1--><!--Device-ScrollSnapAlign-START = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CENTER

```TypeScript
CENTER = 2
```

视图中的中间项将在列表中心对齐。 &lt;p&gt;&lt;strong&gt;说明&lt;/strong&gt; <br>顶端和末尾的item都可以在列表中心对齐，列表显示可能露出空白。 &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapAlign-CENTER = 2--><!--Device-ScrollSnapAlign-CENTER = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 3
```

视图中的最后一项将在列表末尾对齐。 &lt;p&gt;&lt;strong&gt;说明&lt;/strong&gt; <br>当列表位移至顶端，需要将顶端的item完整显示，可能出现末尾不对齐的情况。 &lt;/p&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ScrollSnapAlign-END = 3--><!--Device-ScrollSnapAlign-END = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

