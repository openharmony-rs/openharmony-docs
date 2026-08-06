# LayerMask

定义节点的图层掩码.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface LayerMask--><!--Device-unnamed-export interface LayerMask-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getEnabled

ArkTS-Dyn:
```TypeScript
getEnabled(index: number): boolean
```

ArkTS-Sta:
```TypeScript
getEnabled(index: int): boolean
```

获取图层掩码是否启用.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-LayerMask-getEnabled(index: int): boolean--><!--Device-LayerMask-getEnabled(index: int): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 图层掩码 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 图层掩码是否启用 |

## setEnabled

ArkTS-Dyn:
```TypeScript
setEnabled(index: number, enabled: boolean): void
```

ArkTS-Sta:
```TypeScript
setEnabled(index: int, enabled: boolean): void
```

设置图层掩码是否启用.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-LayerMask-setEnabled(index: int, enabled: boolean): void--><!--Device-LayerMask-setEnabled(index: int, enabled: boolean): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 图层掩码 |
| enabled | boolean | 是 | 图层掩码是否启用 |

