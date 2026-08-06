# OnVisibleIndexesChangeCallback

```TypeScript
declare type OnVisibleIndexesChangeCallback = (start: int, end: int) => void
```

懒加载布局容器\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_、 [LazyVGridLayout]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_、 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_所显示的子组件索引发生变化时的回调 类型。 > **说明：** > > - 当懒加载布局容器没有子组件时，start和end都返回-1。 > > - 当懒加载布局容器在可视区域内无子组件时，start和end都返回-1。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnVisibleIndexesChangeCallback = (start: int, end: int) => void--><!--Device-unnamed-declare type OnVisibleIndexesChangeCallback = (start: int, end: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 可视区域起始位置的索引值。\_\_\_HTML\_TAG\_USD\_0\_\_\_取值范围：[0, 子节点总数-1]，当没有子节点或所有子节点都在可视区域外时，返回-1。  |
| end | int | 是 | 可视区域终止位置的索引值。\_\_\_HTML\_TAG\_USD\_0\_\_\_取值范围：[0, 子节点总数-1]，当没有子节点或所有子节点都在可视区域外时，返回-1。  |

