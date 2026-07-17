# RenderSort

渲染排序层。在渲染槽中，层可以定义排序层顺序。可用值为0-63（0最先，63最后）。默认id值为32。典型用法：1. 将渲染排序层设置为对使用深度测试但未写入深度的对象进行渲染。2. 始终首先渲染角色和/或相机对象以剔除大部分视图。3. 对平面层进行排序。

**起始版本：** 20

<!--Device-unnamed-export interface RenderSort--><!--Device-unnamed-export interface RenderSort-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderSortLayer

```TypeScript
renderSortLayer?: number
```

用于在渲染槽中对子网格进行排序的排序层.有效值为0-63.

**类型：** number

**默认值：** 32 默认渲染排序层id。

**起始版本：** 20

<!--Device-RenderSort-renderSortLayer?: int--><!--Device-RenderSort-renderSortLayer?: int-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## renderSortLayerOrder

```TypeScript
renderSortLayerOrder?: number
```

排序层内描述精细顺序的排序层顺序.有效值为0-255.

**类型：** number

**默认值：** 0 默认渲染排序层顺序。

**起始版本：** 20

<!--Device-RenderSort-renderSortLayerOrder?: int--><!--Device-RenderSort-renderSortLayerOrder?: int-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

