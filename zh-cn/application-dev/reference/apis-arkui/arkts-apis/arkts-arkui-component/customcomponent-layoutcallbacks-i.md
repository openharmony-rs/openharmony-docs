# LayoutCallbacks

Defining interface of LayoutCallbacks for custom component, when decorate with @Layoutable.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface LayoutCallbacks {  /**   * Custom component override this method to layout each of its sub components.   *   *******/  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void--><!--Device-unnamed-export interface LayoutCallbacks {  /**   * Custom component override this method to layout each of its sub components.   *   *******/  onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onPlaceChildren

```TypeScript
onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void
```

Custom component override this method to layout each of its sub components.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LayoutCallbacks-onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void--><!--Device-LayoutCallbacks-onPlaceChildren(selfLayoutInfo: GeometryInfo, children: Array<Layoutable>, constraint: ConstraintSizeOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selfLayoutInfo | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |
| children | Array&lt;\_\_\_MD\_LINK\_USD\_0\_\_\_&gt; | 是 |  |
| constraint | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 |  |

