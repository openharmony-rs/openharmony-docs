# LayerMask

定义节点的图层掩码.

**起始版本：** 12

<!--Device-unnamed-export interface LayerMask--><!--Device-unnamed-export interface LayerMask-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getEnabled

```TypeScript
getEnabled(index: number): boolean
```

获取图层掩码是否启用.

**起始版本：** 12

<!--Device-LayerMask-getEnabled(index: int): boolean--><!--Device-LayerMask-getEnabled(index: int): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 图层掩码 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 图层掩码是否启用 |

## setEnabled

```TypeScript
setEnabled(index: number, enabled: boolean): void
```

设置图层掩码是否启用.

**起始版本：** 12

<!--Device-LayerMask-setEnabled(index: int, enabled: boolean): void--><!--Device-LayerMask-setEnabled(index: int, enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 图层掩码 |
| enabled | boolean | 是 | 图层掩码是否启用 |

