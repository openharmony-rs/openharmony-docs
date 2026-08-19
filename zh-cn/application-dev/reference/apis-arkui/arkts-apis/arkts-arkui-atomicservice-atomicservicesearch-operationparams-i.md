# OperationParams

AtomicServiceSearch中“功能区”的初始化参数。

**起始版本：** 18

<!--Device-unnamed-export interface OperationParams--><!--Device-unnamed-export interface OperationParams-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## auxiliaryItem

```TypeScript
auxiliaryItem?: OperationOption
```

附属于搜索区（右侧）的功能位。默认值为`undefined`。

**类型：** [OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-OperationParams-auxiliaryItem?: OperationOption--><!--Device-OperationParams-auxiliaryItem?: OperationOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## independentItem

```TypeScript
independentItem?: OperationOption
```

独立于搜索区（右侧）的功能位。默认值为`undefined`。

**类型：** [OperationOption](arkts-arkui-arkui-advanced-subheader-operationoption-c.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-OperationParams-independentItem?: OperationOption--><!--Device-OperationParams-independentItem?: OperationOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

